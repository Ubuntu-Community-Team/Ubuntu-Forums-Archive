---
title: "Problems with 9.04 installation"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by roypk on 2009-07-22
I downloaded the 64-bit 9.04 a few days ago.  I made the CD and checked for errors.  Everything went find at that stage but I ran into problems when I either tried to install it on the HD or running it on the CD.  What I got was the logo and the progress bar.  At the end of the progress bar, the screen just went blank.  The setup screens, when I tried installing it, or the OS, when I tried to run from the CD, never came up.  The problem must exist somewhere but I don't know where to start.  Most of the hardware on my machines are not new.  The specifications are as follows:

Asus P5K Mainboard P35
512Mb XFX 9600GT running 2xLCD screens
Q9300 CPU
8 GB(2x4) OCZ DDR2-800 (running in dual channel mode)
2x250GB Seagate SATA connected to ICH9, both run in enhanced mode.
1x1TB Western Digital connected to JMB363 as SATA
1x22X Samsung SATA DVD burner connected to ICH9
1x20X LG SATA DVD burner connected to ICH9

I don't overclock and the current OS on this machine is WinXP64.  Any help or suggestions would be greatly appreciated.  I really want to run Ubuntu on this machine.

Best regards,
Roy

---

### Post by bacil on 2009-07-22
Safest bet would be your dualhead graphics card i would probably try to disconnect secondary screen and try again. then i would try install it in text mode.

---

### Post by roypk on 2009-07-22
> **bacil said:**
> Safest bet would be your dualhead graphics card i would probably try to disconnect secondary screen and try again. then i would try install it in text mode.

Thank you.  I'll give it a try.  Do you think switching the 2 SATA drives on the ICH9 back to compatible mode will also help?  I plan to install Ubuntu on one of the two.

Best regards,
Roy

---

### Post by bacil on 2009-07-22
i am usin ICH on all my laptops and havent got any issues with it. did you try to boot it as live cd ?

---

### Post by roypk on 2009-07-22
> **bacil said:**
> i am usin ICH on all my laptops and havent got any issues with it. did you try to boot it as live cd ?

I did.  Unfortunately, that didn't work either.  Thanks anyway.

Best regards,
Roy

---

### Post by roypk on 2009-07-23
> **bacil said:**
> Safest bet would be your dualhead graphics card i would probably try to disconnect secondary screen and try again. then i would try install it in text mode.

You were right.  Disconnecting the secondary LCD solved the problem straightaway.  It booted up from the CD in no time.  Now, it's just a matter of creating some unpartitioned space for the Ubuntu.  Thanks again for the advice.

Best regards,
Roy

---

### Post by Neavo on 2009-07-23
Hi. Im kind of a noob at this. but i seem to be having the same problem. except im not using Dual monitors, and i took my second video card out to see if that was the problem. 
it isnt. 
im having the same problem, where when i try to install ubuntu upon startup, or even try to Live boot it, it will get to the Ubuntu Logo screen where it loads stuff, but after it loads and goes to the next screen, its blank. sometimes i hear sounds from, like the next screen is loaded, but i can not see it. a buddy of mine had basically the same machine, and he got it to work really well. 
i wanna put htis installation on the maxtor, but ive got plenty of other oppurtunities if needed. somebody, please help! 

Thanks
Jon

Specs: nothing too new. 
Athlon64 3500 OC 2.7G-Venice Core
Ati Radeon X1900GT 256Mg 256Bit 12 pipes-Sapphire
Msi Neo-f/2 Mobo
Maxtor 100G 10kRpm
Seagate 80G 10kRpm
WD 250G 7200Rpm
Iomega External 300G @ ?rpm

---

