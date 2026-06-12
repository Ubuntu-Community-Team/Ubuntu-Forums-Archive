---
title: "Kernel Starts to Load and then Nothing happens"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by synaptiv on 2007-07-20
ok here is the scenario, im running 7.04 on my gateway laptop, 1.33 ghz celeron, intel graphics chip, 256 ram. Everyting was running fine until yesterday, i accidently rebooted while it was booting up, now it wont get past the kernel loading ....   it just sits there and it looks as though its accessing the HDD but nothing happens, i also tried loading it in recovery mode which gives me the verbose readout and i cant remember the exact error but it seems its going cylinder to cylinder finding errors, or something, is there another way to get past this error, or am i going to have to reinstall and if so , is there a way to safely install without losing all of my work on the drive, ive never had to do a rescue with linux which is one of the reasons i like linux .

---

### Post by bdtgp on 2007-07-20
If you put in your Ubuntu CD or DVD and boot from it, before it installs there is a menu that has options like "Start or Install Ubuntu" and stuff.  A lot of times one of the options is to recover a system.  You might want to hit enter on that Option and see what its gonna do.  If you don't think it'll work for you after you see where its going, then don't actually start the recovery.

If you decide to do a fresh install, sometimes you can copy data from the old partition onto your new install.

---

### Post by synaptiv on 2007-07-20
yea i was thinking about doing that , i just wasnt sure what that error is, and thank you for the resonse.

---

### Post by Maxtorm on 2007-07-20
Try booting in recovery mode as your already have done. When you get to the command prompt, try:
```
e2fsck /dev/hda1
```
(That assumes that hda1 is your primary hard drive.  If it is not, substitute the appropriate device name as listed in /etc/mtab.)

---

