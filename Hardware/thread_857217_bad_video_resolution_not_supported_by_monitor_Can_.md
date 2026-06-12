---
title: "bad video resolution not supported by monitor Can I reset?"
date: 2008-07-12
forum: Hardware
---

### Post by theedudenator on 2008-07-12
I was playing with my video resolutions and now it is not supported by my monitor, so I cannot see anything.

Can I reset this from the command line?

---

### Post by matt$2 on 2008-07-12
But just how did you do that?
If you can't see anything, how can you execute a suggested repair???

---

### Post by overdrank on 2008-07-12
> **theedudenator said:**
> I was playing with my video resolutions and now it is not supported by my monitor, so I cannot see anything.

Can I reset this from the command line?

Hi and yes, you can use the ctrl, alt, F1 keys and reach the command line and login. Use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Or reboot into recovery mode and use the xfix option.
Edit @ matt$2
If your GUI is not working in most cases you can still reach command line as suggested above.

---

### Post by theedudenator on 2008-07-12
I tried the xfix option.
It does not work.

I was just changing the model of the video card, since it was locked on just vesa

---

### Post by overdrank on 2008-07-12
> **theedudenator said:**
> I tried the xfix option.
It does not work.

I was just changing the model of the video card, since it was locked on just vesa

Ok what is the model of the graphics card and did you try to reconfigure as I suggested?

---

### Post by theedudenator on 2008-07-13
I just now tried to run Ubuntu live from the CD.
Same problem...


I have two ATI Radeon HD3600 cards with crossfire adapters.

---

