---
title: "Monitor configuration problems"
date: 2010-02-24
forum: Hardware
---

### Post by datpapi on 2010-02-24
I've scoured the internet and a number of forums but I am still unable to resolve my problem.

I am running Ubuntu 9.10 with an ATI Radeon X600 video card. Everything installs well and appears to work fine, except that Ubuntu cannot detect my display. I am connecting directly to my LCD TV using the VGA output on the video card to the VGA input on my TV.

Ubuntu detects the monitor as UNKNOWN and as a result I only have 640x480(4:3) and 800x600(4:3) resolution modes.

I've followed a number of tips such as [http://ubuntuforums.org/showthread.php?p=8302145#post8302145](http://ubuntuforums.org/showthread.php?p=8302145#post8302145)
here [http://ubuntuforums.org/showthread.php?t=1415284](http://ubuntuforums.org/showthread.php?t=1415284) and a few other places.

I've followed the instructions to the T and with the first link, I end up getting "Signal not compatible" message on my TV. To make it worse, the steps to undo the changes didn't work and I've had to reinstall Ubuntu 5 times now.

Needless to say I am at my wits end. I really wish I was able to use the ATI CCC to see if I could manually configure the monitor, but it doesn't appear the Linux ATI driver includes this. 

The latest proprietary driver does not support my card and to make matters worse, the last driver revision 9.4, is apparently not compatible with Ubuntu 9.10 ( I got an error running the SH command about some include versions were wrong and not specified)

The Video card and TV can support the 1024x768 resolution I am wanting to use ( Works on my dual boot Windows OS)

Any other ideas?

---

### Post by datpapi on 2010-02-25
I see that 36 people have viewed this but not a single reply:D. Guess everyone is as stumped as I am! 
 
If I can get my LCD TV to work using my ATI card that would be great, but if push comes to shove, I am looking into buying an Nvidia based card with an HDMI output. At least this way I know I can use the NV proprietary driver which comes with the X Server app.

---

### Post by zeusrock1 on 2010-02-25
I can't help, I'm pretty new to Ubuntu also, but do feel your pain. Last weekend I ran into the same problems as you... Install, try linux ati driver, modify xorg.conf, boot into terminal, uninstall driver, install flgrx driver, uninstall driver, repeat. Nothing worked. I couldn't even install 9.10 or 9.04 unless it was in safe graphic mode.

I ended up installing Ubunutu 8.04 and ATI Catalyst propietary 9.8 and everything worked without setting up anything manually.

I still don't know if it's my soyo LCD monitor or my ATI HD 4200 onboard card, but at this point I'll just wait and see if 10.04 is any better in a couple months.

My laptop on the other hand has no install problems whatsoever.

Hope it works out for you.

---

### Post by datpapi on 2010-02-25
I was considering downgrading to an older version of Ubuntu, but I'd rather dump the video card before doing that. It's pretty old anyway.
 
BTW Ubuntu 9.10 runs beautifully on my laptop as well

---

### Post by datpapi on 2010-03-01
> **datpapi said:**
> I see that 36 people have viewed this but not a single reply:D. Guess everyone is as stumped as I am! 
 
If I can get my LCD TV to work using my ATI card that would be great, but if push comes to shove, I am looking into buying an Nvidia based card with an HDMI output. At least this way I know I can use the NV proprietary driver which comes with the X Server app.
 
Update: I purchased a cheap Nvidia based card (this box is just a simple media server) with HDMI output. As I hoped, it worked like a charm. I connected the HDMI cable, booted the machine and linux immediately detected the TV. I then downloaded the prop. driver and was even able to set HDTV settings such as 720P or 1080p resolutions. So all is well and I am extremely satisfied with my system now.

---

### Post by zeusrock1 on 2010-03-03
Glad to hear it's working, I've been considering buying a cheap nvidia card for mine also.  I think I'll give it a try.

---

