---
title: "Failing Hard Drive? Tell me what you think."
date: 2009-06-23
forum: Hardware
---

### Post by asuastrophysics on 2009-06-23
So the other day, as I was putting my loved Acer Aspire 4720Z laptop to sleep, it encountered a sudden power loss. On restart, I got DRDY UNC error (but it booted up just fine, just wouldn't log in). I could here a "kathunk."

To make a long story short, I learned that sudden power failures can be repaired by writing a "zero" to every sector on the drive, thereby remapping all the bad sectors to the drive's "don't read" list. Below are the steps I've taken to approach this concept:

1) I did a ```
dd and whatever /dev/zero of=/dev/sda.
``` This FAILED at 13%. "kathunk". This was done from ubuntu livecd.

2) BTW: I installed several operating systems on the drive successfully before I proceeded to the next step. They installed successfully probably because it was formatted each time. However, all would freeze and crash after logging in. 

3) I downloaded hitachi's specialized boot software from their website. Using their program, I hit "erase disk", thereby zeroing the drive. It was successful. I then ran several "fitness" tests, both basic and advanced. The advanced took over two hours. Both were completely successful. :D

Here I am, typing to you on my newly-installed ubuntu 9.04. No more "kathunk". No more DRDY errors (yet...) What should I look out for, apart from more bad sectors appearing?

---

