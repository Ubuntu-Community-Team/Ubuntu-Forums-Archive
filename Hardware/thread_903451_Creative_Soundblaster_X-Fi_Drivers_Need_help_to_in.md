---
title: "Creative Soundblaster X-Fi Drivers Need help to install?"
date: 2008-08-28
forum: Hardware
---

### Post by Finger78 on 2008-08-28
This is a re-post form the Multimedia section as I'm not sure if it belongs in one or another.

I've been doing some research and all popular opinion seems to dictate that X-Fi drivers are not available. Well I have downloaded some OFFICIAL BETA drivers directly from Creative

[XFiDrv_Linux_US-1.18.tar.gz]("http://support.creative.com/downloads/download.aspx?nDownloadId=10530")

Release date: 16 Apr 08
According to the manufacturer’s release note:

This download is a beta driver providing Linux® 32-bit / 64-bit OS support for Creative Sound Blaster® X-Fi™ series audio devices. For more details, read the rest of this web release note.

Take note of the following:

* THIS IS AN UNSUPPORTED BETA DRIVER. There is no technical support for this driver.
* This beta driver has only been tested on the following 32-bit / 64-bit Linux distributions: Ubuntu® 7.10, openSUSE® 10.3 and Red Hat® Enterprise Linux® 5.1 (64-bit only).
* We recommend that only experienced users install this driver. Do not install this driver on a system used to perform critical tasks.
* Your feedback is a valuable part of our development process. To submit feedback on this driver, visit the Sound Blaster X-Fi Linux Beta Driver Feedback Program.

This download is intended for the following audio devices only:

* Creative Sound Blaster X-Fi Elite Pro
* Creative Sound Blaster X-Fi Platinum
* Creative Sound Blaster X-Fi Fatal1ty®
* Creative Sound Blaster X-Fi XtremeGamer
* Creative Sound Blaster X-Fi XtremeMusic

Current release features:

* ALSA PCM Playback
* ALSA Record
* ALSA Mixer

Added Features or Enhancements:

* Supports GCC version 4
* Supports Linux 64-bit and 32-bit OS

Known issues:

* S/PDIF passthrough is not supported in this driver release.
* External I/O modules are not supported in this driver release.
* Applications from the original Sound Blaster X-Fi Installation CD will not work with this driver.

Requirements:

* Linux x86 / x86_64 OS
* Creative Sound Blaster X-Fi audio devices listed above

Notes:

* To install the driver, do the following:
1. Download the XFiDrv_Linux_US-1.18.tar.gz package onto your local hard disk.
2. Double-click the downloaded package to unpack its contents.
3. Read the README file and follow the instructions.



Now, from other information I have read, these drivers take an experienced hand to install and I am asking if anyone could take the time to write a step-by-step tutorial for even the absolute beginner to understand and install these drivers.

I come from a very long history in PC gaming, Game/Website/Application alpha/beta testing and multimedia editing. And in all of these having a quality sound card is crucial to doing your job and, I hope that someone with this knowledge and experience can step up and show the masses how to take advantage of these quality cards (despite the company that makes them, I don't agree with many of their views on "alternate OS's" or 3rd party driver assistance) and I think this could show a fairly nice influx of newer users once they realize they can use their gaming rigs and make the switch to a morally better OS.

Please pardon if what I'm asking already exists, I've done quiet a bit of Google searches and forum searches and none of my results have yielded any information.

The masses beg for this, I hope someone can show us the light!

---

### Post by Benjamin_Vedder on 2008-08-28
Try this:

[http://ubuntuforums.org/showthread.php?t=870001]("http://ubuntuforums.org/showthread.php?t=870001")

I have the same sound card too, and I managed to get it working with the oss and the alsa driver. As explained in the howto i posted, its MUCH easier with the oss driver, but the alsa driver works better once you get it working (at least in my opinion). 

The driver from creatives site is not easy to install (impossible?) for beginners. You have to unpack it, edit the make-files, recompile your linux-kernel and more... I am quite experienced with ubuntu, and it took me days to get that driver working, but I DID get it working at last.

Anyway, try the oss4 driver, I think you will be able to install it quite easy.

Good luck.

---

### Post by Nepherte on 2008-08-28
Although I prefer ALSA as well, I can confirm you'll find it a lot easier to use your card in combination with OSSv4 (it's pretty much copy/paste the commands from the supplied tutorial in the post above).

---

### Post by Finger78 on 2008-08-28
I have been following the tutorial listed with the c&p commands (using the 6a method) but I have become a little confused by step 7
"7. Add a new custom application launcher to the panel that runs the command: ossxmix - That's ossxmix, not ossmix, Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon."

Being a new user I'm unsure on how to complete this step. Also, do I still use the second command in step 6? ```
sudo soundon
```

---

### Post by Finger78 on 2008-08-28
Well I'd still like my previous question answered but it does appear that I now have sound (was tryin to get flash installed and was testing it and it had sound!)

---

### Post by Nepherte on 2008-08-29
You kinda made it yourself hard by choosing 6a, but hey you got sound. That's the most import thing. I'm not really sure what your problem is with the launcher. Just right click on the gnome panel where you'd like your launcher (ossxmix is a volume manager) and continue with filling the required fields (name is for example Mixer, the command is ossxmix and you can also set an icon). They do this step because the default gnome volume manager can't handle OSSv4 so they add the volume manager that comes with it.

The first addendum patches the issue with gnome volume manager so that it does handle OSSv4, making the custom launcher a bit unnecessary. It is up to you what you like. ossxmix gives you more things to control but with gnome volume manager you can use the preset keys for volume up & down. I recommend you patch it and see which one you like.

---

