---
title: "Can Ubuntu have somehow &quot;modified&quot; my hardware?"
date: 2010-11-11
forum: Hardware
---

### Post by fabecool on 2010-11-11
Hi there!

I have had a laptop for like 5 years, and I've been very happy with it (Acer Aspire 1681 WLMI). I has a Centrino configuration and came with Windows XP Home CDs. After a while, I got tired of Windows, so I switched to Ubuntu, and it has worked even better. 

But now, I'd like to sell it, and the buyer wants Windows on it. So I took the Windows CDs that came with it, and it crashes all the time. I installed from a WinXP pro CD I got from work, and installed the drivers one by one. I was able to identify the problem: the intel wi-fi driver makes the computer unstable and I get the blue screen. I've tried the latest drivers, etc. but nothing helps.

I have never had that before, so I tried and installed Ubuntu again to test it, and the WiFi works perfectly. 

So my question is: can it be that Ubuntu has changed something "physically" on the wi-fi adapter? Or have you heard of similar things happening of hardware not working under Windows after they are used with Ubuntu? 

I know that usually, the questions on this forums are like "my hardware works fine in Windows, but not in Ubuntu. That sucks!". Well, for me it's the other way around! :)

Thanks in advance!

Fa

---

### Post by mastablasta on 2010-11-11
no it didnt' change anything phisically. but if windows was preinstalled then usually it had a recovery partition which should be used to recover the WinXP. it could be it used some special drivers. then again if you found **correct** drivers for winXP and installed them then it should work.

---

### Post by fabecool on 2010-11-11
Thank you, Mastablasta.

Back then, the manufacturer provided recovery discs on CD, not on a partition. 

Mine are kind of a bootable Norton Ghost image. I had used them a couple times when I was still using windows and they worked well back then. Now the recovery process is smooth and quick, as before, but the PC crashes when Windows is booting. It actually crashes when the desktop is already visible. I suspect it happens when WinXP is loading the Wi-Fi drivers. 

As I said, I have tried the recovery CDs, but also another WinXP installation with the latest drivers (from Acer's website), but I get the same issue.

Thanks for the suggestion anyway!

Anyone else has an idea?

Cheers,

Fa

---

### Post by P4man on 2010-11-11
Linux (like windows) loads firmware on the wifi card. Though AFAIK, that gets erased when you turn the machine off, and overwritten anyhow as you load other drivers. If somehow this would be related to your problem ( I still doubt it), you could try turning wifi OFF in the bios, or even physically remove the wifi card, install windows + drivers, then activate it again / turn it on.

Honestly a more likely cause is that something went bad in the laptop, like RAM. And perhaps a region ubuntu rarely if ever used, which is why you may not have noticed. Have you tried running memtest?

---

### Post by fabecool on 2010-11-11
Thanks P4man,

I must confess that I have not run memtest. It did not even cross my mind that it could be something else than the wifi card, since everything else runs smoothly until I install the driver for it. As long as it remains as unrecognized hardware in the hardware manager, there's no problem. 

I was looking at the bios yesterday (it's very basic), and I don't remember seeing any option for turning wi-fi off. I'll have a look though, maybe I just did not look well enough. Removing the adapter is not possible, since it's embedded in the computer. And the wifi on/off button usually only becomes available when the driver has loaded, which does not help me...

Anyway, I'll run memtest tonight when I get home and see what happens...

Cheers,

Fa

---

### Post by P4man on 2010-11-11
Ok, if its stable before installing the driver then forget all my suggestions. You are most likely simply installing the wrong driver. Try grabbing the one off Acer's site.

---

### Post by fabecool on 2010-11-11
The latest drivers I've tried did come from Acer's website. I have also tried to use those (older) that were provided with the laptop. The WinXP recovery image does not have the drivers in them. These are on another CD with an automated routine to install everything when recovering. Of course, you can also use the CD to install the drivers separately. Besides, since the old ones worked well before, I don't see why they do no longer, especially since the configuration hasn't changed a bit. Really puzzling...

Thanks for you suggestions and help! I'll try to see how a USB wireless LAN adapter works with it.

Cheers,

Fa

---

