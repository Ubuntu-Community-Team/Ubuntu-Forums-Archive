---
title: "Compaq Presario F572US Notebook PC"
date: 2008-07-26
forum: Hardware
---

### Post by DarkW0lf on 2008-07-26
Compaq Presario F572US Notebook PC
1.7 GHz AMD Athlon ™ 64 X2 Dual-Core Mobile Technology TK-53
NVIDIA GeForce Go 6150 (UMA)

MFG link
[http://h10025.www1.hp.com/ewfrf/wc/d...41671&lang=en#](http://h10025.www1.hp.com/ewfrf/wc/d...41671&lang=en#)

Edit follows:

Thread moved after archive became read only.
My system is xubuntu 8.04

For Wireless support:
[http://ubuntuforums.org/showthread.php?p=5456980](http://ubuntuforums.org/showthread.php?p=5456980)
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)
Warning Ubuntu has borked wireless support, you need to reload driver modules.
Instructions at the above links.

Repository ndiswrapper works with the drivers from the no-fluff docs.

For Native Widescreen Resolution:
Monitor spec is 1200x700
Don't know what resolution is in 8.04 without nvidia driver
Most recent nvidia restricted driver sets to 1158x700 res.

For SoftModem support:
Doesn't look good (HD Audio Softmodem from Conexant non-DSP chipset; requires key for speeds over 14.4k)

For Sound support:
None needed, it works out of the box.
Unless you upgraded to 8.04 then there is sounds issues, clean install or update you are good.

Known (to me) Issues:
USB hot swapping still an issue, don't know about IRQ 7.
IRQ 7 is for (non-existent) printer port according to service manual. But might be reassigned to soundcard/(non-existent) PC card.
USB Devices have to be connected at boot and are not redetected if reinserted after unmounting.
Will lose mount after a while ( half hour maybe more ? )

I may have the same suspend issue as ragingocelot, but I don't know if it my video card or not. (see archived thread)
No suspend / hibernation / monitor power down without crashing the video.
Video scrambled on shutdown, the splash screen is all screwy (I have no better description).

---

### Post by DarkW0lf on 2008-07-26
Got Email from HP; there is service for WiFI not detecting WAPs or not displaying device in Device Manager.

Also video display problems; not showing display on boot or on external monitor.

Update to firmware (F.1F). (wow someone uses hex version numbers ?)

MFG Link: [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01480071&dlc=en&printable=yes&encodeUrl=true&](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01480071&dlc=en&printable=yes&encodeUrl=true&)

I am emailing HP cause I am looking for more information regarding what hardware is faulty.

---

### Post by DarkW0lf on 2008-08-01
Well, HP didn't give me much more info on what "exactly" is being replaced.

They also said that Linux is not supported on HP Pavilions (like how they said that even though they know it's a Compaq Presario).

And a note to Linux users:

> 
By sending your (HP Presario/Pavilion Notebook) to HP to be repaired, you agree to the following conditions: It is your responsibility to backup your data. This includes hard drives, ROM chips, flash cards, etc.

During the repair process "your notebook hard drive will be re-imaged if it fails Quality Assurance testing" , and in this event you will not have the opportunity to retrieve your data once the repair is complete. Hence, I request you to take backup of all the important data present on the notebook. 

All BIOS passwords should be removed before shipment. In cases where HP receives units with passwords, they will be cleared, but this will delay the repair of the unit.


HP will re-image back to windows (though they didn't exactly say factory defaults).

---

### Post by DarkW0lf on 2008-12-20
I am late in posting,

Don't know what was wrong their documentation is poor at best.
They replaced the whole motherboard.

Not sure how much relates to Linux but I still can't suspend the laptop (or power-save just the monitor) without it locking up the display.

---

### Post by DarkW0lf on 2009-04-24
Looking to upgrade hardware before I add more VM's to machine
Anyone know good places for these:
Last number at the end is HP replacement number from service manual.

120 GB HDD 5400RPM 4428882-001

1024 MB (PC2-5300, 667-MHz, 1-DIMM) 450610-001**

---

