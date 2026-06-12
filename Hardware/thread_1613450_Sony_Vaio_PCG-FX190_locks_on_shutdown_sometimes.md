---
title: "Sony Vaio PCG-FX190 locks on shutdown sometimes"
date: 2010-11-04
forum: Hardware
---

### Post by double1116 on 2010-11-04
I have a Sony Vaio PCG-FX190 laptop with Ubuntu 10.10 Desktop. Detailed specs are below, but the most important info is that it has an Intel i815 graphics chip. This laptop works fine with Ubuntu for the most part. I had to adjust the quirks to get suspend working, but now suspend is working fine. However, sometimes when I shutdown by choosing the Shutdown option from the Me Menu or from GDM the laptop locks up with the scroll lock and num lock lights flashing. It appears to occur when X is terminated, the screen goes black and it locks up. If instead of clicking those shutdown buttons I logout, go to VT1, login to the terminal and run "sudo shutdown", there is no problem.

The following steps make it always happen:
1. Bring up to the GDM screen
2. Choose suspend from the menu
3. Resume
4. Shutdown

The following steps make it sometimes happen:
1. Login via GDM
2. Use the machine for 30 minutes or so
3. Shutdown from the Me Menu

Machine:
- Sony Vaio PCG-FX190
- 512MB RAM
- i815 video
- 32MB Shared Video RAM (breaks with 48M configured too)
- DRI and AIGLX enabled (these are the defaults)
- Depth of 16 configured in X. I forgot exactly why, but I think DRI/2D accel won't work otherwise. I don't/can't use desktop effects/compiz.
- Ubuntu 10.10
- KMS not available for this chipset

I tried disabling AIGLX with no difference. I've tried many combinations of video quirks for suspend, but that would not explain the lockup when I don't use suspend.

Any ideas?

---

### Post by P4man on 2010-11-04
Could it be a modeset issue when X is unloaded and kernel takes over for the shutdown splash ? Though I wouldnt expect that to cause a kernel panic, its easy enough to try. Boot with nomodeset kernel option (see my sig if you need help with that).

---

### Post by double1116 on 2010-11-05
The i815 does not have kernel mode setting support (KMS) so this isn't the issue. I tried with the option anyway, no difference.

---

### Post by double1116 on 2010-11-07
I think I fixed it. DRI requires a depth of 16. I changed the depth to 24, which disabled DRI, but I haven't had the lock up yet. So either the depth of 16 is the problem, or DRI. I tried either disabling DRI and leaving the depth at 16, but X would start. Without DRI I can't do 3D accel stuff, but compiz won't run without 24bpp anyway, and this machine is too slow for 3D intense games anyhow.

---

### Post by chris1379 on 2010-11-11
I had this problem also on a PCG-FX150. It hasn't done it lately but I'm not sure what I did. The problem I have is that the backlight will not go off either automatically or using ```
xset dpms force off

``` . Does yours work OK? I have a thread on the topic with no good solution yet. [http://ubuntuforums.org/showthread.php?t=1471349](http://ubuntuforums.org/showthread.php?t=1471349)

Chris

---

### Post by double1116 on 2010-11-12
> **chris1379 said:**
> I had this problem also on a PCG-FX150. It hasn't done it lately but I'm not sure what I did. The problem I have is that the backlight will not go off either automatically or using [CODExset dpms force off
][/CODE] . Does yours work OK? I have a thread on the topic with no good solution yet. [http://ubuntuforums.org/showthread.php?t=1471349](http://ubuntuforums.org/showthread.php?t=1471349)

Chris

I tried ```
xset dpms force off
``` and the backlight won't turn off. I don't have that problem with suspend or hibernate though. I have a page at [https://sites.google.com/a/patdouble.com/pat/computer/sony-vaio-pcg-fx190](https://sites.google.com/a/patdouble.com/pat/computer/sony-vaio-pcg-fx190) that explains what I did to get this machine working. I added a couple extra files for suspend to work. Most notably I need to switch to a text terminal before suspend otherwise I still get lock ups.

---

### Post by chris1379 on 2010-11-13
Thank you so much for the info on your website. I applied the fixes and they work. As for the backlight, let me know if you find a solution.

---

### Post by double1116 on 2010-11-24
I still had some problems with the machine locking after resume. I updated the 99quirks file on my page (referenced above). I have not had any further problems, I highly recommend you update. As for the backlight, no ideas. Possibly these models don't allow the backlight to be turned off? Does it turn off when using Windows?

---

### Post by chris1379 on 2010-11-24
I updated the 99quirks file and I'll let you know how it goes. As for the backlight, it works like it should in Windows XP. There may be something added by Sony to make it work because there are some Sony library files installed. Do you know of any forums or sites that have good info on this series of laptop? By the way, I was able to use DRI without any issues but I have the 1024 x 768 screen. Doesn't turning off DRI affect your video (movies) play?

---

### Post by chris1379 on 2010-12-18
Nope, I still get lockups with flashing lights on shutdown. What issues will this cause other than having to hold the power button to turn it off?

On a different note, I just had a major ordeal with my Windows desktop machine. I had a virus that I got rid of but an improper registry edit caused Windows to lose my entire profile and delete my entire "My Documents" folder. Don't ya love Microsoft!

---

### Post by double1116 on 2011-01-10
I have no other ideas for you. Yes, turning off DRI makes videos unable to play, but for my needs suspend is more useful than videos. Apparently YYMV with the settings.

Every once in a while I do get a lockup when trying to resume. It seems to be related to the length of time I leave it suspended.

---

### Post by chris1379 on 2011-01-10
I can suspend mine most of time without any problems with DRI on. Maybe turning it off just masks a hidden problem. There seems to be no rhyme or reason to it in my case.

---

