---
title: "ASUS 1201HA (gma500) external monitor resolution problem"
date: 2013-03-10
forum: Hardware
---

### Post by fir3wir3d on 2013-03-10
Hello,
After enduring the slide-show like desktop experience with win7 on my netbook for way to long I have decided to try ubuntu as a slimmer and faster alternative. My initial experiment with 12.10 and the gma500_gfx kernel module had rather discouraging results (never ending screen flickering, weird artefacts around the cursor and the image on the external screen shaking horizontally to the point of being unreadable for most of the time). I have now downgraded to ubuntu 11.04 and the emgd driver from ppa:gma500/emgd and I am completely blown away by how much snappier my computer has become. Video playback and flash video are both fluent and more importantly don't freeze the whole system for a long time like they did on 12.10. 

My netbook is now quiet, cool and super fast. I am however problem connecting my external screen I need to work with any degree of efficiency. Initially connecting my screen to the vga output on my computer had no effect. The only solution I was able to find is using this configuration file and placing it in /usr/share/X11/xorg.conf.d/:

```

Section "Module"
    Load "dbe"
    Load "dri"
    Load "dri2"
    Load "record"
    Load "extmod"
    Load "glx"
EndSection

Section "Monitor"
    Identifier   "MainMonitor"
    ModelName    "LCD Panel 1366x768"
EndSection

Section "Screen"
    Identifier    "MainScreen"
    Device        "MainDevice"
    Monitor       "MainMonitor"
    SubSection "Display"
    Depth     24
    Modes    "1366x768"
    EndSubSection
EndSection

Section "Device"
    Identifier "MainDevice"
    Driver     "emgd"
#    Driver "vesa"
    VendorName "Intel(R) DEG"
    BoardName  "Embedded Graphics"
    BusID      "0:2:0"
    Screen      0
    VideoRam    32768
    Option     "PcfVersion"             "1792"
    Option     "ConfigId"               "1"
    Option     "ALL/1/name"             "lvds-display"
    Option     "ALL/1/General/PortOrder"        "24000"
    Option     "ALL/1/General/VideoRam"                 "32768"
    Option     "ALL/1/General/DisplayConfig"        "2"
    Option     "ALL/1/General/DisplayDetect"        "1"
    Option     "ALL/1/General/Accel"            "1"
    Option     "ALL/1/General/DRI"          "1"
    Option     "ALL/1/General/DRI2"         "1"
    Option     "ALL/1/General/XVideo"           "1"
    Option     "ALL/1/General/XVideoBlend"      "0"
    Option     "ALL/1/General/TearFB"           "0"
    Option     "ALL/1/General/ShadowFB"         "0"
    Option     "ALL/1/General/SWCursor"         "0"
    Option     "ALL/1/Port/4/General/name"      "LVDS"
#    Option     "ALL/1/Port/4/General/Rotation"     "0"
    Option     "ALL/1/Port/4/General/Edid"      "1"
#    Option     "ALL/1/Port/4/Attr/70"          "100"
#    Option     "ALL/1/Port/4/Attr/71"                   "20300"
    Option     "ALL/1/Port/4/Attr/72"           "0"
#    Option     "ALL/1/Port/4/FPInfo/BkltMethod"         "1"
#    Option     "ALL/1/Port/4/FPInfo/BkltEnable"         "1"
    Option      "ALL/1/Port/2/General/name"     "SVDO"
    Option  "ALL/1/Port/2/General/Edid"     "1"
    Option  "ALL/1/Port/2/General/EdidAvail"    "1"
    Option  "ALL/1/Port/2/General/EdidNotAvail"     "7"
EndSection

# Secondary (for dual-head only) display
Section "Monitor"
    Identifier   "VGAMonitor"
    ModelName    "VGA Output"
EndSection

Section "Screen"
    Identifier    "VGAScreen"
    Device        "VGADevice"
    Monitor       "VGAMonitor"
    SubSection    "Display"
    Depth   24
    Modes   "1440x900"
    EndSubSection
EndSection

Section "Device"
    Identifier "VGADevice"
    Driver     "emgd"
    VendorName "Intel(R) DEG"
    BoardName  "Embedded Graphics"
    BusID      "0:2:0"
    Screen     1
EndSection

Section "ServerLayout"
    Identifier     "Dual Head Layout"
    Screen  "MainScreen"
    Screen  "VGAScreen" RightOf "MainScreen"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
#   Option "AutoAddDevices" "false"
EndSection


```

The resulting resolution and aspect ratio on the external screen are incorrect, however. I have tried changing the Modes "1600x900" line to read: Modes "1920x1200" but this had no effect. The proper resolution is not even available in the Monitors configuration applet. Instead I get cloned output to both screens with the resolution toggling between 1366x768 and 1920x1080 on both screens with the use of Fn+F8. Commenting out the internal screen from the ServerLayout section causes the system not to boot, although up to the point when it freezes (at Checking Battery ... OK) an external screen is used properly.

Under windows I can use Fn+F8 to toggle between built in display, clone mode and extended desktop. I can further disable the internal screen and use vga port output only using the configuration software which came with the intel driver. On ubuntu I understand the corresponding utility is emgdui but I can't find any documentation explaining how it should be used. Currently running it with no arguments gives the following output:

```

Lib version: 1.0.0

OS name: OS NAME: Linux, Release: 2.6.38-16-generic
Version: Version: #67-Ubuntu SMP Thu Sep 6 18:00:43 UTC 2012
Distribution: Distribution: Ubuntu 11.04 \n \l
Additional Info: X Server Version: 1.9.0.0


Driver name: Intel Embedded Media and Graphics Driver
Driver version: 161952
Driver build date: Apr 26 2011
Chipset name: Intel GMA500
Config id used: 42112

Total DCs available: 4
DC list: 
[1] 0x21
[2] 0x400022
[3] 0x400028
[4] 0x41

Current DC: 0x400022

Width    Height    Refresh Rate

640    480    60
640    480    70
640    480    72
640    480    75
640    480    85
640    480    100
640    480    120
720    480    60
720    576    50
800    480    60
800    600    60
800    600    70
800    600    72
800    600    75
800    600    85
800    600    100
800    600    120
960    540    60
1024    768    60
1024    768    70
1024    768    75
1024    768    85
1024    768    100
1024    768    120
1152    864    60
1152    864    70
1152    864    72
1152    864    75
1152    864    85
1152    864    100
1280    720    60
1280    720    75
1280    720    85
1280    720    100
1280    768    60
1280    768    75
1280    768    85
1280    960    60
1280    960    75
1280    960    85
1280    1024    60
1280    1024    70
1280    1024    72
1280    1024    75
1280    1024    85
1366    768    60
1400    1050    60
1400    1050    75
1600    900    60
1600    900    75
1600    1200    60
1920    1080    50

Width    Height    Refresh Rate

1366    768    60
640    480    60
720    480    60
720    576    50
800    480    60
800    600    60
960    540    60
1024    768    60
1280    720    60
1280    768    60

Setting 16 bits per pixel
Set the Primary mode to: 640 x 480 x 60

Setting 32 bits per pixel
Set the Primary mode to: 640 x 480 x 60

Port on Primary display location 0 is 2
Port 2 is not flipped
Port 2 is rotated by 0 degrees

```

The detected modes are not even correct for my monitor and only very low 16:10 resolutions are listed. In cloned mode using 1920x1080 the performance is still brilliant and I would really like nothing better then to continue using the linux/emgd setup for everyday work. I am not a very technical person and don't have much linux experience so any guidance as to getting the correct resolution and output on the external screen would really be appreciated. Currently all the fonts are blurry and hard to read so I am forced to either use the miniature netbook screen or windows 7 with external monitor. If there is a way to also disable the internal screen and use the vga port I would be even more pleased but this is a very minor issue by comparison.

---

### Post by mikewhatever on 2013-03-12
The problem is, both 11.04 and EMGD are unsupported. GMA500 is 5years old, and more then ever, it now seems to be a dead end with no support and no interest from anyone.

---

### Post by fir3wir3d on 2013-03-12
Seems strange because laptop GPUs are exactly the ones that users are stuck with forever. If ubuntu chose not to support some external card I could just switch to a different one. But I can't exactly throw away an otherwise perfectly good laptop. With an ultralight desktop enviorment like llvm, dwm, etc. and external keyboard, mouse and screens the old Atom netbooks could make cheap, power efficient, compact and quiet PCs. But some rudimentary external display support would be required. So far I have tested ubuntu 12.10 with the gma500_gfx module (terrible performance, choppy video and constant screen flickering) as well as 11.04 and 11.10 with the newest versions of emgd available for those systems (good performance, smooth flash and video playback and no ability to force a proper resoluton and refrash rate on the external screen). I am yet to try 12.04 but most likely I will be stuck with windows 7.

[COLOR=#ff0000]EDIT:
[/COLOR][COLOR=#000000]I installed 12.04 and I am using the gma500_gfx under the 3.5.0-23-generic kernel. Performance and stablitiy are way better then 12.10 but there is still some occasional screen flickering on the external display that gets worse under heavy cpu load. Unity 2D shakes like mad (the left edge of the screen moves to the center of the display continously several times a second) but under dwm the screen flickers much less frequenly and usually by only a small distance. It is incredibly annoying but since I can't get EMGD to detect proper resolution and nobody is willing to help me it will have to do. The flickering under the gma500_gfx was also helped a little by increasing the amount of memory available to the graphics card as suggested by the ubuntu paulsbo support wiki page (GRUB_CMDLINE_LINUX="mem=1920mb") altough I went with 256M instead of 128 just to be safe. I was also able to isolate the killing the gnome-settings-demon (font smoothing?) and unplugging the the 3.5mm headphone jack (connector sensing? - mine is somewhat bent and broken) as probably beneficial to reducing the annoying external screen flicker.[/COLOR]

---

### Post by mikewhatever on 2013-03-12
I know exactly how you feel, as I am also rather unhappy about the state of affairs, but what does it have to do with Ubuntu? Intel, doesn't release a driver we can use, so why is Ubuntu to blame? What made you think that "ubuntu chose not to support" GMA500? EMGD doesn't work on Ubuntu, and, AFAIK, on any mainstram Linux distro, and please correct me it I am wrong.

---

### Post by fir3wir3d on 2013-03-13
> **mikewhatever said:**
> I know exactly how you feel, as I am also rather unhappy about the state of affairs, but what does it have to do with Ubuntu? Intel, doesn't release a driver we can use, so why is Ubuntu to blame? What made you think that "ubuntu chose not to support" GMA500? EMGD doesn't work on Ubuntu, and, AFAIK, on any mainstram Linux distro, and please correct me it I am wrong.

well EMGD used to work on older ubuntu releases and was used by quite a lot of people. please note this >5000 post support thread [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345). It is peppered with dozens of xorg configuration files that people have used successfully to get external monitor output with PSB and EMGD drivers. they were all uploaded to [http://paste.ubuntu.com](http://paste.ubuntu.com) and they are ALL no longer available. there were also patched versions of the emgdgui application that could be used to set up resolution on the external screen but the ppa maintainer uploaded them to dropbox and they are also not available. I was hoping that since thousands of people used this setup, somebody will be able to help me or at least point me in the right direction. when I mentioned lack of support I meant lack of support for external screens in the new gma500_gfx driver used since the 3.3 kernel. The external screen gets now detected properly but when I try to use it instead of the laptop display the image moves left and right frequently for no reason and large stripes of the image are constantly flickering whenever something is scrolling in the terminal, and under heavy io or cpu load (like copying files to a usb stick, generating image thumbnails in a directory, launching applications, rendering web pages...  pretty much all time since for the atom cpu moving a cursor around is a heavy compute workload). This stuff did not happen in emgd when outputting 1920x1080 so I was just hoping somebody can tell me how to force 1920x1200 and I would have been a happy camper.

---

### Post by mikewhatever on 2013-03-13
Yes, both emgd and psb still work on older releases (10.10 was probably the sweet spot), and all the work done by the [gma500 team]("https://launchpad.net/~gma500gma500") is still available through PPAs linked on that page. Unfortunately, the effort proved unsustainable and collapsed, as both drivers became more and more incompatible with every subsequent Ubuntu release. Linux users tried pleading for support on the [Intel Embedded forum]("http://www.intel.com/content/www/us/en/search.html?keyword=gma500&lstLanguages=en_US") and other places, and were told that the company wasn't interested. So, now we are stuck with old but still rather decent hardware, and zero vendor support.

I hope you'll find a solution, or else someone might help you. Good luck.

---

