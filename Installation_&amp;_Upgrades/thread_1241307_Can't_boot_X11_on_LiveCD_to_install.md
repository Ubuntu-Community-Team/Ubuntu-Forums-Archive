---
title: "Can't boot X11 on LiveCD to install"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by fongandrew on 2009-08-15
I'm trying to install Xubuntu 9.04 on an old Averatec 3200. During the install, it tries to start X and crashes to the command line. The error message flashes by pretty quickly but I caught something about having to go to [http://linuxwireless.org/en/users/Drivers/b43#device_firmware](http://linuxwireless.org/en/users/Drivers/b43#device_firmware) and upgrade my firmware.

All of my Google searches turn my results that presume you already have a working Ubuntu system from which you can download the firmware and install. Given that I'm limited to a command line on the LiveCD, does anyone have any tips on what I should do? Is b43-fwcutter located somewhere on Xubuntu disc? How do I use it?

---

### Post by fongandrew on 2009-08-16
Bump.

---

### Post by presence1960 on 2009-08-16
[boot options]("https://help.ubuntu.com/community/BootOptions")  scroll down to section dealing with F4. You may want safe graphics mode. You may also want to try the F6 options since you have an older machine.

or try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") 
I know you need firmware for broadcom, but X is crashing so try these. After you get up and running you can upgrade the firmware.

---

### Post by cthulhu_54 on 2009-08-31
Here's a question:

I did the Wubi installation. rebooted, got the dual boot option selected xubuntu, got the to the ubuntu desktop it started repartitioning and installation then i get the popup saying there's no root file system. Also it says there is an ERROR FIRMWARE b43.ucode5.fw is missing. I have 4.3 gigs free the install wizard says 253 meg of ram. I would do the installation directly from the cd but it that error thing happens again how would I take ubuntu off? I'm not dissuaded from trying Linux... Yet... I might need to wait until i get a new laptop... Not sure...


fongandrew, did it work for you? How did you solve it?

---

