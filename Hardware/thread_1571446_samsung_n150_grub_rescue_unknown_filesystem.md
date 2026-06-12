---
title: "samsung n150 grub rescue unknown filesystem"
date: 2010-09-09
forum: Hardware
---

### Post by r4zi3l on 2010-09-09
Hi guys:

Linux newbie and forum oldie, I have found an issue I cannot solve asking uncle google... or Mrs. Bing...

[I]error: no such device 3919a0f0-1b6c-47cd-a329-607dd95293c7
grub rescue>[/I]

Seems easy, but alas this is a Samsung N150 without "boot from usb" option. 

So then you think: Use the terminal!

*insmod /boot/grub/linux.mod* **gives** *error:unknown filesystem*

Ok, so I am kind of stuck. Only option I can think of is to take the N150 apart, buy a IDE/SATA to USB, format the HD0 and HD1 (or atleast delete the sys folders) and never install ubuntu again.

But the option of never installing ubuntu isn't totally of my liking. Any chance there is someone with enough knowledge to solve this riddle without me having to get the screwdriver out?? He would have a cookie rationing for a lifetime :D

Thanks a bunch in advance :KS

---

### Post by ajgreeny on 2010-09-09
> **r4zi3l said:**
> Hi guys:

Linux newbie and forum oldie, I have found an issue I cannot solve asking uncle google... or Mrs. Bing...

[I]error: no such device 3919a0f0-1b6c-47cd-a329-607dd95293c7
grub rescue>[/I]

Seems easy, but alas this is a Samsung N150 without "boot from usb" option. 

So then you think: Use the terminal!

*insmod /boot/grub/linux.mod* **gives** *error:unknown filesystem*

Ok, so I am kind of stuck. Only option I can think of is to take the N150 apart, buy a IDE/SATA to USB, format the HD0 and HD1 (or atleast delete the sys folders) and never install ubuntu again.

But the option of never installing ubuntu isn't totally of my liking. Any chance there is someone with enough knowledge to solve this riddle without me having to get the screwdriver out?? He would have a cookie rationing for a lifetime :D

Thanks a bunch in advance :KS
So, is Ubuntu installed or not, and if not where and when do you see that error message.  It seems most likely that it appears after grub, but grub is pointing to a partition with a UUID that does not exist, but if you can't install Ubuntu, where did grub come from?

More details please.

---

### Post by r4zi3l on 2010-09-10
Hi Ajgreeny:

Ubuntu for netbooks remix is installed, I was working on it. It installed it on a windows 7 starter partition (loaded the iso and let it install). 

All fine managed to get wireless working and such, then I hit update (big error, if something works don't touch it) and, well, it turned off after update. 

I forgot about the netbook and, a day later, turned it on again. Voila, grub rescue, no access to terminal via liveCD (no boot from usb) and possibly unrescueable MBR (i hope grub didn't install into sector 0 or I will be very pissed off).

I am in the process of extracting the HDD to rescue Win7 boot, but need to buy a few things... If anyone can save lil netbook from evil grub2 w/o loading a CD I will be very grateful.

---

### Post by huygens on 2010-11-07
Hello,
Did you manage to find a solution to this problem?

---

### Post by MelissaCutler on 2011-02-08
I'm very confused about you saying you can't boot from a USB.  I also have an Samsung N150 netbook.  All I had to do was go into the BIOS settings whist the machine was booting up, and change the boot priority order.  I have set mine up so that it will look for a USB pen drive, and look for an external USB CD drive, and then boot from the hard drive if if doesn't find either.

I've only had a problem once; when a Samsung recovery tool re-wrote my boot sector and stoped my laptop from booting.  I fixed that my booting from the Ubuntu installation flash drive, and using that to get a terminal and reinstall grub.  It was a bit of a hassle, but I figured it out.

Why can't you boot from a flash drive, is it just a bios settings thing, or am I missing something fundamental?

Good luck

---

