Software Transactional Memory (STM) with HW-Acceleration
===

EE382N Parallel Computer Architecture, 2013 Spring
University of Texas at Austin
Course Project

In this project, we ask a fundamental question: when to choose between transactional memory and locks? Our intuition is that it is better to stall a thread if a transaction is doomed to being aborted in future.

We propose a two-level prediction scheme that predicts if a transaction will be aborted in future. This allows dynamic adaption between transactional memory and locks during runtime.

The first level prediction is based on (coarse-grained) abort ratio. If the abort ratio is low, we always allow the thread to enter the transaction for speculative execition.  The second level prediction keeps track of (fine-grained) pairwise conflict history. If two transactions conflict before, they are very likely to conflict in the future, and therefore one has to wait until the other exists the transaction before it can enter.

We implement our algorithm in RSTM. We are able to achieve 17.2% performance improvement on STAMP benchmark over LLT for applications with high contention rate. We also design and evaluate potential hardware implementation of our algorithm. CACTI modeling results show that it is feasible to finish prediction in one cycle.

Report: https://github.com/poolmaster/stm/blob/master/ParallelArchReport.pdf
