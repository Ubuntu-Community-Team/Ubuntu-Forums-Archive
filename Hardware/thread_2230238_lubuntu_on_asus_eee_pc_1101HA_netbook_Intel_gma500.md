---
title: "lubuntu on asus eee pc 1101HA netbook Intel gma500"
date: 2014-06-18
forum: Hardware
---

### Post by giel2 on 2014-06-18
Hi!

I recently installed lubuntu 14.04 on my asus eee pc 1101HA netbook.... Works great if you consider the specs! One issue though...:

flash and video keep freezing the netbook. After googling a while I get the feeling that my video-graphics card (Intel gma500) might be a problem. Everything I found however was about fixes for ancient lubuntu versions....

Is a better driver available than the one that is installed out of the box after a fresh install of lubuntu 14.04???

Or should I use another linux-distribution or an older version of lubuntu?

Hope someone can help!

---

### Post by sudodus on 2014-06-19
You may have too weak CPU and graphics for flash and video. Maybe it works better with lower resolution. The standard graphics drivers are the best for Intel graphics.

You might try a tweak that helps some intel graphics chips, UXA acceleration

> John Hupp <lubuntu@prpcompany.com> wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format, should be a tab before each line except the first and the last).

```
Section "Device"
            Identifier "Intel Graphics"
            Driver "intel"
            Option "AccelMethod" "uxa"
EndSection
```

Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.

-o-

Nio Wiklund wrote:

This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.

Otherwise you might have better luck with a community re-spin of Ubuntu 12.04 LTS, ***Bento, Bodhi or LXLE***
or kansasnoob's tweaked Ubuntu [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by giel2 on 2014-06-20
I added the xorg-file with the text, and a reboot created a kernel panic. Second reboot went well though! 

After that I was able to watch a whole Paradise Lost concert (1h38) without a crash/freeze with gnome-mplayer!! A record!!!

If the netbook remains stable this fix is the way to go for other 1101ha-users!

Thanks for your effort!

---

### Post by sudodus on 2014-06-20
I'm glad it works better now :-)

Please come back after some more tests and

- if problems, ask for more help
- if solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by Melodie on 2014-06-28
Hi,

I have been handed the same Asus eeepc 1101 and booted Bento with a USB stick, but the screen was cut in half, the upper part visible and the bottom part black. The above xorg.conf made it right though, once done I just had to go to a tty and restart lightdm (sudo service lightdm restart). As you are saying it might not be perfect I wanted to know more about the uxa acceleration method, so a search brought me to the Archlinux wiki and to the Freedesktop.org specification page related to another Xorg driver, which is "glamor". Here are the info:
[https://wiki.archlinux.org/index.php/Intel_Graphics](https://wiki.archlinux.org/index.php/Intel_Graphics)

[http://www.freedesktop.org/wiki/Software/Glamor/](http://www.freedesktop.org/wiki/Software/Glamor/)

This glamor driver looks quite interesting (I think their say about DDX, must mean something such as "dynamic data exchange"), so I am next going to try glamor, in a second attempt.

I might also produce a new ISO specifically for these machines (I have found lots of information related to improvements which can be done). Bento is a 12.04.4, and I also tried to boot to Lubuntu 14.04 and to Xubuntu 14.04. In this case the display was fine immediately, but there is an issue with network manager, which is able to start the connection with wifi, but not with Ethernet, which is a bit bizarre. (In my other machines, a home made Bento for Trusty also has issues with network not being "hotplug", so I am not yet ready to distribute a 14.04 edition of Bento, mainly for this reason).

Another thing is that even though the above xorg.conf setup works, the use of the system is quite slow. The machine has 1 GB ram, the processor is powerful enough, not much of the RAM is used, but something slows down the display of the launched programs. I don't know if the issue comes from the usb stick or if the problem comes from the graphics, or from something else. This is why more tests are needed.

giel2: if you visit here again, could you tell us if once installed, Lubuntu is snappy on your machine?

---

### Post by Melodie on 2014-06-28
Hi,

In Bento it works with "glamor", but not good with a current kernel, it works best with the latests 3.13 kernel and headers.

---

### Post by sudodus on 2014-06-30
Thanks for sharing your results, Mélodie :-)

---

### Post by Melodie on 2014-07-05
> **sudodus said:**
> Thanks for sharing your results, Mélodie :-)

You are welcome. There is also a Bento Remix configured especially for the eeepc1101HA notebooks, available here: [http://bento-remix.phillw.net/bento-eeepc1101HA](http://bento-remix.phillw.net/bento-eeepc1101HA) (fully up to date as of July 4th). Of course this is not an official edition, and it is provided as is, tested and with all the care possible, and without any guarantee. :)

---

