---
title: "Can't boot computer from hard disk or from Parted Magic CD."
date: 2013-04-11
forum: Hardware
---

### Post by thunderpenguin on 2013-04-11
Hi

I have a desktop computer with Windows 7 Ultimate 64 bit and Ubuntu 12.10 64 bit.

My motherboard is Asrock 970 Extreme 4 [http://www.asrock.com/mb/AMD/970%20Extreme4/](http://www.asrock.com/mb/AMD/970%20Extreme4/) which is a UEFI motherboard but I have my hard disk partitioned as MBR not GPT.

My hard disk is 1 TB and Linux and Windows partitions get half space each.

Last night on Windows I was downloading a torrent with uTorrent and before going to bed I set uTorrent to shut down the computer when the download completes.

Today after I woke up the computer is off so that must mean the download completed.

I booted the computer but instead of getting the GRUB menu I got an error```
out of memory
Aborted. Press any key to exit
```.

I guessed that the torrent download filled up my hard drive so I booted from a Parted Magic CD [http://partedmagic.com](http://partedmagic.com) to delete any unneeded files on my hard drive and get my computer to boot again.

I have previously successfully used Parted Magic's included Clonezilla to create images of my Windows C and Linux root partitions.

When I booted Parted Magic I got this error ```
syslinux_boot_linux() failed: Error 0
linux.c32: Boot aborted!
```

Please help me get my computer booting correctly again.

---

### Post by oldfred on 2013-04-11
Be sure to boot any repair flash drives or DVDs in BIOS mode, or else you may get efi changes which will further corrupt system. Since MBR you have to boot with BIOS. 
Windows only boots from UEFI with gpt partitioning, but Ubuntu will boot gpt in BIOS mode also.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by thunderpenguin on 2013-04-11
I booted from my Ubuntu 12.10 DVD and I did Memtest.

At Pass 45% it showed more than 300000 errors

```
Pass 45%

Test 0%

Test #7  Random number sequence

Testing 196K - 2048M 3378M

Pattern 9ed42d40 

Errors more than 300 000

ECC Errs 0
```


My computer has a single stick of 8GB RAM.

This is a new computer and its been working fine for two weeks so I don't know why there's a problem in the RAM now.

Is there a way to fix this other than replacing the RAM?

---

### Post by ahallubuntu on 2013-04-11
~

---

### Post by thunderpenguin on 2013-04-11
The video card is MSI GTX 660 which is already overclocked by MSI [http://www.msi.com/product/vga/N660-TF-2GD5-OC.html](http://www.msi.com/product/vga/N660-TF-2GD5-OC.html) but nothing else is overclocked.

---

### Post by thunderpenguin on 2013-04-11
I contacted the shop I bought my computer parts from and they said bring the RAM module to them tomorrow. I hope everything is solved.

---

