---
title: "Installing ubuntu on usb stick messed up macbook pro"
date: 2010-01-04
forum: Hardware
---

### Post by Olnex on 2010-01-04
I tried to install Ubuntu 9.10 on usb stick on my macbook pro, I did not set GRUB installed to usb so it might be installed on MBR, then I restarted, there is a folder icon with question mark on a white background, what can I do now?

Thanks a lot!

---

### Post by madmax.santana on 2010-01-04
Could you please explain what exactly appears? Is there some text like "there is no such partition" or "file not found" or "grub rescue>" thing?

And also, which type of Karmic did you install? Was it a netbook remix, a ppc, a x64 or what?

---

### Post by Olnex on 2010-01-04
I booted from Ubuntu 9.10 desktop cd x86, at the same time I inserted a usb stick into macbook pro, then I pressed C to start from CD, then I selected Install Ubuntu, in partition window I selected erase and use entire disk to sdb(usb stick), then after install, I restarted, then I got a white screen with a gray folder icon at the center, on the icon there is a question mark.

I tried to insert the OSX disk but it does not help, also, I remembered I've set up a password for firmware something so it cannot be started from other source.

---

### Post by Pascal11110 on 2010-01-04
Basically you get that same screen if you put a new hard drive into a mac computer, so I'm wondering if you somehow erased your partition table or something like that. I would suggest downloading parted magic and booting to that to see what your hard drive looks like at this point

---

### Post by Olnex on 2010-01-04
I solved the problem, what I did:

1 remove the hard disk in Macbook Pro, move it to another PC laptop, boot from GParted livecd.

2 delete all partitions sda*

3 move it back to macbook pro

4 boot using OSX install disc(this time there is no question mark)

5 Run terminal and use fdisk -u and fdisk -i to restore MBR (I used both, can't remember the order)

6 Install OSX without problem.

7 Boot into OSX and use bootcamp to allocate some space for Ubuntu

8 Install Ubuntu dual-boot with OSX on the previous allocated space

9 Of course I installed refit

---

### Post by Pascal11110 on 2010-01-04
Did you also figure out what caused the problem in the first place or is that still a mystery?

---

### Post by Olnex on 2010-01-04
Yes I did, what I did was:

1 Boot from Ubuntu 9.10 Desktop livecd, at the same time, a usb stick is inserted.

2 Install Ubuntu, in the partitioning window, select erase and use entire disk with the usb stick

3 Install

I guess the problem is the installer modified my hard disk's MBR so OSX won't recognize the harddisk

---

### Post by darkksyde on 2010-01-06
unfortunatly u have a mac and theres nothing u can do

---

### Post by Pascal11110 on 2010-01-06
I still think that's odd that that happened though because I've never heard of anyone else having this problem and I'm sure people have tried it before. Also I suggest using this for USB ubuntu loads (although I think it may only work for 8.1 and it only runs on windows) it's called USB-Installer-for-Ubuntu-8.10-v0.2. I'm sure they'll come out with later versions of it but it has worked great for the pen drives I've done, and it allows you to set you pen drive as eith 1, 2, 3, or 4 gig with persistence or 1 gig without persistence so is a great tool.

---

