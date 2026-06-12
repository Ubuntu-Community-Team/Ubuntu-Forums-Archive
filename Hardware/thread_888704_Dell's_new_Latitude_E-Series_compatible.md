---
title: "Dell's new Latitude E-Series: compatible?"
date: 2008-08-13
forum: Hardware
---

### Post by elektronaut on 2008-08-13
Hi,

I'm tempted to order a laptop from Dell's new Latitude series (E5400, E5500, E6400, E6500), namely the E6500. As I need the laptop pretty soon, I don't have the patience to wait for some review about Linux compatibility, hence this posting. It would be great if anyone who installed Ubuntu on one of these models could report here about things that work or don't work, especially in regard to the many configuration options you have with a Dell.

---

### Post by stchman on 2008-08-13
> **elektronaut said:**
> Hi,

I'm tempted to order a laptop from Dell's new Latitude series (E5400, E5500, E6400, E6500), namely the E6500. As I need the laptop pretty soon, I don't have the patience to wait for some review about Linux compatibility, hence this posting. It would be great if anyone who installed Ubuntu on one of these models could report here about things that work or don't work, especially in regard to the many configuration options you have with a Dell.

I was looking at the specs and the only problems I can see are the wireless and the video card.

Dell makes Ubuntu pre-installed laptops so I recommend one of them.

The E series look to be a high end rugged laptop that comes with a huge price premium.  If you don't need such a rugged laptop you can save yourself quite a bit of cash.

---

### Post by elektronaut on 2008-08-13
Here in Germany, according to Dell's website, there are only two laptops with Ubuntu preinstalled: The Inspiron 1525 and the XPS M1330. Both have a reflecting display (TrueBrite), which is a show stopper for me. I also want a digital monitor interface, be it DVI or DisplayPort, and at least a 14 inch display (rather 15 inch). Given these requirements, I'm left with the E6500 (and I also really like it's other features like the magnesium shell, the eSata interface,...).

---

### Post by PC_load_letter on 2008-08-20
> **elektronaut said:**
> Hi,

I'm tempted to order a laptop from Dell's new Latitude series (E5400, E5500, E6400, E6500), namely the E6500. As I need the laptop pretty soon, I don't have the patience to wait for some review about Linux compatibility, hence this posting. It would be great if anyone who installed Ubuntu on one of these models could report here about things that work or don't work, especially in regard to the many configuration options you have with a Dell.

The Dell Ubuntu line-up is a joke in my opinion. Maybe good for a new Windows convert, but with only minimal knowledge of Linux one could do much better. 
Why don't you go after the components, and see if you can setup a system with components known to be compatible with Ubuntu?
I did this with a Dell Vostro recently, installed Heron with no problems,everything works, even suspend!

---

### Post by shrndegruv on 2008-09-10
I received my E6400 last night and succesfully installed xubuntu 8.04 (did an encrypted lvm) with no problems.  I didn't get to play with it too much but the following appears to work out of box


* graphics -- the intel card is configured and I can use xfce's compositing with no performance problems
* wireless -- network manager sees wireless networks.  I have the dell wireless card and the restricted driver manager is telling me it is using a restrcited driver
* touchpad -- i haven't tried scrolling, but it appears everything else if working


tonight i am going to try the various suspend modes, the touchpad scrolling, install compiz, etc....

---

### Post by elektronaut on 2008-09-11
Thanks for your comments! Nice to hear that the laptop seems to work without trouble. Which Wifi card did you take? Here in Germany Dell offers two different ones, one is a 802.11 b/g card, the other one can do b/g/n.

---

### Post by shrndegruv on 2008-09-11
I have el-cheapo default card.  its the dell 1397 i think.

last night I did not get to play with the new toy because I had to do work.  hopefully tonight I will.  I saw another post on this forum saying that the scroll feature of the touchpad doesn't work -- Ill have to look into this (I cannot confirm or deny at this point).  Plus, because its a laptop, i really want the suspend modes to work.  I also need to see if the drive suffers from the load_cycle_count issue common to laptops.  


maybe i should throw up a guide/review...;)

---

### Post by in-dust-rial on 2008-09-11
> **PC_load_letter said:**
> The Dell Ubuntu line-up is a joke in my opinion. Maybe good for a new Windows convert, but with only minimal knowledge of Linux one could do much better. 
Why don't you go after the components, and see if you can setup a system with components known to be compatible with Ubuntu?
I did this with a Dell Vostro recently, installed Heron with no problems,everything works, even suspend!

you hey, how much money was it? back then?

thx
.me

---

### Post by elektronaut on 2008-09-11
shrndegruv, how is the noise level of this laptop? How often is the fan running, and how loud is it?

---

### Post by pdub on 2008-09-12
I received my E6500 last week and promptly installed Ubuntu 8.04 64bit. My system has the T9600 Processor, Intel WiFi Link 5300 and NVidia Quatro and 4GB RAM.

The install was fine, video worked perfectly with restricted drivers but I installed the latest drivers from nvidia anyway. 

Wireless is not working for me. I followed a few threads and did that card initialized but could not connect to see and wireless networks. I will probably take the card out of my D820 and install it in the E6500 for now.

The fan noise is a real problem for me though. The CPU fan starts almost immediately after turning the computer on, even if I just let it sit at the BIOS Settings screen. I am going to call Dell to see if the noise is normal. My D820 fan rarely came on and my MacBook Pro almost never comes on, even under load. This thing is running the fan right now even though I am just typing this note, nothing else running.

Otherwise the notebook is very nice, the WXGA+ screen is extremely clear and crisp. Probably the nicest screen I have had on a notebook.

Will post again once I contact Dell.

---

### Post by elektronaut on 2008-09-16
> **pdub said:**
> The fan noise is a real problem for me though. The CPU fan starts almost immediately after turning the computer on, even if I just let it sit at the BIOS Settings screen. I am going to call Dell to see if the noise is normal. My D820 fan rarely came on and my MacBook Pro almost never comes on, even under load. This thing is running the fan right now even though I am just typing this note, nothing else running.
Did you check for 'kacpid' in the process list? I had the same problem lately, and this process was the cause, eating > 90% of CPU! I then switched to an older kernel, and the problem was gone. About a week later, some updates for the newer kernel were installable, so I checked again with that kernel, and then it surprisingly worked with that one also.

---

### Post by ezTol on 2008-09-16
Since I also consider buying a Latitude E6400, some questions about linux compatability. I sorted them by importance :D
[LIST]
[*] Could you measure the power comsumption with powertop (maybe also while playing video/hd content as comparison)?
[*] There is no video acceleration in the intel driver for HD content like in windows, right? apart from XvMC for mpge2 which is rather useless with today cpu's
[*]Has the intel driver also problems playing videos/OpenGL apps with compiz fusion? (I'm a tortured fglrx user). Really looking forward to Dri2 :-)
[/LIST]

Not that important...
[LIST]
[*] what about the display port? does anybody know how long it will take for drivers to support sound over displayport? (in case the hardware supports it at all)
[*] I read about a dvd burner issue on notebookreview.com? Have you already used k3b or whatever?
[/LIST]

Still worth an answer... :)
[LIST]
[*] Is there the possibility to switch between quick charge and normal charge while running the OS (Linux?), or do you need to make a swith in the BIOS (the needed reboot would be a bit absurd)?
[*] What about this dell support/diagnostics partition? Can it be booted from GRUB or may there be problems when you call the support and have deleted it? Or can it be moved to (or booted from) a usb hdd?
[*] Can the functions of the Dell Control Point Software be used in linux (not the software itself)? Maybe command line? scripts? Which "important" functions are there in windows that could be absent in linux?
[/LIST]

Well, many many questions and you have certainly not tested everything yet, so take your time. Would be really nice to get some positive!!! feedback 
Thanks you very much in advance.

Intel Chipset/Graphics/Wireless is already supported, but not in hardy. Intrepid should have the drivers, but is still alpha...
There are also two threads on notebookreview, but there seem to be some problems even in intrepid (touchpad not working, suspend)
[Guide/Experiences: Ubuntu Linux @ Latitude E series (highly experimental!)]("http://forum.notebookreview.com/showthread.php?t=295957")
[ Linux on Latitude E6400 ]("http://forum.notebookreview.com/showthread.php?t=298130")

---

### Post by shrndegruv on 2008-09-16
I have an e6400

1) yes you can measure with powertop -- i have done this
2)I dont know about video accel for intel; i have that card and am not impressed by its performance.  im thinking of trading in and getting the nvidia
3)yes there is video tear with compiz/movies

i have not tested video out or the burner


dont know about battery charging modes.  I deleted all partitions and did an install that took the entire disk.  The machine comes with a cd with diagnostic tools on it, which i have used because smartctl was saying i  had errors.  I ran all he hd diagnostics from the disk and they came up clean, and i believe them.

---

### Post by Idefix82 on 2008-09-16
> **PC_load_letter said:**
> 
I did this with a Dell Vostro recently, installed Heron with no problems,everything works, even suspend!

I have two questions: which Ethernet card do you have and are you dual booting?
I have a Vostro 1710, dual booting with XP and Ubuntu 8.04 the AMD64 version. Everything works perfectly (WLAN was a matter of one line with ndiswrapper) including the fanciest Compiz effects except for the ethernet card. Sometimes when I boot Ubuntu the Ethernet card is not recognised and only starts working after I start Windows and then restart immediately again. Did you ever have this issue or is this a typical dual boot problem? My Ethernet card is a Broadcom 8168C(P)/8111C(P) according to Windows.

---

### Post by ezTol on 2008-09-16
> **shrndegruv said:**
> 
1) yes you can measure with powertop -- i have done this
2)I dont know about video accel for intel; i have that card and am not impressed by its performance.  im thinking of trading in and getting the nvidia
3)yes there is video tear with compiz/movies


1) Well, actually I didn't mean if it was *possible *to measure the power consumption with powertop... :-) I know that you *can * it. I rather asked if somebody could actually *do* a real world power consumption test: 
[LIST]
[*] ilde
[*] surfing
[*] video playback
[*] full hd video playback (1080p and 720p)
[/LIST]
If you have used powertop, would you be so kind to post any your results?

3) I had hoped that there are no problems with compiz and videos. what's in your xorg.conf? do you use EXA or XAA for acceleration? Some people reported that the following options in the xorg.conf device section helped:
Option "AccelMethod" "EXA"
Option "ExaNoComposite" "false"
Option "MigrationHeuristic" "greedy"

in /etc/environment
INTEL_BATCH="1"

But maybe the drivers in hardy are just too old... Hardy has still intel drivers 2.2.1, Intel is currently working on 2.5. Debian Sid for example uses 2.4.2.

Here's a thread in [Launchpad]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492")

---

### Post by shrndegruv on 2008-09-16
> **ezTol said:**
> 1) Well, actually I didn't mean if it was *possible *to measure the power consumption with powertop... :-) I know that you *can * it. I rather asked if somebody could actually *do* a real world power consumption test: 
[LIST]
[*] ilde
[*] surfing
[*] video playback
[*] full hd video playback (1080p and 720p)
[/LIST]
If you have used powertop, would you be so kind to post any your results?

3) I had hoped that there are no problems with compiz and videos. what's in your xorg.conf? do you use EXA or XAA for acceleration? Some people reported that the following options in the xorg.conf device section helped:
Option "AccelMethod" "EXA"
Option "ExaNoComposite" "false"
Option "MigrationHeuristic" "greedy"

in /etc/environment
INTEL_BATCH="1"

But maybe the drivers in hardy are just too old... Hardy has still intel drivers 2.2.1, Intel is currently working on 2.5. Debian Sid for example uses 2.4.2.

Here's a thread in [Launchpad]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492")


XAA accelaration breaks suspend to ram.  I use exa explicitly.  I haven't tried the other xorg options, but will definitely do it tonight because I want to get performance up.

I did some basic tests from the m1330 powersaving thread.  

I *believe* powertop reported a drain rate of 20W over a 60 second period with display at max brightness.  With the display at lowest brightness the drain was 16.7W.  (Both doing absolutely nothing with the machine

Ill do more tests in the future....

---

### Post by ezTol on 2008-09-16
Thanks. Wow 20W idle seems to be a lot. The test on notebookreview reported 14W to 18W with light usage (XP SP3). I hope there's some room for some power comsumption tweaking.

---

### Post by shrndegruv on 2008-09-16
well i did no tweaking.  I imagine shutting down the bluetooth system will save that watt.

Is there any way to upgrade the intel driver to the latest version?  I noticed last night that 2.2.1 is the one that comes with hardy.  I was wondering if i would notice any performance gains by upgrading.

seems like the 4500GMAHD card is capable, but there isn't good driver support in linux.  


Does anyone know if the nvidia card that is available from dell on this model suffers from the manufacturing defect that nvidia has revealed on a lot of its cards?
the card is
NVIDIA Quadro NVS 160M

how does that card compare to the 8600M?  Or the newer one (9800M or whatever it is...)

---

### Post by ezTol on 2008-09-16
There is a [Repo]("http://people.ubuntu.com/~bryce/Testing/intel/hardy-i386/") that has version 2.3.1. Intrepid uses 2.4.1.

---

### Post by shrndegruv on 2008-09-16
is there a guide on how to install it?

---

### Post by theburningor on 2008-09-16
I posted instructions in the following thread on how I got the wireless working on my Dell Latitude e6500 with Intel WiFi 5100

[http://ubuntuforums.org/showthread.php?t=879134&page=7](http://ubuntuforums.org/showthread.php?t=879134&page=7)

Its about halfway down the page.

Has anyone been able to get the gsynaptics working?  My touchpad works as a basic mouse, but when I try to run gsynaptics, I get the error about needing to enable shmconfig in xorg.conf.  I have already done that and restarted X but to no avail.

Any thoughts?

---

### Post by shrndegruv on 2008-09-16
ok i added the X changes and didn't notice any significant speed increase.  glxgears went from 950 fps to about 1050.  incidently, when i move the glxgears window there is horrible artifacts left on the screen.  

this indicates to me that the intel drivers just arent there.  i think i am going to trade up for an nvidia card....

---

### Post by hasinasi on 2008-09-17
I am using (k)ubuntu on the new Latitude E6400. 

I tried 8.04, 8.04.1, and 8.10-alpha5 (2.6.27-3 kernel). In all those versions, I have the problem that the touchpad is not recognized correctly (not present in /proc/bus/input/devices).

This means: (1) NO recognition by X. (2) only very basic functionality (PS/2 emulation) is available. (3) NO tapping, (4) NO scrolling, (5) NO adjustments of sensitivity. 

This is a major, major issue for me, as I am really unhappy with the touchpad default sensitivity. Has anyone a touchpad with working scroll?

I have posted more details in another thread: 
[http://forum.notebookreview.com/showthread.php?t=298130]("http://forum.notebookreview.com/showthread.php?t=298130"). 
Someone else has seen the same problem: 
[http://ubuntuforums.org/showthread.php?p=5805477#post5805477]("http://ubuntuforums.org/showthread.php?p=5805477#post5805477")
I also filed a bug for it: 
[https://bugs.launchpad.net/ubuntu/+bug/270643]("https://bugs.launchpad.net/ubuntu/+bug/270643")

If anyone has an idea how to fix this, please help me!
--hasi

---

### Post by hasinasi on 2008-09-17
I am using (k)ubuntu on the new Latitude E6400 (all 32 bit versions). 

Here are some of my observations: 
[LIST]
[*]The **8.04 Live CD does not work** (most likely due to graphics card issues). It can be made workable by booting in safe graphics mode and switching to vesa mode in xorg.conf. I also seem to remember that both ethernet and WiFi were not working
[*]Surprisingly, the **8.04.1 Live CD DOES work**. The **Intel 4500MHD graphics card is recognized** out of the box. Also, the **ethernet card works** out of the box. **Wireless does not work (Intel 5300)**. Skype crashes when I try to make a call. 
[*]**8.10-alpha5 Live CD works**. **Graphics card (4500MHD), ethernet, and wireless recognized out of the box. Webcam is recognized**. Skype phone and video calls work. In the Kubuntu flavor (KDE 4.1.1, there are keyboard/mouse issues that make it pretty unusable. Ubuntu is fine 
[*]The **touchpad is not recognized** in any of the tested versions. See my previous post in this thread for more details. [*]Surprisingly, if have **OpenGL** out of the box in 8.04, but not in 8.10-alpha5! In both I just have nothing in device section in xorg.conf and tested it by glxinfo.[/LIST]

---

### Post by shrndegruv on 2008-09-17
> **hasinasi said:**
> I am using (k)ubuntu on the new Latitude E6400 (all 32 bit versions). 

Here are some of my observations: 
[LIST]
[*]The **8.04 Live CD does not work** (most likely due to graphics card issues). It can be made workable by booting in safe graphics mode and switching to vesa mode in xorg.conf. I also seem to remember that both ethernet and WiFi were not working
[*]Surprisingly, the **8.04.1 Live CD DOES work**. The **Intel 4500MHD graphics card is recognized** out of the box. Also, the **ethernet card works** out of the box. **Wireless does not work (Intel 5300)**. Skype crashes when I try to make a call. 
[*]**8.10-alpha5 Live CD works**. **Graphics card (4500MHD), ethernet, and wireless recognized out of the box. Webcam is recognized**. Skype phone and video calls work. In the Kubuntu flavor (KDE 4.1.1, there are keyboard/mouse issues that make it pretty unusable. Ubuntu is fine 
[*]The **touchpad is not recognized** in any of the tested versions. See my previous post in this thread for more details. [*]Surprisingly, if have **OpenGL** out of the box in 8.04, but not in 8.10-alpha5! In both I just have nothing in device section in xorg.conf and tested it by glxinfo.[/LIST]



what type of performance are you getting on glxgears?

---

### Post by hasinasi on 2008-09-17
> **shrndegruv said:**
> what type of performance are you getting on glxgears?

Just by hacking in glxgears, I am getting the following: 
```
5030 frames in 5.0 seconds = 1005.875 FPS
5786 frames in 5.0 seconds = 1157.058 FPS
5850 frames in 5.0 seconds = 1169.844 FPS
5881 frames in 5.0 seconds = 1176.070 FPS
5875 frames in 5.0 seconds = 1174.918 FPS

```

I am not a heavy graphics or gaming person. Do I need to feed any other parameters to it? Let me know if you want me to run something else. 

edit: I forgot to say that this is on 8.04 (intel driver version 2.2.1)
--hasi

---

### Post by shrndegruv on 2008-09-17
if you move the glxgears window do you see artifacts left on the screen?

I am asking these questions in the context of compiz.

---

### Post by hasinasi on 2008-09-17
> **shrndegruv said:**
> if you move the glxgears window do you see artifacts left on the screen?

I am asking these questions in the context of compiz.

I do not see any artifacts. Looks ok to me. However, I do not have compiz installed. Currently, I have other problems... (touchpad, wifi...)

---

### Post by hasinasi on 2008-09-17
Oh, another thing I noticed is that CPU frequency changing is not reliable. In some cases I saw it stuck at 800 MHz in my P8600 (2.4 GHz). 

I remember that being the case in Ubuntu 8.10-a5 at some point. After rebooting it would go up to the full 2.4 GHz. 

Right now, I am in kubuntu 8.04.1, and I am stuck at 800 MHz, even under full CPU load. I played with the Power manager settings (Performance/Powersafe/Dynamic), but no effect so far. Or is it possible that simply the reading is wrong?

Does anyone else have experience with this issue?
--hasi

---

### Post by hasinasi on 2008-09-17
Oh, one more thing:
For the (aka CPU frequency scaling or similar), it may also be important which power supply is used. Dell offer 65W and 90W models for the E6400/6500. The peak power usage of these systems (while charging the battery) is around 70W. I am currently using one of my 65W bricks. I am unsure whether and how that would affect the CPU policy. 

I am positive, however, that I already saw the CPU go up to the full 2.4 GHz using the 65W supply under ubuntu 8.10-a5.

---

### Post by jfluhmann on 2008-09-23
> **hasinasi said:**
> I am using (k)ubuntu on the new Latitude E6400 (all 32 bit versions). 

Here are some of my observations: 
[LIST]
[*]...snip...
[*]**8.10-alpha5 Live CD works**. **Graphics card (4500MHD), ethernet, and wireless recognized out of the box. Webcam is recognized**. Skype phone and video calls work. In the Kubuntu flavor (KDE 4.1.1, there are keyboard/mouse issues that make it pretty unusable. Ubuntu is fine 
[*]...snip...
[/LIST]

Another thing to note is that the **alpha6** release *(current)* could potentially break your network hardware, requiring replacement -- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555")

My new E6500 came in today and I was about to download the CD image and test it out, but now I think I'll wait a little while.

---

### Post by shrndegruv on 2008-09-24
ok I got my e6400 with nvidia graphics and performance is much better.  

I have a problem with suspend to ram -- when I tell it to suspend it does so then immediately wakes up again -- has anyone seen this?  I think it is an nvidia problem as my e6400 with intel graphics did not do that.

---

### Post by theburningor on 2008-09-25
I have the same problem with my e6500.  I tried running the kernel with acpi=off (add that to the really long line in /boot/grub/menu.lst) but that was even worse for supporting power saving modes.  I also have the problem where when I close the lid it will generally keep the display off, even though the keyboard backlight is still on.

---

### Post by numberCruncher91144 on 2008-10-23
Hello everyone.

I just want to put this out as a data point.  I have a shiny new Dell E6500 with an intel wifi link 5300 wireless card and a NVIDIA Quadro NVS 160M graphics card.

I am successfully dual-booting vista and ubuntu.  Everything in ubuntu is working (wireless was a bit of a trick, see the 6th page of [this thread]("http://ubuntuforums.org/showthread.php?t=906865")).  I didn't have any trouble getting the proprietary drivers working for the NVIDIA graphics card.

If you plan on ordering this laptop, be advised that the 9 and 12 cell battery packs stick out the back of the laptop.  The smaller batteries don't.  I currently have a 6 cell and a 9 cell.

Other than spending a few hours trying to get the wireless card working, it wasn't too bad getting ubuntu up and running.  So far this appears to be a great laptop.

---

### Post by AncientPC on 2008-10-26
> **numberCruncher91144 said:**
> If you plan on ordering this laptop, be advised that the 9 and 12 cell battery packs stick out the back of the laptop.  The smaller batteries don't.  I currently have a 6 cell and a 9 cell.

The 12 cell battery actually is a thin battery back that goes on the bottom of your laptop.

I bought an E6500 with Intel 4500MHD and Dell Wireless 1397 802.11b/g.  I successfully dual boot using Ubuntu v8.04.1.

glxgears gives me ~1000 fps.

Almost everything works from a fresh installation except two nagging issues for me:

1) The (scrolling) middle mouse button for the pointing stick doesn't work.

2) Despite the decent glxgears score, running Compiz lags my computer.  For example, whenever typing into Firefox's address bar I have to wait for the screen to catch up to my typing.  By comparison, my other Dell laptop has a discrete Radeon 7000 with lower glxgears results but no screen lag.

---

### Post by rasmus91 on 2008-10-29
Well...

I own a Latitude E6400. my wireless is a Intel(R) WiFi 5100 AGN, and my graphics are: Intel(R) GMA 4500 MHD with 128 mb ram, and 1.4GB of shared ram.

I intrepid Ibex Wireless runs fine. But my FPS while doing glxgears are only 300... I'm still searching for a solution to this problem... but so far nothing has turned up.

i got 4 GB of 667MHz of ram, and a Intel(R) Centrino(TM)2 2.26 2.27 GHz duo core processor. everything but the graphics are fantastic, so if you need a Dell latitude this one is surely recommendable. I Just still need some better driver for the graphic card. but i guess I'll get it sometime...

(btw i dual boot with Vista. I'm more or less Leasing this from the place i educate, and they recommend us to keep Vista... i have no idea why :S 
Dual booting works fine. i just use vista so rarely...)

---

### Post by AncientPC on 2008-10-29
> **rasmus91 said:**
> I own a Latitude E6400. my wireless is a Intel(R) WiFi 5100 AGN, and my graphics are: Intel(R) GMA 4500 MHD with 128 mb ram, and 1.4GB of shared ram.

I intrepid Ibex Wireless runs fine. But my FPS while doing glxgears are only 300... I'm still searching for a solution to this problem... but so far nothing has turned up.

i got 4 GB of 667MHz of ram, and a Intel(R) Centrino(TM)2 2.26 2.27 GHz duo core processor. everything but the graphics are fantastic, so if you need a Dell latitude this one is surely recommendable. I Just still need some better driver for the graphic card. but i guess I'll get it sometime...

(btw i dual boot with Vista. I'm more or less Leasing this from the place i educate, and they recommend us to keep Vista... i have no idea why :S 
Dual booting works fine. i just use vista so rarely...)

BTW the 4500MHD doesn't have any built-on RAM, only shared RAM.

I'm running the same config / RAM, but I can get ~1000fps for glxgears.  Did you install Ubuntu 8.04 or 8.04.1?

---

### Post by shrndegruv on 2008-10-29
AncientPC

do you have trouble running abiword (or openoffice) in a composited environment?  I returned my e6400 and got one with nvidia because typing in abiword with compiz running caused the cpu to max out ...

---

### Post by jlambeth1 on 2008-11-03
I just got my E6500 and cannot burn a DVD using brasero.  I am using Intrepid Ibex.  I tried to make a copy of a DVD with K9copy and everything went smoothly until I got to the burn process.  It said it burned for around 30 seconds and then was finished.  Of course there was no data on the disc.  I then took random video files and tried to burn them to a dvd using Brasero and got the same result.  I have different brands of DVD's and still no luck.  I am dual booting with Vista and I had to install a driver from Dell to get the SATA burner to burn properly in Vista.  Anyone else having these issues?

---

### Post by AncientPC on 2008-11-12
> **shrndegruv said:**
> AncientPC

do you have trouble running abiword (or openoffice) in a composited environment?  I returned my e6400 and got one with nvidia because typing in abiword with compiz running caused the cpu to max out ...
No, I have no trouble running Abiword within a composited environment.  It doesn't stress my CPU at all . . .

Update: [Title bars are missing]("http://ubuntuforums.org/showthread.php?t=975596") from windows when running in Compiz, and I'm getting [screen tearing]("http://ubuntuforums.org/showthread.php?p=6164795") in both Metacity and Compiz (but it occurs much more often in Compiz).

Does anybody know how to get the middle scroll button working within Ubuntu 8.10?

---

### Post by AncientPC on 2008-11-12
filler

---

### Post by Skipster on 2008-11-23
I have a e6500 intel 5300 wireless Verizon 5720 WWAN NVIDIA Quadro NVS 160M Web Cam...

First I Installed 64Bit Ibex, only issue that I had was with the Cisco VPN Client...  Couldn't get it to run properly.

I backed off the Ibex 32bit and haven't looked back...  every thing worked OOB I did have to activate the broadband card on a windoze box, a little irritating...  other than that I every thing works with no tweaking building or hacking.   Only thing I've fiddled with is the GPS on the 5720 card, haven't got it working but not really all that concerned either.

glxgears reports ~2000 fps.

---

### Post by shrndegruv on 2008-11-23
what about the finger print reader and the web cam?

---

### Post by Skipster on 2008-11-24
Web cam worked OOB with ekiga and Xawtv, didn't get the finger print reader...

---

### Post by jokerfox on 2008-11-25
*Do I have to download drivers or linux will pick it up?how does it work?
*you said 8.04 64 bit worked on yours,how aobut 32bit? & also 8.10?

note:im newcomer to linux

Thanks

---

### Post by Donalb on 2008-11-30
I got an e6400, 2.2gh, 4gb RAM, with Integrated Intel graphics this week. I'd used 7.10 & 8.04 on my 5 yo D400. I had wanted to try Intrepid but my old laptop was very underpowered so with the new one I did a fresh install of Intrepid, dual booting with Vista business.

I had been tempted to blow away Vista esp. after spending a day setting up FW & AV etc and dealing with the new UAC (I'd never used Vista before), but due to some current Intrepid issues (see below) I'll keep it. (Plus I use an old Rio Karma and could never get Rio to work in Amarok, so using an whole OS just to load the occasional bit of music...overkill extreme). After 9 months almost exclusively on Ubuntu Windows was painful.

I haven't tried bluetooth or wireless yet, so can't comment there.

Compiz runs great, but the integrated graphics won't support compiz on 2 screens. My old docking station of course, doesn't fit the new laptop just I just plugged the ext screen intot the vga port. However I can't then disable the laptop screen, Fn+F8 don't seem to work in 'buntu, so i'm running 2 screen, which i don't particularly want. Oh the irony, since we've all heard so often that's it's difficult to get 2 dual monitor system working in 'buntu. That's a problem I'll need to solve.

Biggest problem at the moment is sound, i.e. none.(faint crackling sound)
I did get shut-down problems, hanging for up to 15 mins on ALSA shutdown, known bug, 274995 in Launchpad. The first fix (shutting down eth01) worked for me, and after finishing writing this, I'll reboot having enabled the Intrepid-Proposed repositories and the main update/fix and see if that does anything for the sound.

Another thing I've noticed (and seen mentioned elsewhere) on Conky, is that the CPU often seems to "stick" at 800MHz. If I didn't have conky running though I'd never know this.

All in all I'm still reasonably happy. After having such an old system the e6400 on Intrepid is blazingly fast. OOo shoots open! Transmission & Firefox can both co-exist without maxing out the CPU (currently 5 to 15% with Transmission running & 10 tabs open in Firefox, with tons of extensions loaded), which used to happen all the time on Hardy, often requiring a restart.

I love the new Nautilus particularly, since I used to use Nautilus PLUS Krusader for dual pane. Nautilus isn't quite there (would love dual-pane and better Properties for various media) yet but way way better, and particularly excellent if you use a lot of external media which I do, having 4 various external HDDs and 2 Iomega Rev drives. 

Touchpad works fine. So does LCD brightness adjustment.

So synopsis, still to do:

Troubleshoot sound problem,
troubleshoot monitor setup
test wireless & bluetooth & webcam (I've read good reports elsewhere)

A big deal for me to test is HSPDA modem compatibility which I'll do later today. I couldn't get my gf's HSDPA working on Hardy. I'd love if it worked out-of-box on Intrepid.

By troubleshoot of course, I mean read everything until I find some instructions by someone who knows what they're talking about that an idiot like me can follow and apply them. Despite the above I've been on Ubuntu for about 9 months, and not an expert. 

I'll report back on anything of interest to anyone else using/planning an e6400.

Regards
Donal
Ireland

---

### Post by Donalb on 2008-11-30
Well the Intrepid-Proposed update restart does fix a PulseAudio issue of which the restart hang was a symptom, according to the Launchpad discussion ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)). Also my sound is now working! Wahoo.

However I've also noticed that my startup is now verbose rather than usplash. Not that this is a problem as such.

Hope to test HSDPA this afternoon.

regards
Donal
Ireland

---

### Post by Donalb on 2008-11-30
HSDPA Huawei E220 modem, connecting to Three ireland, works out of the box! This is a biggie for those who are in broadband free zones or who travel. I need it when visiting my elderly mother who doesn't have broadband.


 I couldn't get HSDPA working on my old laptop in Hardy so I'm delighted. All I had to do was select the provider (Three) and connect.

This makes the Intrepid upgrade incredibly valuable to me.

Regards
Donal
Ireland

---

### Post by shrndegruv on 2008-11-30
i urge anyone with this laptop to monitor their load cycle count.  I have to do a 

sudo hdparm -B 254 /dev/sda

to avoid about 10 increments a minute.  

when i upgraded to intrepid sound stopped working (intel sound).  A few days after i upgraded some more updates made sound work again.  so what i am saying is I have no problem with sound now, only a slight hiccup when i upgraded to intrepid, which was fixed.

---

### Post by ja4 on 2008-12-03
Don't buy only the 65W adapter!


Unfortunately, I opted for the slim 65W travel adapter for use at home since I already had a 90W one at work.  

Anytime the 65W adapter is plugged in, the BIOS locks the cpu to 800 MHz (I have the Core 2 Duo at 2.54 GHz in the E6400).

---

### Post by Donalb on 2008-12-03
That's very interesting. I got the slim AC/DC adapter, 90W I think, (VxI? if I remember correctly , 19.5Vx4.624A).
I didn't have an option as I bought a Dell Outlet Latitude e6400 and saved about €400 euro as a consequence. I did notice in Conky that CPU is running 800mhz most of the time. However I notice also when I'm opening a new app the cycles will go to 2.26ghz and CPU is fine. I currently have open: Ffox with 7 tabs, and tons of extensions, Thunderbird, Banshee, Transmission, Nautilus (with a 10gb file copy) and CPU is fine at around 25 to 35%, mostly the file copy, while also showing 800mhz.
I had a docking station for my old d400, of course that now no longer fits...just like bloody Nokia phone adaptors. So I use the old adaptor and kept the slim one in my bag to save climbing under the desk all the time. Just checked...the old adaptor is a 90W... ....


BTW, for anyone considering buying Dell, I recommend trying the Dell Outlet route and being patient while you find what you want. The Dell site (here in Ireland) only lists consumer options on the Outlet and business (Vostro, 'Plex & Latitude) outlet systems are actually handled through a 3rd party vendor on eBay UK. 
My system in Ireland would be over €1200 (with 3 year next day warranty). I got it for €840 (inc. postage from UK). Service Tag is registered with Dell. I received the system 2 days after ordering (faster than Dell) and when I initially got the wrong size HDD, I received the correct replacement within another 2 days. 

Regards

---

### Post by el mariachi on 2009-06-22
I'm using a E5400 and the fan noise is really boring...has anyone figured this one out?

---

### Post by Captain_Falafel on 2009-06-28
> **el mariachi said:**
> I'm using a E5400 and the fan noise is really boring...has anyone figured this one out?

I've got an E6400.. and the fan noise automatically goes on full blast for a good hour or so.. I brought up conky and the CPUs run at 800 MHz most of the time, and for an instant, jump up to the 2.4 Ghz of which the processor is supposed to be. And when I open up the System Monitor, one CPU is running at 100% all the time, even when I'm idling.. and sometimes, when I'm idling, both CPUs are at 100%.. What's wrong.. the cooling fan is soo obnoxious

is anyone else having this problem? all my experience with Dell has been awful.

---

### Post by el mariachi on 2009-06-28
yeah me

---

### Post by Captain_Falafel on 2009-06-28
I've been reading up on this in a Dell forum, and of what I gather, I don't think it is an software problem but a hardware problem.

any other people having these problems?

here's the link
[http://en.community.dell.com/forums/p/19247293/19502938.aspx?PageIndex=1](http://en.community.dell.com/forums/p/19247293/19502938.aspx?PageIndex=1)

---

