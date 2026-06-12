---
title: "rtc timeout after upgrade to Feisty"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by epolin on 2007-07-04
Since my upgrade to Feisty last night, the boot stops with the msg:

select() to /dev/rtc to wait for clock tick timed out

Indeed, hwclock -D returns that exact same error, while hwclock -D --directisa works fine.
After some research, I added the following line to /etc/defaults/rcS:

HWCLOCKPARS=--directisa

There is no more error msg, but the boot still stops: I am left in command line under root just after "Setting up console font and keymap... [OK]" (everything is [OK] above), and need to exit to have the graphical interface start.

My questions are:
1) Was my workaround correct?
2) Any idea about why it stops there and what to do to prevent it?

---

### Post by epolin on 2007-07-06
Here is the end of the story (it's not very conclusive, sorry):
 - The stop was due to a silent switch to the safe boot.
 - I made a brand new install from scratch of Feisty, and the hwclock bug vanished.

---

