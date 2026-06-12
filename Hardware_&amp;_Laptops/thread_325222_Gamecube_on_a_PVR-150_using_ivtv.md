---
title: "Gamecube on a PVR-150 using ivtv"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by SuperMightyMo on 2006-12-25
Hey

I have succesfully instalt ivtv ( using this guide : [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy))

The only thing i would like to have is play a console on my system, but when i try the composite of my PVR-150 i will get a delay on screen. Does anyone know how this problem is solved?

Thanx SuperMightyMo

---

### Post by superm1 on 2006-12-29
> **SuperMightyMo said:**
> Hey

I have succesfully instalt ivtv ( using this guide : [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy))

The only thing i would like to have is play a console on my system, but when i try the composite of my PVR-150 i will get a delay on screen. Does anyone know how this problem is solved?

Thanx SuperMightyMo
This is an unfortunate side effect of the design of the PVR-150/250/350/500.  Each has an mpeg2 encoder, and hence will take 1-2 seconds delay encoding all the content before it is output.

---

### Post by thomgeo1 on 2006-12-29
I had the same problem with using my Xbox with a PVR-150.  I was able to purchase an Adaptec USB Gamebridge device from Ubid for $26.  Unfortunately it only works with windows currently but the product works very well.  I think that any raw format USB tv tuner will work but I do not know that for sure.  The gamebridge was specifically designed for streaming game related content but more importantly it was pretty cheap 8) . I have not been able to find any linux drivers for this device.  I tried VMware but I could not get past an error about not being able to detect USB 2.0 devices.  I am not sure that the would work anyways.

---

### Post by thomgeo1 on 2007-01-05
I just got my Xbox working with my ATI Tv wonder pro using TVtime.  This worked out of the box, I am not sure about sound since my speakers are currently broken but I think it would work.  Picture looks great at least.

---

### Post by The Keg on 2007-02-15
> **superm1 said:**
> This is an unfortunate side effect of the design of the PVR-150/250/350/500.  Each has an mpeg2 encoder, and hence will take 1-2 seconds delay encoding all the content before it is output.

I have to disagree. Using dscaler or even wintv in windows I was able to get no delay with my wintv pvr 150. wintv required a registry edit to work and there was no de-interlacing.

I have been looking for a program to play Wii within linux (no tv in my room on residence). so far mplayer has proven the easiest except for the bloody delay. everything else mostly just refuses to even show anything.

---

### Post by superm1 on 2007-02-15
> **The Keg said:**
> I have to disagree. Using dscaler or even wintv in windows I was able to get no delay with my wintv pvr 150. wintv required a registry edit to work and there was no de-interlacing.

I have been looking for a program to play Wii within linux (no tv in my room on residence). so far mplayer has proven the easiest except for the bloody delay. everything else mostly just refuses to even show anything.
I haven't heard of any way to disable this in linux, I was always under the impression that it was mpeg2 encoding doing this.  When you watch it through dscaler is it still mpeg2, or raw content?

---

### Post by The Keg on 2007-02-16
it was decoded. there might have been half a second or less delay. dscaler runs at almost 95% cpu usage so I have a feeling it was taking the raw stream and decoding it. as for wintv 2000 I'm not certain.

clostest i've found for linux was enabling the passthrough command through ivtvctl. right now though I have to re-install the ivtv drivers before I can test it.

---

### Post by link141 on 2007-02-16
SuperMightyMo,
Which program are you using with your tuner?  I have the same exact card, followed the same tutorial (successfully), but I can't find any programs (other than myth tv) that support my card.  

Anyway, I was able to get my Gamecube working on my other Ubuntu PC (which also has a tv tuner) by using an RF switch.  What it does is plug into the cable input of your TV (or tuner) without the need to unhook the cable completely (thanks to a jack on the back of the switch that your cable plugs into).  You could probably find one relatively cheap at a local store.  A composite switch (like yours) may yield a higher quality signal, but I've found the analog output to look just about as good.  In fact, nintendo removed the digital AV out from the back of the gamecube because they found that under 2% of gamers actually used it.  If I were you, I'd just get an RF switch if this problem bothers you too much.

Tell me if you find this useful,
link141

---

### Post by link141 on 2007-02-28
Sorry, I was thinking of component...

---

