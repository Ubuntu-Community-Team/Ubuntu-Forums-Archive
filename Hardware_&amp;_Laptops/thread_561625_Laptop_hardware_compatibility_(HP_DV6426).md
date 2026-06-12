---
title: "Laptop hardware compatibility (HP DV6426)"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by cyberblade3001 on 2007-09-27
I'd like to move away completely from Microsoft OS's (at home anyway-work still requires XP), but I want to be sure that my laptop can handle Ubuntu. I have a HP Pavilion DV6426. I'm pretty sure the graphics, ethernet, wireless, etc. will work, but here are the things I'm concerned about:

Built in webcam
Built in microphone
All the audio control buttons (mute, volume up/down, etc)

As much as I'd like the remote, and HP quickplay to work I'm pretty sure those are goners... I can handle that.

I looked through the posts on the forum here and checked out [http://www.linux-laptop.net/](http://www.linux-laptop.net/) but they don't mention this model. Can anyone tell me if this will work or not?
Thanks!

Just for reference the product spec sheet is here:

[http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN)

---

### Post by ddrichardson on 2007-09-27
Actually, the remote works fine as X treats it as keyboard input. There's a good guide (albeit for the tx1000 series) [here]("http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z").

Try the Live CD and see if any problems arise. A word of caution though - most all HP laptops wont boot Ubuntu without the noapic option being added to the kernel line.

BTW, the link doesn't work, but this [one]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01061067&cc=uk&lc=en&dlc=en&product=3439463&dlc=en&lang=en") does.

---

### Post by RVO on 2008-02-04
Hey guys, I'm new here but I have been considering making the move from windows to ubuntu myself and I too have a DV6426. I was just wondering if cyberblade3001 made the move and if so how it played out. Anybody else wandering through here who has pertinent info are more than welcome to post it too! BTW I have never been on a linux system before but have been on computers since the vic20 (Pre commador64) was out. Thanks in advance!

---

### Post by cdtech on 2008-02-04
I have the HP dv9608nr laptop and had no problems installing from the Alternate CD.  The graphics and wifi have to be configured to work properly but there are many howto's to follow in here.  I installed Ekiga Softphone and my webcam worked without any configuration.  I did have some problems with my headphone jack sense but got that worked out.  The HP is not as bad as you may read.

---

### Post by RVO on 2008-02-05
What is needed to run the 64bit version? Can the DV6426 run the 64-bit version or must I run the 32-bit version?

---

### Post by cdtech on 2008-02-05
> **RVO said:**
> What is needed to run the 64bit version? Can the DV6426 run the 64-bit version or must I run the 32-bit version?

Core 2 Duo is a 64-bit processor and the Core Duo is a 32-bit.  To find out your processor just type in terminal:
```
lshw
```
This will list your hardware information.

---

### Post by RVO on 2008-02-05
Core Duo T2450 so I guess I'll be trying the 32bit ver eh? Also what is the best method for dual booting this with vista?

---

### Post by cdtech on 2008-02-05
On a single drive, you would need to set up a partition on some extra Vista hard drive space.  I'm running two drives (one Vista one Ubuntu).  I switch hard drives through BIOS.  If you set it up on a single drive (Vista), grub can handle the boot between Vista and Ubuntu.

---

### Post by RVO on 2008-02-05
> **cdtech said:**
> On a single drive, you would need to set up a partition on some extra Vista hard drive space.  I'm running two drives (one Vista one Ubuntu).  I switch hard drives through BIOS.  If you set it up on a single drive (Vista), grub can handle the boot between Vista and Ubuntu.

I've been thinking about checking this out on a desktop I built some years ago but it's a very old machine and not something I am on often. But that system does have two drives and I have read how dual boot systems can sometimes try and reclaim partitions with foreign files systems on single drive setups. I've never used grub or any other dual boot loader. Have you ever experimented with LILO or NTLDR? How do you switch in bios? Just disable whichever drive that has the system you are not using at the time? Thanks for the input, you're being a big help for me to determine what route I'll take.

---

### Post by Rome.konig on 2008-02-06
for bios all you have to do is change the order of the boot operations, make the hard drive with Vista installed boot first if you want Vista up and running and the same would go for Ubuntu.

---

### Post by RVO on 2008-02-06
> **Rome.konig said:**
> for bios all you have to do is change the order of the boot operations, make the hard drive with Vista installed boot first if you want Vista up and running and the same would go for Ubuntu.


So you could just hit your boot menu key and load whichever drive then right? Or could you edit the boot.ini to offer a selection of which you would like to load? Probably not because I imagine the file systems are different and incompatible right?

---

### Post by cdtech on 2008-02-06
> **RVO said:**
> So you could just hit your boot menu key and load whichever drive then right? Or could you edit the boot.ini to offer a selection of which you would like to load? Probably not because I imagine the file systems are different and incompatible right?

Two separate hard drives (two separate systems).  This will explain LILO and NTLDR if both systems are on the same hard drive: [[COLOR="Blue"]LILO / NTLDR[/COLOR]]("http://jaeger.morpheus.net/linux/ntldr.php")

Try not to edit the MBR in windows yourself, let GRUB do it for you if you use the same hard drive.
The installation will ask where you want GRUB installed.  I just chose to keep both drives separate and use GRUB on its own drive (Ubuntu OS).

---

