---
title: "Fluxbox and slit first time compiling"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Shininggg on 2009-03-07
I just switched to Fluxbox and i'm trying to get the bubblemon-dockapp-1.4 working 

i never compiled anything from source so the error might be really stupid 
the install read me stated 

1. read README

2. make (on FreeBSD, make -f Makefile.FreeBSD)

3. make install (this will put bubblemon in /usr/local/bin)

4. bubblemon &

here's the output for "make"

bubblemon.c:675: error: ‘BubbleMonData’ has no member named ‘waterlevels’

bubblemon.c:675: error: incompatible types in assignment

bubblemon.c:675: warning: statement with no effect

bubblemon.c:679: error: ‘BubbleMonData’ has no member named ‘waterlevels_dy’

bubblemon.c:680: error: ‘BubbleMonData’ has no member named ‘waterlevels’

bubblemon.c:680: error: ‘BubbleMonData’ has no member named ‘waterlevels’

bubblemon.c:680: error: invalid operands to binary +

bubblemon.c:681: error: ‘BubbleMonData’ has no member named ‘waterlevels’

bubblemon.c:681: error: invalid operands to binary *

bubblemon.c:681: error: ‘BubbleMonData’ has no member named ‘volatility_int’

bubblemon.c:681: error: invalid operands to binary *

bubblemon.c:682: error: invalid operands to binary >>

bubblemon.c:682: error: invalid operands to binary +

bubblemon.c:682: warning: statement with no effect

bubblemon.c:684: error: ‘BubbleMonData’ has no member named ‘waterlevels_dy’

bubblemon.c:684: error: ‘BubbleMonData’ has no member named ‘viscosity_int’

bubblemon.c:684: error: invalid operands to binary *


i'm not gonna post the entire log because it's the same error repeating over and over 

i'm guessing there's a c library missing?

thx for your help

---

