---
title: "[SOLVED] Netbook with ubuntu, apache server, mysql and so on"
date: 2008-11-25
forum: Hardware
---

### Post by Nonsense on 2008-11-25
Hi
I'm in the market of buying a netbook to use on the buss and train.
I want it to be able to handle Ubuntu and function with the basic applications such as Firefox (with non-free flash plugin), OpenOffice, Gimp, VLC and so on. I also want it to be able to handle a local install of apache server, mysql, php and python (in order to use local installs of Joomla, Wordpress, Textpattern and so on).

I have been looking at:
Asus EeePC 900 (16GB ssd, 1GB Ram, 8.9" screen) - cheap
Acer Aspire One A150-B (120GB HD, 1GB Ram, 8.9" screen) - not so cheap

My main use will be browsing the web, writing documents (shorter) and coding websites.

---

### Post by harrison23 on 2008-11-25
Hi I would reccomend the Acer Aspire A110

its cheaper than the a150 but has a smaller hdd but its not needed

---

### Post by Nonsense on 2008-11-25
Yes, but it also has less ram, only 512MB.
And the ssd is only 8GB, will that be enough to fit all apps?

There seems to be some problems installing Ubuntu on the Aspire One.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

> 
**Partial Function:**

 
[LIST]
[*]Audio - there is sound, issues detailed below 
[/LIST]
 
**Not Functional:**

 
[LIST]
[*]Hibernate on A110L 
[*]Card Reader power saving 
[*]wifi power saving 
[*]wifi kill switch
[/LIST]


---

### Post by johnkzin on 2008-11-25
Have you looked at the Raon Everun Digital Note?

It has vendor supported Ubuntu, it's out, and the windows version has had great reviews over on umpcportal.com.

You can buy it in the US through dynamism.com (work ordered one for me, and I'll be getting it next week).

---

### Post by Nonsense on 2008-11-25
Sorry, I'm in Sweden, and that thing hasn't hit Europe yet.

---

### Post by Nonsense on 2008-11-25
But will the Acer work with Ubuntu running Apache, mysql and php?
I guess it needs the ram upgrade?

---

### Post by liniaal on 2008-11-25
i would advice a 1gb ram machine indeed for such dev-like operations as a (small) joomla site server et cetera. but if you like the price of the a110 very well.. you can always buy extra memory? but yes i think you would need the upgrade soon.

---

### Post by johnkzin on 2008-11-25
> **Nonsense said:**
> Sorry, I'm in Sweden, and that thing hasn't hit Europe yet.

Sorry, didn't realize it wasn't there yet.  I know the XP version is in Europe, but I don't know about Sweden.  I just assumed the Ubuntu version hit all markets at the same time.

Does that also rule out the Dell Mini 9 with Ubuntu, or the newer HP that has Ubuntu (not the 2133 that has Suse, but the mini 1000 or something like that).

---

### Post by Nonsense on 2008-11-27
In the end, I decided to buy a HP 2133 since I got a good deal and paid about 300€! (about 370$)
I've seen prices as high as 610$... today I looked at the prices in the same store and it was almost 500$...

The config I went for was:

1.6 GHz, 2GB Ram, 120 GB 5400 RPM SATA, & Vista (the Linux version wasn't available), 1024*600.

---

### Post by Nonsense on 2008-11-29
So I got the Hp 2133, but I'm having problems installing Ubuntu from a USB stick.

I tried PartedMagic, but that didn't work as I couldn't set the screen resolution so I tried Gparted Live Usb.
I managed to start it, and the resolution is right, but it doen't recognize my HD, only the usb stick.

Then I tried the Ubiquity-installer, no luck. The usb stick fails to be recognized as properly formated.

I'd very much like to either use the Wubi-installer or manage to get gparted working since I would like to set the partion-size myself.

I'm gonna try this and see what happens:
[http://extelopedia.wordpress.com/hp-2133/](http://extelopedia.wordpress.com/hp-2133/)

---

### Post by Nonsense on 2008-11-29
Ah.
Th UNetbootin seems to work.



Ed: Or at least that's what I thought...
When I start the system the graphics are all scrambled and a notice which is illegible pops up.

---

### Post by vegipowrd on 2008-11-30
Please keep us posted.  I (and probably others) will be doing the same procedure in the next week or two.  
I hope all goes well.

---

### Post by the3dman on 2008-11-30
The Slyvania g Meso netbook comes stock with Ubuntu and works great for me with all that. I have tried alot of netbooks and I personally think this is the best one (at least for me), runs fast and battery life is excellent.

[http://www.amazon.com/Sylvania-GNET28001ON-8-9-Inch-Netbook-Processor/dp/B001FTD1VU/ref=pd_bbs_sr_2?ie=UTF8&s=electronics&qid=1228027082&sr=8-2](http://www.amazon.com/Sylvania-GNET28001ON-8-9-Inch-Netbook-Processor/dp/B001FTD1VU/ref=pd_bbs_sr_2?ie=UTF8&s=electronics&qid=1228027082&sr=8-2)


or

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4107593&CatId=4013](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4107593&CatId=4013)

---

### Post by Nonsense on 2008-11-30
My experience so far has been both a good and bad one.

The HP 2133 has a very nice keyboard and I like the screen, it's nice to have a big HD (which is fairly quiet), it looks really slick. The performance is what I expected, not as fast as my desktop, but sufficient for basic apps.

Now for the annoying part.
HP did not include a Vista recovey disc (just a recovery partition using 9GB of space) so I had to dl that from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download)
(I want to keep Vista if I may need it later for some reason)
As I wanted to keep the Vista installation I needed to partition the HD. I thought Gparted was right for the job, but it turns out that it will cripple the ntfs-partition so that the Vista installation will be corrupt. 
Instead I used the Vista partition-tool (type "partition" in the control panel search field). 
I shrunk the Vista ntfs partition to 50GB (Vista is hungry for space so I figure it needs the space) and was left with 50GB of free space. 
Then I made a Ubuntu LiveUsb stick with [Unetbootin]("http://unetbootin.sourceforge.net/") and added "xforcevesa" to the default installation (otherwise the screen would just go blank). Once logged into the Live installer my first impression was that the screen resolution was set to 640x480, since my screen is 1024x600 and thus widescreen I couldn't see the lower part of the desktop, which made it impossible to see any installation buttons so I had to do it by using tab, kind of a trial and error. I then started Gparted (since I couldn't get it to recognize my HD if I just tried the Gparted LiveUSB) and made 3 new partitions, one ext3 for Ubuntu (20GB), one swap (2GB) and a ntfs-partition for XP (30GB). 
Since one HD can only have 4 primary partitions, and the vista partition is a primary partition and the recovery partition is also primary, I had to make the ext3 and swap extended, and the xp ntfs primary. 
For the installation I choose a manual partition setting since I wanted to keep my partition-settings. I selected the ext3 partition and used it as root by setting the option to "/" and to be formated as ext3 (just a  security measure).
After that installtion went as usual. 

Everything worked after the install except the Wifi and the screen resolution. The Wifi-card need propertiary drivers which was identified automatically, the screen however was not that easy. I'm still struggling to get it right.

---

### Post by Nonsense on 2008-12-09
So I finally got the screen res working.

I chose "CN700+VT8237S/VT8237R PLUS" and the "[Unified 2D driver Ver85a-43862(04Nov08) (593.3K)]("http://linux.via.com.tw/support/beginDownload.action?eleid=222&fid=423")" at the driver dl page at [VIA]("http://linux.via.com.tw/support/downloadFiles.action").

Then I used [these]("http://ubuntuforums.org/showpost.php?p=6105258&postcount=11") xorg.conf settings, but subtracted a few lines:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
  BoardName    "Framebuffer Graphics"
  Driver       "via"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "VIA Technology"
  Option "NoDDCValue"
  Option "ActiveDevice" "LCD,CRT"
#  Option "PanelID"      "17"
  Option  "DisplayHardwareLayout" "LCD"
  Option  "ForceLCD"
#[<bool>]
  Option  "VideoOnDevice" "LCD"
#  Option "LCDPort" "DVP0"
EndSection

Section "Monitor"
  DisplaySize  250 150
  HorizSync    28-500
  Identifier   "Monitor[0]"
  ModelName    "VIEWSONIC VA912-4SERIES"
  Option       "DPMS"
  VendorName   "VSC"
  VertRefresh  43-60
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline     "1280x768" 80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
  Modeline     "1024x768" 92.05 1024 1088 1200 1376 768 769 772 806
  Modeline     "1024x768" 90.83 1024 1088 1200 1376 768 769 772 805
  Modeline     "1024x768" 89.72 1024 1088 1200 1376 768 769 772 805
  Modeline     "1280x600" 88.68 1280 1352 1488 1696 600 601 604 630
  Modeline     "1280x600" 87.48 1280 1352 1488 1696 600 601 604 629
  Modeline     "1280x600" 85.59 1280 1344 1480 1680 600 601 604 629
  Modeline     "1024x600" 71.11 1024 1080 1192 1360 600 601 604 630
  Modeline     "1024x600" 69.32 1024 1080 1184 1344 600 601 604 629
  Modeline     "1024x600" 68.48 1024 1080 1184 1344 600 601 604 629
  Modeline     "800x600" 55.22 800 840 928 1056 600 601 604 630
  Modeline     "800x600" 54.47 800 840 928 1056 600 601 604 629
  Modeline     "800x600" 53.80 800 840 928 1056 600 601 604 629
  Modeline     "768x576" 50.62 768 808 888 1008 576 577 580 605
  Modeline     "768x576" 49.92 768 808 888 1008 576 577 580 604
  Modeline     "768x576" 49.32 768 808 888 1008 576 577 580 604
  Modeline     "640x480" 34.80 640 672 736 832 480 481 484 504
  Modeline     "640x480" 34.38 640 672 736 832 480 481 484 504
  Modeline     "640x480" 33.90 640 672 736 832 480 481 484 503
EndSection

Section "Screen"
  DefaultDepth 32 
  SubSection "Display"
    Depth      32
    Modes      "1024x600"  
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

```

There it is.
Haven't tried compiz yet, but I'm not interested since I want the system to be as fast as possible.

---

