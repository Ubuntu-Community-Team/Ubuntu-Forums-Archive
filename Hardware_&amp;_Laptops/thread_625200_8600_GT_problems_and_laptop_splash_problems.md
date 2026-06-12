---
title: "8600 GT problems and laptop splash problems"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by TaylorHelferty on 2007-11-27
Two problems:

1. On my desktop I recently installed Ubuntu 7.10 x64, with an 8600 GT video card. When booting and shutting down, my screen turns off (does not just go black, but actually temporarily loses the signal during the loading screen) but comes back on on the welcome screen. Before installing the restricted drivers, I couldn't do anything very graphic intensive, but my screen was at the correct resolution of 1650x1080 (that's it, right) for a 22" widescreen monitor and everything looked great. I installed the restricted drivers and now it's completely ******. When I put it to full resolution, everything goes enormous and I have to scroll around the screen by moving my mouse to the sides to see the rest of it. When I uninstall the restricted drivers, resolution goes back to normal. This also happens when I use envy to install the up-to-date drivers from Nvidia. Any ideas?

2. I also installed Gutsy i386 on my Toshiba A20 laptop, and everything works fine except upon startup - while loading and on the splash screen - the screen resolution is at 1280x1024, which is too large for my laptop screen (although when I'm at the actual desktop the resolution is at its normal and working 1024x768). I tried changing /etc/usplash.conf to 1024x768, but that didn't change anything. What else is there to do?


Any help would be very much appreciated, as I love Ubuntu and would love to have it working properly, especially for my desktop.

EDIT:3rd minor question: Can two versions of Linux on the same hard drive use the same swap partition? I have XP and Ubuntu now, and I was thinking of putting on Ubuntu Studio, so would I have to create a new swap partition for Studio, or could it just use the same swap as Ubuntu?

---

### Post by nickelby on 2007-11-27
Hello,

I can't really help with problem no.1(lack of experience with problems like that :)) but for no.2, I would suggest trying adding vga=791 at the end of your kernel line in your GRUB entry and see if it works.

To be more specific, this is the output of my /boot/grub/menu.lst

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=347c4c00-061d-4843-af6a-17971325bd71 ro splash vga=791
initrd          /initrd.img-2.6.22-14-generic
quiet

However, I notice that when enabling this, you will not be able to use the other tty logins (e.g. tty1, tty2, etc.). Disabling vga=791 will make it work again ;-).

---

### Post by TaylorHelferty on 2007-11-30
Tried that, didn't work. Although I just found out that it was using the wrong video driver on my laptop, so changing that fixed most of it. The loading screen is still out of proportion, but the logon screen is fine now.

I hope someone has an answer for the first problem, as I'd really love to start working on a full conversion over to Ubuntu from windows, but can't with my video card not working. Is Gutsy still not able to support the 8 series of Nvidia cards? Or is it a just something I need to set up properly?

---

### Post by jasnix on 2007-12-30
I have a Dell M1530 laptop which has the 8600m GT card. This card works fine with the nvidia-glx-new driver installed.  All I had to do was go log into ubuntu, click System > Preferences > Appearance, and then enable visual effects. It auto installed the driver for me and everything worked.

The problem I am seeing now though, is the splash screen doesn't work, it just turns the display off like you mentioned.

Hopefully we can help each other get this fixed.  Please let me know if you find a fix and I will do the same.

---

### Post by Vesslan on 2007-12-30
hi, I have the 8800GT, 64bit Ubuntu and a 22" wide screen,
and i have also noticed when booting that the screen loses its signal, but for me this is just for a few seconds then i get to the log in screen and everything is peachy.

do you have the nvidia X server settings GUI?

when i first installed ubuntu i couldn't get the video card to work, but after installing the driver from nvidias homepage it seem to work. there is however a fan bug in the latest driver, but nvidia are aware of it and have fixed it for the next version of the driver. there are ways around this bug so no need to worry.

---

### Post by XP-FREAK on 2007-12-30
I can confirm this problem.
My Dell Vostro 1500 with it's 8600GT Mobile has also problems shwoing the ubuntu splash (gusty 64bit)

It doesn't anoy me, it's only a disfigurement, but it would be nice to know how to fix it.

---

### Post by dburnett77 on 2007-12-30
If you look on Nvidia's website, the driver should be available mid-summer '08.
Until then, I hear some have luck throttling down the processor speed.  If your an avid over-clocker, this is bad news.  Go with the 7xxx series in that case.

---

### Post by Vesslan on 2007-12-30
according to:
[http://www.nvnews.net/vbulletin/showthread.php?t=104713&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=104713&page=3)
zander (of nvidia): "I don't know when an updated driver will become available, but due to christmas, etc., it won't be until sometime early next year"

---

### Post by XP-FREAK on 2007-12-30
Well, the driver makes no problems, beryl and so on a running really great with my 8600GT
Only the ubuntu splash on booting and shutting down is not shown. It's no the end of the world but it's a bit annoying >_<

---

### Post by tgalati4 on 2007-12-30
Regarding swap:

You can have many distros share the same swap partition.  Be sure to turn "Hibernate" off in power management.  During hibernation a snapshot of the entire RAM is compressed and written to the swap disk as "restore image".  When booting, the detection of this "restore image" will load it back into memory to resume your hibernation session.  On my computer, this takes as long as a cold boot (with 2 GB RAM), so I don't use it.

If you hibernate in one distro and resume in another distro, strange results will surely happen.  I use suspend-to-RAM instead.  Although Gutsy broke this for some machines (a kernel change in memory allocation from SLAB to SLUB).

Good luck.

---

### Post by miig on 2008-01-28
I had the same problem (black screen) with my   Vostro 1500 NV 8600GT

I followed this how to  and it worked for me

[http://ubuntuforums.org/showthread.php?t=622018&highlight=black+screen+gutsy]("http://ubuntuforums.org/showthread.php?t=622018&highlight=black+screen+gutsy")

---

