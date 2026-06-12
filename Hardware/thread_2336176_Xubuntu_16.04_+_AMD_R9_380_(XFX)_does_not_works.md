---
title: "Xubuntu 16.04 + AMD R9 380 (XFX) does not works"
date: 2016-09-05
forum: Hardware
---

### Post by adamitj on 2016-09-05
Hello.

First of all, I have to say that I tried out everything that I found in Internet about install and remove amdgpu packages, but no one worked.

I have a new fresh install of Xubuntu 16.04 and can boot only with "nomodeset" option in grub. 

With amdgpu drivers installed, the boot takes from 5 to 7 minutes to drop to console login. Then More 2 minutes to open the login screen. After login with the right user, a low resolution version of my desktop is showed and then the mouse pointer freezes with the whole computer freezed.

Can anyone give any directions? Maybe downgrade to Xubuntu 14.04 and use fglrx drivers?

P.S: openSUSE Leap is working fine, but all Debian based distros have problems (tested Debian 8.5, Xubuntu/Ubuntu 16.04 and Mintlinux 17.2).

---

### Post by adamitj on 2016-09-08
Ok, after a lot of debugging I found something weird. I believed the problem was in my R9 380 VGA because of nomodeset, however, it doesn't. The mobo of my PC is an ASUS Z97M-Plus/BR with an Intel Core i5 4690K and 16 GB of DDR3 RAM 1600.

I was able to install Ubuntu along Windows 10 (I'm using Windows it only for some games, phew!) and after perfectly Ubuntu 16.04 64-bit installation the computer does not passed the ASUS logo when powered on. So I have clean out the BIOS configuration (hard reset by the jumper on the mobo). 

After that, either Windows 10 and Ubuntu booted perfectly, and the XFX R9 380 was fully functional with AMDGPU drivers with Linux.

Then I enter BIOS setup and reapplied  ASUS Easy Overclock into my CPU and memory: my RAM is factory default of 1333 and was set XMP OC to 1600, my CPU is stock 3.5 GHz and was set to 4.2 GHz O.C. with stock cooler.

After that, Windows 10 can boot perfectly and runs all games very well. But Ubuntu Linux does not boot after choosing it from GRUB menu.

Again, if I set "nomodeset" at Linux GRUB entry, it boots but with wrong resolution.

How can I discover if this is a GPU or CPU/RAM problem? Can I have Linux log entry to identify where it stopped when booting?

---

