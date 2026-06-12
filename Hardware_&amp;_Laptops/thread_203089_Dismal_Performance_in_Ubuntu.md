---
title: "Dismal Performance in Ubuntu"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by hbweb500 on 2006-06-24
I have been trying to switch to Ubuntu Dapper over the past month, but the poor performance I get keeps sending me to Windows. 

Some background on my system: 2.4 GHz Celeron w/ 768mb RAM, 64mb GeForce4 MX4000 PCI card from NVIDIA, Intel Integrated i845 graphics card. I have a dual monitor setup.

Basically, the graphics are slow, but Im not so sure its because of the graphics drivers. Whenever I scroll in Firefox, SwiftFox, or Nautilus (basically anywhere) the scrolling graphics are choppy. Switching between tabs in Firefox yields noticeable delays. Moving windows is not fluid either, and leaves trails.

My main gripe is just switching between tabs and programs and such. In Windows, I can switch between Firefox tabs lightning fast. I can minimize windows fluidly and rapidly. Not so in Gnome, or KDE.

What Ive tried: I have the most up-to-date linux NVIDIA drivers installed (Ive done so both by apt-get and compiling them myself). I have used both a 2.6.16 custom compiled kernel with the performace patch and a 2.6.15 stock Dapper kernel. I have tried switching to only the integrated card, but I get the same poor performance (worse that Windows). I have a minimalistic theme going on. I have tried using dual monitors and without dual monitors, with Xinerama, without... Ive tried KDE as well. I really like Gnome, Id like to stay with it.

Ive tried everything in this thread: [http://ubuntuforums.org/showthread.php?t=189192&highlight=performance](http://ubuntuforums.org/showthread.php?t=189192&highlight=performance)

Is this what Ubuntu is like? I think I should expect some pretty fast performance, my computer isnt that old. Please tell me if I should post any log files, etc...

And thanks for the help :-D 

Justin

---

### Post by aysiu on 2006-06-24
[QUOTE=hbweb500]
Is this what Ubuntu is like? I think I should expect some pretty fast performance, my computer isnt that old.[/QUOTE] Unfortunately, I can't help you with any of your other problems, but I can answer this question: No, that's not what Ubuntu is like. I wouldn't be using Ubuntu if it were like that. I don't think anyone would be.

I'm not sure what's wrong, though. Your computer has much better specs than mine does.

---

### Post by hbweb500 on 2006-06-24
Well, SUSE Linux runs fine on my laptop, which is equipped much less favorably. I think this must be some sort of conflict between either Linux (or, perhaps, just Ubuntu) and my desktop computer.

I am in the process of installing Ubuntu on my laptop, and I may try to install another Linux distro on my desktop to see if the problem is with Ubuntu or Linux in general.

EDIT: Ubuntu on my laptop works wonderfully. So, it must be my desktop computer mixing with Linux...

---

### Post by hbweb500 on 2006-06-25
I just installed an old version of Ubuntu from several years ago, and I get the same slowness. With it, I even get noticeable lag when making a selection on the desktop.

I think tomorrow I will pull out everything I have added on to my computer, reinstall Ubuntu and see whats up. Ill try to pinpoint any hardware conflicts...

---

### Post by dpicker on 2006-06-26
Dapper drake feels the same for me as well. The graphics are very choppy and there just seems to be a sluggish feeling with everything.

This is really frustrating because in contrast, breezy was fine. In fact breezy badger feels better running with vesa drivers than dapper drake does running with nvidia drivers.

My specs:

AMD Athlon 64 3200+ (2.01 GHz), 1gb ram (64mb given to onboard graphics) and Nvidia GeForce 6100.

---

### Post by hbweb500 on 2006-06-26
Well, I took out all of my PCI cards this morning, reinstalled, got the exact same result. With all of the PCI cards out I had my system as it was from the factory, plus 512mb RAM. 

I ran memtest this afternoon, no problems.

Im not giving up quite yet. I will try to see if there is a certain process that is slowing down the computer this evening. Maybe ACPI or something, I dunno.

Dpicker: Tell me if you get anywhere. Although our systems are pretty much opposite eachother, there may be something in software that is causing the slowdowns.

---

### Post by tseliot on 2006-06-26
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by hbweb500 on 2006-06-26
[QUOTE=tseliot]Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")[/QUOTE]

Done so. Plus, this isnt an Nvidia issue: I get terrible performance using my Integrated card too. I have the same integrated card in my laptop and the laptop works perfectly fine under Ubuntu.

---

### Post by tbdombrosky on 2006-06-27
[QUOTE=hbweb500]I have been trying to switch to Ubuntu Dapper over the past month, but the poor performance I get keeps sending me to Windows. 

Some background on my system: 2.4 GHz Celeron w/ 768mb RAM, 64mb GeForce4 MX4000 PCI card from NVIDIA, Intel Integrated i845 graphics card. I have a dual monitor setup.

Basically, the graphics are slow, but Im not so sure its because of the graphics drivers. Whenever I scroll in Firefox, SwiftFox, or Nautilus (basically anywhere) the scrolling graphics are choppy. Switching between tabs in Firefox yields noticeable delays. Moving windows is not fluid either, and leaves trails.

My main gripe is just switching between tabs and programs and such. In Windows, I can switch between Firefox tabs lightning fast. I can minimize windows fluidly and rapidly. Not so in Gnome, or KDE.

What Ive tried: I have the most up-to-date linux NVIDIA drivers installed (Ive done so both by apt-get and compiling them myself). I have used both a 2.6.16 custom compiled kernel with the performace patch and a 2.6.15 stock Dapper kernel. I have tried switching to only the integrated card, but I get the same poor performance (worse that Windows). I have a minimalistic theme going on. I have tried using dual monitors and without dual monitors, with Xinerama, without... Ive tried KDE as well. I really like Gnome, Id like to stay with it.

Ive tried everything in this thread: [http://ubuntuforums.org/showthread.php?t=189192&highlight=performance](http://ubuntuforums.org/showthread.php?t=189192&highlight=performance)

Is this what Ubuntu is like? I think I should expect some pretty fast performance, my computer isnt that old. Please tell me if I should post any log files, etc...

And thanks for the help :-D 

Justin[/QUOTE]

I had the EXACT same problem with a laptop I had.  No matter what I did, Dapper ran awfully slow.  The specs on that system are strikingly similar to yours (Celeron 2ghz, 768mb ram).  I attributed it to the slow Celeron because I had a P3 933mhz system that ran Dapper a whole lot faster.

---

### Post by 3rdalbum on 2006-06-27
Try typing "top" into the command line (without the quotes) and press Enter - that gives a list of the programs that are using the most amount of CPU time. This may help you track down your problem.

When I dist-upgraded, I noticed a significant slowdown; until I realised that Beagle was indexing my hard drive in the background, killed it and removed it from the startup items.

---

### Post by slimdog360 on 2006-06-27
this may seem stupid but are you sure you enabled the nVidia drivers? Though I'll admit it doesnt sound like a graphics driver problem.

---

### Post by hbweb500 on 2006-06-27
> **tbdombrosky]I had the EXACT same problem with a laptop I had.  No matter what I did, Dapper ran awfully slow.  The specs on that system are strikingly similar to yours (Celeron 2ghz, 768mb ram).  I attributed it to the slow Celeron because I had a P3 933mhz system that ran Dapper a whole lot faster.[/QUOTE]

My laptop has a Celeron chip (albeit a Celeron Mobile) and runs fine, although I dont doubt that the Celeron might have something to do with it.

[QUOTE=3rdalbum]Try typing "top" into the command line (without the quotes) and press Enter - that gives a list of the programs that are using the most amount of CPU time. This may help you track down your problem.

I dont see any glaring use of resources:

```
top - 09:31:58 up 12:03,  5 users,  load average: 0.57, 0.30, 0.11
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0% us,  6.0% sy,  0.0% ni, 82.1% id,  0.0% wa,  0.3% hi,  2.7% si
Mem:    767380k total,   761520k used,     5860k free,     3852k buffers
Swap:  1052248k total,    18908k used,  1033340k free,   543200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4380 root      16   0  150m  14m 7316 S  8.3  2.0  17:07.73 Xorg
 5127 universe  15   0 54844  16m 9820 S  3.3  2.2   1:02.71 gnome-terminal
 4902 universe  15   0 35896  14m  10m S  0.7  2.0   4:32.34 gnome-panel
 4904 universe  15   0 58948  15m  11m S  0.7  2.1   4:07.18 nautilus
24738 universe  16   0  2200 1096  856 R  0.7  0.1   0:00.08 top
 4896 universe  15   0 15148 9160 6396 S  0.3  1.2   0:17.49 metacity
 5396 universe  15   0  3820 1580 1232 S  0.3  0.2   1:06.52 wget
 5418 universe  15   0  3820 1584 1232 S  0.3  0.2   1:08.66 wget
 5440 universe  15   0  3824 1588 1232 S  0.3  0.2   1:08.91 wget
 6292 universe  16   0 42932  15m  10m S  0.3  2.1   0:03.61 gaim
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.52 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 kblockd/0

```

When I dist-upgraded, I noticed a significant slowdown said:**
> 

[QUOTE=slimdog360]this may seem stupid but are you sure you enabled the nVidia drivers? Though I'll admit it doesnt sound like a graphics driver problem.

Ive tried using the nvidia drivers, downloading and compiling once, and installing via apt once. Also, I get the same slowness with my integrated card.

Thanks to all who responded! I think we are on the right track...

---

### Post by hbweb500 on 2006-06-27
Update: Installing Fedora Core results in the same poor performance. Since it uses XFree86, I have now ruled out the Xserver, Gnome, Kde, and Ubuntu as causing the slowdown.

I also cut down on all running services to no avail.

Im wondering what I should try next...

---

### Post by slimdog360 on 2006-06-27
You can have the drivers installed but not enabled.You have already probably tried this but its worth a shot.

 I used synaptic to install the nvidia driver, but to get it working I had to type in the following. 
```
sudo nvidia-glx-config enable
```

---

### Post by 3rdalbum on 2006-06-28
I'm stumped. From the output of your top command, there's nothing that I can see that's causing a slowdown. BTW, what were you downloading at that time?

---

### Post by hbweb500 on 2006-06-28
[QUOTE=slimdog360]You can have the drivers installed but not enabled.You have already probably tried this but its worth a shot.

 I used synaptic to install the nvidia driver, but to get it working I had to type in the following. 
```
sudo nvidia-glx-config enable
```[/QUOTE]

Yep, did that, but thanks anyways.

[QUOTE=3rdalbum]I'm stumped. From the output of your top command, there's nothing that I can see that's causing a slowdown. BTW, what were you downloading at that time?[/QUOTE]

If I remember correctly, I was downloading Fedora Core 6 Testing iso's.

---

### Post by dicaguido on 2006-06-28
Hi! I'm getting the same damn problem!
top:
top - 20:07:14 up 34 min,  2 users,  load average: 0.11, 0.41, 0.44
Tasks:  83 total,   1 running,  82 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3% us,  0.0% sy,  0.0% ni, 88.0% id,  0.0% wa,  0.3% hi,  2.3% si
Mem:    449268k total,   438128k used,    11140k free,    27740k buffers
Swap:  1285160k total,    17964k used,  1267196k free,   126872k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4158 root      15   0 66644  41m 7720 S  7.7  9.5   7:40.90 Xorg
 5659 guido     15   0 64952  14m 9128 S  1.3  3.2   0:01.93 gnome-terminal
 4806 guido     15   0  156m  61m  21m S  0.3 14.0   1:19.93 firefox-bin
    1 root      16   0  1568  532  460 S  0.0  0.1   0:01.29 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  113 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.05 kswapd0
  700 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kseriod
 1762 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid-work-0

If it can be useful xorg.conf...

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
   FontPath   "/usr/share/X11/fonts/misc"
   FontPath   "/usr/share/X11/fonts/cyrillic"
   FontPath   "/usr/share/X11/fonts/100dpi/:unscaled"
   FontPath   "/usr/share/X11/fonts/75dpi/:unscaled"
   FontPath   "/usr/share/X11/fonts/Type1"
   FontPath   "/usr/share/X11/fonts/100dpi"
   FontPath   "/usr/share/X11/fonts/75dpi"
   # path to defoma fonts
   FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
   Load   "i2c"
   Load   "bitmap"
   Load   "ddc"
   Load   "dri"
   Load   "extmod"
   Load   "freetype"
   Load   "glx"
   Load   "int10"
   Load   "type1"
   Load   "vbe"
EndSection

Section "InputDevice"
   Identifier   "Generic Keyboard"
   Driver      "kbd"
   Option      "CoreKeyboard"
   Option      "XkbRules"   "xorg"
   Option      "XkbModel"   "pc105"
   Option      "XkbLayout"   "it"
EndSection

Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "mouse"
   Option      "CorePointer"
   Option      "Device"      "/dev/input/mice"
   Option      "Protocol"      "ExplorerPS/2"
   Option      "ZAxisMapping"      "4 5"
   Option      "Emulate3Buttons"   "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
   Identifier   "Generic Video Card"
   Driver      "vesa"
   BusID      "PCI:1:0:0"
EndSection

Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   HorizSync   28-51
   VertRefresh   43-60
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Generic Video Card"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      Depth      1
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      4
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      8
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      15
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      16
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth      24
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen      "Default Screen"
   InputDevice   "Generic Keyboard"
   InputDevice   "Configured Mouse"
   InputDevice     "stylus" "SendCoreEvents"
   InputDevice     "cursor" "SendCoreEvents"
   InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
   Mode   0666
EndSection

I use laptop acer aspire with: intel m 350 (1.5GHz 400MHz FSB 1MB L2 cache with  sis monitor.
Firefox is REALLY CHOPPY (scrolling in all applications IS, vertical scrolling), damn slow graphics

---

### Post by hbweb500 on 2006-06-28
Well, I can solve your problem at least.

```
Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection
```

See the "vesa" part? You need to switch that to a driver for your card. If you have integrated graphics, it could be something like "i810". If you have an Nvidia or ATI card in the laptop, then you need to install the drivers and change that line.

The vesa driver is just a generic driver designed to work on most any hardware, so it is by definition slow. Im getting slow performance after changing the driver; you should get much faster performance.

---

### Post by hbweb500 on 2006-06-29
Update: I installed Debian with a 2.4 kernel and got the same slowdown, so my hunch was incorrect...

---

### Post by Indifferent on 2006-06-29
I noticed you said you had removed all of your PCI cards and that you had returned it to the factory shipped state thus you would be using the onboard graphics controller. When the PCI graphics card is in are you disabling the onboard graphics controller in your BIOS? If this is a dumb question, I apologize!

---

### Post by hbweb500 on 2006-06-29
[QUOTE=Indifferent]I noticed you said you had removed all of your PCI cards and that you had returned it to the factory shipped state thus you would be using the onboard graphics controller. When the PCI graphics card is in are you disabling the onboard graphics controller in your BIOS? If this is a dumb question, I apologize![/QUOTE]

No, not a stupid question... at this point all questions are valuable.

I have a DELL, so I can select Auto or Integrated for my video cards. Selecting Auto initializes my Nvidia card, and thats what I use. Neither selection helps though...

Thanks, though, for the try.

---

### Post by dicaguido on 2006-06-30
I resolved the problem by switching to sis drivers (not official, they don't support).
Thank you very very much!

---

### Post by hbweb500 on 2006-06-30
Ive been running out of things to try lately, and so I thought "this problem is a lot like there is a shortage of RAM." I have 768 MB of RAM, though, so this couldnt be it. "free -m" shows that all of it is recognized.

```

free -m
                 total       used       free     shared    buffers     cached
Mem:           749        262        487          0          6        145
-/+ buffers/cache:        109        639
Swap:         1027          0       1027

```

One thing I am wondering is: what are the buffers? "free -m" on my laptop shows that I have 54 buffers (on 512 mb ram), and I only have 6 on my desktop. That may be a problem, but I have no idea. Any input?

---

### Post by hbweb500 on 2006-07-01
Well, I got some Kubuntu CDs today, decided I might try them, and honestly, Kubuntu feels faster. It is odd, though, because I tried KDE and I remember it suffering the same slowdowns. 

Ive pinpointed the problem, in that I believe it is Gnome. Pity, too, I like Gnome.

---

### Post by sexcopter on 2006-07-02
Hi,
I've had some similar experiences to what you guys are describing. Though not cripplingly slow performance, it doesn't seem at all as "slick" as breezy was. I've got a 1.7gig Centrino laptop, 512meg ram and an Nvidia NV43 (geforce go 6600 with 128meg memory).
I noticed something *very* perculiar in particular: The graphics can be noticably smoother if I'm moving the mouse at the time. Case in point: if you "preview" the Wormhole screensaver (I'm using xscreensaver, but I guess it makes no difference), it becomes radically smoother (perfect in fact) if i wiggle the mouse around in circles. Weird huh? Also notice it with flash in webpages (for example, [http://www.stickcricket.com/game.php)](http://www.stickcricket.com/game.php)). Does anyone else find this?
I thought I'd try some different video drivers in xorg.conf. Vesa gives of course poor performance. For some reason can't use the nv driver though -- xserver fails with some gibberish I can't make sense of -- even if i do a dpkg-reconfigure xserver-xorg.
Based on your thoughts that it could be Gnome, I'm going to try installing xfce, since that's supposed to be a lightweight alternative, isn't it? If it does turn out to be that, I'll be disappointed too, 'cos I know and love Gnome :s

---

### Post by sexcopter on 2006-07-03
Ok I tried xfce, and it yields exactly the same performance. I think the only thing I can pin it down to is quite simply naff nvidia drivers, at least for 2D applications. I still get a decent score (3700fps) for glxgears, whereas the cpu goes crazy if I scroll fast, or for flash applications etc.
It's a shame it's all closed up, so no-one can really do much to improve things. I guess we're in the hands of nvidia. Does anyone know how often they release new drivers, and if they'll come through as a regular update for us Dapper users?
By the way, when I put the nv driver in the xorg.conf file, it doesn't "crash" as such, but I get a blank screen (I can hear the sound at the login screen) -- still not much use! Any ideas what could be wrong?

---

### Post by hbweb500 on 2006-07-03
Did you download and use the proprietary NVIDIA drivers, or are you just using the "nv" driver? THe "nv" driver is open source and a hack attempting to get your card to run, the "nvidia" driver is made by NVIDIA for your card. If not, apt-get install nvidia-glx, and that should help out.

KDE itself felt faster, but was still slow (probably felt faster because it has a built-in composite manager). I installed SLED 10 last night, and feels faster but is still slow. Im going to reinstall Windows completely today, because I cant work on a computer that isnt responsive. I think in the end that my hardware was not suitable for Linux, because it is all proprietary from Dell, and designed for Windows.

Im going to build a computer from parts and make sure it is Linux compatible.

---

### Post by sexcopter on 2006-07-03
> Did you download and use the proprietary NVIDIA drivers, or are you just using the "nv" driver? 
Yeah, first thing I did when I installed Dapper was to get the propietary drivers. What I'd like to do is try the open-source nv driver so I can compare it to the nvidia driver. Anyway, you'd at least expect the nvidia driver to be better than the nv driver!
> KDE itself felt faster, but was still slow (probably felt faster because it has a built-in composite manager)
I believe xfce also has a built-in composite manager, which means at a guess windows and menus etc. may draw faster and better, but actual 2d applications (like some screensavers, for example) are at no advantage.
> Im going to build a computer from parts and make sure it is Linux compatible.
Supposing it is the graphics card which is slowing things down, what do you consider getting that's better? I can't compare myself, but I wonder if an ATi card would be a better or worse choice. There are of course others, but I guess choice becomes limited!

---

### Post by lordmule on 2006-07-05
Has anyone tried rolling back to older versions of the nvidia driver. I ran breezy and unreal tournament 2004 in high res and all features enabled running smoothly. Now in dapper I have very low res with all features off and its still jerky. :mad:

---

### Post by sexcopter on 2006-07-05
> Has anyone tried rolling back to older versions of the nvidia driver.
I was wondering about this. Do you know what version of the nvidia driver is currently in the Breezy repository, specifically if it's current with Dapper (8762)? If there's an easy way to roll back to an older version, I'd be very interested, even just for experiment's sake.

---

### Post by cracker on 2006-07-05
[QUOTE=sexcopter]Supposing it is the graphics card which is slowing things down, what do you consider getting that's better? I can't compare myself, but I wonder if an ATi card would be a better or worse choice. There are of course others, but I guess choice becomes limited![/QUOTE]

I would advise strongly against getting a new ATi card. The drivers are a real nightmare.

It sounds to me that for some reason the PC isn't using the VRAM, or is only using 1-4MB of it. I really don't know of any way to check or change this, but in my experience, this is how cards with very low video memory behave.

---

### Post by sexcopter on 2006-07-05
> It sounds to me that for some reason the PC isn't using the VRAM, or is only using 1-4MB of it.
Yeah that would sound reasonable for graphics cards that use VRAM, but mine's got 128meg of its own, so can't really be that. At least it works, can't grumble too much!

---

### Post by Jasper Houtman on 2006-07-05
[QUOTE=hbweb500]Done so. Plus, this isnt an Nvidia issue: I get terrible performance using my Integrated card too. I have the same integrated card in my laptop and the laptop works perfectly fine under Ubuntu.[/QUOTE]

It is. Both integrated graphics and Nvidia can be a pain to get working proparly in dapper. Just look for a thead on setting up the proper drivers for either one. Things will run much smoother after that.

---

### Post by cracker on 2006-07-05
[QUOTE=sexcopter]Yeah that would sound reasonable for graphics cards that use VRAM, but mine's got 128meg of its own, so can't really be that. At least it works, can't grumble too much![/QUOTE]

The 128MB on the card _is_ VRAM.

---

### Post by sexcopter on 2006-07-06
[QUOTE=cracker]The 128MB on the card _is_ VRAM.[/QUOTE]
Oh, sorry my bad. I thought that was the kind of memory which is shared with the system RAM. So yeah, if it's only using a tiny portion of the VRAM then that's a Bad Thing, me thinks!
However when I run nvidia-settings, it does say "Video Memory: 128MB". Not sure if that counts for much...

---

### Post by setakht on 2006-07-09
It's got something to do with cairo and GTK being slow at drawing things, and some particular ubuntu slowness that I haven't figured out yet.  I have an Athlon 64 3500+, a Geforce 6600GT and a gig of RAM.  Ubuntu Dapper is easily the slowest distribution I've used.  Debian unstable is far quicker.  Things in Dapper take almost twice the time to draw or to start up than any other distribution.  For instance, I wait about a second and a half for the shell prompt to appear on a terminal in Dapper, where in Debian and Arch Linux it's instantaneous. I really want to like Ubuntu, but I've installed it twice and within a week I've canned it because the UI experience is too painful.  And yes this is with the K7 kernel, Nvidia drivers and other performance hacks enabled.  None of them make a difference.  It's back to unstable with all its problems.  Sure, Gnome is bloated, but Ubuntu makes it even more painful.

---

### Post by sgtBiafra on 2006-07-18
Please excuse my ignorance concerning the setup of a multi-screen environment (as I've never done this), but I'm assuming that X does this using something like "Screen1" and "Screen2" in the "ServerLayout" section. If so, you'd only need to get the individual Screen configurations (and their  corresponding Device sections) fixed up.

I've had separate experiences with an integrated i810 device at work and nVidia at home. Here's what I've found:

* Intel - requires the i810 driver; need to specify VideoRam for internal devices; available video modes could be dependent on limitations set in the BIOS (my IBM had a 1MB and an 8MB setting so I'm not sure that the 32MB I specified in xorg.conf is being used correctly); 3d-acceleration seems limited to 16-bit color depth

* nVidia - requires the nvidia driver (in the nvidia-glx package; not nv); a card with built-in memory doesn't require a VideoRam setting (the driver will scan the card during startup); there are some extra parameters you can set through the nvidia-glx driver package, but nothing necessary (tweaks mostly)

Once you get X running with the appropriate devices, things seem quite nice in Ubuntu. I hope my painful experiences help you out.

---

### Post by phen on 2006-07-18
Hello!

I have the same experience with dapper. For example: If i use the gnome-panel aaplications menu, and browse through the sub menus, it takes about a second or maybe a half second for the images to appear. i use a pentium M 1400Mhz with 512MB ram, all drivers and stuff is installed. 

Or even better: if i load up XFIG, it takes about 20 seconds for the splash screen to disappear. thats unbelievably slow!

i tried to monitor "top" while browsing the applications menu. it says that gnome panel takes 116MB virtual and 22mb "res". thats a bit to much for just the panel isnt it?

i dont know what to do... breezy was faster, but hoary was even faster than  breezy! in each case, the application menu is nothing special bleeding edge technology that needs more memory because it has changed so much over the last year :-(

edit: other processes use unbelievable amounts of mem as well: xorg, firefox (220MB???) evolution, everything...

---

### Post by sexcopter on 2006-07-19
> **sgtBiafra said:**
> 
* Intel - requires the i810 driver; need to specify VideoRam for internal devices; available video modes could be dependent on limitations set in the BIOS (my IBM had a 1MB and an 8MB setting so I'm not sure that the 32MB I specified in xorg.conf is being used correctly); 3d-acceleration seems limited to 16-bit color depth


Actually a friend's laptop has an Intel and uses the i810 driver (it's a ThinkPad). I don't know about specifics, but the 3d and 2d acceleration work a treat - screensavers are almost *too* fast! This was all out of the box with no configuration at all. Puts my system to shame in that respect, which is annoying because the specs of my laptop are leagues ahead of said ThinkPad.
Oh well, I'm just looking forward to Edgy now :p

---

### Post by Visitor.Q on 2006-08-03
I have got the same experiences on a Toshiba A15-S129 laptop. General specs are:
Intel celeron M proc @ 2.4GHz
512 MB ram
60 MB harddisk (dapper installed on partition after windows, so it is not on the fastest part of the HD... should this matter??)
intel 852GM integrated videocard (i think with shared videomem, which I cannot configure anywhere in the bios)

When I am browsing through directories on my harddrive, every time I open one the system thinks for about a second before it actually enters the dir.  When doing so in Windows, it immediately shows the content of the folders. Starting the terminal also takes about 5 seconds.
I also have the problem with other programs, such as firefox (opening a page using a fast internet connection takes time to 'build' the page on screen, whereas windows displays it immediately). Switching tabs in Firefox also is slow. Actually, everything is quite slow, it even limits me when working.
Another example is in any program with a menu bar (file, edit, ..., help). When I am going over the menu, it should display the contents of the menu when the mouse is over it, but when the mouse is moving from file --> help, the menu is displayed with a delay. This makes it very uncomfortable to search for a function (I'm sure it helps learning the hotkeys fast, although this is probably not the way it should be).

I just though about turning on the DMA of my harddrive, as I feel it is also not as fast as it could be.. But using 'sudo hdparm -d /dev/hda' says DMA is already turned on... The intel 810i videodriver is being used. I still think the shared video memory might be troublesome in this case, but in this thread also problems are reported with onboard vmem. Anyway, I still would like to know how to setup the amount of RAM to be used as vmem, I could not find it. (it's probably somewhere in xorg.conf)...
I also checked my CPU speed, but it is indeed 2.39GHz (for some time i though the processer was at half speed for energy savings or so), but this was also not the case. glxinfo displays that direct rendering is used.

I can also display the output of 'top' in the console, but it is not very different from earlier posting in this thread.

Okay... sorry for the long post, but it displays some of the annoyances of my current system, especially because I know the system can perform much, much better. I have tried to pinpoint the problem but I wasn't able to. On the other hand, the problem even got me registered :)

---

### Post by Visitor.Q on 2006-08-03
As mentioned in another topic on this forum, the problem is probably due to the 386 kernel (which I used for quite a long time, unaware of the possibility to change it), which can be upgraded easily to the 686 kernel. I installed it, and now I think that everything is faster than it was... At least the mouse pointer runs over the screen smoothly and this already feels so much better... I'll try some things out before I know for sure, but anyway, here's the code that the other dude posted (I lost the topic :P)

[code]
sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686
[\code]
Hope this works for you...

---

### Post by regeya on 2006-08-05
> **hbweb500 said:**
> 
Is this what Ubuntu is like? I think I should expect some pretty fast performance, my computer isnt that old. Please tell me if I should post any log files, etc...

And thanks for the help :-D 

Justin

I know it's no consolation, but I've been dealing with odd performance issues, too.  Whereas I could pull down DV video on Warty while working on other stuff, under Breezy I have to leave the computer be, and even then, I only get 50 out of every 120 frames(!)  Drive performance is poor, even though the proper modules are loaded, and the settings when I run hdparm are dismally safe.  Even when I enable settings that *used* to be automatic on this distribution, drive performance doesn't improve.

I'm going to try building a kernel next, and then I'll move on to something different.  I have a one-year-old and a wife who's *not* understanding when I say that the OS can't handle pulling down video any more, let's just keep buying DV tapes until I can dump video again. :-}

Having said all that, yeah, that sounds unusual, what you're going through.  Your specs are WAAAAY better than mine. :-}

---

### Post by liljoe76 on 2006-08-05
i dont quite have the same experiences as others in this thread, but ubuntu and kubuntu are far slower than winxp on my system, which is disheartning. while my system specs are 'slow': athlon 1700, 512ddr 266, geforce 3 64mb, soundblaster live, i hacked in a wd 74gb raptor (read: sata to ide), which made windows RIP!!! install was 20mins, to the desktop (after all programs installed) in 20 secs. i could open explorer and double-click away at directories, well as fast as i could double-click... firefox w/ 20 ext's, cold started in 1 maybe 1.5 secs (compared to 6-10 secs normally)
i've had the raptor for some time and had gotten used to it's speed, infact in making the switch (to kubuntu then to ubuntu) last week, i thought i'd be getting a much faster lighter weight os. but sadly it's slower, by a decent margin. i've done all the commands in this thread + and all appears to be running as intended.  
as an observation, kubuntu ran significantly slower and was much flakier with stability, hence the switch to gnome. thinking i need to pop in xcfe to get my speed back, or maybe simply mepis. i'm a complete nube to linux (having wanted to switch for a few years), i've matured in my computing experience and have relized i only watch the boobtube and browse the web w/ fx, why do i need all the baggage of windows.? (maintenance & threats)
again i dont have the real problems of the other members, i just wanted to share my current experience. hoping edgy is more refined in this manner.
take care, joe

---

### Post by sexcopter on 2006-08-14
Ok, now I've just had the most startling, or should I say bizarre discovery yet. All the graphics issues I and others have complained of only apply when the laptop us on AC power (charging or not). If I unplug it, the graphics zip straight into the kind of performance I should be seeing. Basically, it seems that having the AC plugged in is causing the trouble somehow.

Now, if anyone can figure that one out, and I happen to meet you somewhere in real life, I'll buy you a drink ;)

---

### Post by jesar on 2006-08-15
I'm encountering the same problems as hbweb500.

My specs are:
-AMD Athlon(tm) XP 2100+ with 1737.578 MHz 
-776 RAM
-GeForce4 MX 440 with AGP8X and a second without AGP8X

A week ago I installed Breezy (from which I have the CD) and updated immediatly to Dapper. I got both my monitors running with Xinerama. Great was my disappointment when it seemed impossible to use Blender (my favorite 3d app.). After following all threads regarding this issue and reinstalling three times I found this thread... which makes it appear hopeless for me.

Does anyone have any good suggestions as to installing other versions (breezy had the same problem for me) or distro's? I don't want to go back to Windows because their "we can push the button whenever we want"-mentality really scares me.

---

### Post by lordmule on 2006-08-15
After knowledge of poor performance of graphics in dapper I am running breezy again for my nvidia card. However, I have just picked up a macbook pro and even with ATI graphics I have the same issue, I did notice however that I got a significant speedup when I installed linux-686, but this improved performance most likely due to smp support in the 686 kernel vs the 386 kernel. However, it did not dramatically improve the rendering performance. 

I was just wondering about if people with an installed dapper with NV card tried installing 686 kernel and if they had much better performance, or was it simply the dual core support on my MBP.

I hope its as simple as that since I am still running breezy on my PC :-$

---

### Post by crumja on 2006-08-17
Two things to try:

Make sure hdparm on your drive(s) is set to hi-perf settings. DMA in particular.

Make sure direct rendering is on for your vid card.

The problem you describe sounds very much like xorg taking lots of cpu power to draw windows when the rendering could go directly to the card.

---

