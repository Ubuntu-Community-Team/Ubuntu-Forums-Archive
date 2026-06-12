---
title: "Ubuntu can't run on new PC?"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-08-19
I gave Ubuntu 5.04 a test run on an old P2 350Mhz system and I liked it, but the old system was just too slow. So I got a good deal on an emachines PC that was on sale and planned on using it to run Ubuntu, but when I tried the LiveCD it always freezes at the "Ubuntu Linux is for Human Beings" screen and the mouse doesn't work either. I heard the startup music but that's it. It's frozen and I have to unplug the system from the outlet just to reboot the system.  Why does Ubuntu freeze up and refuse to work on this system?

Here are the specs:
eMachines W3410
AMD 64 3200+
100GB HD
Dual Layer DVD+-RW drive
ATI Radeon Xpress 200 with an open PCI Express slot
15" LCD monitor
512 MB DDR 400 3200 RAM
ATI 6-channel Audio
Network card
IEEE1394
8-in-1 Media Card reader
PS2 Keyboard
PS2 Mouse

Any ideas why Ubuntu freezes on this system? Is it the graphics card? And why doesn't the mouse work either? I can't even get to the Gnome Desktop it always freezes before that. And I can't seem to get the  logon prompt either.  ](*,)

---

### Post by jeremy on 2005-08-19
Are  you trying to install the 64 bit, or the x86 version?

---

### Post by WirelessMike on 2005-08-19
The live cd can be a little flaky, especially with concern to default graphics resolution.  Such a problem would give you symptoms like those you mention.

If you can, try to download the ubuntu-based gnoppix live cd at [http://www.gnoppix.org/](http://www.gnoppix.org/) and see if it gives you the same problem.

---

### Post by ry_ry on 2005-08-19
It's the x86 version.

I can't download CD ISO's because I'm on dial-up. No broadband available in my area. :(

Do you think if I did a full install, that it would work? And shouldn't the LiveCD work anyway, since this is suppose to give you the chance to test drive Ubuntu without a full install?

If I can't get it to work, then I guess I'll have to stick with Windows until I get a copy of a different Linux distro.

Any suggestions on why Ubuntu freezes would be great. I might try a full install and see what happens, but I don't see how that will help, since doesn't the LiveCD contain the same drivers as the full install CD?

---

### Post by guitard00d on 2005-08-19
[QUOTE=ry_ry]It's the x86 version.

I can't download CD ISO's because I'm on dial-up. No broadband available in my area. :(

Do you think if I did a full install, that it would work? And shouldn't the LiveCD work anyway, since this is suppose to give you the chance to test drive Ubuntu without a full install?

If I can't get it to work, then I guess I'll have to stick with Windows until I get a copy of a different Linux distro.

Any suggestions on why Ubuntu freezes would be great. I might try a full install and see what happens, but I don't see how that will help, since doesn't the LiveCD contain the same drivers as the full install CD?[/QUOTE]
 Wouldn't you need an x64 version for an x64 processor, rather than the x86 version? I'm just asking because it seems to me like you'd have to have the x64 version, just like you'd need a PPC version to install it on a Mac. But, I could be wrong, that's why I'm asking.

---

### Post by ry_ry on 2005-08-19
No.
A AMD 64 chip is a x86 chip but with 64 bit ability. You can choose to either run a 32 bit OS, such as Windows XP or 32-bit Ubuntu, etc. or you can choose to run the 64 bit version OS like Windows 64 or Ubuntu 64 version.

You can't use 32 bit drivers on a 64 bit OS, and most software is still only 32 bit versions only. I choose to stick with the 32 bit Ubuntu x86 version because it's got better support in software etc. than the 64bit version.

A PowerPC is based on different chip architecture than a x86 based one. That's why you can't use PowerPC software on a x86 system unless you use some sort of software emulation.

---

### Post by ry_ry on 2005-08-20
Update:
Well, I threw in a spare 80GB drive into this new system and went through the full install of Ubuntu 5.04. Again, when it reaches the "Ubuntu Linux is for Humans" graphics screen the whole system completely freezes up. Can't do anything except pull the power plug out so I could reboot the system. It gave me the login screen and then when that "Ubuntu Linux is for Humans" screen pops up, the system freezes. So why does the login screen work but nothing else does? The mouse pointer just stays frozen in the middle of the screen too.  This really sucks ass, because before I bought this system, I bought a serial modem and a PCI Hauppauge BT878 TV tuner card so I could watch TV when I got my new system and use the external serial modem to access the internet. But now, that plan has been trashed because Ubuntu has some weird problem and completely freezes the PC. I feel like Ubuntu has completely wasted my time and money. Maybe it's the graphics card, or some other hardware issue, but with the system completely frozen, there doesn't seem to be any way to find out what the problem is.

If nobody can help me with this issue, then I'll have to just trash my Ubuntu discs and move on and try either a different Linux distro. or just leave Windows XP on it  and maybe check back with Linux in a year or two when it matures more and has better hardware support.

If anybody has any suggestions to fix this system that would be great, otherwise it's back to Windows.  :(

---

### Post by guitard00d on 2005-08-20
[QUOTE=ry_ry]Update: I feel like Ubuntu has completely wasted my time and money.[/QUOTE]

I guess I don't see the logic there...If Ubuntu is free, how could it have wasted your money? Considering the fact that Ubuntu works on more systems than it fails to work on, I think it's safe to say that you've seriously misplaced the blame here.

---

### Post by ry_ry on 2005-08-20
guitard00d,
If you can't help me then STFU.   :-x  If you bothered to read my above post, I bought this new PC, serial modem, and tuner card just so I could run Ubuntu on it since my very old P2 system is too freakn slow. Hense the money part.

And since I'm a newb, I naturally got very frustrated when Ubuntu was locking up my system and I didn't know what to do. And due to that frustration I vented some of my anger out about Ubuntu because it appeared that I wasn't going to be able to fix the problem.

And while you're too busying making personal comments about me instead of helping me, I decided to make a run through the forums again and found out how to solve my problem, no thanks to you of course.

It turned out that it was my video driver wasn't working right with my graphics card so I found out elsewhere in this forum how to edit the xorg.conf file from the command line and change it to vesa and then reboot. I'm in the process of installing the proper drivers.

---

### Post by crt on 2005-08-20
ry ry,   you have to forgive some these die hard linux people. Any mention of Windows or Micro$oft makes them want to run down the street throwing montoff cocktails at Bill Gates. Alot of these people need to grow up and gain a little more understanding of what computers are and how they actually operate. Instead of bashing anyone who mentions WINDOWS or says that their operating system is WINDOWS LIKE, they should say, yeah, Graphical user interfaces are a great idea, see look at the Macintosh, look at ubuntu, look at Linspire.
But their undying hatred for Micro$oft makes them sweat and they start convulsing.
Fortunately, the true Linux programmers and developers are much more mature than that.
As Rodney would say, "can't we all just get along".

Glad you got it working, ubuntu is really a great operating system.

R

---

### Post by tallbonobo on 2005-08-28
Hope this thread isn't dead yet.  I too bought a new emachines t6520 pc last week and have been trying to get some linux up and running on it.  I managed to get Suse linux live dvd running in a lower resolution mode ( 1024x768 ) after playing with the bios settings (had to change LDT speed from 800MHz to auto detect).  But with ubuntu the live install just hangs with a frozen mouse pointer saying something like "Ubuntu is for humans".   I had to use "live noapic nolapic" to get it this far.  Both 32-bit and 64-bit live cds do the same thing.

ry_ry: you said you managed to get it to work.  What exactly did you do with the graphics settings?  Can you enter an option on the command line when booting the live CD?  Thanks. 

I have now spent a few hours on this stuff and I'd like to get to the bottom of this soon.

---

### Post by ry_ry on 2005-08-28
Hi tallbonobo!

I've gotten further and I'm about to do a final setup. Right now, I've been doing test installs and working through problems and writing down or printing out the answers. Learning Linux is like going back to school. :) Anyway, I do a normal hard drive install using the 32bit version of Ubuntu 5.04. When I reach the login screen for the very first time this is what I do:
1. use Ctrl-Alt-F1 to reach the text login, and login as usual.
2. I use "sudo vi /etc/X11/xorg.conf" and edit my xorg.conf file, I change the driver "ATI" in the Device section to "vesa" and save.
3. I then "sudo reboot".
4. Now you should reach the login screen and be able to login normally and reach the gnome desktop without it locking up.
5. If your clock is running faster than normal, put "noapic" in your grub file and reboot. Then set your clock. Also set UTC=yes to UTC=no because this will fix the clock to use local time.
6. If you want 3D graphics, go and download the ATI installer program to install the graphics driver for the ATI Xpress 200. I'm guessing that you have this type of graphics card.

My motherboard is a MSI 7145 RS480M. You might notice that Ubuntu  runs slower than my grandma even on this nice AMD64 system. DMA does not work right out of the box on my system. As far as I can tell I'm going to have to compile my kernel to use DMA. I know 2.6.11 kernel has DMA support for this system out of the box, but I'm going to try the recompile option that I found in this forum to turn on DMA in the kernel 2.6.10.

Here is the link to the forum post on how to use the ATI installer, this worked on my emachines W3410 with Xpress 200 onboard graphics:
[http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13](http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13)
Scroll down to the post by Epskampie and follow his how to.

HOWTO: Kernel Compilation for Newbies
[http://www.ubuntuforums.org/showthread.php?t=56835&highlight=ati+fglrx+8.14.13](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=ati+fglrx+8.14.13)
I'm going to use this to turn on DMA for the Ubuntu kernel 2.6.10 and give that a shot.

Unofficial Ubuntu 5.04 Starter Guide
[http://ubuntuguide.org/](http://ubuntuguide.org/)
Here you'll found out how to edit the UTC to change it from yes to no.
You're also found out how to edit the grub file "/boot/grub/menu.lst"

If you use "lspci" in terminal window and a bunch of stuff comes up Unknown devices just make a connection to the internet and type "sudo update-pciids" and after that finishes then type "sudo update-usbids" and these two will download updated information for your devices so the next time you type "lspci" in the terminal window most if not all of your devices will be listed and named correctly.

To use "sudo vi /etc/X11/xorg.conf at the command line:
"I" key will insert text
"Ctrl-C" will bring you out of inserting text and if pressed again will take you to where you can save the changed file. I think I typed ":save /etc/X11/xorg.conf"
"Ctrl-Z" exits editing mode completely

I hope this helps, or at least helps someone out there.

---

### Post by ry_ry on 2005-08-28
Oh yeah, one more quick thing.
In installing the ATI drivers, use the 8.16.20 newest version and just insert this version number into that "how to" above.

---

### Post by fragmental on 2005-08-28
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA) is some information on enabling DMA, which might help.

---

### Post by ry_ry on 2005-08-29
Hi fragmental,

Yes I tried what was stated in the DMA wiki but it doesn't work on my system. But the wiki is a great source of information.

---

