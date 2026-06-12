---
title: "HP Pavillion Laptop resolution issue.."
date: 2010-04-19
forum: Hardware
---

### Post by Baldrick_NZ on 2010-04-19
Hi all,

My Mum has the above Laptop (I'm not sure of any further details at this stage, however) when I run the latest Lucid live CD on it, the best resolution I can get is 800/600. 

Can anyone give me any tips as to troubleshoot this issue to get a higher resolution please?

It's currently running Vista, but Mum's growing really tired of the constant security/antivirus/other updates that we have all come to know and love so well of Windows. :P

I'd like to create an Ubuntu dual-boot for her, so she can do most of her stuff (Internet/E-mail/Skype/Aislerot, etc..) hassle free. But I'm not going to do so if I can't resolve this issue.

Any help would be much appreciated.

---

### Post by cascade9 on 2010-04-19
Its probably from there being no installed video card drivers.

---

### Post by byStanderone on 2010-04-19
...check on this thread:[http://ubuntuforums.org/showthread.php?t=1413027](http://ubuntuforums.org/showthread.php?t=1413027)

---

### Post by Mark Phelps on 2010-04-19
You need to find out what video chipset the machine has installed.  There are a lot of Pavilion models and they don't all use the same chipset.

If it's one of the older ATI chipsets (not one of the new HD 3x/4x/5x), then you're stuck with the open-source driver in anything newer than Ubuntu 8.10.  ATI dropped Linux support for the older chipsets over a year ago.

---

### Post by _0R10N on 2010-04-20
You shouldn't be worry, I have a laptop pretty much like your mum's, and the screen resolution issue went away when I updated the system.

Kind regards!

_0R10N >>

---

### Post by cespinal on 2010-04-20
I also own an HP, and I am 99% sure it is just the live CD doesnt come with the drivers for your graphics cards. Once you install ubuntu, It will detect which extra drivers you will need. Install them, reboot, and voila...

This is not a problem on the mere sense of the word...

---

### Post by Iowan on 2010-04-20
> **Mark Phelps said:**
> You need to find out what video chipset the machine has installed.  There are a lot of Pavilion models and they don't all use the same chipset.
+1
I have two HP's here - the one I own has an ATI chipset, the one I'm trying to resurrect for a friend has an Nvidia chipset. Mine is new enough (running Jaunty) that I could use the proprietary driver.

---

