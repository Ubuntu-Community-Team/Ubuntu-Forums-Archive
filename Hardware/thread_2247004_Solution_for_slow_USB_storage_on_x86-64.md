---
title: "Solution for slow USB storage on x86-64"
date: 2014-10-04
forum: Hardware
---

### Post by skinny honkie on 2014-10-04
There's been an annoying bug with x86-64 installs for YEARS now, back as far as 2008, where USB storage write speeds start off normally for a few seconds and then tail off to ridiculously slow speeds (less than 1MB/s). For copying small files, it's not really a problem, but when you want to backup a large directory to USB, you need to start your copy weeks in advance of when you need the copy completed.

Doing some sleuthing, it looks like the contributing factors are the 64bit kernels, ACPI, and some types of partitioned storage (eg, an NTFS formatted volume visible to a legacy windows box). I got a working solution by doing 2 things (can someone please sanity-check the need for step 1?): 

1 - modify /etc/default/grub file (assuming grub 1.99 or later, legacy grub instructions in first link below), change the GRUB_CMDLINE_LINUX_DEFAULT= so that it reads: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=acpi"

Then run grub-update from the terminal

2 - reboot into the BIOS and disable ACPI, save, and exit.

Done.

I found info in the two threads below via google, but it is annoying that they have been closed and no other replies in those threads can be posted, because it means anyone else searching will find those threads...and no solution. The policy of closing old threads prevents solutions to long-standing issues to be consolidated and made easily discoverable. Mods - please revise this policy for non-version specific faults, like in the "All variants" section. This would be really helpful.

[http://ubuntuforums.org/showthread.php?t=1867460]("http://ubuntuforums.org/showthread.php?t=1867460") and [http://ubuntuforums.org/showthread.php?t=1821162&page=3]("http://ubuntuforums.org/showthread.php?t=1821162&page=3")

---

### Post by Michael_McKenney on 2014-10-05
USB Storage is slow on small file transfers.  It is the nature of USB with its header files.   I switched to Firewire 800 drives and installed a Firewire 800 controller.  You don't have the overhead of USB.

---

### Post by sudodus on 2014-10-05
It may help you to switch off ACPI, but I would use another solution. See this link

[https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

-o-

USB 3 is much better than standard USB 2, but still suffers, particularly if it is a pendrive, where the flash hardware might limit the speed, when copying many small files (as described by *Michael_McKenney*). So it can be a problem of the memory hardware as well as of the USB system.

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

Another alternative is ***eSATA***, which I use.

-o-

It may also be considerably faster to manage ***ext4*** file systems than NTFS. So use NTFS only if you have to access it directly from Windows. You can access it via a local network and use ext4.

---

### Post by skinny honkie on 2014-10-06
Michael, Sudodus - I totally agree re. 1394 and eSATA, I would prefer to use better-quality hardware solutions. Unfortunately, I can't in all cases, and most other folks are probably in this situation too. USB is so ubiquitous that you can't avoid it - what can you do when one turns up via courier with a data request? There simply are times when you have to do large transfers onto usb targets and 150KB/s isn't an acceptable transfer rate, and workarounds like booting off an i386 image or having a decent filesystem on the disk in the first place may not always be practical, and probably shouldn't be necessary for such a common use-case scenario.

I live in hope that SSD's with eSATA become more common than rats in a plague.

---

### Post by sudodus on 2014-10-06
For those urgent cases, maybe booting off an i386 image is a good option :-)

---

