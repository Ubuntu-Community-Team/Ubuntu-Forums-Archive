---
title: "Ibex / New X.org + Intel 945GM = problems"
date: 2008-11-03
forum: Hardware
---

### Post by SveinT on 2008-11-03
I recently installed a fresh install of Ibex on my laptop. Previously I used Hardy which worked very well. I have two problems related to video.

The first one is that I can not use any external monitor anymore. With Hardy I could use Fn+F3 to change to external screen or dual screen. Now this combination does nothing. Using screen resolution dialog in the settings menu it detects both screens + an unknown one. Setting the settings here and restarting x in order to make the settings apply does nothing (no signal to TV) except setting the virtual desktop resolution completely screwed up so I have to reset xorg.conf. Any ideas? 

The other problem I have is that if I change resolution with same app with no external monitor connected I just get a black screen afterwards, no response whatsoever and I have to do a cold restart.

Seeing as the intel drivers are open source I assumed the support would be great, but this is just a major disappointment seeing as things work perfectly in windows...the 945GM chipset is very common so it's amazing that not more testing has been done before relasing the new xorg version..? Or am I the only one with these problems?

---

### Post by SveinT on 2008-11-03
bump

---

### Post by styyle14 on 2008-11-04
I am having the exact same problem.  The new version of Xorg does not have the i810 driver installed anymore because it is supposed to have been replaced by the driver "intel".  In my Xorg.conf file, the driver is automatically set to "Vesa".  If set to "i810", like in Hardy, it crashes. with the output: "(EE) No devices detected.", where (EE) means "error".  If set to "intel", like it should be with the new version of Xorg, the login screen appears. After logging in, the screen turns black and takes me back to the login screen.  I have tried installing the package "xserver-xorg-video-i810" yet this seems to do nothing significant because the same problem continues.

I can post xorg.conf (although it is only the default configuration) and the error log for xorg if anyone needs it.

I got information from [https://wiki.ubuntu.com/X/Drivers#-intel%20video%20driver]("https://wiki.ubuntu.com/X/Drivers#-intel%20video%20driver")
and
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/282609]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/282609")
yet nothing seems to work.

---

### Post by SveinT on 2008-11-09
bump :(

---

### Post by popk1d on 2008-11-10
Me too.
Toshiba Satellite U-200, Intrepid 8.10, 2.6.27-7
I'm a newbie, so I didn't configure anything
Exactly the same: ran perfectly under 8.04 with intel driver, now bailing out to VESA exactly as described above. Bang go all the nice effects.
Willing to post anything that would help.

---

### Post by wgrant on 2008-11-10
Did you all upgrade from 8.04? Does the 8.10 live CD work?

---

### Post by styyle14 on 2008-11-10
As it turns out, if you change your xorg.conf to use the "intel" driver, you must set ubuntu "Visual Effects" in System->Preferences->Appearance to "none", or if that doesn't work, completely remove "compiz" and "compiz-core". 

The advantage to this is that you get 3D graphics acceleration for programs like openarena, where Vesa does not work well.

I am not sure yet as to whether this is an error related to the compiz package or the xorg package, although no such error occurs with the i810 driver.

---

### Post by styyle14 on 2008-11-10
In response to "wgrant", no, I did a fresh install of the 8.10 Ubuntu off of the CD, while others have reported the same symptoms while using the upgrade feature.  It is quite possible that this error was present in 8.04, yet in 8.04 the driver i810 was available which did not have these errors.

---

### Post by popk1d on 2008-11-10
wgrant: I updated from 8.04 - I can try the 8.10 Live CD later this week, but don't have the bandwidth now. Thanks for responding.

Compiz Fusion used to work perfectly before upgrading.

---

### Post by styyle14 on 2008-11-11
Don't bother with reinstalling, the medium used to install 8.10 is irrelevant.  The source of the problem is almost definitely in the "intel" driver for the new Xorg.  This driver, although theoretically superior to "i810", on several cards is quite inferior.  Due to its theoretical superiority, it was removed from Xorg 7.4 as "Obsolete" even though it functioned perfectly on numerous graphics cards where "intel" fails to.  The package "xserver-xorg-video-i810" used to be the package used with the "i810" driver, yet in the Intrepid install it is now just a package meant for upgrading, with no actual function.  If the Ubuntu developers could re-add the "i810" driver (or at least some simple form of re-adding it short of recompiling and installing an earlier version of Xorg), this problem could be alleviated until a more mature version of "intel" is released that has better support for all the graphics cards it covers.

---

### Post by wgrant on 2008-11-11
-intel dropped support for some chips before i855, but nothing later. -i810 doesn't work with the new xserver. You should file bugs to get -intel fixed, rather than trying to use -i810!

-intel works much, much better on most chips.

---

### Post by styyle14 on 2008-11-11
I am aware of that, and I will post bugs on launchpad related to the problem.  The actuality of the situation is that it will take months to get it fixed, if it ever gets fixed at all.  A working driver, i810, is available, yet not included simply because it is obsolete.  If that driver could be re-enabled in an update (even if it is not automatically selected but able to be chosen manually) it will at least provide some support for people who do not have it right now until the "intel" driver is fixed.

---

### Post by wgrant on 2008-11-11
As I said, i810 **doesn't** work. It would need significant porting work to be made usable with the new X server.

---

### Post by styyle14 on 2008-11-11
Oh, my apologies, I was under the impression you simply meant it did not work because it was not included in Xorg 7.4.  If it is in a different format than the new Xserver allows, then I guess the only solution will be to wait for a fix to the "intel" driver. Thanks for all your help wgrant.

---

### Post by popk1d on 2008-11-12
-er, so what I learn from this was that upgrading to 8.10 was a terrible mistake and I'll have to wait until the 'intel' driver is fixed. In the meanwhile, the 'vesa' driver will have to do?

Did I get this right?

---

### Post by wgrant on 2008-11-12
It means that you should check for a bug so that you can be sure we know about your particular issue... we don't magically discover these things without people telling us.

---

### Post by paulblais86 on 2008-11-12
Same problem here:

I have an Acer Aspire 9410Z with an integrated intel 945GM video card.

Problems:

Immediately after updating to Ibex, I got the white screen of death after logon screen.

After repairing the issue, by using grub's recovery mode (2 times), I still get some annoying problems:

When a windows open, the image is distorted for a second.

When I plug the power cord, white rectangle appears on the screen for a second.

Another annoying problem is that I had ooo.org 3 installed on Hardy, but it was erased and and replaced by version 2.4.

Thanks for making such a beautiful system, keep up the good work! (and, of course, thanks for fixing the bugs when someone find one)

Cheers,

Paul

---

### Post by popk1d on 2008-11-13
"It means that you should check for a bug so that you can be sure we know about your particular issue... we don't magically discover these things without people telling us."

sorry if I came off as having an attitude there - I was trying to make sure I understood the story right. Thanks for your help. Distinguishing between bugs and problems of my own making is currently tricky.

---

### Post by Potters Son on 2008-11-14
You guys seem to know what you're talking about... I've searched a lot of threads where people have Intel GM965 GPU's that aren't working correctly. As for me, I'm running an HP dv6985se laptop with an Intel Centrino 64 bit processor and the aforementioned graphics card. When I run displayconfig-gtk, the Graphics Card tab reports that I'm running the VESA driver.
Yet I've since changed xorg.conf so the Device section reads,
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

```
I hope I put the Driver line in the correct section.

Still stranger, xorg is still the most processor-intensive process, taking 15-20% of my CPU. Compiz lags with the Tab Switcher, and Scribus is so laggy it isn't worth using.

I wanted to try downloading and compiling the open source intel driver myself, but I couldn't figure out how. (I think I got hung up on packages)

---

### Post by paulblais86 on 2008-11-16
New issue with the Aspire 9410:

Activate the Bicubic filter in compiz, Every single window appears black 
(and it is a real pain in the "chocolate starfish" to get it back to normal)

&

The computer becomes very hot when I run graphics-heavy applications. That is new to Ibex...

Cheers

Paul

---

### Post by bonfire89 on 2008-11-17
I have this problem as well. :(

---

### Post by Alexander the Pretty Good on 2008-11-27
bump

---

### Post by tkbremnes on 2008-11-27
Any news of this? I miss using Ubuntu as my primary OS.

---

### Post by dotdot on 2008-11-27
I‘ve just installed the latest on my dell x20 - it‘s getting that white screen of nothingness - what happened to progress.

This is absolutely a retro step.

I am so dissappointed.

WHAT IS THE FIX.. how is your average person going to fix this eh ?

This is plainly ridiculous.

---

### Post by angus.hendrick on 2008-12-02
I upgraded to Intrepid Ibex on a Toshiba Satellite P105-S6147 and ran into a similar set of problems.  This machine also has the subject Intel chip set, and a native 1280x800 LCD display.  I am using the xserver-xorg-video-intel drivers.  xorg.conf is unmodified.  

I think the problem is related to a problem detection of the display.  xrandr gives the wrong display:

```

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1440 x 1440
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1360x768+0+0 (normal left inverted right x axis y axis) 367mm x 230mm
   1440x900       60.0 +
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```

The other notable issue with this computer is that the sound is screwed up--it sounds distorted as from too much gain.  I had this problem before when I was running Gutsy, and some kind soul pointed me at a then alpha version of the Hardy kernel as the solution and it worked like a charm.  I can't find the history on this in the forum archives, but it has to be in there somewhere.

Any help on these issues is appreciated.

sudo lspci -vvmm gives:
```
Slot:	00:00.0
Class:	Host bridge
Vendor:	Intel Corporation
Device:	Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	03

Slot:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	03

Slot:	00:02.1
Class:	Display controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	03

Slot:	00:1b.0
Class:	Audio device
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) High Definition Audio Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1c.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) PCI Express Port 1
Rev:	02

Slot:	00:1c.1
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) PCI Express Port 2
Rev:	02

Slot:	00:1c.2
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) PCI Express Port 3
Rev:	02

Slot:	00:1d.0
Class:	USB Controller
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) USB UHCI Controller #1
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1d.1
Class:	USB Controller
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) USB UHCI Controller #2
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1d.2
Class:	USB Controller
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) USB UHCI Controller #3
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1d.3
Class:	USB Controller
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) USB UHCI Controller #4
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1d.7
Class:	USB Controller
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) USB2 EHCI Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02
ProgIf:	20

Slot:	00:1e.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	82801 Mobile PCI Bridge
Rev:	e2
ProgIf:	01

Slot:	00:1f.0
Class:	ISA bridge
Vendor:	Intel Corporation
Device:	82801GBM (ICH7-M) LPC Interface Bridge
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	00:1f.2
Class:	IDE interface
Vendor:	Intel Corporation
Device:	82801GBM/GHM (ICH7 Family) SATA IDE Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02
ProgIf:	80

Slot:	00:1f.3
Class:	SMBus
Vendor:	Intel Corporation
Device:	82801G (ICH7 Family) SMBus Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

Slot:	03:00.0
Class:	Ethernet controller
Vendor:	Atheros Communications Inc.
Device:	AR242x 802.11abg Wireless PCI Express Adapter
SVendor:	Askey Computer Corp.
SDevice:	Device 7106
Rev:	01

Slot:	0a:04.0
Class:	CardBus bridge
Vendor:	Texas Instruments
Device:	PCIxx12 Cardbus Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31

Slot:	0a:04.1
Class:	FireWire (IEEE 1394)
Vendor:	Texas Instruments
Device:	PCIxx12 OHCI Compliant IEEE 1394 Host Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
ProgIf:	10

Slot:	0a:04.2
Class:	Mass storage controller
Vendor:	Texas Instruments
Device:	5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31

Slot:	0a:04.3
Class:	SD Host controller
Vendor:	Texas Instruments
Device:	PCIxx12 SDA Standard Compliant SD Host Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
ProgIf:	01

Slot:	0a:08.0
Class:	Ethernet controller
Vendor:	Intel Corporation
Device:	PRO/100 VE Network Connection
SVendor:	Toshiba America Info Systems
SDevice:	Device ff31
Rev:	02

```

---

### Post by SveinT on 2008-12-02
> The other notable issue with this computer is that the sound is screwed up--it sounds distorted as from too much gain.  I had this problem before when I was running Gutsy, and some kind soul pointed me at a then alpha version of the Hardy kernel as the solution and it worked like a charm.  I can't find the history on this in the forum archives, but it has to be in there somewhere.

Any help on these issues is appreciated.


I had the same problem. I solved it by changing the mixer to control ALSA and then reducing the PCM volume substantially.

See here for more info: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/285866](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/285866)

Please don't hijack this thread though, so if you have more questions about this issue ask me directly or start a new thread.

---

### Post by angus.hendrick on 2008-12-03
Has anyone tried building the drivers from [here]("http://intellinuxgraphics.org/documentation.html"), or are those the ones currently in the intel xorg driver?

---

### Post by destructaball on 2009-01-03
Had the same problem and although this seems a little simple try typing in the teminal:

sudo dpkg-reconfigure xserver-xorg

pressing enter to go through it without changing anything then log out and log back in again. Worked for me. Good luck

---

### Post by bonfire89 on 2009-01-03
Anyone know if this has been fixed yet? I got some time these holidays, I might go back to 8.04.

---

### Post by densou on 2009-01-04
> **angus.hendrick said:**
> Has anyone tried building the drivers from [here]("http://intellinuxgraphics.org/documentation.html"), or are those the ones currently in the intel xorg driver?

many times but stable backports are avaiable on [https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)
simply, just add these lines
deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
to your /etc/apt/sources.list


I have a GMA950 as well (945gz chipset)
The xorg.conf which I used with Hardy, setting manually my default resolution (outdated CRT). Not to try for not i945 (and LCD) users!
[http://spazioinwind.libero.it/densou/xorg.conf.ibex](http://spazioinwind.libero.it/densou/xorg.conf.ibex)
{right-click & save target as .... some browsers couldn't display the text :( }


The same file w/o "i945" string, it should work with every Intel video card (still avoid it, LCD/laptop owners!
[http://spazioinwind.libero.it/densou/xorg.conf](http://spazioinwind.libero.it/densou/xorg.conf)


And last, the generic one I'm using with Intrepid
[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

---

### Post by Acerdestroyer on 2009-02-06
I got rid of the Xorg drivers all together, I've found that a app/driver called 915resolution solved all of my problems but created another,3-d rendering is *slow*. So far it just effects World of Warcraft and some screen savers(not really worried about either my wow trial ends in like 2 days and who watches their screen saver?).

---

### Post by densou on 2009-02-14
> **Acerdestroyer said:**
> 3-d rendering is *slow*

no doubt about it .... Intrepid and OpenSuse 11.1 uses a legacy Mesa build without matching the DRI within included kernel (they should have the same date or nearly), latest Fedora runs out-the-box a Mesa 7.3-devel so users can upgrade it to the stable release. If you check old post, you'd find some post as 'I got more FPS with Fedora on gaming than other distros. Why?'

It's the truth, I made few benchmarks as well (Fedora vs Ubuntu vs openSuse), anyway I don't know much about latest Mandriva release.

---

