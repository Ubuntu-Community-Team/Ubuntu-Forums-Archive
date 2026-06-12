---
title: "I just want to check if this is compat. with Ubuntu"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by Lord Illidan on 2006-09-15
Hi guys.. My motherboard and CPU have finally given up the ghost...so I decided to get a new one..

I was wondering if you could give some advice quickly please..

I am planning to buy an 
[B][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=+1]Asus P5VDC-X S775 Motherboard
                                          [/SIZE][/FONT][/B]AGP & PCI-Express, DDR & DDR2
                                            SATA RAID, LAN, Audio, 64Bit

[IMG]http://www.scanmalta.com/Images/Products/MB-L14965.jpg[/IMG]

with CPU type INTEL LGA775, Chipset VIA PT880, and an Intel Dual Core 915 (2 x 2.8GHz), 4Mb Cache.

Does anyone know whether these specs are good for Ubuntu? I don't want to give up Linux if I can help it :)

---

### Post by Lord Illidan on 2006-09-15
bump..

I need an answer quickly please...can anyone help?

---

### Post by moore.bryan on 2006-09-15
*as i understand it, linux was designed for almost any system; what makes you think this wouldn't be a good choice?*

---

### Post by MrHorus on 2006-09-15
> **Lord Illidan said:**
> bump..

I need an answer quickly please...can anyone help?

Yes, it will work.

---

### Post by yota on 2006-09-15
The via 880 has problems with Dapper, but probably will work fine in Edgy.

See [http://ubuntuforums.org/showthread.php?t=190341](http://ubuntuforums.org/showthread.php?t=190341)

---

### Post by Lord Illidan on 2006-09-15
Thanks for the replies.

I got everything connected, yet it will not boot from the harddisk. It says
[I]
Uncompressing linux

crc error

System halt.

[/I]I don't think it is due to probs with my harddrive as it is fairly new.. It is IDE, too. It is master on the first IDE channel, and mounted as hd0 with grub...which should be correct, I think?

Can anyone help with this?

EDIT : It also won't boot from cd. reason = crc error...why the heck is this going on?

---

### Post by Lord Illidan on 2006-09-15
BUMP : Please, can anyone help?

---

### Post by John.Michael.Kane on 2006-09-15
Lord Illidan the board should be supported.if your getting crc errors the data on the cd is corrupt. i would try to re-burn the disk.

---

### Post by Lord Illidan on 2006-09-16
> **SD-Plissken said:**
> Lord Illidan the board should be supported.if your getting crc errors the data on the cd is corrupt. i would try to re-burn the disk.

I fixed the crc problem.. was a problem with defective RAM chip.

I now have the "cannot mount root partition problem" experienced by many people, apparently.

I am now using Fedora...hopefully, the problem will be fixed by Edgy...very annoying, too.

---

### Post by bmt on 2006-09-16
Google is your friend ;-)  There is a lot to look at, but many crc errors seem to have been caused by memory faults.  Try a memory test [http://www.memtest86.com/](http://www.memtest86.com/)

Has this new motherboard ever run at all?  If not, make sure that everything is connected properly -- especially the memory.  Remove and refit the memory modules, to double check.

The CD that you mentioned -- is that the Ubuntu Live CD?  Can you boot another computer with it?  If you get to the initial menu screen, try the 'Check CD-ROM' option, to test the quality of the CD.

*Edit: I took too long looking at Google ... glad you fixed it.*

---

### Post by Lord Illidan on 2006-09-16
Thanks mate.. Eagerly waiting for Edgy.. Fedora is nice, very nice, but not ubuntuish!

---

### Post by philipacamaniac on 2006-10-29
I have this motherboard. Like previous posts state, the kernel in Dapper doesn't properly support the Via controller. Therefore, 3D acceleration will be very hard to get. I had to recompile my kernel 3 times before I got it right.

I was hoping Edgy was the answer to my problems. Nope. I dist-upgraded to Edgy, and had some serious freeze issues. X would just freeze the entire machine (I couldn't even SSH in from another machine). I have an Radeon-9700 Pro. It did this using fglrx, ati, vesa and vga drivers.

So I went to reinstall using the CD. It did the same thing WHILE IN THE LIVECD ENVIRONMENT. So, something in Edgy is completely incompatible with something on this motherboard.

Dapper works fine, other than the 3D acceleration as mentioned before, so I know my hardware is working.

Stay AWAY from the Asus P5VDC-X if you plan to use Ubuntu.

---

