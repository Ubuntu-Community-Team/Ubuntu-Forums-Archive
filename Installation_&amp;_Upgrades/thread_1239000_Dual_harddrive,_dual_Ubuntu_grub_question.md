---
title: "Dual harddrive, dual Ubuntu grub question"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Rambetter on 2009-08-13
I have a rather complicated setup with 2 hard drives: a SATA drive and and IDE drive (which is not sharing its cable and is in the primary IDE slot).

SATA drive: Newly installed 8.04.3.
IDE drive: Complex dual boot of Ubuntu 6.06 and FreeBSD.

Before you shake your head, I am going to say that I can boot both, so long as I change the BIOS setting of "Drive 1" and "Drive 2", putting as Drive 1 the one I want to boot.  So it's all booting OK as long as I'm willing to do BIOS settings to change it.

I will briefly describe the situation on both hard drives.

On the SATA drive, I installed Ubuntu 8.04.3 while the IDE drive was disconnected, to save myself from any potential headaches.  The install options were just about as default as one can get.  It's using Grub, of course, and it's installed in the MBR of the SATA drive.

On the IDE drive, I have essentially 2 primary partitions (well, and an extended for the swap partition).  The first partition is Ubuntu 6.06, and it uses Grub to boot.  I specifically used grub-install to install the Grub loader into the boot sector of the first partition of the IDE drive, not onto the MBR of the overall IDE hard drive.  The second partition is FreeBSD, and it as well has boot code installed in its boot sector.  The MBR of the IDE hard drive is some very small and elegant FreeBSD Boot Manager which just allows you to press F1 or F2, depending on which partition you want to boot.  Based on your choice, it will find the boot sector in that partition and execute the code there.  By default Ubuntu installs the Grub initial boot code in the MBR of a hard drive, but like I said I put it in the boot sector of the first partition to allow everything to work with the elegant Boot Manager that I just described.

Ideally, what I would like to have set up is as follows.

1. In BIOS, make the SATA drive the "Drive 1" so that by default the BIOS tries to boot from it first.  I have already done this and it works.

2. Write some Grub code (/boot/grub/menu.lst) on the Ubuntu 8.04 install that presents an option to boot the MBR on the IDE hard drive, and fool the boot process to think that the IDE is the "Drive 1", not "Drive 2" (the settings in BIOS).

So far I have this code in my menu.lst:

```

title           Boot old hard drive...
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```The second line above, "(hd1,0)", essentially means the Ubuntu 6.06 partition on my IDE hard drive.  I'd actually like to boot the MBR of the IDE, not just the first partition, so that the Boot Manager for the IDE hard drive comes up and allows me to choose Ubuntu 6.06 or FreeBSD.  I guess I should change "(hd1,0)" to read just "(hd1)"?  I tried this and it complained.  How do I specify just the hd1 hard drive (the entire drive)?

Regardless, I tried the exact code above.  Supposedly it should boot the 1st partition (Ubuntu 6.06) on my IDE.  It does find the Grub loader on that partition OK, and I get these messages:

```

Starting up...
GRUB Loading stage2

```And then it hangs indefinitely.  Also I tried making the root "(hd1,1)" to try booting FreeBSD, and just as well, the boot code for FreeBSD was executed, but then it hangs.

It seems that it's trying to find files on the wrong disk or something maybe?  Perhaps the "map" statements above are not doing their job properly?

---

### Post by mikewhatever on 2009-08-13
I don't think you need the mapping, this isn't Windows after all.

Try the following to point GRUB to the second hdd's MBR
> title           Boot old hard drive...
root    (hd1)
chainloader     +1

or these to the system partition on the second hdd

> title      Ubuntu 6.06
root    (hd1,0)
chainloader     +1

title      Free BSD
root    (hd1,1)
chainloader     +1

---

### Post by Rambetter on 2009-08-13
```
title      Free BSD
root    (hd1,1)
chainloader     +1
```The above works and FreeBSD boots successfully, thanks so much for the info.

```
title      Ubuntu 6.06
root    (hd1,0)
chainloader     +1
```The above fails, the error messazge is as follows:

```
  Booting 'Ubuntu, kernel 2.6.15-54-686'

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.15-54-686 root=/dev/hda1 ro quiet

Error 15: File not found

Press any key to continue...
```I could probably fix it by modifying the menu.lst on the Ubuntu 6.06 install, but I really don't want to do that, because if and when I make that hard drive the "Drive 1" again in BIOS, I will have to un-do those changes.  Any ideas on how to elegantly make Ubuntu 6.06 load on my second (IDE) hard drive?

By the way, 

```
title           Boot old hard drive...
root    (hd1)
chainloader     +1                      
```That worked too, and it did load the Boot Manager on the IDE, and I was able to successfully boot FreeBSD using the Boot Manager.  However, when I select Linux (Ubuntu 6.06) from the Boot Manager, it fails with the same error as above.

---

### Post by mikewhatever on 2009-08-14
Well, root (hdX,Y) must point to a /boot directory with the files specified in the menu.lst. root (hd0,0) apparently points to the other hdd, so I am afraid you'd have to decide on the way you want to boot and modify things accordingly.

---

### Post by presence1960 on 2009-08-14
boot into Hardy and download the Boot Info Script from my signature to the desktop. Open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
``` 
This will create a RESULTS.txt file on the desktop. paste the contents of that file back here. This will shows us more info about your setup and boot process.

---

