---
title: "Installation"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by zloyzenka on 2009-02-27
Trying to install Ubuntu 8.10 on acer 5920 laptop.
successfully finishing first 6 steps, i the middle of seventh screen becomes black, does some check up but after 'Battery check   OK' it just stops.

---

### Post by sukhhari on 2009-02-28
Your Installation CD / DVD Problem, download fresh Ubuntu and try to burn cd / dvd and check the cd /dvd then install.

---

### Post by tommcd on 2009-02-28
> **zloyzenka said:**
> Trying to install Ubuntu 8.10 on acer 5920 laptop.
successfully finishing first 6 steps, i the middle of seventh screen becomes black, does some check up but after 'Battery check   OK' it just stops.

There have been some recent threads on this. See post #16 from this thread:
[http://ubuntuforums.org/showthread.php?t=998991](http://ubuntuforums.org/showthread.php?t=998991)
The bottom line is to boot the Ubuntu install CD, then hit F6 to load extra boot options, and type: **acpi_osi="Linux"** including the quotes, and hit enter to start the install. This may not work, but it is worth a try.
Also this thread:
[http://ubuntuforums.org/showthread.php?t=1077048](http://ubuntuforums.org/showthread.php?t=1077048)
If acpi_osi="Linux" doesn't help, boot the Ubuntu CD again, hit F6, and type:
```
"acpi=force pci=noacpi"
```
Include the quotes. If that doesn't work, the boot the CD and hit F6 and try:
```
"acpi=off"
```
This may be a bug in the Ubuntu installer, or a problem with a proprietary (secret) acpi implementation from Acer. Hope some of this helps.

You might try burning a new CD also. Be sure to burn at the slowest possible speed, and check the CD for defects by choosing that option from the menu when Ubuntu boots up. The wiki says Ubuntu does work on the Acer 5920 as far back as Fiesty:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920)
Try burning the CD with Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And welcome to the Ubuntu forums!

---

### Post by zloyzenka on 2009-03-01
Thanks for help 
*acpi_osi="Linux"*  was a solution, except it didn't let me partition my disk. Now I'm proud user of Ubuntu System.

---

### Post by tommcd on 2009-03-01
> **zloyzenka said:**
> Thanks for help 
*acpi_osi="Linux"*  was a solution, except it didn't let me partition my disk. Now I'm proud user of Ubuntu System.

If you got Ubuntu installed you must have at least one partition, which will be root. More likely, you will have 2: root and swap. Swap is like virtual memory in Windows. 
To list your partitions run this from the terminal 
```
sudo fdisk -l
```

The ideal situation is to have 3 partitions: root, swap, and home. Home is for all your data, so if you ever reinstall Ubuntu all your data is safe on a separate partition. The next time you need to partition your hard drive, consider trying the Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
The GParted live CD is also very good:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Glad you got Ubuntu installed.

---

