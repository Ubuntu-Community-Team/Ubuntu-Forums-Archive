---
title: "Gnome interface not responding"
date: 2008-10-16
forum: General Help
---

### Post by Stupid_newbie on 2008-10-16
All I can say is "Thank God for Laptops!" My Ubuntu system is not responding to anything on the Gnome menu. I have AWN window manager and I am able to get the Open Office Word to work and thats about it. EVEN MY TERMINAL wont load.. OF ALL THINGS!!

So here is the deal, I was trying to get OSS sound working instead of ALSA and I must have effed with the wrong code. When my machine loads up I get the login screen, once I log in everything seems normal. I go to Applications then I click on my "Thunderbird Mail" once I do that my Top navigation bar (gnome) freezes..I try to use the terminal shortcut on my AWN , it just gives me some blank screen... and then freezes. Is there anything I can do to get my system online again?!?!?!?!

Please note... UNIX NOOOB so go easy on me. I am not a moron when it comes to computers... JUST UNIX! :P

thanks for any help

---

### Post by phidia on 2008-10-16
Create a test user. To do that get to commandline by booting in recovery mode or press the Alt+Ctrl+F1 keys then enter > sudo adduser test

Remember the password you created for that account and boot into that account.

Do you still have the problem?

---

### Post by Stupid_newbie on 2008-10-16
I tried to do the xsystem recovery and my monitor(s) are going insane, My main monitor is flashing multiple colors, and my secondary is stuck at a screen that resembles the way your tv would look like if the nintendo game was entered wrong (if you remember ninteno)

I can login by trying CTRL ALT F1, but I just get a terminal screen now... I have gone and screwed myself havent I

---

### Post by phidia on 2008-10-16
> **Stupid_newbie said:**
> I tried to do the xsystem recovery and my monitor(s) are going insane, My main monitor is flashing multiple colors, and my secondary is stuck at a screen that resembles the way your tv would look like if the nintendo game was entered wrong (if you remember ninteno)

I can login by trying CTRL ALT F1, but I just get a terminal screen now... I have gone and screwed myself havent I

If you can get command line (terminal screen) you should be able to issue the command I provided in my 1st post here, and then try to login with the test user.

---

### Post by Stupid_newbie on 2008-10-20
I am able to log on as the "test" user but no GUI just terminal.

---

### Post by Stupid_newbie on 2009-09-26
Well then, I am still confused. It has been over 3 months,2 different HD's and a brand new motherboard and I STILL cant get Ubunto to even INSTALL

Ladies and Gentlemen I IMPLORE you to help me get Ubuntu back on my main computer.

Here is the issue.
I have windows XP SP3 installed on a 500GB HD with 40GB Allocated (sp) for XP the rest is unpartitioned space.
I have a 250GB drive I use for backup and temp files. and another 500GB drive to "raid" my important stuff.

When I use the CD to install Ubuntu,  I get the "splash loading screen" fine. Once the loading phase is done, my left monitor (HDMI cable) goes crazy like a multi colored strobe light. My Left monitor is stuck between ANSI Characters and does NOTHING. if I press Ctrl, Alt F10 (or F11) the screens go blank with a curser blinking and THAT IS IT!!

Here is where I wanted to jump off a bridge last night.....if I unplug the HD with windows XP and install ubuntu on a different hard drive... BAM everything works perfectly, but once I re-boot, the computer automatically boots into windows and I cannot access ubuntu. I even tried to install the multi OS bootloader (GAG) but it will not let me choose O.S,'s from different Hard Drives.

if there is some sort of boot-up logfile or something I can do to give you more info please let me know.

THANKS IN ADVANCE!!!!!!!!

-Holding baseball bat firmly

---

### Post by Iowan on 2009-09-26
CTRL-ALT-F1 through CTRL-ALT-F6 will provide usable terminals. CTRL-ALT-F7 *should* be the desktop. CTRL-ALT-F10 and CTRL-ALT-F11 have only a blinking cursor on this box.
GRUB *should* let you choose which OS to boot into. I haven't done multi-HD boot or used multiple monitors.

---

### Post by Stupid_newbie on 2009-09-27
> **Iowan said:**
> CTRL-ALT-F1 through CTRL-ALT-F6 will provide usable terminals. CTRL-ALT-F7 *should* be the desktop. CTRL-ALT-F10 and CTRL-ALT-F11 have only a blinking cursor on this box.

How do I get Ubuntu GUI to install once I get into terminal. I know for sure its not a Hardware issue because I used to have this OS on my machine before.

I will attach hardware specs just to be safe


Operating System
Windows XP Professional Service Pack 3 (build 2600)
Install Language: English (United States)
System Locale: English (United States)
Processor a
1.80 gigahertz Intel Core Duo
64 kilobyte primary memory cache
1024 kilobyte secondary memory cache
64-bit ready
Multi-core (2 total)
Not hyper-threaded
Drives
790.17 Gigabytes Usable Hard Drive Capacity
347.23 Gigabytes Hard Drive Free Space

ETETSVE 2RSLEVST2J SCSI CdRom Device [CD-ROM drive]
HL-DT-ST DVD-RAM GSA-H55N SCSI CdRom Device [CD-ROM drive]
HL-DT-ST DVD-RAM GSA-H55N SCSI CdRom Device [CD-ROM drive]

ST3250620AS [Hard drive] (250.06 GB) -- drive 0, SMART Status: Healthy
WDC WD5000AAKS-00A7B2 [Hard drive] (500.11 GB) -- drive 2, s/n WD-WCASZ0447387, rev 01.03B01, SMART Status: Healthy
WDC WD5000AAKS-00D2B0 [Hard drive] (500.11 GB) -- drive 1, SMART Status: Healthy





Controllers
Intel(R) ICH10 Family 2 port Serial ATA Storage Controller 2 - 3A26
Intel(R) ICH10 Family 4 port Serial ATA Storage Controller 1 - 3A20
Primary IDE Channel [Controller] (2x)
Secondary IDE Channel [Controller] (2x)
Bus Adapters
AZ4SE5G2 IDE Controller
Marvell 61xx RAID Controller

Board: ASUSTeK Computer INC. P5QL PRO Rev 1.xx
Serial Number: MS1C93BDUJ00165
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. 1001 03/12/2009
Memory Modules c,d
3072 Megabytes Usable Installed Memory

Slot 'DIMM0' has 1024 MB
Slot 'DIMM1' has 2048 MB
Slot 'DIMM2' is Empty
Slot 'DIMM3' is Empty
Local Drive Volumes
		
c: (NTFS on drive 2)	40.01 GB	20.05 GB free
d: (NTFS on drive 0)	250.06 GB	134.04 GB free
f: (NTFS on drive 1)	500.11 GB	193.14 GB free

Network Drives
None detected
Display
NVIDIA GeForce 6200 LE [Display adapter]
Acer AL2216W [Monitor] (22.0"vis, s/n L740903863C2, January 2008)
Acer AL2216W [Monitor] (22.0"vis, s/n L740903863C2, January 2008)

---

### Post by Stupid_newbie on 2009-09-29
Still no takers? wow. I guess im stuck with xp! :(

---

### Post by Iowan on 2009-09-30
... or you could try Jaunty. After reading thread after thread about networking problems with Hardy and Intrepid, I was a little apprehensive to install Jaunty on a laptop, but it went rather painlessly. Network Manager is much improved, as is hardware support (except for some ATI cards which are no longer supported).

---

### Post by Stupid_newbie on 2010-07-29
It was the Video Card, Something happened with the hardware on the video card and Ubuntu wanted nothing to do with it. I got an ATI radion video card and I can now have my multiple screens on Ubuntu and 7.  Thanks all for your suggestions and help :)

---

