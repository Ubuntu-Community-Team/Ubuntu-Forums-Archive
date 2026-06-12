---
title: "eeepc Netbook 1005 PE Flicker and BSOD 9.10"
date: 2010-02-11
forum: Hardware
---

### Post by lbravo on 2010-02-11
Hello friends,

I've installed the Netbook Remix 9.10 on my new EEE PC 1005PE and everything works mostly great -- except for a screen flicker and a seemingly random Black Screen of Death.  

If someone could help me troubleshoot those things -- probably related to display drivers, I'd certainly appreciate it.

I found one guy online with similar symptoms who changed an xorg.conf file -- but I don't seem to have one at the stated location in /etc/X11.  Weird.

Anyway, I'd really like to be confident with this install.  The thing came with Win7, and I don't want to have to use that.

Thanks in advance!

Lori

---

### Post by lessmemorelove on 2010-02-16
solve the screen flicker with power management in system. uncheck "dim display when idle" for the bsod, uncheck "spin down hard disks when possible"

---

### Post by lbravo on 2010-02-20
Thank you SO much. Now all is perfect!

Lori
:biggrin:

---

### Post by hoyer801 on 2010-02-21
That worked for me, too. I hadn't experienced the BSOD, but went ahead and unchecked the spin down disks option anyway.

The flicker went away instantly. Thanks!

---

### Post by lbravo on 2010-02-24
OOOPS!  Spoke too soon - the flicker went away instantly, but I just got another bsod.  Any other ideas?

Thanks,
Lori
:confused:

---

### Post by lessmemorelove on 2010-02-25
is everything up to date? i use karmic on my 1005pe with proposed updates checked in synaptic. the only other idea i can think of is maybe you have a bad battery? i have heard of the bsod happening on windows and ubuntu when a battery is bad.

---

