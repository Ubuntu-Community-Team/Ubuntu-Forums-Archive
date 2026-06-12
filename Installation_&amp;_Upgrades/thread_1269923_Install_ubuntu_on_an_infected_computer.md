---
title: "Install ubuntu on an infected computer"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by aaronlong on 2009-09-18
Well I have a computer, that is completely messed up by a virus. So my dad was going to just throw it out. I want to turn it to a linux. The only problem when I tried to put my live cd, it won't work. It is an hp pavilion desktop, does anyone have a good idea how to get it to work.

---

### Post by ubuntu1sttimer on 2009-09-18
Was it that it did not try to access the CD or was it that the CD spun up but then it did not load?

You have to have the BIOS in your motherboard check the cdrom drive for a boot disk before it uses the the hard drive to boot from. You may have to go into the BIOS at boot up and change the boot order to use the CD drive to boot up. If you watch the screen as the machine boots you should be given an option to access the BIOS and make the change in the boot order.

---

### Post by skatinjj on 2009-09-18
Are there any errors?  does it boot to the cd at all or just go straight to the hard drive?

---

### Post by ubuntu1sttimer on 2009-09-18
After the BIOS screen(s) display you should see the CD drive start. It takes a while to load from the CD and you get a screen asking what language you want to use. Then a screen listing options to use in Ubuntu. 

If you are having a problem, you might try the disk in another machine to make sure it is good. When the screen listing options comes up there is one choice where you can check your CD to make sure that it is a good copy. Another thing you might do if you have another computer available is to try the CD on that machine. 

In either case, you should see the CD spin up and after a delay to load files you go to the option list display. If that is not happening, it could be the CD disk or the BIOS options set to not check the CD first before booting from the HD. If you go right to your bad OS then it may not be trying to use the CD first.

One last thing, just in case, you have to start from a cold start to boot the CD. You can't start from it via your old OS.

---

### Post by aaronlong on 2009-09-19
Well I tried to setup the bios to cd, last night. I could get it to do that(I've never did that, but I tried and think I am doing it wrong; any tutorials to help me in that?) I can't set it up from my old os. The virus on the computer sets my computer to restart every time windows fully loads.

---

### Post by marcopolo1981 on 2009-09-19
Press F9 at the screen before windows tries to load, then select the ROM drive.
This should bypass your bios settings and boot straight to the Live CD.
If it doesn't, do the following:

**Configuring the boot order**
The boot order can be configured on the Advanced tab in the BIOS settings menu. The steps for modifying the boot order may vary depending on the model of the computer. 
 NOTE:  BIOS configurations vary depending on the computer. For further information on a specific computer, refer to the documentation provided with the computer or go to the HP Drivers and Downloads page . The BIOS settings are generally listed in the Maintenance and Service Guide.  

Follow the steps below to configure the boot order on most computers.
Turn on or restart the computer.
While the display is blank, press the f10 key to enter the BIOS settings menu. 
 NOTE:  The BIOS settings menu is accessible by pressing the f2 or the f6 key on some computers.  

Select the Advanced tab using the right and left arrow keys. 
Use the up and down arrow keys to select Boot Order . 
Follow the on-screen instructions to change the boot order.

This was taken from [http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979](http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979)

---

### Post by ApEkV2 on 2009-09-19
> **marcopolo1981 said:**
> 
**Configuring the boot order**
The boot order can be configured on the Advanced tab in the BIOS settings menu. The steps for modifying the boot order may vary depending on the model of the computer. 
 NOTE:  BIOS configurations vary depending on the computer. For further information on a specific computer, refer to the documentation provided with the computer or go to the HP Drivers and Downloads page . The BIOS settings are generally listed in the Maintenance and Service Guide.  

Follow the steps below to configure the boot order on most computers.
Turn on or restart the computer.
While the display is blank, press the f10 key to enter the BIOS settings menu. 
 NOTE:  The BIOS settings menu is accessible by pressing the f2 or the f6 key on some computers.  

Select the Advanced tab using the right and left arrow keys. 
Use the up and down arrow keys to select Boot Order . 
Follow the on-screen instructions to change the boot order. 


laymen's terms: 

1. Enter bios 
2. Find boot order and change the 1st drive to cdrom
3. ** Save ** and exit bios

KISS

---

### Post by aaronlong on 2009-09-19
It works! Thank you !!!!

---

### Post by aaronlong on 2009-09-19
So I am to load the live cd and I can't install it yet (my dad being an ***.) I couldn't get it to shut down in the live cd, so I manually restarted it, took the disk out. Could I **** anything up by that?

---

### Post by jonobe on 2009-09-19
no, veru unlikely to **** anything up.

You perhaps should persuade your Dad to throw out the computer.  Tell him you'll take it to the tip.  Take it to the tip, then bring it back. Say to your dad, 'hey, look what I found at the tip - a computer!'

Then the computer will be yours and you can put Ubuntu on without his permission.

It worked for me.  Sort of.

---

### Post by gadolinio on 2009-09-19
> **jonobe said:**
> no, veru unlikely to **** anything up.

You perhaps should persuade your Dad to throw out the computer.  Tell him you'll take it to the tip.  Take it to the tip, then bring it back. Say to your dad, 'hey, look what I found at the tip - a computer!'

Then the computer will be yours and you can put Ubuntu on without his permission.

It worked for me.  Sort of.
 
hahahahahahahhaah nice plan!

As far as I've studied in a short course i did in 2003, the hard disk drive suffers some damage if the power supply is gone suddenly, while it's still working. HD's in use have a flat disk spinning, and reading/writing "arms" are moving over its surface but without touching it. When you turn the computer off in the civilized way, those arms go to a safe position where they can rest without doing any harm. But if they suddenly stop receiving electricity they just fall onto the disk, in the parts destinated to the actual data storage, doing some mechanical mess. So if the computer is still "active" when you turn it off, it could be unhealthy. Anyway, i've never heard of that causing data loss; i just know it should be avoided, like smoking for us humans (but this is REALLY dangerous).
Don't know for sure if that kind of technology has changed in these six years... Maybe HD's are now immune to sudden power-off.

Try to convince him to let you install linux there!! there's nothing to loose... i mean, right now, the pc is just furniture with no use at all.
Good luck!

---

