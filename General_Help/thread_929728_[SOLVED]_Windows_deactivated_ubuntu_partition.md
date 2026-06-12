---
title: "[SOLVED] Windows deactivated ubuntu partition"
date: 2008-09-25
forum: General Help
---

### Post by godd4242 on 2008-09-25
Hello all. Just recently had to use a small empty 2gig partition on my Toshiba tecra m4 HDD to install linux, because I need to run some programs for school. However, this has deactivated my 50gig ubuntu partition. THe worst part was that windows didn't have any drivers for my WiFi and LAN, so it's been brutal trying to fix. But, the problem is, I'm stuck in windows, and I really really really don't want to be. I cringe every time I see that milky blue sky over a green hill desktop background. I need to know how, in windows, how to reactivate my main linux partition with all off my crap. Since this partition is small, I have room for my programs, GSP and iTunes, that my school demands that I use. However, I only have 220mb free. Not enough to do any real recreational computing obviously. 

So I need my linux partition to be reactivated through windows. It's designation is C. When I installed Windows it warned me it was going to deactivate my other partition and gave me a system path to reopen them. However, I've been through every option under control control panel and HDD and there's nothing there. Windows thinks my entire HDD is just this 2gig partition. So, Ubuntu users, how do I save my computer from having only Windows be bootable?

---

### Post by Elfy on 2008-09-25
You need to reinstall grub I suspect, use your livecd to do so or you can use supergrub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by godd4242 on 2008-09-25
> **forestpixie said:**
> You need to reinstall grub I suspect, use your livecd to do so or you can use supergrub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Right, did that, and am now thankfully back in Ubuntu. However, GRUB does not identify my windows install. 

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 8.04, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 8.04, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 8.04, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=0f285761-27d4-4dbd-bad1-396a98d8029f ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows XP
rootnoverify    (hd0,1)
makeactive
chainloader +1


the last one I just added, as per instructions in the ubuntu documentation you provided.

---

### Post by Elfy on 2008-09-25
can you run ```
sudo fdisk -l
``` and post that here please.

---

### Post by godd4242 on 2008-09-25
> **forestpixie said:**
> can you run ```
sudo fdisk -l
``` and post that here please.

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42244223

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7108    57094978+  83  Linux
/dev/sda2   *        7109        7295     1502077+   7  HPFS/NTFS
dking@dking-laptop:~$ 

```

Just for posterity really, I've managed to resolve this error by manually telling grub that the second partition has windows on it. Heres the link

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by godd4242 on 2008-09-25
Also, if you tell me how to place the "solved" designation on this thread, I'd appreciate it.

---

### Post by overdrank on 2008-09-25
> **godd4242 said:**
> Also, if you tell me how to place the "solved" designation on this thread, I'd appreciate it.

Hi and to mark the thread solved you can use thread tools, also see the link in my signature.

---

### Post by semitone36 on 2008-09-25
To mark as solved go up to the top of the thread and click on "thread options". It'll give you 5 or so options but the last one will be "mark as solved"

---

