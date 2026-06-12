---
title: "Lenovo X200s Owner's Thread"
date: 2009-02-26
forum: Hardware
---

### Post by Mr.Carramba on 2009-02-26
Hi,

I 'm now proud owner of Thinkpad x200s with ssd. And I want to report installation progress. 

Have tested both 64 and 32 bis ubuntu 8.10 and almost everything worked out of the box.
Im now on 32 bits so reports is based on it.

Installiation was tested both from ultrabase DVD and from USB.

**Out of the box**


[LIST]
[*]Ethernet
[*]Wireless
[*]Bluetooth
[*]Camera
[*]Fan (havent heart it started yet :D )
[*]Brightnes controll
[*]Volume controll
[*]Compiz
[*]Skype + webcam
[*]aMSN + webcam
[/LIST]

**Needs fixing**
Resolution is not correctly recognized, but is simple fixed with advice from blog [1]
```

#xorg.conf
Section "ServerLayout"
      Identifier     "X.org Configured"
      Screen      0  "Screen0" 0 0  
EndSection                            

Section "Files"
#for 32 bits
      ModulePath   "/usr/lib/xorg/modules"
#for 64 bits
#ModulePath   "/usr/lib64/xorg/modules"
      FontPath     "/usr/share/fonts/misc/"
      FontPath     "/usr/share/fonts/TTF/"
      FontPath     "/usr/share/fonts/OTF"
      FontPath     "/usr/share/fonts/Type1/"
      FontPath     "/usr/share/fonts/100dpi/"
      FontPath     "/usr/share/fonts/75dpi/"
  FontPath    "/usr/share/fonts/corefonts/"
  FontPath    "/usr/share/fonts/mathematica-fonts/"
EndSection                                        

Section "Module"
      Load  "dri"
      Load  "extmod"
      Load  "glx"
      Load  "record"
      Load  "xtrap"
      Load  "dbe"
      Load  "freetype"
EndSection           

Section "Monitor"
      Identifier   "Monitor0"          
      VendorName   "LEN"               
      ModelName    "4010"              
      Option      "DPMS"               
  Option  "PreferredMode" "1280x800"   
EndSection                               


Section "Monitor"
  Identifier "FakeHDMI-1"
  Option  "Ignore"    "True"
EndSection                 

Section "Monitor"
  Identifier "FakeHDMI-2"
  Option  "Ignore"    "True"
EndSection                 

Section "Device"
  Option     "DRI"
      Identifier  "Card0"
      Driver      "intel"
      VendorName  "Intel Corporation"
      BoardName   "Unknown Board"
      BusID       "PCI:0:2:0"
  Option  "monitor-HDMI-2" "FakeHDMI-2"
  Option  "monitor-HDMI-1" "FakeHDMI-1"
  Option  "monitor-LVDS"  "Monitor0"
EndSection

Section "Screen"
      Identifier "Screen0"
      Device     "Card0"
      Monitor    "Monitor0"
  DefaultDepth    24
      SubSection "Display"
              Viewport   0 0
              Depth     24
      Modes   "1280x800" "1024x768" "800x600"
EndSubSection
EndSection


```

How ever this do not fix Fn+F7, and it is not working.
To enable second output you have to go to screen setting and either enable virtual resoliution or mirror screens. 

Annoing problem is that brightness do not get restored to the level I have left, so this requares manual ajustment. 

I had this laptop only for few days so these are things I havent tested yet.


To sumarize: Im really hapy with the performance and the smooth installiation.



[1][http://www.jaduncan.com/2009/02/ubuntu-intrepid-on-lenovoibm-x200s.html](http://www.jaduncan.com/2009/02/ubuntu-intrepid-on-lenovoibm-x200s.html)

---

### Post by Mr.Carramba on 2009-02-27
can report that compiz-fusion works out of the box!

---

### Post by RawDR on 2009-03-06
I also own an x200s and love it! I am assuming you are outside of the US? x200s in the US still does not have the option for webcam or WWAN. :-(

Middle button scroll not working was a big hinderance when I installed 8.10 but I was able to get that fixed.

---

### Post by Mr.Carramba on 2009-03-06
> **RawDR said:**
> I also own an x200s and love it! I am assuming you are outside of the US? x200s in the US still does not have the option for webcam or WWAN. :-(

Middle button scroll not working was a big hinderance when I installed 8.10 but I was able to get that fixed.

yes Im from outside of US and loving the x200s too!
middle button works for me in some applications, for example thunderbird.
please do post you fix for middle button, so we can have a collection of fixes :)

---

### Post by Mr.Carramba on 2009-04-18
have upgraded to Jaunty beta, and everything works out of box :)

boot time from the grub to log in screen is... 14s :D

---

### Post by Jabz.biz on 2009-05-12
Hi, I'm, planning to upgrade to jaunty tonight. Any experience with Intel Graphic Cards and WLAN? Do they work out-of-the-box? 
Thank you for letting me know.

---

### Post by Mr.Carramba on 2009-05-12
> **Jabz.biz said:**
> Hi, I'm, planning to upgrade to jaunty tonight. Any experience with Intel Graphic Cards and WLAN? Do they work out-of-the-box? 
Thank you for letting me know.


I had some issues with virtual screen, but it was resolved by restoring xorg.conf manually
audio works better
wlan is out of box
in terminal I lost ctr-d and ctr-x. i cant terminate application running in terminal

otherwise everything works fine, expect for incredible start up time :)

---

### Post by Jabz.biz on 2009-05-12
I can confirm this bug: [https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912) ...I saw some others online which I susppect to suffer from as well...but still not sure. The problems seem to be spread quite widely.

---

### Post by Mr.Carramba on 2009-05-13
> **Jabz.biz said:**
> I can confirm this bug: [https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912) ...I saw some others online which I susppect to suffer from as well...but still not sure. The problems seem to be spread quite widely.

hum, my logs are empty.
on the other hand I have no clue what it is :)

---

### Post by Jabz.biz on 2009-05-13
This thing is known as the "Tracker index corruption" bug, where a popup lets the user know that the Tracker (Search in Ubuntu) does not stop indexing. It loops with another nasty popup. 

Bug Fixes & Solutions: 

Solution 1 [Beginner]: 
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560/comments/30](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560/comments/30)

Solution 2 [Advanced]:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/65](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/65)

---

### Post by jimmyfergus on 2009-10-23
Since this is the first result Google gives me when searching for "Thinkpad X200s Ubuntu", I'll report here about 9.10.

No hardware-related problems found yet with Karmic Beta - everything all special keyboard buttons, camera, suspend/resume...

Haven't tried external monitor but will soon, and will report if anything goes wrong.

Only tweak I performed was to [get scrolling from the trackpoint/middle button]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Vertical_Scrolling").  I suppose it would be *nice* if that was automatic, but that's pretty trivial.

---

### Post by Jabz.biz on 2009-10-23
That's great news...at first I thought I gonna wait a while. Thanks for this thread. Thanks for keeping us posted.

---

