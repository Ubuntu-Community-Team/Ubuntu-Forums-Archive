---
title: "Install issue  with ASUS express gate"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Rudedawg on 2009-02-03
Hey all, 

Trying to get 8.04LTS to install as a dual boot on the new pc I just built last month. The ASUS MB has "express gate" technology and I'm wondering if it is causing an issue when trying to run the live cd. I know it might be a bad cd as well. The cd runs and after I make any selection on the ubuntu menu (it does go that far) it shows the ubuntu loading screen (with the logo and orange bar) and then it show a series of errors: 

[ 303.720827] Buffer I/O error on device fd0, logical block 0 
which continues to repeat with only the numbers in the brackets changing on each new line. If anyone has any idea, please let me know. I'll keep any eye on this thread incase anyone needs any frther info about the system.

---

### Post by jimv on 2009-02-03
You could try installing from a thumbdrive if you have one.  UNetBootin will make a thumbdrive that you can install from.

---

### Post by Rudedawg on 2009-02-03
Tried disabling express gate and still got the same error. Tried using another disk (that has worked before on other machines) Neither things worked. I have 2 SATA drives in SATA slots 4 and 6 on the motherboard. The DVD drive is also a SATA device connected to SATA 2 on the motherboard. The box is a Quad core intel chip with 8Gigs of pc8500 ram. It's running Vista 64bit very well. Wubi ran without a problem inside of Vista too. Hope some of this helps.

---

### Post by JSchoeck on 2009-02-04
I haven't yet installed Express Gate on my ASUS board, but as soon as I get Ubuntu installed (white screen problem right now) I'll post if installing Express Gate afterwards works or not.

Good luck to you!

---

### Post by wisedog on 2009-11-19
the problem with fd0 is the asus motherboard enabled floppy disk in the bios(default).

disable it and this error message will no longer come.

---

