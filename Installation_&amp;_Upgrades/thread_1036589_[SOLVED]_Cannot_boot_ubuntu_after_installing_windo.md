---
title: "[SOLVED] Cannot boot ubuntu after installing windows 7!!!"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by theproc64 on 2009-01-11
I installed windows 7 to test it out but it seems to have written over my mbr or something like that.  So I just pulled out my trusty super grub disk and tried restoring grub that way and it comes up with "file not found" errors when it looks for my grub files.  I also tried booting ubuntu right from the super grub disk menu and that comes up with the same error.  Does anybody know what could be going on?  I want my linux back!!!

update- now something is REALLY wrong because it comes up with "missing operating system" in the bios when I try to start normally instead of booting windows or grub.

update- I started up a live cd and the menu.1st file is there and looks correct.  When I try to boot a certain partition and select my ubuntu partition it says "bad file or directory type"... whatever that means.

---

### Post by taurus on 2009-01-11
What's the output of this command from a terminal (from the LiveCD)?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by theproc64 on 2009-01-11
The output is
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c5d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sda2             123        1338     9767520   83  Linux
/dev/sda3            1339       16103   118599862+  83  Linux
/dev/sda4           16104       19458    26941440    7  HPFS/NTFS


The first partition is swap, then the ubuntu install, then /home and then the windows partition.  Could the problem have to do with the fact that there's only an asterisk under the swap partition?  I also got windows to boot through the super grub disk but still no luck getting Ubuntu up and running.

---

### Post by taurus on 2009-01-11
I would assume the * should be on /dev/sda2 since that is probably your / partition.  Gparted from the LiveCD would let you change to boot flag.

---

### Post by theproc64 on 2009-01-11
I did this and it didn't really seem to help anything surprisingly.  I also tried using the command > sudo grub-install /dev/sda2 and > sudo grub-install /dev/sda and both come up with errors saying "could not find device for /boot: not found or not a block device."

---

### Post by taurus on 2009-01-11
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by theproc64 on 2009-01-11
Thank You!!! this worked perfectly.  thanks for the help so late at night.

---

### Post by cariboo on 2009-01-11
I had the same problem this afternoon I followed [this]("http://ubuntuforums.org/showthread.php?t=224351"), and was up and running in less than 5 minutes.

Jim

---

### Post by cheaptrick on 2009-01-11
i've got a grub error 15. Ran gparted.. to my horror the ubuntu partition is shown as "unallocated", empty. I guess that ubuntu partition is gone?

---

