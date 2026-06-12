---
title: "Hardy or Intrepid for 64 bit?"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by yanksguy on 2009-01-04
Please bear with me on this somewhat lengthy post.  I've been combing the forums for answers but nothing is working for me.

I've been trying to install Ubuntu on my Acer Aspire 5050 to no avail.  I've tried Intrepid 8.1 and Hardy 7.1, but I only get as far as the third bar on install and then it freezes (Intrepid) or toward the end of the install bar and a freeze (Hardy).  I've tried both the 32 and 64 bit installs.  I then tried Mandriva thinking that a different distro would work, but that froze up as well.  

My Acer came loaded with Vista and gigabytes of bloatware from Acer.  It worked for about 3 months and then crashed hard.  I couldn't even reinstall from the partition.  Acer support was no help at all.  They didn't even think my pc existed even though I sent them the serial number and copy of my invoice.  Grrr...  

So at that point I installed XP, which worked, but started thinking Linux, mainly because I have friends who swear by it.  I checked out different distros and came to Ubuntu.  To check it out I loaded 8.10 onto a Gateway 450ROG (32 bit, 1.4 MHz, M processor, with 1gb ram) and it started up right away.  It was AWESOME!  I'm a total convert now!  After the Gateway success I wanted to load it onto my Acer (the Gateway is my company computer and they don't want Ubuntu on it.  Oops...)

So, now I'm at the point that nothing is loading.  I have tried numerous times to get this to work.  I've used the officially wrapped Ubuntu disk, downloaded and burned several others (all checked out okay before attempting load), downloaded and tried the 64-bit, and tried Hardy Heron 7.1. I have run DBAN before each load to make sure that I had a clean system.  I tried loading xp first and then Ubuntu alongside but it still wouldn't load.

Nothing is working, and I've tried, tried, tried to make it work.  I'm an noob at Linux but not with pc's.  I've built several pc's by myself and have loaded many os's (windows and mac) before.  

I've read that some people have had trouble with Acer, Atheros, 64-bit, and SATA working while others have no trouble at all.  

I'm stymied.  Please help me.

System:
Acer Aspire 5050
AMD Athlon 64 x2 dual-Core TK-53
1700 MHz
Hitachi 120 Gb hdd
2gb Ram
Atheros Wireless 802.11 b/g with Signalup high efficiency antennae
Atheros AR5BXB63
ATI Radeon Xpress 1100 integrated graphics (64-256mb shared memory)
ATAPI Model:  HL-DT-ST-DVDRAM GSA-T20N
BIOS: v 1.3315
VGA BIOS: ATi 008.050I.052.000
KBC: VO.029

That should about cover the specs.

---

### Post by Pumalite on 2009-01-04
Try Intrepid Alternate amd64 CD
Be wired to the Internet.

---

### Post by yanksguy on 2009-01-04
> **Pumalite said:**
> Try Intrepid Alternate amd64 CD
Be wired to the Internet.

Thanks, I tried that already.  

I'm wondering if I should try 8.04.  Might as well.

---

### Post by yanksguy on 2009-01-04
[Numbers] Bug: soft lockup- Cpu#0 stuck for 11s! [modprobe:1291]

---

### Post by Pumalite on 2009-01-04
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by yanksguy on 2009-01-04
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

Thanks, but that's not helping.  It won't even begin installing the os, so how can I edit anything?  I get the Ubuntu splash screen with the choices: 

Try Ubuntu...
Install...
Check CD...
Test...
Boot from...

I've tried installing, checked the cd for defects (okay), ran the memory test (okay), and I cannot boot from first hard disk because there is nothing there.

So, I start with "Install" and the brown bar slides back and forth, the screen goes black except for a blinking cursor at the top left, and there it sits, and sits, and sits.  The cd is not turning or running.  Nothing is happening.

I'm trying this with the 8.1 disk.

---

### Post by yanksguy on 2009-01-04
I've gone back to trying the Ubuntu issued cd with the 32bit 8.1.  It starts installing, gets about 2.8 bars into it and freezes.

What's up?

---

### Post by yanksguy on 2009-01-04
I hit f6 and deleted the splash and quiet and started the install.  It was going well until it hung on "loading hardware drivers..."  

The last thing I got was: 
[81.660193] ath_hal:module license 'Proprietary' taints kernel."  

And then my cd/dvd drive got quiet.

Any ideas?

---

### Post by yanksguy on 2009-01-04
Okay, I tried it again with only deleting "quiet" and now I'm getting somewhere.  It seems to be loading, the orange script telling me what's happening (and now I know what "quiet" means). 

But, it freezes at "Loading hardware drivers..."

I sit for ten minutes while searching the forums for the above message, all the while waiting for a miracle to occur.  I finally hit Ctrl-Alt-del and get a whirring of the drive and "Asking all remaining processes to terminate..." and another freeze.

---

### Post by Pumalite on 2009-01-04
Try adding 'all_generic_ide' to your boot line
(F6; add at the end of the line)

---

### Post by yanksguy on 2009-01-04
> **Pumalite said:**
> Try adding 'all_generic_ide' to your boot line
(F6; add at the end of the line)

I got a "ata2: SRST failed (errno=-16)

Was I supposed to type in all_generic... after the -- or before?

Never mind.  Same thing either way.

---

### Post by yanksguy on 2009-01-04
Okay, now I'm trying 6.06.  

Froze.  

Try again.

6.06 installed as the trial version.  I'm now running a full install.

Currently running the partition.

Install: 25%

Going to get lunch @ 34%.

---

### Post by yanksguy on 2009-01-04
My mistake.  I loaded the 7.10 Gutsy.  I don't know why it worked this time when it hadn't before.  Who knows...

But I have an operating system.

---

### Post by Pumalite on 2009-01-04
Probably a good CD...

---

### Post by yanksguy on 2009-01-04
It's the very same cd I used before.

---

### Post by Pumalite on 2009-01-04
Human error then or your burner needs the lens cleaned.

---

### Post by DforVendetta on 2009-01-04
I had the same problem you did man. I have intel quads at 2.4 ubuntu x64.

I ended up having to go through the bios and disabling all hardware not needed for the install (i.e. video, usb). I took out my nVidia pci-e and used the onboard video. once Ubuntu was up and running I added one device at a time then rebooted each time. i had the best luck adding my nvidia card last. Then I set each bios setting back to optimium performance one at a time. My bios has a setting for "OS Install mode" which made the install very slow but stable.

---

### Post by yanksguy on 2009-01-04
> **DforVendetta said:**
> I had the same problem you did man. I have intel quads at 2.4 ubuntu x64.

I ended up having to go through the bios and disabling all hardware not needed for the install (i.e. video, usb). I took out my nVidia pci-e and used the onboard video. once Ubuntu was up and running I added one device at a time then rebooted each time. i had the best luck adding my nvidia card last. Then I set each bios setting back to optimium performance one at a time. My bios has a setting for "OS Install mode" which made the install very slow but stable.

Frankly, I don't think it's worth it.  I have 8.1 running on an older Gateway and I love it and will keep using it.  But to get this to work on my Acer has been a huge headache.  I'm all for moving away from Microsoft, and Apple for that matter, and into free distro, but not when it means that I have to spend dozens of hours trying to make it work.  I'll stick with xp until Ubuntu and Acer get things worked out.

I really wish I could get Ubuntu to work on my Acer, I really do.  I gave up and have been reinstalling xp on my machine this evening because I have to have a working os on there this week.  The entire time I'm loading it I'm thinking how flat it looks and how clumsy it works and how much I dislike it.  

But, it works.

Good luck to you.

---

### Post by warpasylum on 2009-04-10
Hi,
     I've got an Acer Aspire 5050-4570 n' it's taken some work as well as a lot of searching through the forums (I'm a noob too), but it's been worth it. There's a definite learning curve, but lots of help here too. I'm running Intrepid 64 with no issues other than my DVD RAM showing up as a CD ROM. Actually in the process of fixing now. Not sure what the issue is as far as your install, just wanted to let you know don't hold your breath for Acer to play nice with the Linux world. If you are able to get it installed and have any issues let me know, I might have had the same. Good luck!

---

