Loom
========

Loom is a set of CRDT's that are designed to compose and maintain their CRDT
properties. They are also designed to be extensible with whatever domain logic
that you want to add in.

One of the primary goals of this project is to create a javascript CRDT library
so that fully offline apps can sync their data-structures simply without having
to worry about conflicts and updates. You can use any transport mechanism you
want, and just send the same updates over and over again, and because CRDT's
contain causal history, all updates are idempotent and commutative. Basically,
You will get the same value no matter how you apply them or in what order you
apply updates).

Loom is not ready for production use. It may be ready soon. Most of the hard
in implementing CRDT's comes from understanding the academic literature, rather
thank anything too logically or algorithmically complicated. Writing adequate
tests is also be a challenge, but that should be address soon with a property
test suite which will test for datatype invariants.

## δ-CRDT's ##

In order to combat issues with large objects, δ-CRDT's are supported for some
datatypes. δ-CRDT's will return a two-tuple when updated, and the delta can be
joined with other deltas as a single-object "buffer" for periodic updates. As a
convenience, most δ-CRDT's will take a 2-tuple of primary state and a current
delta. It will update the delta for you as well as the primary object. In
Elixir, this means that you can simply pipe the return value around to other
update functions until you want to do something else with the object.

## What the heck is a CRDT? ##
Conflict-free, Coordination-free, Commutative, or Convergent datatypes, CRDT's
are usually formally described as "join semi-lattices". Mathematical jargon
aside, CRDT's track causality for modifications to your data. Because of this,
time becomes less relevant, and coordination becomes unnecessary to get accurate
values for your data.

## Can you give me an example of one? ##
I will have a simple explanation here for a basic gcounter and a pncounter.

For now, I can simply point you to the GCounter code in here.

## Where can I learn more? ##
1. Strong Eventual Consistency and Conflict-free Replicated Data Types
 - A good introduction to the concept of CRDTs: http://research.microsoft.com/apps/video/default.aspx?id=153540&r=1
1. A comprehensive study of Convergent and Commutative Replicated Data Types
 - A survey with references for several popular CRDTs: http://hal.inria.fr/docs/00/55/55/88/PDF/techreport.pdf
2. Efficient State-based CRDTs by Delta-Mutation
 - Talk: https://www.youtube.com/watch?v=y_ewFP-lgyM
 - Paper: http://arxiv.org/pdf/1410.2803v1.pdf