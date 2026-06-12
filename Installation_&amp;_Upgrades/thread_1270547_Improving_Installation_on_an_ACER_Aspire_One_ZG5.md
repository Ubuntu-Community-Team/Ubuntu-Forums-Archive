---
title: "Improving Installation on an ACER Aspire One ZG5"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by lingot on 2009-09-19
My Windows XP had a problem installing the .NET Framework 3.5 SP1, after following Microsoft instruction, I end up corrupting the OS to the point that it would require to much time to fix it manually. So I decided to re-install, or should I say, I installed Ubuntu Netbook Remix 9.04 on my Aspire ONE ZG5 (8GB SDD version)

Community Documentation is pretty good, so I will refer to it as much as possible, thank you to all the people that took the time writing them, the only thing missing is a step by step approach, so here are my steps:

During installation.

I manually configure my partition: 100MB for the boot partition and the remaining for the root partition.
I use ext2 file system and didn't allocate a swap partition to optimize performance of the SDD, i.e. minimize writes. I think there is a way to have a swap partition only for hibernate but since I never hibernate I didn't look at how to do this. I will read a little bit later on ext3 and 4 to see the difference and if they are good for SDD.

After installation:

First, I optimize the SDD Performance:

[https://help.ubuntu.com/community/AspireOne#OPTIMIZING SSD PERFORMANCE:]("https://help.ubuntu.com/community/AspireOne#OPTIMIZING SSD PERFORMANCE:")
[https://help.ubuntu.com/community/AspireOne#REDUCING SSD WEAR:]("https://help.ubuntu.com/community/AspireOne#REDUCING SSD WEAR:")
[https://help.ubuntu.com/community/AspireOne#DISABLE SCROLLKEEPER:]("https://help.ubuntu.com/community/AspireOne#DISABLE SCROLLKEEPER:")


Then I install all the latest update, when it ask if you want to modify the /boot/grub/menu.lst, say yes, made the mistake to say no, it's not hard to fix later on but I would have like to avoid the extra steps.

Second: FireFox Optimization for SDD Netbook:

[https://help.ubuntu.com/community/AspireOne110L#Speed up Firefox]("https://help.ubuntu.com/community/AspireOne110L#Speed up Firefox")


Since I use Firefox most of the time, I added /usr/bin/firefox to the Startup Applications using the GUI under Preferences.

Third: activating Wireless LED

[https://help.ubuntu.com/community/AA1/Fixes#WiFi LED]("https://help.ubuntu.com/community/AA1/Fixes#WiFi LED")


Fourth: Reducing the FAN Noise

[https://help.ubuntu.com/community/AA1/Fixes#Fan Control]("https://help.ubuntu.com/community/AA1/Fixes#Fan Control")


Fifth: Unlock Keyring

Thanks to T5Dave from the Aspire One User Forums: In Network Manager, simply right click on it, select "Edit Connections", click your Wireless one, click Edit, authorise the session, click the check box next to "Available to all users" and bingo - no more network manager needs to unlock the keyring on startup

Sixth: Fix Audio Recording

Didn't work with cheese, so I followed the instruction @

[https://help.ubuntu.com/community/AspireOne#line-43]("https://help.ubuntu.com/community/AspireOne#line-43")

Still didn't work, I figure out that if I reduced the recording resolution to 320x240, it works but there is sound noise and the images are choppy. I will need to do more test. Suggestion are welcome?

Seventh: Installed the different codecs using Add/Remove Application

GStreamer ffmpeg video plugin
GStreamer extra plugins
GStreamer plugins for mms, wavpack, quicktime, musepack

Tested an XVID MPEG-4 624 x 352, work very well, sometime there are artefact like lines on the screen.
Tested an H.264 / AVC 1280 x 720, as expected, it was choppy, Tested some 480p video on Apple Web Site, work well.

Eight: Activate Card Readers when cards are not present at boot time.

[https://help.ubuntu.com/community/AA1/Fixes#Card Reader(s)]("https://help.ubuntu.com/community/AA1/Fixes#Card Reader(s)")


It added 5 seconds to the boot time, but I can't say if it use some CPU cycle during usage.

So far so good: The Nebook is operationnal and I'm happy with the performance, 45 seconds for cold boot with Firefox loaded, impressive!

If you have any suggestion to improve my installation, let me know.

Cheers,

---

### Post by lingot on 2009-10-12
Found a problem, I have a Kingston SD Elite Pro 2GB 50X

And the card is not detected.

Anyone has similar issue with some SD card?

Regards,

Huy

---

