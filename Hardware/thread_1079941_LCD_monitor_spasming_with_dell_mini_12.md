---
title: "LCD monitor spasming with dell mini 12"
date: 2009-02-24
forum: Hardware
---

### Post by Crash.hm on 2009-02-24
Hi,
 I'm kinda new to linux, but I did a few searches and the best I could come up with from those was check my connections which I've done.

I've had my dell mini 12 for a few days now, for the most part it seems good but sometimes a bit slow. My new viewsonic 19" monitor is great except that it keeps spasming. It's like haveing the screen twitch right and left. It also won't generally offer me the ability to change my resolution to 1400x900 (or ever its supposed to be) which would be neither here nor there except that it does occasionally seem to support the option.

Does anyone have any idea what I should do?

---

### Post by HittingSmoke on 2009-02-24
> **Crash.hm said:**
> Hi,
 I'm kinda new to linux, but I did a few searches and the best I could come up with from those was check my connections which I've done.

I've had my dell mini 12 for a few days now, for the most part it seems good but sometimes a bit slow. My new viewsonic 19" monitor is great except that it keeps spasming. It's like haveing the screen twitch right and left. It also won't generally offer me the ability to change my resolution to 1400x900 (or ever its supposed to be) which would be neither here nor there except that it does occasionally seem to support the option.

Does anyone have any idea what I should do?

Sounds like the monitor is not correctly adjusting or scaling the resolution. Does it still do this when you set it to it's native resolution? What is the monitor's model #?

Have you tried using the auto adjust feature in the monitor settings menu? Also, are you using DVI or VGA monitor connection to your PC?

---

### Post by Crash.hm on 2009-02-24
The monitor is a viewsonic va1926w

its reccomend resolution is 1440x900

I connect via vga

I just got the option again to use the 1440x900 but I don't understand why this appears as an intermittant option. I'm going into the resolution control and doing the same thing each time and it doesn't seem to have any consistancy about offering the higer resolution. 

right now I am using the reccomended resolution and tried the auto adjust feature. Hopefully that works, but i still have no idea if i'll be able to consistantly use the the reccomended resolution. 

thanks for the quick feed back

---

### Post by Crash.hm on 2009-02-25
I'm still having problems. I got it set to the right resolution and i used the auto ajust feature in the monitor. Does any one have any ideas?

---

### Post by happycube on 2009-02-25
You might want to repost this to the Dell section, and file a bug.

Sadly the mini 12 uses the GMA500/Poulsbo chipset.  This is PowerVR based and the driver situation is currently far worse than for any other chipset that intel's ever done, all the way back to i810.

[http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ) for more info. :(

Since you just bought it, you may want to consider exchanging this for something with a GMA950 instead.  And make sure that the relevant people at Dell and intel know *why*.

---

### Post by Crash.hm on 2009-02-25
thread moved: [http://ubuntuforums.org/showthread.php?p=6796610#post6796610](http://ubuntuforums.org/showthread.php?p=6796610#post6796610)

---

### Post by Crash.hm on 2009-02-26
Final solution was to turn down the res. to 1280x960. so far it seems stable. Dell claims that it will not support higher res of an external.

---

