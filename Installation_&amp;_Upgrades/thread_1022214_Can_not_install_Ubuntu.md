---
title: "Can not install Ubuntu"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by thejavabuddha on 2008-12-26
Hello,  I am COMPLETELY new to linux and thought I would give it a try.  I'm building a new HTPC and plan to run myth tv on it so I thought I would go ahead and play with linux while I'm waiting for parts to ship.  

First off, here are my specs:

Asus P5W DH Deluxe MOBO; 
Core 2 Duo E6600; 
G.SKILL 2GB (2 x 1GB) DDR2 800 RAM; 
COOLMAX CUG-700B ATX 12V( V.2.2) 700W Power Supply; 
WD Caviar RE 160GB 7200 RPM SATA 3.0Gb/s HDD; 
WD Caviar Green WD10EACS 1TB SATA 3.0Gb/s Hard Drive;
FREETECH GeForce 6200 128MB DDR PCI-e x16 Video Card

Trying to install from a CD on an external USB dvd drive from an image burned from ubuntu-8.10-desktop-i386.iso

I have Windows XP sp2 installed on my 160GB drive and initally set up umbutu from windows.  The process started and seemed to take a long time.  All this wonderful esoteric code started to stream across my screen and I left it alone.  I got a message that said:

"Synchronous SCSI scan failed without making any progress.  Switching to async" 

Or something along those lines.  I remembered reading somewhere that installing linux takes a long time and not to be afraid if I see error messages as this is normal.  I believed them so I left it alone for a while.  I came back a while later and noticed that the same message was repeating itself over and over again, with the only difference being the numbers at the begining of each line.  I will try to replicate them here, but I had to hand write them on a piece of paper and errors are likely:

"[  173.12033] ata7.00: Status: {DRDY}
 [ a higher #] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
 [ a higher #] ata7.00: cmd a0/00:00:00:24:00/00:00:00:00:00/90 tago pio 36 in
                        cdb 12 00 00 00 24 00 00 00   00 00 00 00 00 00 00 
                        res 40/00 ::00:00:00:00/:00:00:00:00:00/00 Emask 0x4 (timeout)"

I left this alone for 12 hours and when I woke up the next day it was still doing the same thing with ever increasing numbers at the begining of the lines.  I typed "exit" out of desperation and got some error message and more crazy code but I actually got a GUI interface and was able to log in and run Ubuntu.  I played with it for a while, got the internet working etc.  I installed some updates and had to restart.  When I did I get the same error message as before.  However, now if I try to type "exit" I get some message about something being "killed" (sorry, didn't write that one down) and my caps and scroll lock lights on my keyboard start blinking and have to hard boot to get it to restart.  

I uninstalled it and tried installing it again from booting from the disk at startup but get the same message.

Oh, when I initially installed it I installed it to my 1TB WD green drive.  After I uninstalled it I created a new partition on that same drive to install it to wondering if that would make a difference, but I never even got to a place that asked me where I would like to install it to.  If that makes any difference.

Thank you so much for any help you can offer!

Bill

---

### Post by oldos2er on 2008-12-26
" I remembered reading somewhere that installing linux takes a long time"

 Ubuntu installs on my machine, which has roughly similar hardware specs, in about 20 mins.

 The first thing you should do when booting the LiveCD is to run 'Check CD for defects'. And do an md5sum check too.

---

### Post by cariboo on 2008-12-26
I would also check to see if the BIOS is in compatability mode. It should be set to ACHI. Changing the setting may not allow Windows XP to boot, but if you upgrade to SP3 the problem will be fixed.

Jim

---

### Post by thejavabuddha on 2008-12-26
> **cariboo907 said:**
> I would also check to see if the BIOS is in compatability mode. It should be set to ACHI. Changing the setting may not allow Windows XP to boot, but if you upgrade to SP3 the problem will be fixed.

Jim

I tried that...no luck.  Seems to have made no difference.  I tried about every HDD mode that was offered me.  The only thing most of them did was make XP unbootable.

When I try to check the CD for errors I ALSO have the same problem.  I can't even check the CD.

---

### Post by thejavabuddha on 2008-12-29
Anyone else?

---

