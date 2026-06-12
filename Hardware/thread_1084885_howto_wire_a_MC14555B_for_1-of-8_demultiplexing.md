---
title: "howto wire a MC14555B for 1-of-8 demultiplexing?"
date: 2009-03-02
forum: Hardware
---

### Post by c174 on 2009-03-02
Hello!

I am working on a little electronics project, which is supposed to end up as a checkerboard that I can connect to the parallel port of my computer and then play against Arasan (or another chess program).

Each square on the board will have a switch, so I can move a piece by pressing down on the current position and then on the new position.

In order to scan each of the 64 squares I want to use a counter. The first three bits (b0, b1, b2) will be demultiplexed into one the the 8 rows (which then becomes electrically high), and the next three bits (b3, b4, b5) will be used to scan a column (using a multiplexer).

Now my question is: I have a MC14555B which is a Dual Binary to 1-of-4 Decoder/Demultiplexer. On the data-sheet it says that the circuit is *expandable*. The problem is I simply can't figure out how to connect the bits from the binary counter to get 1-of-8 demultiplexing?? Can it be done without adding extra external logic? :confused:

The thruth table looks like (there are two sets of pins of the chip)
Enable   B   A   Q3  Q2  Q1  Q0
0        0   0    0   0   0   1
0        0   1    0   0   1   0
0        1   0    0   1   0   0
0        1   1    1   0   0   0
1        X   X    0   0   0   0 (X=don't care)

Maybe I just need to buy another demultiplexer chip. I know this post might be a little outside the scope of this forum, but I'm a novice with electronics and don't know where else to ask... If anybody can guide me along the way I would be very happy.

---

