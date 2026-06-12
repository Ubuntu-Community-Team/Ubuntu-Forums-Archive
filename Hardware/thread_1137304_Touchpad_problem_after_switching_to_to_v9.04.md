---
title: "Touchpad problem after switching to to v9.04"
date: 2009-04-25
forum: Hardware
---

### Post by osial on 2009-04-25
Hi, yesteday I've updated my Ubutu 8.10 to 9.04 and after the instalation was over my touchpad stopped working. I'm using old Acer Travel Mate 2400. Do you have any idea how to turn it on again? (in mouse and touchpad settings everything looks ok).

---

### Post by shl_junk on 2009-04-30
Yes, same here.  If anyone has information, please help.

---

### Post by yoasif on 2009-04-30
I'm having a similar issue:

[https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/368985](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/368985)

I'd suggest that you do ```
apport-collect 368985
```to try to help out if you can, I also plan to submit the bug report to bugs.freedesktop.org, so you may want to follow up there as well.

---

### Post by shl_junk on 2009-04-30
yoasif, sorry for being ignorant ... fairly new to Ubuntu, but what do you mean when you say to:

apport-collect 368985

can you lay out the steps? for me?

---

### Post by yoasif on 2009-04-30
> **shl_junk said:**
> yoasif, sorry for being ignorant ... fairly new to Ubuntu, but what do you mean when you say to:

apport-collect 368985

can you lay out the steps? for me?open a terminal (applications > accessories > terminal) and then type that (or copy and paste that) into it and hit enter. 

you may need to sign up for a launchpad.net account as well, but basically, this collects your information and submits it to the bug report. 

If you have a juanty install cd, and it works when booted from there, you may want to submit the same information when booted into the live cd (if it works). 

basically, you are trying to submit information that should theoretically help fix the bug.

---

