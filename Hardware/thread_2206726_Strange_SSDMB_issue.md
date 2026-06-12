---
title: "Strange SSD/MB issue"
date: 2014-02-20
forum: Hardware
---

### Post by DXD828 on 2014-02-20
Hi Guys / Girls,

Have built two identical machines this week with these specs:

- 60GB Kingston SSDnow 300
- Gigabyte GA-78LMT-USB3
- AMD FX 4130 (4 core, 3.8Ghz)
- Corsair 8GB XMS3 RAM
- Using built in graphics

I first installed Ubuntu 13.10 64bit via DVD with AHCI turned on in the BIOS. The install went fine, used a single partition on the SSD for root rebooted and got a frozen login screen. USB mouse and keyboard do nothing, not even pressing the Num Lock changes the LED indicator and the disk access LED stops flashing completely.

After a reboot sometimes i can make it past the login screen and the machine works fine for a few hours. This is only 1 out of 3 boots though. The rest of the time I just get the frozen login screen and have to do a hard reset.

I built the second computer hoping to rule out a faulty component and I get the same issue. I also get the same with the 13.04 64bit DVD install.

But if I plug the SSD into another of my AMD computers it boots fine everytime, if I plug a normal 13.04 64bit HDD into one of the new machines it also runs fine (that's what I'm on currently).

When it has been booting checking the log files show nothing useful, i'm guessing everything has locked up so no writes are going on at all.

So i'm completely stuck with what to try next, it seems to be a combination of SSD and motherboard. Any ideas?

---

### Post by oldfred on 2014-02-20
My old Gigabyte motherboard has settings for USB keyboard & mouse. If I do not turn them on, keyboard works in Windows (XP) and Ubuntu, but not grub. Grub must not have drivers that full systems install. I also updated BIOS and it reset to defaults and I had to turn on USB key board & mouse again.

Some newer boards have issues with certain USB ports. Have you tried all? Particularly USB2 ports for keyboard & mouse.

Someone posted this, I am not even sure what it is.
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.


 Gigabyte 970 chipset board  - GRUB_CMDLINE_LINUX="iommu=soft" and Disable iommu in bios
[http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)
Gigabyte GA-MA790GPT-UD3H USB boot issues
[http://ubuntuforums.org/showthread.php?t=2205776](http://ubuntuforums.org/showthread.php?t=2205776)

---

### Post by DXD828 on 2014-02-21
The keyboard & mouse work fine though, I can use it when in Grub and when it does manage to boot it works fine. The issue is the whole system locking up completely, ie no hard drives writes / reads :/

---

### Post by The Spectre on 2014-02-21
The BIOS on the Motherboard or Firmware on the SSD may be different on the two different setups check and see if both are running the same version.

Even if they are the same I would check to see if there is an update available.

---

