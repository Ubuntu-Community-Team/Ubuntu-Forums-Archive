---
title: "Windows 7 not booting"
date: 2010-02-20
forum: Hardware
---

### Post by alexbardasu on 2010-02-20
Some time ago I tried to install OS X on my laptop. I wanted to try it out and to see how hard is programming for it. I forgot to install a driver and I couldn't finish the setup because after the first reboot it didn't recognize my keyboard.

It was fine since I could reinstall ubuntu whenever I wanted. The problem was that my Windows partition didn't boot up anymore. I tried to flag it as bootable from gParted but without luck. Then I booted up and Ubuntu live CD and searched for fixes.

I found a utility called mbrtools I think which should have worked as a fixmbr for Ubuntu. I was in zombie mode at 4 o'clock in the morning trying to fix my partition and I didn't realized that I installed the mbr on the Windows 7 partition. After that the system didn't recognize the partition as NTFS. I searched for recovery software and managed to rewrite the NTFS headers.

I installed Ubuntu and I was able to browse the OS partition; however, when I try to boot it from grub, it seems to load another GRUB(it says GRUB loading after I press enter) and the it gives me Error 18.

I reinstalled GRUB, but without results. I searched for an answer, but it seemed that Error 18 occurs only when loading the Linux kernel.

If you have an idea that could help me I would appreciate it.

Additional details:
fdisk -l output:
Windows 7 is on sda1

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004f004e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14590   117194143+   7  HPFS/NTFS
/dev/sda2           14591       19457    39094177+   5  Extended
/dev/sda5           14591       19251    37439451   83  Linux
/dev/sda6           19252       19457     1654663+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc4827d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
```

---

### Post by alexbardasu on 2010-02-20
If I _bump_ in any of you guys on the street, you'll have one one me.

In the mean time, can someone please move my post to general help?

---

### Post by arele on 2010-02-20
Hi... you are a lucky man!!!!!
:D

---

### Post by alexbardasu on 2010-02-20
How come?

---

### Post by HarshReality on 2010-02-20
If your trying to restore a win 7 boot mgr just use the repair function of the install CD and do 'bootrec' if I remember correctly.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Incidentally.. I setup my Win 7 drive entriely seperate (dont know why as I have only used it for a whole of 3 hours since June of last year) then I set it as a slave and installed a drive for Karmic as the primary. Once that was done I simply edited the boot menu to add the secondary windows drive as a boot option.

Of course the final result to look at here is.. linux is on a linux drive.. windows is on a windows drive and if either one fails the other keeps on going. OR I can use the boot menu in BIOS to boot the slave first and go right into windows..

grub.cfg
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 5e60a13360a112b7
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

Of course for yours it should be 0,0 Im thinking for the hd

---

### Post by alexbardasu on 2010-02-20
Thanks for the info, I already tried it and I don't think it did something because I didn't see any difference.

You have a nice setup. I also have 2 drives on my netbook, as you can see from my fdisk, but I keep one for media storage.

---

### Post by alexbardasu on 2010-02-23
I **bumped** into a dead end here. Could someone help me out?

---

