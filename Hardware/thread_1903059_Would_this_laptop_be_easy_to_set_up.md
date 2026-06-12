---
title: "Would this laptop be easy to set up?"
date: 2012-01-01
forum: Hardware
---

### Post by abtekk on 2012-01-01
I got a Toshiba Satellite L750D-14R for christmas and I want to install Linux to it to use it as a dev center.

Here are my specs:

Dual Core AMD E-450 processor @ 1.65GHz
AMD Radeon HD 6320 with 3GB memory
640GB HDD
6GB RAM

[http://www.currys.co.uk/gbuk/toshiba-satellite-l750d-14r-15-6-laptop-red-11306306-pdt.html](http://www.currys.co.uk/gbuk/toshiba-satellite-l750d-14r-15-6-laptop-red-11306306-pdt.html)

I've never set up Linux on a system with an ATI or Nvidia graphics card, that's why I ask.

---

### Post by Mark Phelps on 2012-01-02
Unless someone with EXACTLY the same make and model laptop replies (and no one has so far!), the only way you'll find out is to try it yourself by downloading and burning the ISO to a CD, booting from that, and selecting Try Ubuntu.

That will show how well Ubuntu detects your laptop hardware and installs the proper drivers.

---

### Post by moteprime on 2012-01-03
Yes try booting it up a see for yourself.

The graphics has been performing badly, but after the latest update from amd it seems to get better.
[http://ubuntuforums.org/showthread.php?t=1857911&page=9](http://ubuntuforums.org/showthread.php?t=1857911&page=9)

---

### Post by kjm2664 on 2012-01-03
probably to late for you - but I just bought this model, and everything works fine. the proprietary graphics drivers installed through jockey caused awful tearing artifacts, but things work just fine with the opensource ones installed by default.

---

### Post by moteprime on 2012-01-03
@kjm2664
the newer 11.12 drivers seems to work better. especially if you disable "sync to vblank" in ccsm.
I'm on ubuntu 11.10

---

### Post by kjm2664 on 2012-01-03
thanks moteprime - I may give it a try. Thanks!

---

### Post by kjm2664 on 2012-01-05
> **moteprime said:**
> @kjm2664
the newer 11.12 drivers seems to work better. especially if you disable "sync to vblank" in ccsm.
I'm on ubuntu 11.10

Have you had any luck with the drivers moteprime? I've tried through most of today to get 'em installed, and playing with different settings. But, I haven't had any luck. Still get tearing and artifacts. I have tried disabling the sync to vblank option, that doesn't seem to do anything about the graphics glitches.

It's not a show stopper for me, but I would like to get proper 3D drivers running for this machine.

I should mention that I installed the amd64 version.

---

### Post by moteprime on 2012-01-07
kjm2664
Sorry for the late reply.
I'm on the 64 bit (Ubuntu) version to. Iv'e been through all the versions of the proprietary driver since I got this laptop and version 11.12 are the first one that performs reasonably well and in my opinion better than the open source Radeon driver.
My laptop are a Lenovo s205 but with the same APU, so I guess it should work the same as yours.
I have had the most luck installing the catalyst by just following the readme file that are linked to at the AMD driver download page.
Be sure to uninstall older versions of the driver or other drivers or it will not work properly.

---

### Post by zbanghy0ne on 2012-01-07
Stick with Windows. Linux  gfx performance sucks

---

### Post by kjm2664 on 2012-01-07
zbanghy0ne - there are other reasons other than graphics performance to select an OS. I've been using linux for 9+ years, and will continue doing so. But, thanks for the constructive advice.

moteprime - I've had no luck with either the propietary drivers installed through jockey, or installing the 11.12 version I got from ATI. I ensured all versions of fglrx we removed before trying anything, and still get these well known tearing problems. Ah well, I will try again at some point when I get the chance. As I have said, not a show stopper, but would be nice to get the correct power outta this video card.

---

### Post by moteprime on 2012-01-09
kjm2664
I'm afraid I'm not a wiz at theese things, it's just the first driver for this APU that performs good enough to actually give a decent desktop.
It's not unlikely that my setup doesn't perform better that yours, but that I am just so happy to finally have a driver that works at all. The performance can be described as being slightly better than the default open source driver.  
For reference check out the last two or three pages of this thread:
[http://ubuntuforums.org/showthread.php?t=1857911&page=8](http://ubuntuforums.org/showthread.php?t=1857911&page=8)

---

### Post by kjm2664 on 2012-01-09
Thanks moteprime - I will give that thread a good read when I get back on my machine at home.

---

### Post by moteprime on 2012-01-09
kjm2664
-and if you can figure out why i can't get of that 60 fps and have the +2-300 while testing the gears thing, please tell me..  ;-)

---

### Post by kjm2664 on 2012-01-10
moteprime - just to follow up. I have not tried reinstalling the drivers yet. As, I was googling around for solutions and seeing what success people have had with this hardware and I ran across this thread:

[http://forums.linuxmint.com/viewtopic.php?f=60&t=91159&p=524169&hilit=ati#p524169](http://forums.linuxmint.com/viewtopic.php?f=60&t=91159&p=524169&hilit=ati#p524169)

Which states (if you don't want to click on the link) that ATI will be releasing an update 12.1 driver that should fix these issues with Gnome 3. So, I'm just going to wait for that to be out in the wild and give it another try.

---

### Post by moteprime on 2012-01-10
kjm2664
Thanks for your follow up.
Yes, it looks like it will be worth waiting for, the performance can be improved alot.

---

### Post by davidshelton on 2012-02-28
I have a Toshiba L750D with AMD A6-3400M with ATI Radeon HD graphics and Blu ray dd. Tried live session off USB with 10.04LTS and 11.10 both amd64 versions. In LTS it booted up fine(once I used Unebootin) but wireless and LAN didn't work while 11.10 booted with a blank screen(that's the Radeon driver issue fixed via modeset, right?). My question would be will Ubuntu work well on my machine and which version would best? Can I fix the live USB OS so 11.10 boots to test other areas for compatibility? Anyone done this with this exact machine?

---

### Post by moteprime on 2012-02-29
Try 12.04 out from at live usb, and see if any of the issues has been fixed.
Beta 1 is going to be available from tomorrow 1. march.

---

### Post by davidshelton on 2012-02-29
@moteprime thanks for the suggestion. I'll wait to try that release. As far as creating a live USB I have found them not to work at all when I use the Universal USB installer(vers. 1.8.8.4) but they do work to a point with the latest version of Unetbootin. With the Universal USB installer I get a message about a missing kernel and in another instance about a problem with "vesa menu"(Sorry didn't have a chance to write that down). Which live USB creator would you recommend? Thanks again.

---

### Post by moteprime on 2012-03-01
@davidshelton
I know your problems from when I play around with other distros, but the one program that always work for me with Ubuntu are Ubuntus own "Startup disk creator". It's installed per default.
If you are doing it from windows I haven't tried that in years, i can't help you i'm afraid.

---

