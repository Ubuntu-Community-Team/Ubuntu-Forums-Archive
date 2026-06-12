---
title: "Is my hardware fully supported?"
date: 2016-02-22
forum: Hardware
---

### Post by infinexe-twistedfury on 2016-02-22
I have an i5-6500, 8 GB DDR4 and a GTX 960, is this hardware supported in Ubuntu? Will I come into some incredible issues if I attempt to install?

---

### Post by weatherman2 on 2016-02-22
Boot the latest Ubuntu "live" to see how it works. No risk in doing that.  Then you can try installing.

If you are worried about losing Windows, make a full backup of your hard drive first before installing Ubuntu.  Then you can always go back to the way your computer is now.  Not much to lose except some time.

---

### Post by TheFu on 2016-02-22
> **infinexe-twistedfury said:**
> I have an i5-6500, 8 GB DDR4 and a GTX 960, is this hardware supported in Ubuntu? Will I come into some incredible issues if I attempt to install?

Impossible to say.  Trying it is easier than doing all the research.  But if you want to do the research, you can begin by making a list of 
* all the major chips in the system - North-bridge, south-bridge, audio, video, networking, USB controller(s), SATA controller(s), IDE controller(s), then try to find the firmware versions for each of those. Be certain to get the BIOS firmware release too.  Next, start web searching on each of those for the specific version of Ubuntu and close relatives looking for issues/problems/complaints, etc.  For me, I'd guess this research would take 2+ days, assuming any data could be found at all.  For example, many motherboards have realtek networking (8111-chips), but different revisions of that chip either work great or not at all, so be certain to look at that too.

Oh - I forgot wifi.

Or download the ISO, put it on a flash drive (mkusb) and boot into a liveBoot version then see how all the hardware works.  This is a good estimate of whether that hardware will work once a distro is installed, but it isn't any guarantee. As an example, I installed Ubuntu Server onto a chromebook last fall. During the install, it recognized both the wifi and a USB-ethernet adapter, but at the first boot post-install, neither were working.  The team who created the HW compatibility stuff for the installer isn't the same as the people that decided that for Ubuntu Server. It isn't like lots of people install Ubuntu Server on a chromebook ... I'm odd that way (and many other ways).

Nothing is perfect and just because specific hardware works today, with the specific kernel, that doesn't mean it won't break with the next kernel update or next release. HW vendors just don't do testing for Ubuntu/Linux compatibility like they do with that other OS.

In short, pick the hardware carefully, go with specific versions known to be nice towards Linux and avoid companies who don't acknowledge Linux.  For example, be careful with Logitech webcams. They worked with Linux, then they didn't.  Some printers are like that too - some models of printers have issues while others "just work."  I used to buy HW to save $20, then realized that 2 weeks of effort trying to get HW working with Linux was too much of a hassle - buy hardware from companies that go to the extra effort to support Linux - that's good for you and for them.  

Also, be careful buying the newest version of anything. There is usually a 6-12 month lag for support of popular HW with Linux. Sometimes there aren't any issues, but if there is a new model, watch out.

If you are a kernel driver developer, please get the latest hardware and fix any issues you see. That helps everyone else. ;)

---

### Post by oldfred on 2016-02-22
Intel works.
 Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)


 Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
[http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work](http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work)

You will have issues with nVidia, but everyone with nVidia need to install nVidia driver from repository or ppa for newer nVidia cards to have decent video support. If you only want open source driver, you may only be able to run with Intel video or much older nVidia card.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

