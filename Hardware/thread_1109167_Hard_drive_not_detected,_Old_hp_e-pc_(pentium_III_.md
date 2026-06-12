---
title: "Hard drive not detected, Old hp e-pc (pentium III 1000MHz)"
date: 2009-03-28
forum: Hardware
---

### Post by Emorroiman on 2009-03-28
Hi everybody.

I got an old PC and wanted to install xubuntu, but to no avail. The hard drive is not detected, so I cannot setup the partitions during the installation process.

I'm using xubuntu 8.10 desktop i386 (I should have downloaded the alternate version, this one takes too long to start).

These are the PC specs:
* HP e-pc system number P4266A
* Pentium III 1000EB MHz 256 MB RAM 256KB cache
* AMIBIOS 02/22/2001
* System Name: e-Vectra
* Chipset: Intel 810E
* HP BIOS: IN.02.02
* Hard drive: Seagate 120GB (this is newer than the computer)

I have also tried with ubuntu 7.10 desktop i386, with the same results (the drive is not recognized by gparted).

Windows XP install CD recognizes it without issues.

Any help will be appreciated.

---

### Post by ranch hand on 2009-03-28
When you boot with the live CDs do any files from your computer show up under Places-> Home-> file system?

If so; right click on them and unmount them and then try gparted.

I saw your post in the old crappy thread.  I am on a HP pavilion xt993 right now.

---

### Post by Emorroiman on 2009-03-29
Thanks for your help, ranch hand.

Unfortunately, there is nothing to unmount there. It seems the kernel of the current xubuntu does not support the chipset anymore. Is this possible?

I tried with another linux distro: vector linux light 5.9. This one recognizes the drive and allows me to prepare the partitions. It is using version 2.6.22.19 of the kernel. Since I am not a linux expert, I don't know it this is relevant or not.

I really like (x)ubuntu, maybe I should try with an older version to check if that one supports the chipset.

---

### Post by ranch hand on 2009-03-29
Well, I am giggered.

To start with - on being expert - you will note that my join date is all of 7 months ago.  This is my first foray into linux myself.

This HP that I am on right now is running an AMD Athlon 1300B.  All of 1300MHz.  I am running Ubuntu 8.10 with no problems other than it suffering from performance in comparison to my main computer (54 blizzard closed miles out on the ranch).

It seems to me that it should run on the 256Mb ram that you have but that is pretty tight.

I know that folks run Ubuntu on P3s.

I have Xbuntu installed on the other box but it is a really new box (see sig).  It is pretty nice but I have not really fooled with it.  I do know that I like it a lot better than Kubuntu (or any other KDE flavor).

What happens if you:
```

sudo cfdisk

```
?

If cfdisk sees it you could format from there and I bet the install would see that.  I would make 1 extended partition (if all you will have on it is Xbuntu) and a swap partition inside that at the right hand end (1G), a root partition at thre left hand end (10G), and the rest for home.  make them "linux native" which will be ext2.

Assuming your Live CD sees the drive;
When you try to install choose the Manual option for partitioning.
Click on the first partition in the gui and then on edit partition.
Choose "/" which is root for the first one and click the box to format and choose ext3.
Click OK (or what ever)
When that is done click on the second partition.
Click edit.
Choose /home
Choose format.
Choose ext3
OK
Click on 3rd partition.
click edit.
Choose /Swap
Choose format
Choose linux swap.

See what happens.  Speaking of which, I am also a Blacksmith.  If you know any of us you will know that we enjoy learning by doing things.  Gee what happens if I do this?  This is fun as long as you don't mind the occassional absolute diasaster.

---

### Post by mister_p_1998 on 2009-03-31
> **Emorroiman said:**
> Hi everybody.

I got an old PC and wanted to install xubuntu, but to no avail. The hard drive is not detected, so I cannot setup the partitions during the installation process.

Does your Bios see the drive?
is it set to autodetect IDE devices?
a 120GB might be a bit big for a PIII, I usually use old 20gb or 40gb in old hardware, (Ive got a lot lying around!)
Try a smaller drive and see what happens.
Steve

---

### Post by Emorroiman on 2009-04-04
Hi again.

Thanks ranch hand and mister_p_1998 for your help.

I've solved the problem: the drive was defective. I don't know how, but Windows XP didn't care about that and installed successfully on that drive. That misled me. But after testing with another drive (even older, but smaller) things started to go better.

The CD-ROM also gave me headaches; it seems too picky for my media, resulting in I/O errors when trying to install the full distro. Then, I tried to boot from USB, but to no avail. I learned from another thread here that this machine includes a fake option in the BIOS to boot from USB :mad:.

In the end, I downloaded the minimal CD (it is small enough to avoid I/O errors) and successfully installed from the net.

So, thanks again.

Emorroiman

---

### Post by ranch hand on 2009-04-04
Great news, have fun.

---

