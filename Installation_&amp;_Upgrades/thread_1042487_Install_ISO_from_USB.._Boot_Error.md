---
title: "Install ISO from USB.. Boot Error?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by tiger.woods on 2009-01-17
I'm trying to install the 8.10 ISO from my USB drive using the following program ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) and am getting a boot error?

Does anyone have some instructions for setting up a USB drive for installing from an ISO or can give some help with the current process?

Thanks for any help.

TW,

---

### Post by tommcd on 2009-01-17
Try this guide from the Ubuntu wiki:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and also:
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html)

---

### Post by Rhubarb on 2009-01-17
If you already have access to a computer that is running Ubuntu 8.10, and you have an ubuntu 8.10 iso file and a spare usb flash drive, then simply run this program:

System --> Administration --> Create a USB startup disk

And it'll do all the work for you.

---

### Post by tiger.woods on 2009-01-18
> **Rhubarb said:**
> If you already have access to a computer that is running Ubuntu 8.10, and you have an ubuntu 8.10 iso file and a spare usb flash drive, then simply run this program:

System --> Administration --> Create a USB startup disk

And it'll do all the work for you.

I don't have that option? 

Will it matter if the original OS is 32 bit and I'm installing 64 bit?

---

### Post by tiger.woods on 2009-01-18
> **tommcd said:**
> Try this guide from the Ubuntu wiki:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and also:
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html)

tommcd, I tried the second option you suggested and after creating the bootdisk when I try to boot the system from the usb I get "boot error"?

Any ideas?

---

### Post by registerkar on 2009-10-09
Well I too struggled through the problem for weeks...Tried all available Bootable USB Linux software, but no good. Googled all the forums...no solution...

Here is what worked for me...

Prob: When I created Live Usb and restart my pc with all bios settings done right I get a "Boot Error" ...thats it...No number...

Solution: The problem is not in Ubuntu or Live USB creator softwares...the problem is in ur bios settings...

go to Bios Boot Menu...
Search for ' USB Mass Storage Emulation type'
Default:<Auto>
Change it to:<All Fixed Disc>
or something similar

This was the Bios of Intel DP35DP MainBoard with P35 Chipset...
Right Now i am working from a USB Ubuntu !!!...

---

### Post by garak on 2009-11-22
> **registerkar said:**
> Well I too struggled through the problem for weeks...Tried all available Bootable USB Linux software, but no good. Googled all the forums...no solution...

Here is what worked for me...

Prob: When I created Live Usb and restart my pc with all bios settings done right I get a "Boot Error" ...thats it...No number...

Solution: The problem is not in Ubuntu or Live USB creator softwares...the problem is in ur bios settings...

go to Bios Boot Menu...
Search for ' USB Mass Storage Emulation type'
Default:<Auto>
Change it to:<All Fixed Disc>
or something similar

This was the Bios of Intel DP35DP MainBoard with P35 Chipset...
Right Now i am working from a USB Ubuntu !!!...

This solution worked for me also.
Thank you very much

---

### Post by pbouf on 2009-12-25
Worked for me too, thanks! (Karmic USB live desktop, eMachines W3611).

---

### Post by zbot on 2011-01-24
THANK YOU!!!!!  This worked on a 975XBX2 Mother Board.  Freakin' eh... so much time wasted.

---

### Post by zhoulab on 2013-04-10
What a life saver!! it solved my problem as well (Wasted two days before I found this thread).  In [COLOR=#010101][FONT=Verdana]ASUS KCMA-D8 ATX Server Motherboard the "similar" option is "Forced FDD".[/FONT][/COLOR]

---

### Post by oldos2er on 2013-04-10
Old thread closed.

---

