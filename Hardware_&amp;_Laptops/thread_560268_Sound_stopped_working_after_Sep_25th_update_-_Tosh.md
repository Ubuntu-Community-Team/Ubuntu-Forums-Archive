---
title: "Sound stopped working after Sep 25th update - Toshiba A135-S4427"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by YusukeJai on 2007-09-26
Sound has been an issue with this laptop and Feisty for alot of people. It ships with Vista and has no XP drivers. So it's either Vista or Linux on this laptop, which happens to be a popular laptop. Hopefully sound, and a few other things will work with Gutsy out-of-the-box. Anyhow, I did get sound to work properly with Feisty and it worked fine for months. However, after this update on September 25th (I believe it was a kernel patch - slightly under 40mb), the sound stopped working after I rebooted. I use the current alsa-drivers and gedit'ed the alsa-base options, and yet it doesn't work anymore. I've got to the point to where I don't even pay much attention to Ubuntu updates and just install them all, because I've yet to have any problems from them until now. Can anyone give me some suggestions? Thanks.

---

### Post by metol on 2007-09-26
Hello, I had the same problem with my A135.  I recompiled and installed the ALSA driver, lib, and utils as outlined on this [page]("https://help.ubuntu.com/community/HdaIntelSoundHowto").   (all you need to do is the steps outlined in the "Update to the Latest Version of ALSA" section). Then I rebooted and the sound worked again.

---

### Post by YusukeJai on 2007-09-27
Thanks metol, I recompiled everything and it works great now as it did before. I also tried out the Gutsy beta (live cd) today and sound, as well as some other bugs Feisty had with the A135 were fixed :)

---

### Post by metol on 2007-09-27
Glad to here I will not have any issues moving to Gutsy (I have not tried it yet).  Did you notice if sleep & suspend were working correctly?  In feisty, I have a tendency to lose my wireless when doing this.

---

### Post by earnoth on 2007-10-06
I tried this on my A135-S4427 with kernel 2.6.20-17 and it failed.  Before I tried it, there were no errors, but no sound either.  After I tried it, alsa_mixer wouldn' load, complaining about an alsa_ctl call failing. 

Thankfully, I was able to boot into 2.6.17-10 and still have sound, but that's the only kernel where sound works for me.  (it was my install kernel, 2.6.20-17 is an upgade through Ubuntu upgrade facilities).

Help?

---

### Post by Boelcke on 2007-10-13
Hi. I just recently got a Toshiba A135-S4527 laptop, which came with Vista.  When I boot from the Feisty LiveCD, the wireless works right away (icon on the top bar, click to get onto my network, I'm running), yet the sound doesn't.  From this and a few other posts, I see that I should be able to get the sound working.

However, with Gutsy coming along so soon, it seems like I should wait.  So, I tried booting off the Gutsy beta CD, hoping that the issues were fixed, and: No Wireless, No Sound.

I guess I'm wondering if I should just install Feisty, and wait before messing with Gutsy.  I'd like to get up and running without too much instability!

EDIT: Hm, I just re-tried things with the Gutsy beta live CD, and the wireless seems to work fine.  I wonder what I missed before.

Still no sound, but I'm presuming that I'll be able to fix it using the same method described for Feisty, once I get the thing properly installed on the HD.

Now my only question is whether to wait until the official release, or install now and let the updates bring it up to speed.  I've read in these forums that the updates will really make the install "equivalent" once the thing is all installed.

---

### Post by metol on 2007-10-14
Good News,

I just upgraded to Gutsy Beta this afternoon and the procedure indicated in my first post works fine.  I let the upgrade trash my /etc/modprobe.d/alsa-base file.  After I rebooted, I recompiled the ALSA drivers and then did...

```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then I added the following line to the very bottom of the file...

```
options snd-hda-intel position_fix=1 model=lenovo
```

Rebooted and then sound worked again.

Metol

---

### Post by metol on 2007-10-15
More good news, I just did a kernel update in Gutsy to  2.6.22-14 and was fully expecting to have to recompile the ALSA drivers.  After the update, I rebooted and the sound was still working.  That was too easy.  All-in-all, my upgrade to Gutsy Beta was fairly painless, every thing seems to work well.  Knock on wood.  I have not tried sleep and suspend yet, maybe I will give it a go this evening.

---

### Post by Boelcke on 2007-10-15
Well, with just 3 more days until the official release, I'm just going to wait until later this week to install Gutsy.  I've waited this long...

I'll add my experience with sound issues here too.

---

