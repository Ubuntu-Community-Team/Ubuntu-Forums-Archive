---
title: "Many problems with Ubuntu 9.10!"
date: 2009-11-08
forum: Hardware
---

### Post by Conner526 on 2009-11-08
Hello, total Ubuntu noob here looking for help. I have a Averatec 3700 series laptop that I am having problems with.

First of all, the video card has no drivers so everytime I startup the login screen is all the way off to the side. Someone said openchrome supports this. But I have no idea what to do.

Also, the trackpad doesn't work, but that's not as important as I always use a mouse.

---

### Post by pharnet on 2009-11-10
I have been working on this on my sister's Averatec 3700 (Averatec AV3715-ED1). Her problem is that the gdm login screen and usplash are defaulting to a 1900 x ???? virtual resolution at the start but after I login the screen switches to the correct 1024 x 768 resolution.

There is a setting for the default usplash resolution in /etc/usplash.conf. The instructions here ([http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html")) are helpful but out of date since the new Karmic/grub2 does things differently and putting vga=791 on the kernel line is deprecated. So I have usplash working at the correct resolution but gdm is still defaulting to the wrong virtual resolution. 

I am still working on it when I have access to the machine (once a week when visiting).

I don't remember the trackpad being an issue but you may want to double check that it is enabled in the mouse settings (System->Preferences->Mouse).

Another problem this Averatec 3700 is having is related to the wireless device not reconnecting after resume from suspend. Which is the higher priority problem. It has always been a cranky beast.

I will update as I work on **defining the problems better** or if I find some solutions.

btw, they really like the performance Ubuntu is giving them compared to the old freedom lacking os.

---

### Post by ssdt on 2009-11-10
All these types of problems come up and for noobs it will be better if you use 8.04 which is a LTS version so there would not be much problems.

---

### Post by pharnet on 2009-11-10
There is some wisdom in sticking to the most recent LTS but you miss out on the double edged sword(the good as well as the bad) that the newest stuff brings. 

Another strategy would be to wait for a month or so after a new release for problems to shake out a bit more.

Sadly some hardware is better supported than others as well. I am not sure how well represented the Averatec 3700 (Averatec AV3715-ED1) is out there. It will likely take longer to figure out the nuances required to make it work better after each new release.

I don't think you need to track down a different video driver.

---

### Post by pharnet on 2009-11-10
I used the xorg.conf from here:

[http://launchpadlibrarian.net/30406077/xorg.conf]("http://launchpadlibrarian.net/30406077/xorg.conf")

discussed here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/186103]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/186103"), post #22

The gdm resolution is correct now.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
There is a line in the xorg.conf file titled "virtual". Change that to the proper resolution and you should be set (mine defaulted to 2048x1536!)

---

### Post by pharnet on 2009-11-11
There was no xorg.conf and no virtual setting since these days x is automagic. It was guessing/detecting the wrong resolution (I assume) but creating a correct xorg.conf file at 1024x768 forced the correct resolution. No virtual setting was needed or desired but thanks for the suggestion.

For the wireless/suspend problem I am trying the suggestion here:

[http://www.seephar.com/2009/04/tweaking-the-rt2500pci-for-jaunty/]("http://www.seephar.com/2009/04/tweaking-the-rt2500pci-for-jaunty/")

Typed:

sudo gedit /etc/pm/config.d/rt2500pci

to place a file called rt2500pci in the /etc/pm/config.d/ directory containing:

SUSPEND_MODULES="rt2500pci"

I will see over the next week if they report success.

---

