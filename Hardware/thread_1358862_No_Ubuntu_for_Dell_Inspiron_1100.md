---
title: "No Ubuntu for Dell Inspiron 1100?"
date: 2009-12-18
forum: Hardware
---

### Post by Breath! on 2009-12-18
I've been trying for a while now to get Ubuntu to boot on my Dell Inspiron 1100, but no avail. It goes to the boot splash, then I hear the login sound and the screen is blank. 

I have 512MB RAM, a 1.99 GHz Celeron Processor, and a 82845G Intel Graphics card.

Is there a way to fix this?

---

### Post by HappyFeet on 2009-12-18
What version of ubuntu are you trying to boot?

---

### Post by teward on 2009-12-19
Might I guess 9.04 (whats listed under his name)?

---

### Post by shakma on 2010-01-25
I don't know if you stuck with it, but I'm running 9.10 on my Inspiron 1100.  I'm not just going to launch into it without a response, but I'd be happy to explain what I did if you're still trying.

For starters, 9.10 installed much easier than 9.04 (or 8.10, 8.04, or 6.10...)  But black screens are a problem until you set the xorg.conf.  Respond if you're still out there.

Peace.
shakma

---

### Post by cchhrriiss121212 on 2010-02-02
I would like to know how you set 9.10 up with an Inspiron 1100 shakma, I couldn't even get 9.04 to install. Once you set the xorg.conf, does everything else run OK (video, sound etc.)?
thanks
chris

---

### Post by david2m3h on 2010-02-02
I also have an inspiron 1100 with 82845G Intel Graphics card, 512 mb ram, and 2.0 celeron processer. Ubuntu 9.10 has been the easiest of all the versions of ubuntu for me to get working on my computer.

First before trying to install any of the ubuntu distros you need to make sure your bios is the A32 bios. I had to update my bios because the one that came with my 1100 was an old bios. If you need to update your bios you can get it from dell at:

[http://support.dell.com/support/downloads/format.aspx?c=us&cs=28&l=en&s=dfb&deviceid=5003&libid=1&releaseid=R87514&vercnt=8&formatcnt=0&SystemID=INS_PNT_CEL_1100&servicetag=&os=WW1&osl=en&catid=-1&dateid=-1&typeid=-1&formatid=-1&impid=-1]("http://support.dell.com/support/downloads/format.aspx?c=us&cs=28&l=en&s=dfb&deviceid=5003&libid=1&releaseid=R87514&vercnt=8&formatcnt=0&SystemID=INS_PNT_CEL_1100&servicetag=&os=WW1&osl=en&catid=-1&dateid=-1&typeid=-1&formatid=-1&impid=-1")

Once you are sure you have the A32 bios you need to then enter the bios and set the video memory usage setting from 1 mb to 8 mb.

Prior to 9.10 the only version of ubuntu that would run stable on my 1100 was 7.10 -- and that required the alt install cd and several tweaks. 

But with 9.10 I was able to install right from a live cd.

And it worked pretty well except for an occasional freeze caused by the video driver install by 9.10. I was able to fix this freeze by following the instructions to roll back to the 2.4 video driver found here:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

After rolling back the video driver 9.10 has been running well on my inspiron.

---

### Post by shakma on 2010-02-03
David is right, 9.10 is the first successful Ubuntu on the Inspiron 1100 since 7.10.  First things first though, update your BIOS and change the video memory setting to 8MB as he stated.

I also installed directly from the LiveCD.  However, I had no problems with the video driver, per se.  My problem was being limited to 800x600 resolution.  1024x768 is native for the 1100's screen.  
To overcome this, I borrowed the "HorizSync" and "VertRefresh" settings from LennoxRock's excellent 7.10 thread:

[http://ubuntuforums.org/showthread.php?t=651451](http://ubuntuforums.org/showthread.php?t=651451)

Most of the step-by-step instructions in the thread don't work (don't really apply) in 9.10, but the settings are spot-on!  I only needed to add these two to the "Monitor" section of "/etc/X11/xorg.conf" (note: this file is essentially empty in 9.10 by default):

HorizSync  31.5-48.5
VertRefresh 59.0-75.0

DON'T change the driver in the "Device" section.  You don't even need to manually add any resolutions.  I've attached my xorg.conf if you want to view or even use it.  You do, however, need to reboot. :mad:

But that's it.  Next time you do a fresh boot, 1024x768 will be available (and running already, iirc)!

Keep us posted on your results.

Peace.
shakma

---

### Post by david2m3h on 2010-02-03
> **shakma said:**
> 
I also installed directly from the LiveCD.  However, I had no problems with the video driver, per se.  My problem was being limited to 800x600 resolution.  1024x768 is native for the 1100's screen.  
To overcome this, I borrowed the "HorizSync" and "VertRefresh" settings from LennoxRock's excellent 7.10 thread:

The reason you did not have the same freezing issue I had and why you needed to manually set your horz sync/vert refresh rates is that you are using the "vesa" driver -- which was what we had to do to get our graphics working in 7.10.

The freeze problem I had was caused by the Intel driver included in 9.10, which is why I had to roll back to the 2.4 Intel graphics driver. 

Either solution will work fine in Ubuntu 9.10 -- vesa driver with manual settings in the xorg.conf or the roll back Intel driver. 

Just for anyone following this thread don't get confused and try to use both solutions at the same time or it could get real frustrating.

If your GUI graphics are working (you can login to the ubuntu desktop) and your xorg.conf file has the line

```
Driver		"vesa"
```

then you are using likely using the vesa driver. If this is the case and you are stuck in 800 x 600 resolution then you will need the above mentioned sync/refresh rates from shakma's post for your xorg.conf file.

If your GUI graphics are working and there is no driver defined in the xorg.conf file and your screen automatically sets at 1024 x 728, then you are likely using the Intel driver. In this case you may need to use the roll back driver instructions if you are getting what seems like random freeze ups.

Roll Back to 2.4 Intel Driver instructions
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by cchhrriiss121212 on 2010-02-04
Thankyou to both shakma and David. I still could not run the live cd with an active desktop, but an install went smoothly. My resolution was fine out of the box, so I have rolled back the driver to 2.4 after having a couple blank screens.
Sound seems to be a bit distorted on start-up though, I will try some mp3 files to test further. Other than that things are fine.

---

### Post by shakma on 2010-02-04
> **cchhrriiss121212 said:**
> 
Sound seems to be a bit distorted on start-up though, I will try some mp3 files to test further.

Quick note: I have distorted sound at start-up, too.  However, I play mp3's and radio streams all the time.  I'm listening to live radio right now, and my wife listened for 2 hours to a live streaming program last night.  Not one glitch.  Don't know what's up with the start up sound...  Do you have this issue, david?

Glad to hear of your successful install.  Long live the 1100!!!

Peace.

---

### Post by jenaniston on 2010-02-04
> **shakma said:**
> . . . 9.10 installed much easier than 9.04  . . .   But black screens are a problem until you set the xorg.conf. 


I used a U9.04 USB Live for my install to another 8 GB USB using a Dell university computer -
then booted it up on a different machine - my Sharp laptop with a messed up Windows XP OS. 
I was amazed that the Dell-made USB OS booted up*** at all*** on the laptop.

Anyhoo . . . I used U9.04 first for a netboot reason . . . but then had a 1GB USB which is all the U9.04 Live USB needed . . .

It seems after these posts that maybe it *would* be worth it to upgrade to 9.10 -
either by synaptic package manager upgrade (?) or a whole new fresh start of a  U9.10 Live version.

Thanks for the thread and posts.

---

### Post by david2m3h on 2010-02-04
> **shakma said:**
> Quick note: I have distorted sound at start-up, too.  However, I play mp3's and radio streams all the time.  I'm listening to live radio right now, and my wife listened for 2 hours to a live streaming program last night.  Not one glitch.  Don't know what's up with the start up sound...  Do you have this issue, david?

Glad to hear of your successful install.  Long live the 1100!!!

Peace.

I have not noticed any distortions in my sound at start up or any other time. However I can say that I am able to play media files, dvd and music, and it works just fine. I do have trouble though streaming flash video, but if I go ahead and download and play the flash from my hard drive it works just fine that way.

---

### Post by david2m3h on 2010-02-04
> **jenaniston said:**
> I used a U9.04 USB Live for my install to another 8 GB USB using a Dell university computer -
then booted it up on a different machine - my Sharp laptop with a messed up Windows XP OS. 
I was amazed that the Dell-made USB OS booted up*** at all*** on the laptop.

Anyhoo . . . I used U9.04 first for a netboot reason . . . but then had a 1GB USB which is all the U9.04 Live USB needed . . .

It seems after these posts that maybe it *would* be worth it to upgrade to 9.10 -
either by synaptic package manager upgrade (?) or a whole new fresh start of a  U9.10 Live version.

Thanks for the thread and posts.

I would recommend you do a fresh install, you will likely get better results.

---

