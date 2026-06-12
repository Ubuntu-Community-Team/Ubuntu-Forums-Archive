---
title: "Bad Computer Lock Up!"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by PatrickBG on 2007-04-04
Motherboard
NFORCE 570 Slit-A v5.1
Socket 775 (Intel)

CPU:  P4 (Intel) 3.2GHz
Memory:  1GB Buffalo Select DDR2 (1 Chip)
OS:  XP Professional 

	I just built this computer 3 months ago and it was working fine until my power supply gave out.  I replaced my power supply and started having problems with my computer while gaming.  I ran a Bios Update and the Flash program messed up and my computer wouldn’t reboot after update was complete.  I’m guessing this corrupted my bios:( .  I’ve replaced my motherboard.  After I replaced my motherboard I reinstalled Windows and all the drivers for my motherboard and graphics card.  And now…
My computer locks up, completely freezes after about 5-10 seconds after I start it up.  Does any1 know if this is a Driver or Hardware issue?  If so, is there any test or specific hardware I can replace.  

Tech support for my Motherboard suggested this might be a Memmory setting in my Bios that needs to be changed.  I'm afraid to mess w/ Bios without knowing exactly which settings to change.

Could this be a over clocking from my memory or graphics card that is causing this lock up?  If so, is it possible to change my Bios settings?

Right now my Bios settings are set to Default.

---

### Post by RaZer0r on 2007-04-04
first and for all this is an linux forum, not windows :p
but i'll still help you as much as possible, did you overclock anyhing, if no, try and removing all unnessecairy hardware, such as ram, etc etc, if it boots, it should work, did you try an live cd of ubuntu and see if the same problem occurs? (or a live cd of windows mce for example)

---

### Post by PatrickBG on 2007-04-04
:lolflag: sry bout posting in wrong section <-- Nubby

I have tried Windows Repair and Tried to Reinstall Windows to see if the problem was with the drivers, but the computer locks up on me before any progress is made :( 

I havent had anything overclock, but if the memory settings are incorrect in my Bios, could this cause a lock up?

---

### Post by RaZer0r on 2007-04-04
it could be, but you'll have to check your mainboard settings for that, if there was anything like a guide it could be that your ram isn't supported (or supported halfly) by your mainboard, do you know what the exact name of the ram module is? and mainboard + bios version?

---

### Post by PatrickBG on 2007-04-04
Motherboard: 
ECS
NFORCE 570 Slit-A v5.1
Socket 775 (Intel)

Memory:
Buffalo Select
1 GB 667 MHz DDR2 SDRAM 2Rx8
PC2-5300-555

Not sure of my Bios Version.  Do you know where I could find out that information for my motherboard?

This  is My Exact Motherboard
[http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=2473506&sku=S458-1240](http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=2473506&sku=S458-1240)

---

### Post by RaZer0r on 2007-04-04
seems to be not an hardware issue, you might want to try upgrading your bios (if you're up to it) here is a link to the newest availeble bios atm
[http://www.ecs.com.tw/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=678&DetailName=New&DetailDesc=&CategoryID=1&MenuID=6&LanID=0]("http://www.ecs.com.tw/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=678&DetailName=New&DetailDesc=&CategoryID=1&MenuID=6&LanID=0")
it seems there is a bios issue with ram that should be running on 677 mhz instead of 800 (which the motherboard uses... So my first guess is it is worth upgrading...

---

### Post by PatrickBG on 2007-04-04
That is the update I downloaded before.  When I used the Flash program and loaded that file it ran its sequence then told me it was complete and I should restart my computer.  When I did this my computer didn&#8217;t reboot properly, almost acted as if the Video card wasn&#8217;t installed and I heard Beeps coming from my computers motherboard. :(   I talked to ECS tech support and told me I had corrupted my bios. 

   I went out bought the exact same Motherboard and reinstalled it.  Now I&#8217;m having this lock up problem.  I do agree with you about the memory speeds possibly being the case for my lock ups, but I really don&#8217;t know how to update the bios correctly and I don&#8217;t want to corrupt the bios on this new motherboard I just purchased.

  Is updating one's bios a simple as:

Downloading the update.

Downloading the Flash program and installing it.

Opening the Flash program and loading the update?

Is it possible that when I reinstalled Windows it missed a file or two?  I ran NFTS (Quick) Version on the Partition

---

### Post by RaZer0r on 2007-04-04
that might be the issue although with an quickformat it erases the partition table of the hard drive, and not the files themselves, you might want to try a reinstall and preform a complete format, but i'm not sure that will solve the problem... about the bios upgrade, you have to download the new version, download the flash tool, and put it on a bootable floppy disk (explanation is found here: [http://www.ecs.com.tw/extra/flashutl/winflash.htm](http://www.ecs.com.tw/extra/flashutl/winflash.htm))

---

