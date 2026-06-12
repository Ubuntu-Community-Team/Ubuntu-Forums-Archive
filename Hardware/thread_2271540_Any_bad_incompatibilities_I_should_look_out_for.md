---
title: "Any bad incompatibilities I should look out for?"
date: 2015-03-30
forum: Hardware
---

### Post by Teethdude on 2015-03-30
Hello Ubuntu community. I am looking into a new, higher end laptop, and I want to know how compatible it is with Ubuntu, or Linux in general. Hopefully you can help me out a bit, for I'm not much of a Hardware person. My friend has a Laptop just like it, but he's also a Windows user, and he loves it.

Here's a PDF with the PC's info.
[http://us.msi.com/pdf/GT70%20Dominator-895.pdf](http://us.msi.com/pdf/GT70%20Dominator-895.pdf)

---

### Post by weatherman2 on 2015-03-30
If at all possible, boot Ubuntu 14.04 (most recent LTS version) on your friend's laptop.  Just boot a live USB.  You may have to muck with UEFI firmware settings (aka "BIOS") to allow booting from a USB device, but the newest Ubuntu boot images boot just fine with secure boot in place - I have done it several times.  You don't even need to use "legacy boot" mode in many cases.

Things to check: how does the graphics card work?  Wireless card?  USB 3.0?  If something doesn't work, look up possible solutions online, see if they are easy or a pain.

Try if possible to buy something that you can return for a refund at worst if the laptop turns out not to work well with Ubuntu.

---

### Post by oldfred on 2015-03-30
May be similar, but only other MSI we have recently seen.

 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

---

### Post by Teethdude on 2015-03-31
It's going to take some time, but I'll try a LiveUSB on my friends hardware when the chance arrives. Just by looking at it, things should work, based on some Google searches.

---

### Post by Mark Phelps on 2015-03-31
Be advised that higher-end laptops often use some form of Hybrid/Switchable graphics -- which do not work well in Linux due to lack of specialzed drivers.

Same is true of the hybrid SSD/HDD units that have come out recently.

Also, biometics don't tend to work well -- so avoid anything with a fingerprint reader.

---

### Post by sammiev on 2015-03-31
> **Teethdude said:**
> It's going to take some time, but I'll try a LiveUSB on my friends hardware when the chance arrives. Just by looking at it, things should work, based on some Google searches.

+1 @weatherman2 but I would try 15.04 live on a USB as the hardware drivers would be a little more updated.

---

### Post by Teethdude on 2015-04-07
I tested out a Live USB of 14.04, and it seemed to work nicely. The WiFi card was functioning well, but the last insecurity arrives from the Additional Drivers window. It claimed there are none, and it had an Nvidea brand card (and I'm quite sure that was the only graphics card as well). Does this mean it was using Open source drivers by default? Or had Nvidea drivers working out of the box?

---

### Post by sammiev on 2015-04-07
You will not likely see any additional drivers until you install. Great to see it works well with the default.

---

### Post by efflandt on 2015-04-07
I have an MSI GE60-2OE that I bought Oct 2013 while I could still get it with Win7. If you ask MSI they will tell you that they do not support Linux, but it is all fairly common hardware. While mine can to UEFI, since it had Win7, mine defaults to legacy BIOS and has regular MS DOS partitions including a separate data partition (D:) that I removed and initially install 64-bit 13.10 at that time. The only peculiar thing was that I wanted to install grub to primary partition sda4 where I installed Ubuntu (no swap) to leave the default mbr in place, but every time I tried to clear the boot flag from sda2 and set it to sda4, something kept resetting the boot flag on sda2, and it would boot right to Win7. I even backed up its mbr and put a syslinux mbr on it and it still happened. So I restored its original mbr, put grub on an old USB memory stick, and basically used that as a key when I wanted to boot Linux.

Mine has 2 slots for mSATA SSD cards, although, one of them might be a bit snug against the wireless/Bluetooth card, the other one says SSD right on the motherboard. Crucial kept telling me that their mSATA was incompatible, but could not tell me why. I think it was just that MSI does not publish complete details about their laptops and Crucial did not even know that had mSATA, because some of them come with (2) mSATA SSD's in RAID. So I took a chance and ordered a 512 GB Crucial M550 mSATA, installed 64-bit 14.04.1 to it, set that as boot drive, and it works perfectly, including Steam and Steam games.

Mine has i7-4700MQ with 8 GB RAM and hybrid Intel HD 4600 and Nvidia GTX 765m (with the lighted keyboard in case it is dark). I cannot tell you how to handle Windows Secure Boot and UEFI, but if you can figure that out and install 14.04 or newer**,** contrary to often requiring nomodeset boot parameter for Nvidia graphics on a desktop, I read that someone could not get their laptop with hybrid graphics to work properly until the installed without using nomodeset. So I did not use any boot parameters and everything worked fine. I don't think Additional Drivers shows anything for hybrid graphics, but I would suggest trying **nvidia-331-updates** package or whatever is the most recent nvidia package in the system you install. If you do not know how to install that using **sudo apt-get**, the easiest way would be to install **synaptic** from Software Center and use that to install **nvidia-331-updates**. If you want newer drivers, the xorg-edgers ppa can be added which has **nvidia-346** or **nvidia-349** packages. If you want to switch from nvidia to Intel graphics you will be able to do that from NVIDIA X Server Settings, although, you will likely need to log out of and back into X if switching nvidia to Intel, or may need to reboot if switching from Intel to nvidia.

When you get it all up and running I think you will be pleased.

---

