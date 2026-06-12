---
title: "[SOLVED] Dual Boot problems, again"
date: 2008-07-29
forum: General Help
---

### Post by jasex on 2008-07-29
So, I originally had problems getting Grub to come up by itself... now I've fixed it kind of.... Problem is it won't let me boot my Windows entry... it just says "Starting Up..." and doesn't do anything

title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

There's my entry...

But if I disable the Linux drive it boots perfectly fine... and it is visible and mountable inside Ubuntu

I am on 8.04.

Insight please.

---

### Post by Potatoj316 on 2008-07-29
post the output of this command with all your drives connected
```
fdisk -l
```
that is a lowercase L not a number one

---

### Post by jasex on 2008-07-29
```
[sudo] password for thursday: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89d889d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        9604    67143667+  83  Linux
/dev/sda3            9605        9729     1004062+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000234a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS
thursday@Yggdrasil:~$ 

```

I kind of figured... I've used fdisk before :p

That's what I got... but it's gibberish to me.

Well not exactly... but I don't see anything readily wrong.

---

### Post by northern lights on 2008-07-29
When GRUB starts, do you get a menu?
From what you're saying it cannot ne deduced whether you actually select the Windows entry and it thereupon fails to boot or whether you can't select it in the first place.

In case you can't select it, you have to adjust the menu delay or, as a short term solution, press ESC while GRUB is starting up.
To get to see the menu for good, run ```
gksu gedit /boot/grub/menu.lst
```comment 'hiddenmenu' and set 'timeout' to 10, default is 3 (seconds). Alternatively, install 'StartupManager' from the repos.

In case you can select and it screws up after, (hd1,0) is most likely wrong.
Post 'fdisk -l'

---

### Post by Potatoj316 on 2008-07-29
could you post the bottom of your menu.lst file?  I would like to see all of the items listed as possible boot devices.

I believe if you changed it to hd2,0 it would work.  But I can get a better idea when I see the rest of the entries.

northern lights, did you see the previous post?  Im quite certain that is fdisk -l

---

### Post by northern lights on 2008-07-29
> **Potatoj316 said:**
> northern lights, did you see the previous post?  Im quite certain that is fdisk -lyup. so am i. must have been typin' away already.

Btw, in GRUB syntax, sdb1 should be (hd1,0)...

---

### Post by Potatoj316 on 2008-07-29
I understand that sdb1 should be hd1,0 but aparently that isnt working.  Perhaps hd0,0 would work, or maybe hd2,0 would work, but the fact is it isnt working now and we have to fix it.  Seeing the other menu.lst entries will probably help.  It was previously stated that taking out one of the HDs resulted it it working, this leads me to believe that the number is not what it should be.

---

### Post by northern lights on 2008-07-29
> **Potatoj316 said:**
> It was previously stated that taking out one of the HDs resulted it it working, this leads me to believe that the number is not what it should be.
Very true. Hadn't thought about it that way. If you were right and it's the device number, then, if taking out sda results in it working, logic would have it that sdb "got shifted one up". And if it indeed had gotten shifted up, it would be device hd2 with the Linux drive present. Followed the logic - makes absolute sense.

Nonetheless it'd be very weird, if sdb would not end up being grub device hd1. Which is what led me to thinking that the menu doesn't appear with sda present and that's the issue is in grub just booting the default entry. Unfortunately, the OP hasn't answered the related question.

---

### Post by jasex on 2008-07-29
```
splashimage=(hd0,0)/boot/grub/splashimages/53373-NightOfUbuntu.xpm.gz

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-18-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.24-18-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro single
initrd          /boot/initrd.img-2.6.24-18-generic

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=32624448-d9c6-45a3-9b4b-772dfbbd5099 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows Vista
root (hd1,0)
savedefault
makeactive
chainloader +1

```

That's the entry.

---

### Post by northern lights on 2008-07-30
> **jasex said:**
> title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

There's my entry...

But if I disable the Linux drive it boots perfectly fine... and it is visible and mountable inside Ubuntu

Insight please.
I must have not been thinking yesterday at all. The problem does not lie in grub or its settings whatsoever.

It's Windows. In order for Windows to boot properly it needs to reside on the first partition of the first hdd. Linux doesn't but Windows is that picky.

Since your Windows has a drive of its own, this problem can be solved either via menu.lst entries or physically by swapping drives.

Physically:
Flip slave and master or, respectively, slots on the board/controller. In other words, connect the Windows drive where you had the Linux one and vice versa. Change grub's Linux entries to (hd1,0) and the Windows one to (hd0,0).

Via the grub menu:
If you don't want to refer to the physical solution, you have to make the Windows bootloader (which you are chainloading from GRUB) believe that it's on the first partition, while it really isn't. Use the 'map' command. Add the following to your menu.lst: ```
map (hd0) (hd1)
map (hd1) (hd0)
```

Reading: [GRUB manual 13.3.23 map]("http://www.gnu.org/software/grub/manual/html_node/map.html")
[GRUB manual 4.2.6 DOS/Windows]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows")

---

### Post by jasex on 2008-07-30
And therein lies the problem, every time I try to switch the drives around... it will just try to boot windows without going to grub... Maybe I'm doing something wrong... but this problem of thick cheese sir... It's thick... the map did nothing... linux still boots... still hangs for Windows though. 


By The Way... MAP didn't work.


Furthermore... maybe I placed it wrong??

---

### Post by jasex on 2008-07-31
Perhaps something to do with my motherboard?

---

### Post by 3rods on 2008-07-31
Is this XP or... Vista?  *shudders*

If it's vista, use this to get things cleaned up:
[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

The reason it is going to windows if you switch the drives is because the bootloader is on the other drive (the Ubuntu drive with GRUB), to fix that, you need to have windows be the bootloader and add Ubuntu. You *might* be able to put grub on the windows drive, but I'm pretty positive that I tried this and bashed windows. Had to boot recovery console and bootrec.exe /fixmbr /fixboot to fix it. 

If you boot in to windows and add Ubuntu with either easyBCD (Vista) or My Computer > *right-click* > Properties > Advanced tab > startup & recovery - hit settings button. Edit the bootloader in there. Google it first and make a back up. Obviously, if you mess the XP part up, it won't boot. 

So, either you have XP/Vista bootloader start and then hand off to GRUB or you have GRUB start and hand off to XP (GRUB and Vista don't play nice together last time I tried). Whoever is in the first slot, physically, has to handle the bootloader OR the drive boot flag needs to be switched and the bootloader cleared from the drive.

Good luck.

---

### Post by linux_tech on 2008-07-31
Did you try a supergrub disk yet? 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by logos34 on 2008-07-31
> **jasex said:**
> 

By The Way... MAP didn't work.

Furthermore... maybe I placed it wrong??

Does yours look[ like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")?

---

### Post by jasex on 2008-07-31
You sir, logos34, are my new best friend :D 

Thank you guys very much... Like seriously, you're all getting a thanks from me, this has been plaguing me, since I use Windows to sync my wife's zune, and mod my Moto Rizr Z3, because I haven't found any thing similar to P2K commander for Linux... so...

sorry to rant and rave... I'm actually very ecstatic right now, and she will be too!!! she loves linux, and I am setting her up her own PC soon, so expect me to be asking more dumb things later.

Let's marked this solved :)

---

### Post by jasex on 2008-07-31
Forgot to mention... that it was XP... forgot... haven't been able to boot into it... in like... four months.

Had a vista business disc... but it won't work no more, because it had built in activation, because it was an OEM disc and now I can't use it anymore, after  borking the install.
Thank you so much again.

---

### Post by logos34 on 2008-07-31
Glad it's working again like it should.

Enjoy.

---

