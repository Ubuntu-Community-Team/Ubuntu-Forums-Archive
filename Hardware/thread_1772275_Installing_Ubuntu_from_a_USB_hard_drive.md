---
title: "Installing Ubuntu from a USB hard drive"
date: 2011-05-31
forum: Hardware
---

### Post by j0eb0b on 2011-05-31
Creating an Ubuntu server from a USB disk (posted to Server Platform board previously)

Here is what I am trying to do. I recently acquired a Dell Poweredge 850 blade that I want to configure as an Ubuntu 11.04 server. The server will be used to test some communications software and is presently free standing (not connected to a LAN) but has INTERNET access. I understand my options to load an image of the operating system to be either CD or USB stick. The blade has no CD so USB would seem the way forward.

The Ubuntu FAQ states that an image can be installed from a USB stick with 2 GB free. I don't have one but I have a 1TB USB expansion drive with lots of free space. The expansion drive is formatted NTSF but not presently bootable.

Is there a way to create a partition with an MBR on the drive that will allow the 11.04 .iso to be recognized and auto run (assuming the Dell will boot from USB which I am unsure of)?

---

### Post by Yellow Pasque on 2011-05-31
In your case, I think the best solution is to get a USB stick. They're cheap and very handy (linux installs, BIOS flashing, portable files, etc.)

---

### Post by oldfred on 2011-05-31
This may work. I use grub2 with FAT32 on flash and EXT3 or ext4 partitions and boot ISOs.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by j0eb0b on 2011-05-31
Thanks for the suggestions, I'll give it a try when I get home tonight and advise how it works.  

As much as anything, trying to use the USB drive piqued my intellectual curiosity.

---

### Post by helpad on 2011-06-01
with [this]("http://unetbootin.sourceforge.net/") is easier, only took the ISO and USB. if not boot from usb, with [this]("http://www.plop.at/en/bootmanager.html") you can.

---

### Post by oldfred on 2011-06-01
Most of the USB install creators, format the entire flash drive. I think if you try to install to a 1TB drive it will try to format the entire drive. But probalby crash as I do not think FAT can be 1TB.

---

