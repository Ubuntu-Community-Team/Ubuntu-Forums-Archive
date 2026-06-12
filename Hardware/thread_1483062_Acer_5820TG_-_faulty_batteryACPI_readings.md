---
title: "Acer 5820TG - faulty battery/ACPI readings"
date: 2010-05-14
forum: Hardware
---

### Post by Decline- on 2010-05-14
I recently bought an Acer Aspire Timeline 5820TG laptop, and installed Ubuntu 10.04 64bit. My problem is, the battery indicator is not working as it should, it reports the AC as connected even if it isn't. 

acpi -V gives:
[I]Battery 0: Unknown, 0%, rate information unavailable
Battery 0: design capacity 4400 mAh, last full capacity 4400 mAh = 100%[/I]

cat /proc/acpi/battery/BAT1/state gives:
[I]present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV[/I]

I tried re-attaching the battery, and I tried adding ACPI=force for boot options. Battery indicator is working as it should in Windows.

I also tried upgrading the BIOS, however as this pc is a new model, there was only a minor upgrade available, which apparently didn't help.

Any help is appreciated!

---

### Post by martine4161 on 2010-05-14
Your problem is not because of any hardware but I think the problem is by the OS. So basically you can try it by exchanging the OS or if you don't want that then reinstall the OS with genuine version.

---

### Post by Decline- on 2010-05-14
Sorry, I'm not sure if I understand what you mean. What OS are you talking about? The problem is with Ubuntu, and Ubuntu is as genuine as it can get...

---

### Post by giova.86 on 2010-05-14
Hy Decline, i have an Acer 4820TG and I have the same problem. I tried with other linux os like Fedora, Suse, PCLinuxOS and Slack but I had the same problem: the system doesn't recognize the battery.

The problem is surely in the OS because with windows 7, without installing any particular driver, all works fine.

---

### Post by Decline- on 2010-05-20
Actually, I've been reading a bit about this, and it seems like Acer didn't follow the standards. While Linux distros rely upon the standards being followed, Windows manages to get the battery readings through non-standard methods. There are some guides for downloading a new "DSDT", compiling it, then it should work - the problem is, there is no DSDT for this laptop as of yet. And I don't know how to make one...

---

### Post by Snake231088 on 2010-05-24
I ave the same problem with a Acer Aspire 5745G.
I have also fixed the DSDT table but the problem persist.

---

### Post by lazerradial2003 on 2010-07-03
Same issue on the 4820T, anyone had any luck with this?

---

### Post by terajiv on 2010-07-20
I have bought Acer Aspire 5745G and I am having the same problem. I tried installing acpi, acpid and battery-status
but it still shows 0% battery
If anyone managed to solve it please do write here
Regards
Rajiv

---

### Post by Decline- on 2010-07-20
Still no luck for me either on this problem :/

---

### Post by pemasu on 2010-07-27
there are several working kernels for lucid ubuntu around. People has compiled kernels which has working acpi. Battery status, cd eject, ability to switch dual graphics or shut down ATI. Shutting ATI reduces power usage about 15 W for me and almoust doubles battery time.

[http://georgia.ubuntuforums.org/showthread.php?t=1495123&page=8](http://georgia.ubuntuforums.org/showthread.php?t=1495123&page=8)

You can just download kernel image deb and install it. Reboot.

---

### Post by calzifer on 2010-07-28
I'm using Gentoo with the Kernel 2.6.34 (Vanilla & Gentoo-sources tested) and it works like a charm :)

---

### Post by pemasu on 2010-09-08
Bios 1.18 seems to fix acpi problem.

---

