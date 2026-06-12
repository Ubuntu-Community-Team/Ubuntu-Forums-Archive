---
title: "Serial ports, anybody know how to identify which is which?"
date: 2011-10-16
forum: Hardware
---

### Post by KeithLM on 2011-10-16
I just installed a 4 port serial card in my system for a little project I have coming up.  I'm wondering if anybody can tell me off hand how I can determine which port is which.  I know that they are numbered 1-4 on the card, and they show up as /dev/ttyS4 - ttyS7 under linux.  Their I/O addresses are running in reverse order though, ttyS4 is 0xe800, ttyS7 is 0xd800.  

I know that I can just plug each port into one of my devices until it responds, but then again, if I'm formatting my commands wrong, or there's some other issues, even that won't work well.  I'm wondering if there is some way to be fairly certain as to the mapping of ports up front.

---

