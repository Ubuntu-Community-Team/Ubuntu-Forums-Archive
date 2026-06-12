---
title: "Booting hangs at &quot;Mounting root file system&quot;"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by russasaurusRex on 2007-06-15
Hi,

I've just purchased a PCI card (Silicon Image Sil0680) to add some more IDE channels to my machine, however when I install the card and boot my machine it hangs during the boot sequence near the beginning when it says "Mounting root file system" followed by "Waiting for root file system".

Note, that I've not moved my existing hard drive onto the new IDE channel, in fact I've not connected anything to the new IDE channels as yet!

I'm at a bit of a loss as to what's going on as I'm using GRUB to allow me to boot both Ubuntu and Windows. It's still working perfectly fine, and I'm able to boot Windows without a problem, however for me to be able to boot into Ubuntu I have to remove the PCI card from my machine.

I suspect the problem is being caused by the sequence in which Ubuntu detects the IDE channels, however I don't know this for sure and don't really know how to go about fixing it. My system currently has a single hard drive, which is partitioned. In the hope that it'll help someone diagnose the problem and help me fix it, here's the output I get from running fdisk:

```
russell@homer:~$ sudo fdisk -lu

Disk /dev/hdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   117194174    58597056    7  HPFS/NTFS
/dev/hdc2       117194175   490223474   186514650    5  Extended
/dev/hdc5       117194238   234581129    58693446   83  Linux
/dev/hdc6       234581193   293170184    29294496   82  Linux swap / Solaris
/dev/hdc7       293170248   490223474    98526613+  83  Linux
```

aTdHvAaHnNcSe to anyone who's able to solve this problem for me, or provide any useful information that'll assist.

---

### Post by russasaurusRex on 2007-06-16
Managed to solve the issue by looking around at a few seemingly unrelated threads.

For anyone reading this in the future with the same problem it's caused by the new IDE channels being detected first and thus causing, in my case, hdc to become hdg. I discovered this by using the [GParted live CD]("http://gparted.sourceforge.net/livecd.php").

I then used that information to change /etc/fstab and /boot/grub/menu.lst so that all references to hdc because hdg.

---

