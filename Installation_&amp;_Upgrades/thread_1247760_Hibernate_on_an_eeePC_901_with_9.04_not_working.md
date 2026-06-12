---
title: "Hibernate on an eeePC 901 with 9.04 not working"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by tomsimmons on 2009-08-23
Afternoon All,

I'm hoping someone can help me with this.  I have a 2GB swap partition on an 4GB SD.  I have found today that this wasn't being mounted at boot time (by using System Monitor) so swap size was reported 0 bytes of 0.  I checked the fstab and where the swap was referenced by UUID, I changed this to /dev/sdc1, restarted and can no see in System Monitor that it is being used.  If I close the lid and then wake the machine from suspend, it is still being used.

The problem is if I try and Hibernate I get a black screen, a quick pause, 3 lines I can read, then a lot of line that all say something about read error on swap.  If I look under Log File Viewer the only info I've found so far is under messages saying...

```
Aug 23 16:14:48 eeePC kernel: [  103.482070] sd 1:0:1:0: [sdb] Starting disk
Aug 23 16:14:48 eeePC kernel: [  105.382111] PM: Saving image data pages (82680 pages) ...     <1>Read-error on swap-device (8:32:95)
Aug 23 16:14:48 eeePC kernel: [  105.382292] ^H^H^H^H  0%<1>Read-error on swap-device (8:32:103)
Aug 23 16:14:49 eeePC kernel: [  105.433303] PM: Wrote 330720 kbytes in 0.05 seconds (6614.40 MB/s)
Aug 23 16:14:49 eeePC kernel: [  105.498038] Restarting tasks ... done.
```

Thanks

Tom

---

### Post by stlsaint on 2009-08-24
are you running a dual boot machine...

---

### Post by tomsimmons on 2009-08-24
> **stlsaint said:**
> are you running a dual boot machine...

Nope, just Ubuntu 9.04 NBR on a eeePC 901 with 1GB of memory.

It has the usual 4GB and 16GB (?) SSD, hence why I created the swap on the SD - so as not to over tax the SSD.  The OS is installed on the 4GB SSD.

Thanks


Tom

---

### Post by eltoozero on 2009-08-25
> **tomsimmons said:**
> It has the usual 4GB and 16GB (?) SSD, hence why I created the swap on the SD - so as not to over tax the SSD.  The OS is installed on the 4GB SSD.

Hey there, I've got my swap file defined as a 2048Mb partition at the end of the 16Gb SSD.

Not so sure about having the swap file on the SD, the card reader is a USB 2.0 device, just doesn't seem right to me.

---

### Post by kerry_s on 2009-08-25
if you have uswsusp installed then theres a file in /etc that you need to change to that "/dev/sdc1" in there. i think the file is uswsusp.conf, i'm not sure as i don't have that installed on mine i did my install of unr from the cli.

---

### Post by eltoozero on 2009-08-26
Negative, not using uswsusp.  

I am now able to successfully hibernate after reinstalling and fully upgrading 9.10 Karmic Koala after creating a 2GiB swap partition at the end of my 16Gb SSD using a GParted thumbdrive.

Even after creating the swap partition and adding it to /etc/fstab, and then checking that it was active by running free, I was not able to hibernate, after reinstalling, hibernation works like a charm.

A voodoo fix was suspected because I had just completed a fresh install of 9.10 Alpha 4 on my Dad's Asus EEE 1000H, and it's identical (cpu, chipset, ram) save for the SATA 2.5" HD instead of dual 4GB/16GB SSDs and the screen size.  There was never any hibernation issue there because the swap was created automatically during the install.

My partition setup, my /etc/fstab, and free output is below.

For the observant/curious, the /dev/sda2 partition is used for the Asus EeePC 901 and 1000H to use "Boot Booster", which holds a cache of the POST to allow it to be bypassed during boot.  The option will not show up in the BIOS if the partition does not exist.  Additional info on that [here]("http://forum.eeeuser.com/viewtopic.php?pid=250500").

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005        639       1365          0         76        326
-/+ buffers/cache:        236       1768
Swap:         2047          0       2047

$ cat /etc/fstab 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9bc21413-7b96-47be-aa17-eaccc980cebf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=0c450dcd-516f-486d-95e2-6ed30fb2adf0 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=227261c0-cbb8-4290-8716-5f41b4b009b8 none            swap    sw              0       0

$ sudo fdisk -l /dev/sda 
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb38fb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         489     3927861   83  Linux
/dev/sda2             490         490        8032+  ef  EFI (FAT-12/16/32)

$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1701    13663251   83  Linux
/dev/sdb2            1702        1962     2096482+  82  Linux swap / Solaris

```

rawk.

---

### Post by tomsimmons on 2009-08-26
Thanks for the replies so far.

Not sue I'm quite following you here.

Are you saying that after a fresh install of 9.10 Alpha all is well?  Does this mean that you also found that on 9.04 you couldn't Hibernate to a drive other than the 4/16GB SSD's?

I created by swap partition during the install process on the SD card, it was the installed that created the UID entry in the fstab, but the system seeme unable to mount this at boot time.  Now that I've changed the UID to /dev/sdc1 it is now mounted at boot time, but still no Hibernate.


Tom

---

### Post by eltoozero on 2009-08-26
I'm going off of memory here but in 9.04 my recollection is that I could not hibernate, I had disabled it the GUI using gconf.  I did not have the swap enabled at the time on my machine but...

My Dad has the eee 1000H, which is identical to the 901 except for the 2.5" SATA HD and the screen/keyboard size.  When I set him up on Jaunty I recall that he could not hibernate, even with swap configured during the install.

I was not running a swap file until last night when I enabled it for testing after I'd already been running Karmic Alpha 4.  Initially, even after the swap file was created and added to fstab, hibernate did not function until I did a re-install and whatever hooks for kinit to load the memory image from disk on boot were properly in place.

Summary: Hibernate on Eee 901 and 1000H was not working in 9.04 Jaunty, but works in 9.10 Karmic as long as you've got a swap partition/file.

---

