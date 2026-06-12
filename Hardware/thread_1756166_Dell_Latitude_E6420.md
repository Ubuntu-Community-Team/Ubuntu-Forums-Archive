---
title: "Dell Latitude E6420"
date: 2011-05-11
forum: Hardware
---

### Post by GreginSJ on 2011-05-11
Good news for Dell Latitude E6420 owners:  My one week old laptop is running Ubuntu 10.10 Maverick perfectly.  I tried unsuccessfully to run 10.04 LTS on it first.  Could not connect to the internet in that version, but ver 10.10 has all of the drivers from Dell.  They are available at [http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=04&l=en&s=bsd&ServiceTag=&SystemID=LAT_E6420&os=W764&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=04&l=en&s=bsd&ServiceTag=&SystemID=LAT_E6420&os=W764&osl=en&catid=&impid=) .  I think it is important to download the 32bit drivers and not the 64bit, but you can experiment.  Make sure that you have a hard wire connection to the internet during and after installation, because 10.10 will allow you to connect that way, but not wirelessly until you download the drivers.  Of course you can use a thumb drive to move the drivers as an alternative.

Load the drivers in the following order:
1.  Chipset
2.  Touchpad
3.  Audio
4.  Video

My Laptop is configured as follows: 
Intel Core i7-2720QM
8gb DDR3-1333MHz SDRAM
256gb SSD hard drive (partitioned:  8gb SWAP, 20gb /home, 14gb / )
nVidia NVS 4200M 512mb DDR3 Discrete Graphics
Intel Centrino Adv-N + WiMAX 6520 802.11a/b/g/n
Dell Wireless 5630 Multi-mode EVDO-HSPA Mini-Card
E-Modular Bay, USB 3.0  (I have not tested this yet)
Dell Web Cam

---

### Post by Tuxor on 2011-05-13
Congratulations! That seems to be one mean machine. I'm interested in the same model myself, but since I live in Sweden (which btw is owned by MS) Dell doesn't sell them with the same options as in the rest of the world. For example you can't buy it with preinstalled Ubuntu or 3G modem. I would be grateful if you could answer a copule of questions.

- How long battery life do you have aproximately?
- Can you turn off the Nvidia card to save power?
- Is the noise and heat levels ok?
- Do you have the multitouch screen, if so can you use your fingers to point and click anywhere, and use some kind of on screen keyboard? Or is it just useable in certain contexts or programs?
- Do you run the 32 or 64 bit version of Ubuntu 10.10?

Thank you

---

### Post by Blaze33 on 2011-06-06
I also bought an E6420 and received it on may 23. I still only use it with a live usb because i'm waiting for a refund (told them i don't need windows and they were okay with the refund, :) i'm living in France).

Personally i don't get the point running it on a 32bit OS nor using an old ubuntu release. However you won't get an out of the box okay experience until the release of 11.10.

I'm currently testing it with ubuntu 11.04. You need to boot it with nomodeset option at first (or you'll get a corrupted screen), then upgrade to the latest video drivers and kernel using the xorg-edgers repository : [http://phoronix.com/forums/showthread.php?29110-Intel-s-Linux-Sandy-Bridge-Graphics-Still-Troubling&p=168137#post168137](http://phoronix.com/forums/showthread.php?29110-Intel-s-Linux-Sandy-Bridge-Graphics-Still-Troubling&p=168137#post168137) (be aware you won't get a LTS-grade stability)

I'm still having some troubles with a dual-head setup, otherwise it works well. I don't have the integrated nvidia gpu. I'm expecting 5 to 6 hours autonomy (light usage with the 60Wh battery) (but still not tested it). The linux kernel however has some power regressions but there are ppl working on it : [http://www.phoronix.com/scan.php?page=news_item&px=OTUxMw](http://www.phoronix.com/scan.php?page=news_item&px=OTUxMw)

The laptop don't get too hot and remains really quiet. I do not have the multi touch screen but the 1600x900 panel instead. The only drawback is that the screen contrast ratio is really low.
I'm planning to install ubuntu on the hdd tuesday or wednesday once i get the refund.

There's a good review here : [http://www.notebookcheck.net/Review-Dell-Latitude-E6420-Notebook.51152.0.html](http://www.notebookcheck.net/Review-Dell-Latitude-E6420-Notebook.51152.0.html) which i found useful to make my purchase choice.

---

### Post by vdoki on 2011-06-16
Hi!

Does this mean, that you use an E6420 with fresh ubuntu 64bit?

Are there any new experiences? I plan to order this machine very soon.

> **Blaze33 said:**
> I also bought an E6420 and received it on may 23. I still only use it with a live usb because i'm waiting for a refund (told them i don't need windows and they were okay with the refund, :) i'm living in France).

Personally i don't get the point running it on a 32bit OS nor using an old ubuntu release. 

...

---

### Post by fmeynadier on 2011-06-22
Hi,

I'm running Ubuntu 64 bits on E6420 (core i7, E6420, sandy bridge graphics only). Things went relatively well until I tried to set up my external monitor. Details on [https://bugs.launchpad.net/bugs/794474](https://bugs.launchpad.net/bugs/794474) ...
Main symptoms : heavy flicker on the laptop's screen when waking up from suspend-to-ram, persistent (i.e. when rebooting, BIOS and win7 where affected. Seeing this, Dell has changed the screen and the flicker seems to have disappeared... But I still have issues trying to set the correct resolutions for both screens (and I become wary in trying setups, fearing that it breaks something again... On the other hand, maybe was it totally unrelated). 

@ Blaze33 : did you manage to make things work in the end ?

---

### Post by Blaze33 on 2011-06-29
@fmeynadier : you should check you have the proposed updates or the ubuntu-desktop ppa. The yesterday unity update fixed several bugs : [https://launchpad.net/ubuntu/+source/unity/3.8.16-0ubuntu1~natty1](https://launchpad.net/ubuntu/+source/unity/3.8.16-0ubuntu1~natty1) (see the changelog). My dual screen setup now works correctly.

Now that i got the refund from dell, i completely removed windows, so that i don't have a dual-boot setup. Otherwise, Ubuntu works fine for light desktop usage. Forget about 3D gaming for the moment. Googleearth doesn't work and even hangs my computer.
I suppose graphic driver will improve over time..

---

### Post by Blaze33 on 2011-06-29
I also had to manually install the latest flash player version to have a fluid playback: [http://labs.adobe.com/downloads/flashplatformruntimes_incubator.html](http://labs.adobe.com/downloads/flashplatformruntimes_incubator.html)
Just copy libflashplayer.so in /usr/lib64/flashplugin-installer/

As of today, the latest updates broke the display under unity: desktop and application windows aren't properly refreshed.

---

### Post by frogotronic on 2011-07-05
Hello,

  Just got my new e6420 and followed the first post (Installed 10.10) - could **_not_** get the video to work.

  Then I ran:

```
sudo nvidia-xconfig
```

and rebooted and everything is A-OK!

- CH

---

### Post by hoalu on 2011-09-15
It work for me. Thank you so much

---

### Post by finndo on 2011-09-29
use the link provided by the OP, there is an Ubuntu DVD download for this laptop direct from dell, and may already have the drivers installed.  the direct link to the ubuntu download from dell is:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R284592&SystemID=LAT_E6420&servicetag=&os=WN104&osl=en&deviceid=26290&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=58&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=421648](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R284592&SystemID=LAT_E6420&servicetag=&os=WN104&osl=en&deviceid=26290&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=58&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=421648)

---

