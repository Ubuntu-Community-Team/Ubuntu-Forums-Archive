---
title: "Hardware Issues after Adding RAM"
date: 2012-02-08
forum: Hardware
---

### Post by tumerictj on 2012-02-08
Hi All,

I'm not really that computer-savvy, but I've been enjoyably using Kubuntu on my old laptop (Dell Inspiron E1705) for school for about a year now.  I'm a Math major, and one of the things that attracted me to Linux was the more native integration with Sage and LaTeX.  

Today I installed more RAM, which made the system run faster, but, to my dismay, the computer can no longer detect the touchpad or detect a wireless network. 

I know that the touchpad and wireless card are compatible with Kubuntu because they worked until today.  After the initial installation, nothing was required.  

I considered that there might be a problem before adding the RAM, and I might just try installing Kubuntu again from CD, keeping whatever files I can.  But any more moderate suggestion would greatly be appreciated.  

P.S. Maybe it is a problem that I have 1GB in one slot and 512MB in the other?  But I tried reinstalling the original memory card, and the problem persisted.

---

### Post by jerrrys on 2012-02-09
Any chance you updated your kernel during this?  Try backing up one kernel and see what happens.

If not sure about your kernel, open a terminal and enter:   ls /boot

And like you, it doesn't sound like a ram issue.

---

### Post by Bucky Ball on 2012-02-09
No, wouldn't think is a RAM issue. If you have updated, select the previous kernel (third on the list when you boot to the OS selection screen) which did work with touchpad, etc, and see if problem persists. 

Presuming you're using 11.10?

---

### Post by ahallubuntu on 2012-02-09
Obviously, return the RAM to its previous state and see if you still have the same problem.  If you have been doing updates also, as others have suggested try reverting to the previous kernel.  Change one thing at a time.

You might also run Memtest after installing new RAM.  If you don't get a Grub menu upon boot, hold down the Shift key to get one, then choose Memtest and let it run for about 5 minutes.  It is actually possible to install RAM that's not quite compatible with a computer but still have it boot and kinda work but not reliably.  Memtest should shake out whether your new RAM is really compatible with the computer or not pretty quickly.

---

### Post by jasonrisenburg on 2012-02-09
take out the ram you know is good and if the ramm is bad it will beep and not boot. [http://kb.iu.edu/data/afzy.html](http://kb.iu.edu/data/afzy.html)

---

