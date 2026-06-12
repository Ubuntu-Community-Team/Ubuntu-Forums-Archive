---
title: "Ubuntu 11.04 on Centreno Duo needs PAE how to enable?"
date: 2011-01-15
forum: Hardware
---

### Post by dartdog on 2011-01-15
I have been rescuing an old Toshiba Satellite A-105-s4074 laptop I loaded 11.04 Natty Narwhal on it when I installed the machine had only 512 memory, ran like a dog, looked up on line and the manual said it would support 4gig, so that is what I now have but only 3 gig is recognized (running much better). I attempted an install of the 64bit amd version but apparently the Centrino Duo does not handle that (it does not seem to have the LM flag) so I see that it does handle PAE but when I tried to do: sudo aptitude install linux-generic-pae linux-headers-generic-pae I got aptitude not found... Instructions here [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
So for the time being stuck.... 
I'm not exactly sure why or how I ended up with 11.04... but it has been working except for this issue...;)

I just installed Linux generic kernel PAE from the Ubuntu software center but the system monitor still only shows 3gb after reboot..

update just reinstalled from scratch version 10.10 now shows generic PAE installed bit still just shows 3gb of memory on sys monitor (2.9gb is what it says really) ughh.. I'd like to find the missing 1gb!!

Ok I got a new BIOS (the old was not showing all memory, now it does at least at the BIOS level) but Ubuntu still does not seem to see it although the PAE generic kernel is loaded ???

Ideas??

---

