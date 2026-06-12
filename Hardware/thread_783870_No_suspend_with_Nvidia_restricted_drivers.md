---
title: "No suspend with Nvidia restricted drivers"
date: 2008-05-06
forum: Hardware
---

### Post by BrownieBoy on 2008-05-06
Apologies for yet another post about Suspend.  (I have searched, honest!)

I've a no-name desktop with AMD Opteron CPU, Nvidia 8800 GTS video card.  I've a clean 8.04 Hardy install, running the Nvidia restricted drivers from the repositories.

Suspend doesn't work for me in Hardy and didn't work in Gutsy either.  It worked fine with Feisty.  When it worked in Feisty (and as it still works in Windoze, it pains me to say), Suspend would shut off all the fans etc (natch) and the green LED next to my power button would start flashing to indicate the PC is in suspend mode.  With Hardy (and Gusty) the green light stays fully lit, and the PC fans are still blasting merrily away.  In other words, it's not really suspended at all.  It does fail to respond to any input though.  And a quick push of the power button, which was how to awaken it in Windoze and Feisty, does nothing now; I have to hold the button in and completely reboot.

This is major problem for me; suspend isn't just a laptop feature!

Open source video drivers no good to me: I'm one of those masochists that actually tries to play decent games on Linux!  (Currently on Quake 4).

Any help, much appreciated.

---

### Post by marufaberlin on 2008-05-06
Ive got the same problem, but I didn't think of it coming from the nvidia... Thanx for that post!

---

### Post by BrownieBoy on 2008-05-06
> **marufaberlin said:**
> Ive got the same problem, but I didn't think of it coming from the nvidia... Thanx for that post!

Thanks for the response.  You just reminded me, in fact, that I never tested Suspend before enabling the restricted Nvidia drives on my Hardy install.  So, as a test, I've just disabled the drivers now, leaving me with what ever the default drivers are for Nvidia (Xorg.conf didn't show any recognisable driver at all).  Suspend behaved the exact same way as it does with the restricted Nvidia drivers enable; i.e., still not working.

---

### Post by vaxius on 2008-05-09
I wrote an article/howto showing the steps I took to get suspend working for me with a GeForce Go 6150 on my HP laptop (link below).

[Howto: Get suspend working with nVidia driver]("http://blog.vaxius.net/?p=43")

---

### Post by buckminster on 2008-05-09
Thanks for the howto! It more or less worked for me (nVidia Corporation NV36.1 [GeForce FX 5700 Ultra], abit an7 mboard). I had to add agpart to my blacklist for the "NvAGP" option to stick (suspend didn't work without it). Also, after resuming from a second suspend, my screen is all white where it should be prompting me to unlock my desktop. If I go through the motions of entering my password, my desktop comes back as expected. After disabling screen lock, my computer comes out of suspend like expected.

This is the first time since 6.10 that I was able to successfully suspend my system!

---

### Post by BrownieBoy on 2008-05-11
> **vaxius said:**
> I wrote an article/howto showing the steps I took to get suspend working for me with a GeForce Go 6150 on my HP laptop (link below).

[Howto: Get suspend working with nVidia driver]("http://blog.vaxius.net/?p=43")

Thanks.  Will give it a try and post back here to say how I got on.

---

### Post by BrownieBoy on 2008-05-11
@Vaxius,

I went through the steps in your blog, and rebooted after every stage.  Still no joy for me, I'm afraid.  The green light stays on, and the PC's fans are still whirring away.  The PC just never suspends.

---

### Post by logos34 on 2008-05-11
hmm, interesting...I was never able to get hibernation AND suspend to work in feisty or gutsy, but I always thought it had something to do with the kernel (i.e. ubuntustudio -rt kernel), not nvidia.  Hardy is actually the first time I've been able to get both to work properly.

---

