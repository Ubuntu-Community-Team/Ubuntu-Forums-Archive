---
title: "ATI Graphics Cards and Jaunty: What Works?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Jackelope King on 2009-04-24
I'd like to do an upgrade to Jaunty Jackalope, but in light of the problems I've been hearing about folks using older ATI cards no longer having access to a working driver, I wasn't sure whether or not I'd be able to make the upgrade. So for anyone who knows about this problem, any clarification about specifics? What do I need to do to determine whether or not my graphics card is going to give me heartburn trying to install Jaunty?

---

### Post by oldrocker99 on 2009-04-24
My laptop, which I got 12/08, has an ATI X1200, which is no longer supported by the newest drivers :confused::( .

However, the 9.01 drivers (still available on the ATI site) DO work as far as 2D display goes, but no OpenGL. The 9.04 drivers don't work at all with my ancient :P card.

Not exactly solved, but a workable stopgap until either ATI or the open-source developers get something for these cards that **DOESN'T** use the incompatible fglrx drivers.

:guitar:

---

### Post by Jackelope King on 2009-04-24
My machine is running an ATI Mobility Radeon X700. According to ATI's website, the "ATI Catalyst™ 9.4 Proprietary Linux x86 Display Driver" is compatible with my card, but I don't know if this is sufficient for me to upgrade to Jaunty. It's getting down around exam time my way, so I don't have a day to spare upgrading and then downgrading. Hence my reason for seeking out info first ;)

---

### Post by cljbville on 2009-04-24
I have an IBM Thinkpad R51 with an ATI Mobile Radeon card.  After my upgrade to Jaunty, xorg messed up big time, like what others have been describing.  However I got lucky and found a solution!  :P

After messing around with trying to enable graphic effects on previous versions I came to the conculsion the flgrx driver was no good for me.  I checked my laptop after the Jaunty upgrade and found the xorg-driver-flgrx package was back.  So even though it wasn't referenced in my xorg.conf I took it out and it works fine now.

When the laptop was booting I hit ESC and went in to the recovery option.  On the menu I selected the root shell.  I then removed the xorg-driver-flgrx.  Now I can get in fine just like before the upgrade!  I've never been able to get the 3D graphics to work on any version, but it still looks great even with out the effects.  

Here's the command to remove the flgrx driver:  "apt-get remove xorg-driver-flgrx"

Here's my xorg.conf file too, I left out all the comments to keep it short:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by ALIENDUDE5300 on 2009-04-25
No luck getting X1950 Pro Graphics Card to work :( Dunno if it's supported by ATI anymore -- when I bought it, it was the VERY best card ATI sold, and I expected it to last me longer than 2 years... as an ATI customer I am very disappointed with the lack of drivers, and I'm seriously thinking about buying an NVIDIA GeForce 9800 GT GPU, because at least NVIDIA has drivers that support most, if not all of their cards under linux, and the open source drivers are much better than ATI's. Unfortunately, unlike ATI, NVIDIA does not openly release the technical specifications of their drivers, but if they did, I'm sure that the open soure drivers would be any better, and I rarely hear of NVIDIA cards breaking (I had an ATI X1900 GT that broke -- the fan stopped working, and then it overheated while it was out of warranty).

---

### Post by cutterjohn on 2009-04-25
ATI announced this a while back, R500 and below are deprecated for support in catalyst, so you were originally stuck with the OSS drivers.  OTOH I read somewhere the other day that ATI relented and is providing SOME support for older cards with legacy cat releases but they apparently don't support Xserver 1.6 right now.  No idea how serious ATI is about this.

Windows drivers moved to legacy support too, but in that case in means less frequent driver updates.

R600 and above are fully supported by monthly cats, as far as that goes... (I feel like a freaking alpha tester...)

---

### Post by anystupidname on 2009-04-28
I don't think I've EVER gotten fglrx to work on this "laptop" (more of a desktop replacement from ASUS) since dapper. Jaunty didn't disappoint me. I can only use the radeon driver. ATI radeon mobility X700 and tried 9.4 and 9.3 driver. Perhaps the strange screen size 1440x900 has something to do with it I donno... Every time I weird colors at the top of the screen and have to reboot. Can't Ctrl-Alt-Backspace or switch to another console...

---

### Post by wolfdale on 2009-04-28
I have a HD4850 card and the latest two version of fglrx did work, however I was more impressed with xorg's "radeon" driver which comes standard with Jaunty. Three items that were most concerning to me:

1) Video playback - Radeon now supports xv playback for my card and there is absolutely no video tearing as seen with fglrx.

2) Power saver mode works in radeon for my Samsung T220 LCD screen. I could never get this to work using fglrx.

3) Radeon still doesn't support 3D for my card, which means i have to boot into windows to play games. However, I hear 3D is coming to radeon. Also, this prevents me from using compiz.

Two out of 3 ain't bad, I personally think it's enough to stay with Jaunty.

---

### Post by Mark Phelps on 2009-04-29
Ok, everyone's experience is different, but I've had to resort to using the open source drivers in Jaunty because I have one of the "blacklisted" cards and -- I've been pleasantly surprised by how well these drivers work!

I don't do gaming or other really demanding 3D stuff, but with videos and Youtube, there is no more tearing or stuttering like there was in previous Ubuntu releases.  Plus, can even have compiz turned on -- and this is WITHOUT using the fglrx driver.

---

### Post by pme 72 on 2009-04-29
The open source drivers in 8.10 worked better for me than the proprietary ones in 8.04 first with Radeon Xpress 200 integrated graphics and later with an inexpensive x1550 upgrade. I never felt a need to install proprietary drivers for 8.10. The upgrade to 9.04 was easy. Compiz seems smoother than with 8.10. Videos look great. I spend a lot of time reading the forums and was aware of the support changes from ATI. After reading so many threads about driver issues it is a relief to have working open source drivers that upgrade so seamlessly. Count me thankful...

---

### Post by cdeobald on 2009-05-01
My ATI Radeon HD 2400 Pro works exactly as it did in Inteepid.  I am using the ATI driver.  The only thing that doesn't work is that the ATI Catalyst Control Center does not save my dual-monitor settings; I have to re-set these after any re-boot, but that was the same under Intrepid.

---

### Post by GothPanda on 2009-05-01
My ATI Radeon x700 in my desktop does not work, like at all...  :C

Now, what gets me, is that right now, I'm using the Open Source Driver in Intrepid, and no real problems...  A little bit of trouble putting the shadows from the windows over any kind of video, but seeing as it just goes black, this isn't much of a problem at all...

I'd be completely fine with the Open Source drivers in Jaunty if they didn't drop to 3 frames a second when I turn on Compiz...  Was there some kind of regression between 8.10 and 9.04?  What would have caused the Open Source drivers to break so badly?

I used to be strictly an ATI only customer, but now I'm going to have to rethink this...

And, the list of cards that are no longer supported might as well be renamed "Any ATI card that GothPanda can actually afford..."  :C

---

### Post by peakshysteria on 2009-05-01
> **Jackelope King said:**
> My machine is running an ATI Mobility Radeon X700. According to ATI's website, the "ATI Catalyst&#8482; 9.4 Proprietary Linux x86 Display Driver" is compatible with my card, but I don't know if this is sufficient for me to upgrade to Jaunty. It's getting down around exam time my way, so I don't have a day to spare upgrading and then downgrading. Hence my reason for seeking out info first ;)

Working out of the box here (Compiz as well). Haven't bothered to install the Ati driver yet. All is working very nicely here. Did an upgrade from 8.10.

---

### Post by Dearhell on 2009-05-01
I have an ATI x300 in a dell laptop and like other old ATI cards the desktop doesn't work for me. Also it restarts the screen each few seconds.

I had to downgrade to 8.10 and install restringed drivers there in order to make it work. With 8.10 works like charm, with 9.04 I think there is still no fix for this.

---

### Post by emarkay on 2009-05-01
Here is the thread for all of us (seems like many) where it is NOT working!

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by adromidon on 2009-05-01
I see R500 all the time is that short for any card with 500 in it like x500 or is the model actually R500?

---

### Post by StuartN on 2009-05-01
> **adromidon said:**
> I see R500 all the time is that short for any card with 500 in it like x500 or is the model actually R500?

R500 is the name of the embedded graphics processor unit while X500, Rage etc are the names of the graphics cards. The GPU used in each model of ATI card is listed here: [http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

---

### Post by HydroTech on 2009-05-01
Hey, I've asked this before on another thread but I wanted to ask again. How do I know if an agp video card will play games well and be able to support ubuntu visual effects? Does it have to have 64MB of onboard ram or something? I have plenty of small video cards but they don't play 3D games or support visual effects.:confused: Any advice?

---

### Post by adromidon on 2009-05-01
> **StuartN said:**
> R500 is the name of the embedded graphics processor unit while X500, Rage etc are the names of the graphics cards. The GPU used in each model of ATI card is listed here: [http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

Weird then according to that article you linked my Radeon 9550 is an R300 yet ATI states in the release notes it is supported

---

### Post by StuartN on 2009-05-01
> **adromidon said:**
> Weird then according to that article you linked my Radeon 9550 is an R300 yet ATI states in the release notes it is supported

No, the 9550 is also classified as legacy.

> The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English)

(Note that there are two links to "Release notes" on the Catalyst 9.4 webpage and the second one incorrectly links to version 9.3 release notes).

---

### Post by lekksi on 2009-05-06
**Update from 8.10 -> 9.04:**
My laptop (ATI Mobility Radeon X700) worked out of the box with the open source graphics driver. Compiz works fine and the 2D performance is much better than in 8.10.

I wasn't as lucky with my desktop (ATI Radeon 9500). As mentioned the new fglrx driver doesn't support my chipset anymore and I had to remove the driver from recovery console. The default driver doesn't support 3D and 2D performance is poor.

---

### Post by loudog23 on 2009-05-06
same here, with ATI readon xpress200 on Intel Dual core (integrated Video).

On jaunty, it was smooth a nice, but no 3d support. I downgraded to 8.10 so i can play my game but i miss the little extra of jaunty :(

---

### Post by li_sin_cin on 2009-06-06
Hi.

I have ATI Radeon RS690M [ATI X1200 series].
And I also have upgraded to 9.04.

At start I was upset. My video card is no longer supported by AMD drivers. And at basis even movies playback been Very VERY slowly. 

Then. I read some advices, and got FULL 3D support and normal functionality of card.
I enabled all the KDE effects. Only window shadows are not showing correctly. But thats fine for me :)

You just need to turn DRI support.
Here is the link
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

and my xorg.conf
```
ection "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Load  "dri"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "radeon"
    Option          "DRI" "true"
    Option          "GARTSize" "64"
    Option          "XAANoOffscreenPixmaps"
    #Option "AccelMethod" "XAA"
        Option "AccelMethod" "EXA"
    Option          "TripleBuffer"

EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen          "Default Screen"    
        Option          "AIGLX" "true"
EndSection

Section "ServerFlags"
        Option "AIGLX" "on"
EndSection


```And that string helps to view movies on normal speed. That dont freezing any more :p
```

Option          "TripleBuffer"

```So, now I'm happy. Hope all it helps.

---

### Post by peakshysteria on 2009-06-06
> **lekksi said:**
> **Update from 8.10 -> 9.04:**
My laptop (ATI Mobility Radeon X700) worked out of the box with the open source graphics driver. Compiz works fine and the 2D performance is much better than in 8.10.

I wasn't as lucky with my desktop (ATI Radeon 9500). As mentioned the new fglrx driver doesn't support my chipset anymore and I had to remove the driver from recovery console. The default driver doesn't support 3D and 2D performance is poor.

My old laptop with ATI Raedon 9000 worked out of the box. Nice 2D performance. Compiz is working smooth. But it's no gamerbox thats for sure. My default box with ATI X700 EXCALIBUR PRO also worked out of the box.

---

### Post by wpshooter on 2009-06-06
My custom built desktop machine is using an OOOOOLD ATI Radeon 9600XT card and what I found is that in doing a clean install of Jaunty from scratch (I do NOT trust doing update from previous versions), that after installing from the ALTERNATE CD version the FPS was very low and direct rendering was not enabled. 

Then STRANGELY (because I would have thought that it would have been exactly the opposite) after I WIPED that installation from the drive and re-installed from the LIVE CD version the FPS was much faster and the direct rendering WAS enabled.  At that point, I left well enough alone !!!

---

