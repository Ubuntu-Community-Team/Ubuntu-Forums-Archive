---
title: "need help for video driver and audio driver"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by jjjhackkk on 2009-09-14
newbie here..

i'm planning to install the ubuntu 9.04 on my PC, where can i find the video driver nvidia 8400gs and my EPoX 8NPA SLI motherboard for audio driver.

thanks..

regards to all of you 

:popcorn:

---

### Post by earthpigg on 2009-09-14
drivers do not work the same in Linux as in Windows.

boot from a LiveCD using the 'test without making changes' option you will be presented with.

if you hear the cool rhythmic drums login sound, then your audio has been automatically detected, drivers automatically loaded, and audio is peachy keen (make sure your speakers are turned on and whatnot, obviously :D ).

if you see anything on your screen, then your video has been automatically detected, not-very-great drivers have been automatically loaded, and video is kinda-crappy-but-functional.

well, lets see if we can use great drivers and make it peachy keen.

go to system -> administration -> hardware drivers. pick the latest video driver (highest number, 180 or something) and enable it.

then, go to system -> preferences -> appearance and try to set 'desktop effects' to max. if it works, your video card is peachy keen.

if it doesn't try a lower number (177 or something) and retest until you find peachy keen-ness.

if your computer has wireless, go ahead and test that now, too. if it works, then it has been automatically detected, drivers automatically loaded, and its peachy keen.

if everything is peachy keen, then go ahead and install ubuntu confident in the knowledge that everything is peachy keen.

if anything is not peachy keen, let us know and we will help you out.



going to random websites and downloading random drivers is an absolute absolute absolute last resort in the Ubuntu world. in fact, i have never had to do that a single time across three computers since the migration from Windows.

---

### Post by Tamvolan on 2009-09-14
Earth,

I'm also a real newbie to Ubuntu, and Linux in general.  I've got 9.04 installed, sound is great, visuals are ok.  I have an ATI Radeon 9600 video card installed.  When I open up System -> Administration -> Hardware Drivers, it tells me that there are no proprietary drivers installed on the system.  I do have the ability for 1280x1024, so the video isn't bad, but I don't know if it's using the video card's capabilities, as far as hardware acceleration, etc.

Questions:

1) How can I tell if the card is being used?
2) How do I, if I need to, install a driver for the card?

Thanks for any help/tips/advice you, or anyone else, can offer.

---

### Post by Mark Phelps on 2009-09-15
Tamvolan:

Ubuntu already installed the open source driver for your card when you did the install.  There are no ATI-provided drivers that work with your card and any Ubuntu newer than 8.10.  ATI has dropped support for your card and lots of others in their newer drivers.

---

### Post by Tamvolan on 2009-09-16
Thanks for the response Mark.  It's what I was afraid of, but figured I'd ask.

---

### Post by earthpigg on 2009-09-16
> **Tamvolan said:**
> Thanks for the response Mark.  It's what I was afraid of, but figured I'd ask.

hi,

dont give up yet.

see if you can find your card here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

