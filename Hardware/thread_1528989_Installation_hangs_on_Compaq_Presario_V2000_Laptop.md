---
title: "Installation hangs on Compaq Presario V2000 Laptop"
date: 2010-07-11
forum: Hardware
---

### Post by mattismyname on 2010-07-11
I'm trying to install 10.04 on a Compaq Presario V2000 laptop.  The installer seems to hang when switching from the splash screen to a higher resolution graphics mode.  

There are reports on the web of successful installations on this hardware of older Ubuntu releases.  Are there any options to help me get it installed or debug why it doesn't display anything on the screen after the splash screen?

---

### Post by pbmax on 2010-08-26
I've had many versions of k/xubuntu running on the same machine over the years. Never did they have wireless working right away.
However, 10.04 is the first time I've had a problem with freezing on the install.  After a hard reboot I can get into a command-line interface, but it will freeze when I startx.

---

### Post by efflandt on 2010-08-26
Apparently there are different versions of the Presario V2000 laptop with different cpu and possibly other hardware.  For example some have an Intel cpu and the one I have has AMD Sempron 3300+ (similar to Athlon, but crippled to 32-bit).

Mine actually works better with 10.04 than it did with 9.10.  In 9.10 the keyboard often lagged and dropped characters (making sudo difficult), the mouse was erratic because it would alternately lag and jump, and it would not wake from suspend or hibernate.

In 10.04 keyboard or mouse lag is minimal (maybe occasionally during disk access immediately after starting X, and it can successfully wake from suspend and hibernate.  The only thing I did was use **nomodeset** kernel boot parameter because the new default kernel mode setting (kms) did not work properly with other older ATI video on different laptop and desktop.

---

### Post by NamiJason on 2010-11-16
I'm having this same issue.  Has anyone gotten this working?

---

### Post by mattismyname on 2010-11-16
I've had no luck.

---

