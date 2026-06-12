---
title: "T61P-- Perfect Linux Laptop."
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by saxofoner on 2007-11-23
Thinkpads have, of course, always been hailed as some of the best laptops for Linux.
The T61 series is the newest lineup, and, as the proud owner of a T61P, I would like to say that it is the perfect Linux laptop.  

I've seen some threads recently about getting various things to work on this series, and I'd like to say that, yes, it all works.  (except Hibernate, but that... doesn't count.)

The microphone works, the graphics drivers work very well (I get 70 fps on Team Fortress 2 in WINE  :guitar: I only get 30 FPS in Vista), suspend works nicely, HDAPS can be configured.

Anyway, just wanted to recommend this to any prospective buyers.

Ask me anything you want, some of this stuff does take a while to figure out.

P.S. rocklight is one of the coolest useless things I've seen.

---

### Post by catfishk on 2007-11-23
rocklight is incredibly useful.  sometimes you just need to know that someone, if only your laptop, likes the music you listen to :)

 I run a Thinkpad T60. and i agree these are the best laptops ever assembled by man (though i am certain aliens have better driver support or they couldn't land spaceships in my back yard every full moon).  i have an ACPI question posted if you might like to help.  i am trying to trigger the laptop to wake up upon opening the lid, and without needing to press the power button:

[http://ubuntuforums.org/showthread.php?t=621279](http://ubuntuforums.org/showthread.php?t=621279)

 try this blog for getting hibernate to work with fglrx (ATI X1300).  my machine suspends and hibernates using uswsusp or tux on ice, currently, by adding the SLAB parameter in a custom 2.6.22 kernel

 [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

---

### Post by Ansible on 2007-11-25
Hey saxofoner, I've read that some people are having trouble with the video drivers.  Did you do anything special to install the drivers, or did you just do the regular restricted install?  From what I've read, the restricted drivers can prevent the wireless from working, sound, etc.

---

### Post by firstc624 on 2007-11-25
i have a t61 and i do have problems.  my 3d stuff is blacklisted due to the intel video package is messed up.

how did you get the x3100 working w/o bypassing the 3d cecks?

---

### Post by Ansible on 2007-11-28
The t61p has a different video card than the t61.  Its a quadro FS 570M.

---

### Post by poorbadger on 2007-12-03
I've got a T61P as well.

Suspend sometimes works, sometimes doesn't - I haven't determined a pattern yet but I believe it has to do with how long it's been suspended.  If it's a relatively short time - say an hour - it rehydrates everything and I'm presented with a log back in dialog.  If it's a longer period of time - I don't know, maybe 2-4 hours - it'll either reboot or just hang w/ a blank screen and I'll have to power off and power back up.  As I said, I haven't got the pattern down so don't take those times as gospel.

Relevant settings...

/etc/default/acpi-support
POST_VIDEO=false
SAVE_VBE_STATE=false

One other thing that I find really annoying is the sound clips/distorts at really low levels - I know it's not a multimedia machine but I'm talking newscasts, etc.  I'm not sure if this is specific to the T61P or the T61P/Ubuntu combo because 7.10 is the only OS I've got installed (outside of some VMWare play stuff).  I may install XP and dual boot between the two because I've got Windows Dev work I need to do but then I might just try that via VMWare. Anyway, if I do dualboot I'll check on the clipping.  Does anyone else have this issue?

---

### Post by poorbadger on 2007-12-03
Oh, one more thing - and not really a big deal, just kind of weird.

When booting up and transitioning from the splash screen (ubuntu + progress bar) to the welcome/login screen (blank peach screen in between the two) there's a section in the bottom right about 2" x 1/4" with a white block and then TV static (random RGB pixels).  Have you seen that?

Restricted NVIDIA drivers installed. Desktop effects set to "Normal".

Thanks!

---

### Post by hvac3901 on 2007-12-03
> **poorbadger said:**
> I've got a T61P as well.

Suspend sometimes works, sometimes doesn't - I haven't determined a pattern yet but I believe it has to do with how long it's been suspended.  If it's a relatively short time - say an hour - it rehydrates everything and I'm presented with a log back in dialog.  If it's a longer period of time - I don't know, maybe 2-4 hours - it'll either reboot or just hang w/ a blank screen and I'll have to power off and power back up.  As I said, I haven't got the pattern down so don't take those times as gospel.

My T61 does that and i still use windows on it. havn't made the switch yet. I dont think its an Ubuntu issue, just my opinion.

---

### Post by poorbadger on 2007-12-04
Sorry, I don't think this has anything to do with time is suspend but how often you go into suspend between reboots as others have reported.  I suspended last night ~12:00 and brought it back up today ~8am - no problem.

> **poorbadger said:**
> I've got a T61P as well.

Suspend sometimes works, sometimes doesn't - I haven't determined a pattern yet but I believe it has to do with how long it's been suspended.  If it's a relatively short time - say an hour - it rehydrates everything and I'm presented with a log back in dialog.  If it's a longer period of time - I don't know, maybe 2-4 hours - it'll either reboot or just hang w/ a blank screen and I'll have to power off and power back up.  As I said, I haven't got the pattern down so don't take those times as gospel.

Relevant settings...

/etc/default/acpi-support
POST_VIDEO=false
SAVE_VBE_STATE=false


---

### Post by poorbadger on 2007-12-04
To clarify, are you referring to the sound clipping or the suspend issue?  And this is when running XP, correct?

> **hvac3901 said:**
> My T61 does that and i still use windows on it. havn't made the switch yet. I dont think its an Ubuntu issue, just my opinion.

---

### Post by hvac3901 on 2007-12-04
> **poorbadger said:**
> To clarify, are you referring to the sound clipping or the suspend issue?  And this is when running XP, correct?

the susspend issue, And yes that is with XP running.

---

### Post by McLogic on 2007-12-12
[SIZE="4"]We all wish that Nvidia would just open their drivers:[/SIZE]
[**[COLOR="Blue"]http://www.petitiononline.com/nvfoss/[/COLOR]**]("http://www.petitiononline.com/nvfoss/")

Then it would not have suspend issues.

---

### Post by MRCeltic on 2007-12-25
Glad I have an R40 Thinkpad, although the only issue that I have had is that when I resume from Hibernate mode, My wireless doesn't connect.  once in awhile the wireless will give me a prob but i just reboot the router and/or reboot and problem solved.  I didn't have to download any additional drivers either Ubuntu 7.10 had everything.  This was the first time trying linux on my laptop, many attempts on my desktop which all seemlessly failed. just wasn't meant to be,

---

### Post by [ajax] on 2008-01-01
I would like to also say that suspend to RAM also has issues seemingly dependent on how long it has been suspended.  

Whenever I suspend overnight I can't resume, with the same symptoms of either getting a blank screen  or a re-boot.

I tried suspending and resuming repeatedly and the laptop showed no signs of problems.

I would really appreciate any light someone can shed on this.

---

### Post by samskpun on 2008-01-04
I also have suspense issue. However, it is not related to time. If i suspense more than once without reboot, the screen will remain blank (the moon icon blink). 

Otherwise, it is a rock solid laptop :D. I love it a lot

---

### Post by McLogic on 2008-07-08
> **samskpun said:**
> I also have suspense issue. However, it is not related to time. If i suspense more than once without reboot, the screen will remain blank (the moon icon blink). 

Otherwise, it is a rock solid laptop :D. I love it a lot

I have to say that it is NOT rock solid if it does not come back from suspend. I'm still using the software ("vesa") driver. At a minimum, nvidia could open a driver that has POWER MANAGEMENT, so their chips are not _burning the battery while providing no acceleration_.  

[SIZE="4"]PLEZ sign the nvidia open drivers petition:[/SIZE]
[SIZE="5"][http://www.petitiononline.com/nvfoss/](http://www.petitiononline.com/nvfoss/)[/SIZE]

I'm pissed that nvidia have made getting their $200 professional chip worse then having an Intel integrated card.

---

### Post by vlam21 on 2008-07-08
I'm sorry to deviate from the topic of suspension, but I seem to have a problem with my video. (I also have a T61P, by the way) Whenever I navigate through Firefox (with mousewheel or clicking and dragging), the page moves rather choppily, which is, I believe, somewhat unusual for a laptop of this caliber. Can anyone help me with this, please?

I'm using the nVidia drivers, by the way.

---

### Post by feeshy on 2008-07-11
With the latest EnvyNG Nvidia drivers and the .fdi changes recommended here ([http://rende.se/index.php?n=Main.UbuntuHardyOnT61](http://rende.se/index.php?n=Main.UbuntuHardyOnT61)), suspend and hibernate work perfectly.  173.14.05 drivers and 2.6.24-19-generic kernel in Hardy.  Okay hibernate isn't exactly speedy and it does feature two beeps and some garbled video, but it does come back everytime which suspend didn't always do with older drivers.

---

