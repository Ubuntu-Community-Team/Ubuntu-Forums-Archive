---
title: "fglrx + AGP varient of Radeon HD 2600 = ??"
date: 2009-07-24
forum: Hardware
---

### Post by rocky5051 on 2009-07-24
I remember at some point, much earlier this year, I posted an issue regarding my Radeon HD 2600 XT AGP 8x graphics card, and it freezing and having all sorts of weird issues. The consensus of this thread was that the AMD/ATi drivers were to blame, and I should wait and hope for improvements.

I'm just curious to see if anyone have noticed any improvement (like, the drivers actually letting the card I have work) recently with these AGP cards like mine, as it is STILL the only thing keeping me from using a Linux distro, be it Ubuntu or otherwise, as my primary OS (and I miss very much).

---

### Post by LepeKaname on 2009-07-24
Have you tried the radeon OSS driver? Did you notice any change in performance (fglxgears for example) from Intrepid to Jaunty?

---

### Post by rocky5051 on 2009-07-24
> **LepeKaname said:**
> Have you tried the radeon OSS driver? Did you notice any change in performance (fglxgears for example) from Intrepid to Jaunty?

First off, what do you mean by the Radeon OSS driver, and second I wasn't even able to get Intrepid (8.10 right?) to work on my system because X wouldn't even load with my card, not even in a Live CD situation. So, I my comparisons are from Hardy to Jaunty, wherein Jaunty worked with the VESA driver but when I tried using anything hardware accelerated using the AMD drivers it would work for a moment or two and soon after freeze my desktop and system entirely.

This same phenomenon occurred with Hardy. It's a specific issue with AGP Radeon HD cards.

But I'm guessing the driver you're talking about is an open source version? Is that stock with Ubuntu? I really don't know. :confused:

---

### Post by LepeKaname on 2009-07-25
The driver I was talking about is:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

However I don't see your model listed there. I don't own a Radion HD 2600 but a Radion Xpress 200, so that driver worked for me.

However, there are other drivers, like:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

which may work for your model, but I'm not sure. I recommend you to follow these threads as are about your video card:

[http://ubuntuforums.org/showthread.php?t=570391](http://ubuntuforums.org/showthread.php?t=570391)
[http://ubuntuforums.org/showthread.php?p=6152916](http://ubuntuforums.org/showthread.php?p=6152916)

ATI support for Linux is kind of limited :(

If nothing work, you can try to install Intrepid (not from Live CD). And then install proprietary drivers, as ATI removed some cards support in Jaunty. However, it seems that some people has been able to run Jaunty with your video card (with 3D acceleration) from the live DVD with Open Source drivers, but I didn't find anymore explanation.

Sorry I can't help too much.

---

### Post by lestatto on 2009-07-25
Hmm, fglrx works for me, even in most critical situations (apart from gfx glitches on wine), and I have the newest driver for Radeon 2600 from Ati's website. I had problems with it before (when installing directly from script), but doing --buildpkg Ubuntu/jaunty did the trick. After installing - regular 'aticonfig --initial' and its gtg. Methinks, maybe its problem with your hw, not drivers :?:

---

### Post by rocky5051 on 2009-07-25
No...my hardware works just fine on Windows, with the exception of the fact I have to use Omega drivers to get Half Life 2 to work due to lacking AGP support.

This an issue specific to R6xx cards using an AGP modded chipset, and as far as I know the Linux drivers failed to offer good support for these types of cards. I've tried the fglrx driver with other ATI cards and it worked, but if you Google my card you'll see oodles of threads saying my same issues.

But I'll keep in mind the OSS driver I guess, as I ordered a Kubuntu CD not too long ago and wish to try again with it.

But again, the point of my thread wasn't to ask for a solution really, just to hear about any success stories (if any) if they exist yet.

EDIT: The Radeon OSS driver comes with Ubuntu and that must mean it doesn't work with my card period. Though, the proprietary driver seems to have moved along a good number of releases since I checked it last. Might have to try that again sometime.

---

### Post by Ansraliant on 2009-07-30
Hi, i have a AGP Radeon HD 2600 Pro. I'm using fglrx drivers, i've tried to use other drivers, but in my opinion, the best is fglrx. I know it has a lot of bugs (slows boot up, can't switch user, and more), but I can watch movies like in windows. I do not have compiz enabled.
It is working pretty good. I can play high definition movies in ubuntu!. with other drivers, I couldn't even play youtube videos!.
glxgears shows me 4125FPS, I think that's pretty good.
Strange thing you had to use Omega drivers in windows. I have windows too and I only downloaded agp-fix from ati's website and everything worked fine.
Good luck with your ATI!

---

