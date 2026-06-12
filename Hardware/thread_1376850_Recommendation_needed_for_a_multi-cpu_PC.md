---
title: "Recommendation needed for a multi-cpu PC"
date: 2010-01-09
forum: Hardware
---

### Post by W00ster on 2010-01-09
Hi all!

I've been doing some research trying to locate some PC's with motherboards allowing me to have at least 4 physical CPU's installed and at least 16GB of RAM. Preferably with some high end CPU's like Intel i7 but I have no emotional attachment to any specific manufacturer.

It's not much if any information to be found anywhere so if there are any forum members who have some good suggestions, I'm all ears. Even better if someone have practical experiences or can point me to sites with more information.

---

### Post by moe_syzlak on 2010-01-09
You need to get a server board. And, I think such a set-up, for the board alone, will cost you lots of $$$$$. I'm just curious, what are you going to do with "all dat powa?"

---

### Post by cascade9 on 2010-01-10
Supermicro or Tyan. 

Be warned, everything I've ever seen in quad CPU needs registered, buffered or ECC ram (lots more expensive and slightly slower than 'normal' ram). You also looking at EATX cases (harder to find, more expensive). 

I used to know a few websites on the net that were into server setups, but they appear to be quite outdated now. Since multi-core CPUs came out, less and less people are even interested in dual/quad CPU setups. 

You may find it cheaper....much cheaper....to get 4x 'normal' computers than 1x4CPU server setup. Even large retailers like newegg only have dual CPU boards on sale, you'll be looking at some specialist retailer, and they always charge more $$$. 

See here- 

[http://www.buy.com/prod/supermicro-x7qc3-server-board-intel-socket-604-1066-mhz-fsb-192-gb/q/loc/101/205809323.html](http://www.buy.com/prod/supermicro-x7qc3-server-board-intel-socket-604-1066-mhz-fsb-192-gb/q/loc/101/205809323.html)

Thats $1000 US, just for the motherboard. That is FC-PGA socket as well which is quite old, newer stuff will be even more expensive.....

---

### Post by W00ster on 2010-01-10
Thank you both for the answers.

Money is not really the issue here, finding the right hardware is.

Setting up multiple PC's is not an option either as I need as multi cpu environment. Why? To run numerous different Oracle RDBMS releases, many to be used in testcases were the problems may be related to NUMA and CPU partitioning etc and I need to be able to run some tests at home rather than to acquire a test server and set up the testcase remotely.

Also so I can set up and test dedicating cores and CPU's to certain tasks etc.

Graphics is not an issue here, CPU power basically is for me the issue.

---

