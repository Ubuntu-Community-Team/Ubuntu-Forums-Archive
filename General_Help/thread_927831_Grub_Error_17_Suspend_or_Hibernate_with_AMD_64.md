---
title: "Grub Error 17 Suspend or Hibernate with AMD 64"
date: 2008-09-23
forum: General Help
---

### Post by wetmonkey on 2008-09-23
This post is more to help give back a bit.  There are solutions provided to similar issues, but I found that it was easy to go down the wrong paths in trying to fix the specific problem.  I am using keyword bait for the information I searched for in trying to track down the issue.  I never realized until a day of searching that the hibernate and sleep feature was what was causing this.  I was searching for Grub error 17, superblocks, etc which were symptoms of the main bug.  

From what I can determine through searching and posting to launchpad this only effects AMD 64 systems.
The problem exists when using the sleep or hibernate features.  Putting the system to sleep or hibernate and then restarting the system corrupts the filesystem.

System: 
ASUS M2A-VM AM2 AMD 690G Micro ATX AMD Motherboard
AMD Athlon X2 BE-2400 Brisbane 2.3GHz Socket AM2 Dual-Core Processor
Western Digital Caviar SE WD2500AAJS 250GB
Ubuntu 8.04

Booting the system results in a Grub Error 17.  Attempting to use the well documented fixes for the error 17 does not repair the system.  The procedures outlined usually involve e2fsk, dumpe2fsck, root(0,0), setup grub, grub-install, etc..
Bad Super-blocks, and disk or device already in use, or bad magic number errors are common.  

Installing the OS again appears to be the only (or easiest solution).

The fix for this is outlined in the comments of the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

 Essentially the AMD system has an issue with iommu.  

The fix is to add iommu=soft to the kernel startup once you have a stable system. 

In the terminal 
```
gksudo gedit /boot/grub/menu.lst
```
In Gedit go down to the bottom of the file.
There will be lines similar to 
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e978737-c38a-4364-a48b-214b00784931 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e978737-c38a-4364-a48b-214b00784931 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

add "iommu=soft" at the end of the kernel lines

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e978737-c38a-4364-a48b-214b00784931 ro quiet splash iommu=soft
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e978737-c38a-4364-a48b-214b00784931 ro single iommu=soft
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```


Hibernate and Suspend/Sleep will work now without corrupting the system.

---

### Post by SeanBlader on 2008-10-12
Seems to have worked after testing with a few suspend cycles. Thanks WetMonkey for finding the bug listing and sorting through the comments on it to find this. And thanks for tagging your post here well. Helped me out on my HP tablet. As far as I'm concerned suspend has been my holy grail with ubuntu and is the main issue that has kept me from converting completely.

---

### Post by adrian15 on 2008-10-13
> **wetmonkey said:**
> 
The fix is to add iommu=soft to the kernel startup once you have a stable system. 


Do not forget to add iommu=soft parametre to the kopt update-grub variable inside menu.lst file so that changes resist to kernel updates.

adrian15

---

### Post by wetmonkey on 2008-10-13
> **SeanBlader said:**
> Seems to have worked after testing with a few suspend cycles. Thanks WetMonkey for finding the bug listing and sorting through the comments on it to find this. And thanks for tagging your post here well. Helped me out on my HP tablet. As far as I'm concerned suspend has been my holy grail with ubuntu and is the main issue that has kept me from converting completely.

I am glad it worked out for you!

---

### Post by wetmonkey on 2008-10-13
The original bug on launchpad where I found this ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537))
has a comment that Intrepid may have fixed the bug. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537/comments/39](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537/comments/39)


> 
 Alan Groupe wrote on 2008-10-10: (permalink)

I have the same issue as everyone else here. Motherboard is an Asus M2N-MX SE+ with an AMD Athlon64 X2 5000+, not overclocked.

I downloaded and installed the current 8.10 beta. When suspended, the system still hung on resume, but after hitting reset, I got the GRUB menu and booted just fine, rather than the dreaded Grub error 17. So the new kernel does seem to take care of the critical error, at least for me.

While I still can't resume from suspend (hibernate is fine), I'm much less concerned about being able to use suspend than I am about blowing away my system if I suspend accidentally, so I think I'll go with disabling suspend from /etc/default, but just wanted to respond to Leann.


---

