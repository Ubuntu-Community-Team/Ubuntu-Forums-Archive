---
title: "Some feedback about Lenovo T550 ?"
date: 2015-04-27
forum: Hardware
---

### Post by harobed on 2015-04-27
Hi, I want to buy Lenovo T550 laptop, are there some Ubuntu user with this laptop here ? Are there some issue with this laptop ? Is HiDPI screen easy to use ? Are there some issues with HiDPI (HiDPI + external monitor lowdpi&#8230;) ?

Some spec :

* Intel® Core&#8482; i5-5300U (jusqu'à 2,9 GHz, cache L3 3 Mo)
* IPS 15,5" 3K (2 880 x 1 620)
* SSD 512 Go (SATA3)
* WiFi 802.11b/g/n (2x2) + BT 4.0 ThinkPad

Thanks for your feedback.
Best regards,
Stéphane

---

### Post by oldfred on 2015-04-27
Issues are common across similar models as vendors often have one general UEFI and then slight changes for various options.

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

Since very new, I would only suggest 15.04 (kernel 3.19) as it takes time for kernel, support & video driver updates to be included in any distribution. Intel has been petty good about releasing updates for new processors & video.


 HP 1000-1220LA worked with   i915.i915_enable_rc6=1
Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

      
 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

---

### Post by gbvz on 2015-05-27
Hi :)
My experience on the t550 was quite good.
USB install worked well even with pre boot encryption.
I dont know how good HiDPI support in Unity is, but in Gnome3 its not good, its okay :/
Also 3rd party software is ugly most of the time. Everything is too small, in Thunderbird for example you can make fonts bigger, but then still icons and buttons are awfully small. Anyway my workarround is:
Learn to read small things, and hit small buttons. You'll love it, and you'll have more space ;)

About the external monitor issues, yes there are some. I increased UI size in Gnome3 to fit my needs on the internal display, so now if I plug an lowDPI monitor menues and fonts are too big on it. I hope thats going to be fixed in future gnome releases.

Some links on setting up an HiDPI display:
[https://wiki.archlinux.org/index.php/HiDPI](https://wiki.archlinux.org/index.php/HiDPI)
[http://www.pcworld.com/article/2911509/how-to-make-linuxs-desktop-look-good-on-high-resolution-displays.html](http://www.pcworld.com/article/2911509/how-to-make-linuxs-desktop-look-good-on-high-resolution-displays.html)

What Worked out of the Box:
Trackpad (incl. Trackpoint, the 3 Mouse buttons and two-finger two-way scrolling)
Keyboard (some special buttons needed to be set up manually)
WiFi + BT (I had some power management issues, solved them by turning power management off for wlan0)
Webcam
Microphone

What does not work:
Nothing important, maybe some Windows only anti-theft feature.

What i did not test:
Finger Print Reader (disabled)
LTE modem (don't have one)
Headset Jack (needs a splitter, its a combo port)
UEFI (I'm useing legacy boot option)

Personal thoughts:
I'd love a 4k display, because then I could scale it down to 2k easily. You can only scale by whole integers. Floating point multiplipers will cause a blurred image.  I'd buy that notebook again, praying for better HiDPI support in near future.
I am not an experienced linux user, so there might be things not working i'm not aware of, also if i can provide more info feel free to contact me.

EDIT: Its a 15.04 64-Bit Ubuntu Gnome distro

---

### Post by harobed on 2015-05-28
Thanks for your feedback.

---

