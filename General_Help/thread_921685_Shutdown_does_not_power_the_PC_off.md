---
title: "Shutdown does not power the PC off"
date: 2008-09-16
forum: General Help
---

### Post by cw33514 on 2008-09-16
I am new to Ubuntu; recently upgraded from 7.10 to 8.04.
Can someone tell me how I get control of the PCs on/off switch back?
When I shutdown Ubuntu the PC does not power off; I have to unplug it
to power it down. Also when I plug it in, it starts booting straight
away, without me touching the on/off switch.
Replies for a Ubuntu novice please...

---

### Post by bingoUV on 2008-09-16
First problem - Shutdown does not power off: How do you shutdown? System -> Quit -> Shutdown?


About the second problem, i.e. the PC starts up as soon as you plug it in; there must be an option in BIOS to cause this. It would say some thing like behaviour on power restore after power loss. Set it to power off.

---

### Post by Iowan on 2008-09-16
As an experiment, try (from a terminal) **sudo halt**.

---

### Post by cw33514 on 2008-09-18
I have tried the System, Quit, Shutdown method to no avail.
Sudo halt in terminal also does no better.
I normally use the Shutdown button in the top right of the Desktop window
to Shutdown.
There is no setting in the BIOS for this condition.
The power switch worked normally when the PC was running Windows.
It appears to be a memory problem!
The PC was running with only 256mb; I have upgraded it to 768mb
and much to my surprise the power switch now works as I would have
expected. The only thing Shutdown does not do now is to power off the PC; I still have to hit the power button, but its much better than it was

---

### Post by whizbaby on 2008-09-18
In /boot/grub/menu.list put
```
reboot=no shutdown=no
```
as options at the end of the line of your kernel. They prvent ubuntu from doing reboot/halting and let the mainboard handle it. Worked with most clients I had the same problem with.

---

