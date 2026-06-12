---
title: "Fix for network problem in Ubuntu killed Windows driver"
date: 2010-09-19
forum: Hardware
---

### Post by Jan Dansson on 2010-09-19
Hi,

I installed Ubuntu 10.04 LTS on my Windows XP laptop (Compaq nx6320  / HP).  First my network connection in Ubuntu didn't work.  After search on different forums I found the advice to run this code:

modprobe -r tg3
modprobe broadcom
modprobe tg3

This fixed my problem but a new arrived instead. Now I can't connect to the network in Windows XP any more! I tried to disable and enable the network in both Windows and Ubuntu. The system was restarted many times. 
How can the Linux code above have any effect on Windows XP?  What can I do to get the network back in Windows ( and of course keep it in Ubuntu at the same time)?

Network card: Broadcom NIC Gigabit Ethernet (tg3 driver)

Jan

---

### Post by pneaveill on 2011-05-20
> **Jan Dansson said:**
> Hi,

I installed Ubuntu 10.04 LTS on my Windows XP laptop (Compaq nx6320  / HP).  First my network connection in Ubuntu didn't work.  After search on different forums I found the advice to run this code:

modprobe -r tg3
modprobe broadcom
modprobe tg3

This fixed my problem but a new arrived instead. Now I can't connect to the network in Windows XP any more! I tried to disable and enable the network in both Windows and Ubuntu. The system was restarted many times. 
How can the Linux code above have any effect on Windows XP?  What can I do to get the network back in Windows ( and of course keep it in Ubuntu at the same time)?

Network card: Broadcom NIC Gigabit Ethernet (tg3 driver)

Jan

Have no clue if this thread is still active or if you still have the issue, but will give my 2 cents worth here.  Checking google, I discover that there are several broadcom drivers, one of which is the tg3 one.  Issue #1: how did you come to find out that you needed this higher level driver?  From my understanding, this is a 1000 (gigabit) system.  Issue #2. Assuming that you need that one, certain kernels do not like certain drivers for odd reasons.  If we knew what kernel and all of that, it might help.

```
lspci
``` will show what hardware you have and we can go from there

---

