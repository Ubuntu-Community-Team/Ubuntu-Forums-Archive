---
title: "Everex NC1501 Linux Compatible?"
date: 2010-07-15
forum: Hardware
---

### Post by Zyrtec on 2010-07-15
I'm acquiring this 3yr old budget laptop from my dad now that he's got a new laptop. I plan to use it like a Netbook since it has some pretty low specs and I already have another and better laptop.

The basic specs are:

VIA C7-M CPU  1.5GHz
1.5GB RAM
60GB HDD
VIA Chrome9 HC-IGP 64MB Graphics

I've been trying to find whether or not any Linux distro is compatible with the Integrated Graphics. After some research, I've found that older releases were not very compatible using a VEVA driver, and apparently people complained of being stuck with 800x600 resolution, with the fix being overly complicated.

Does anyone know whether Ubuntu or any other Linux distro has become more compatible with this hardware? I would rather take Vista off of the computer, but if I'm going to run into annoying problems with annoying fixes, I'd rather not bother since I can't find any instructions on how to fix it. 

Please help!

---

### Post by Zyrtec on 2010-07-16
bump

---

### Post by Zyrtec on 2010-07-16
Can somebody at least tell me if I can use the LiveCD to see if I'll run into any problems? Will the same problems arise (if there are any) while running the LiveCD like installing?

---

### Post by gordintoronto on 2010-07-16
Why not try booting the LiveCD?

The Chrome graphics might be a source of grief.

---

### Post by Pareto Optimal on 2011-02-26
Yes, Ubuntu will work.
I've also used, cough, W7 on mine.  
The ONE major problem is the headphone jack wont work in either (any) OS.  
Every manufacturer in the world has a particular BIT in their sound chip set a particular way.  Everex is the ONE company in the world who set it the OTHER way.  Every driver software expects that BIT to be in the usual way.  It isn't the usual way.  So, NO driver except the one Everex packaged with the NC1501 will work.   If you have the discs/driver that came with the NC1501, PLEASE send me the freaking sound driver.  

A GENIUS Linux driver engineer friend of mine spent countless work hours trying to create a driver that would work.  He was able to permanently turn the mono speaker OFF and enable the headphone jack albeit the volume was VERY low in the headphones.  In my attempts to work on the driver, I wrote over his driver code and am back to a mono speaker and no headphones.  

I've read online posts where a couple of people claim to have turned the onboard sound OFF in the BIOS so they could use a USB heaphone jack but my BIOS has no voice settings and any USB device I've used hasn't worked.

Some online posts speak of more expensive USB devices that may work to some extent.  

If you find a solution, PLEASE POST IT.  

SMPlayer will sound louder than VLC Media Player when Playing movies.  SMPlayer has a FILTER setting where you can normalize sound which will make your movie volume louder.  


> **Zyrtec said:**
> I'm acquiring this 3yr old budget laptop from my dad now that he's got a new laptop. I plan to use it like a Netbook since it has some pretty low specs and I already have another and better laptop.

The basic specs are:

VIA C7-M CPU  1.5GHz
1.5GB RAM
60GB HDD
VIA Chrome9 HC-IGP 64MB Graphics

I've been trying to find whether or not any Linux distro is compatible with the Integrated Graphics. After some research, I've found that older releases were not very compatible using a VEVA driver, and apparently people complained of being stuck with 800x600 resolution, with the fix being overly complicated.

Does anyone know whether Ubuntu or any other Linux distro has become more compatible with this hardware? I would rather take Vista off of the computer, but if I'm going to run into annoying problems with annoying fixes, I'd rather not bother since I can't find any instructions on how to fix it. 

Please help!

---

### Post by Pareto Optimal on 2012-03-24
BTW, I took W7 OFF ... it was unacceptably slow.  
This VIA chipset was NEVER meant to run ANY flavor of Windows.  
So, it's odd that it was sold wtih Vista preinstalled.  
I suppose Everex thought they wouldn't move many units with Linux preinstalled.  

Well, back when I posted my first response to this thread, I couldn't find ANY Vista drivers onlline.  Well, this year, 2012-February, I found a free site that had ALL the Vista AND XP drivers for the 1501.  

I tried XP Pro SP3 with the Everex drivers and found it to be waaaay tooooo slow.  

Ubuntu should run everything except your sound wont be very good as I mentioned above.  

If you need the drivers, I could find that webstie again.  I've also downloaded them all and have them somewhere on a HDD.

---

