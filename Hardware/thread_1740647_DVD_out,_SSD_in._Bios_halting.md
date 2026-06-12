---
title: "DVD out, SSD in. Bios halting"
date: 2011-04-27
forum: Hardware
---

### Post by martinyt on 2011-04-27
I have a Fujitsu Siemens p7010 which I have changed the DVD wtith a SSD. However, it takes about 5 min to start up the Bios when the SSD is active. If I deactivate the SSD/DVD in the Bios it starts a regular speed - but then I cant use the SSD :(.
 
I don't understand why the Bios uses that much time when the SSD is enabled. When it finaly starts, I can install ubuntu on it or mount it from ubuntu.
 
I guess I have to do somthing in the Bios - and I have tried different options but it doesent seem to help.
 
It is not recogniced as a hard drive in the bios, but as a cd-rom and I can set the options like:
Multi-Sector Transfers
LBA Made Control
Transfer mode
Ultra DMA Mode
 
but I don't know what this means and the Bios-manual doesen't seem to help much.
 
Anyone have any ideas, tips or maybe a solution?
 
Thanks!

---

### Post by dabl on 2011-04-27
What is the interface to the SSD (that was formerly to the DVD)?  Does the hdd controller on the mainboard, which I assume is SATA, have 2 connectors, or only 1?  It sounds like the interface to the DVD was not a standard SATA interface, but maybe something special for the optical drive.

---

### Post by martinyt on 2011-04-27
Thanks for your interest! 

The ssd is sata, but the interface is pata. So I have a sata to pata caddy where the ssd is placed. I bought it from: [http://www.newmodeus.com/shop/index.php?main_page=index&cPath=2_27](http://www.newmodeus.com/shop/index.php?main_page=index&cPath=2_27)

---

### Post by dabl on 2011-04-27
I'm wondering whether the SATA interface for the SSD really needs to be a true SATA interface.  I'm also wondering whether there is some firmware in the IDE controller that says "it's an optical drive" -- causing whatever you connect to it to be seen as an optical drive.

If you're into tinkering, it would be interesting to see what you have if you reverse the devices -- connect the hdd to the IDE bus (using your adapter) and the SSD to the SATA bus.  I'm guessing your hdd will suddenly be seen as an optical drive, and your SSD will be correctly recognized in BIOS.

In other words, I'm afraid your scheme is not going to be successful.  :-({|=

---

### Post by martinyt on 2011-04-27
I don't think I have a sata interface for the hdd and don't have pata-pata caddy - so I wont be able to try that experiment. But I guess you are right, the hdd would also be seen as a optical drive. 

I am wondering if it is possible to activate the "optical drive" at boot up - after the bios has started?

---

### Post by dabl on 2011-04-27
Ah -- I assumed the hdd would be a SATA, but I just looked up the specs for that computer and you are right, it is also IDE.  Is the optical drive on a ribbon cable that goes back to the same controller as the hdd, or is it a separate controller?

Yes, you might try disabling the optical drive in BIOS.  But, unless you have a ribbon cable that lets you "daisy chain" the SSD on the same controller as the hdd, I don't think it's going to be seen as a hard drive device.

---

### Post by martinyt on 2011-04-27
It is a separate controller (I think). I have a option to set main,secondary or both IDE to controll Lan etc. (I don't have the computer here right now). If I only select main (and main is the hdd) it boots normal but the ssd is not accessible. If I select both, it takes a about 5 minutes to get past bios, but I can access the ssd. (I can't boot from the ssd). 

I guess I could try to replace the hdd with the ssd, but then I would need a pata-sata transition - I don't know if there exist one that would fit in the computer. I could have a look around (and a look into the computer). The hdd is 80gb and ssd is 60gb, so it might be a good use of the ssd.

---

### Post by martinyt on 2011-04-28
I took contact with newmodeus.com and I got this answer:
 
"It sounds like a Master/Slave conflict. We will ship you a replacement board with jumper settings so you can set the drive caddy to "Slave". "
 
So I hope this "replacement board" will solve my problems :D. 
 
I'll let you know when I have tried it.
 
Thanks!

---

### Post by martinyt on 2011-05-05
I have received the new board an placed it in the caddy. Unfortunately I can't get the disk up and running. Maybe i'll have to set the correct sectors,channels etc in the bios?

---

