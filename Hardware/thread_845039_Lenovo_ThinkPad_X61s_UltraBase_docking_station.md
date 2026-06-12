---
title: "Lenovo ThinkPad X61s UltraBase docking station"
date: 2008-06-30
forum: Hardware
---

### Post by kecsap on 2008-06-30
Hi all,

I have an Lenovo ThinkPad X61s with a docking station (UltraBase) and almost everything is working fine with Hardy. My problem is that if the laptop on the docking station and it boots, the USB ports of the docking station work fine. But if I remove the laptop from the docking station and put it back, the USB ports of the docking station do not power up. I have the same issue after suspend/resume without removing the laptop from the docking station.
It does not help e.g. to plug/unplug the AC adapter.
Any other ports after suspend/resume are working fine on the docking station (e.g. serial port, VGA port).

Is it any trick to solve it or command-line tool to fix it?

Thanks,
  kecsap

---

### Post by Camasii on 2008-07-01
Hey,

I'm afraid I cant' be of much help with your issue but I'm currently trying to get the COM port on the dock to work properly. Did you have to do anything special to get it going?

Thanks!

---

### Post by kecsap on 2008-07-03
I don't have any problem with the serial port, it works on /dev/ttyS0 out of box. I'm using minicom with it.

I have an other problem also:

I installed the necessary packages to use the fingerpoint reader for login and if the desktop is locked, then I can't login with both USB and laptop keyboard: I can type the password and press ENTER one time. The password dialog appears, disappears and says Authentication failed several times without pressing ENTER button more times. Anyway I can unlock the desktop with the fingerpoint reader....interesting...

Do the USB ports work for you properly or as I described? If those are working for you: which distribution are you using? Your BIOS version? Your BIOS settings for USB?

---

