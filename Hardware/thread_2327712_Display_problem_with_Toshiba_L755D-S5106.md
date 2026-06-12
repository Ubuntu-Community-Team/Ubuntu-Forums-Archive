---
title: "Display problem with Toshiba L755D-S5106"
date: 2016-06-13
forum: Hardware
---

### Post by michael-e-milliman on 2016-06-13
I have installed Ubuntu Studio on my Toshiba L755D-S5106 which has a Radeon HD6520G graphics chip in it.  The installation went without any problems until I rebooted.  Once off the live CD, the display goes completely blank during the boot.  Disk activity seems to indicate that the system continues to boot with no indication on the display whatsoever.  Upon rebooting and selecting the recovery option on the Grub menu, and then Resume, the system boots and I get low-resolution video (I assume software acceleration as opposed to hardware is being used), but the system is usable.  Any suggestions to getting the hardware working properly would be appreciated.

I am new to Ubuntu, however, I have run other distributions of Linux for several years, predominantly Debian and LinuxMint, both of which work properly with the display on the Toshiba laptop (I have a dual/multi-boot system with Windows and a couple of different distributions of Linux installed for evaluation)...Though as I recall, with LinuxMint, I had to install the fglrx drivers for the display to work properly (LinuxMint seemed to have the same problem as Ubuntu).  I tried that with the Ubuntu Studio installation, but that did not solve the problem this time.

---

### Post by X-RED_Tech on 2016-06-13
Linux Mint is a derivative of Ubuntu. Hardware support should be the same.
What release have you installed?

---

### Post by michael-e-milliman on 2016-06-14
Yes, LinuxMint is an Ubuntu derivative, and so I thought that I would not have any problems.  I have installed Ubuntu Studio 16.04, the latest stable release.  I was surprised to have this problem, or at least to not be able to get it solved as easily as it was in LinuxMint.

---

### Post by michael-e-milliman on 2016-06-14
I have the problem fixed, though I'm not sure how the fix occurred, which is unusual for me -- I may not know how I broke things, but I always know how I got them fixed.

This may be a problem with grub ... as the only change that I made to the system, that I know of, between not working and working is I re-installed the grub bootloader to the hard drive from the LinuxMint partition.  In other words, I booted to LinuxMint (which is based on Ubuntu 14.04) and ran grub-mkconfig to update the configuration files in that installations /boot/grub folder.  I then ran grub-install.  The object was to make LinuxMint the default boot distribution...doing it the easy way instead of editing the config files myself.  Now, Ubuntu Studio 16.04 boots properly as well when I select that distribution from the grub menu.

I hate to mark this thread solved, at this point, as I'm not sure what the solution was.

---

