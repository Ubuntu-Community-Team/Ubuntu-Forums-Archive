---
title: "Cannot run Samsung T240HD at 1920x1200"
date: 2009-05-16
forum: Hardware
---

### Post by jellyfisharepretty on 2009-05-16
Hi everyone

I have been searching the web intensely for a solution to this problem, but alas nothing seems to work.  I got this new monitor, a Samsung T240HD, which has a native resolution of 1920x1200.  According to the Samsung user manual for this monitor, the maximum resolution is 1920x1200@60Hz with horizontal freq. range 30-81 kHz and vertical freq. range 56-75 Hz with maximum pixel clock 162.00 MHz.

At first I couldn't get beyond 1680x1050 with a DVI cable.  I then read on Samsung's tech support website, and other posts, that single-link DVI cable won't allow me past this resolution because of bandwidth limitations, so I hooked up an analog cable, which got me to a maximum resolution of 1920x1080.  A dual-link DVI cable won't work, since this Monitor only supports a single-link connection.

This, however, is not the monitor's native resolution and gives me an image quite stretched vertically, which I find unacceptable.

I have tried many xorg.conf tweaks to get a 1920x1200 resolution choice to appear in the nvidia-settings utility, but to no avail.  The highest that still appears is 1920x1080.  I am using an Nvidia Geforce 8800GTS card with the Nvidia 180.44 linux drivers on a fresh, clean Jaunty install.  I was hoping switching to Jaunty would solve the problem, but I had the same problem in Feisty.

Here's what my xorg.conf file currently looks like :
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "DontZap"  "false"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "T240HD"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1920x1200_60.00" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -Hsync +Vsync
    Modeline       "1920x1200_59.95"  192.99  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
    Modeline       "1920x1200_50.00"  158.08  1920 2032 2240 2560  1200 1201 1204 1235  -HSync +Vsync
    Modeline       "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView"     "0"
    Option         "MetaModes"    "CRT: 1920x1200_60.00 +0+0; CRT: 1920x1200_59.95 +0+0; CRT: 1920x1200_50.00 +0+0; CRT: 1680x1050_60.00 +0+0"
    Option         "UseEdidFreqs" "false"
    Option         "NoLogo"       "true"
    Option         "Coolbits"     "1"
    Option         "TripleBuffer" "true"
    SubSection     "Display"
        Depth       24
	Modes       "1920x1200_60.00" "1920x1200_59.95" "1920x1200_50.00" "1680x1050_60.00"
    EndSubSection
EndSection
```

, where I have generated modelines using the gtf command-line utility for 1920x1200@60Hz, 1920x1200@59.95Hz, 1920x1200@50Hz and 1680x1050@60Hz.

I was trying to implement the solution posted in [**_this_**]("http://ubuntuforums.org/showthread.php?t=792198") thread for another Samsung monitor with quite similar specs, but that didn't work.

I told the nvidia driver to stop using EDID for frequencies, and use the ones specified in the monitor section instead (which I took right out of the monitor's user manual), but that had no effect either.

Did I miss anything ? I'm running out of ideas here ;)  Hope someone can help...

---

### Post by jellyfisharepretty on 2009-05-17
bump

---

### Post by coffeecat on 2009-05-17
I experienced a completely unrelated issue with the nvidia 180 driver [here]("http://ubuntuforums.org/showthread.php?t=1155878") which was solved by downgrading to the 173 driver. According to the notes in Synaptic for the nvidia-glx-173 driver your Geforce 8800GTS card is supported, but you might want to check this. Have you tried the 173 driver? Since I managed to unearth one (very) obscure bug with the 180 driver, you may have come across another.

Have you got (or got access to) a Windows machine with the 180 nvidia driver? Since much of code would be shared between the Linux and Windows drivers, it might be interesting to see if this problem with your monitor is duplicated in Windows. But if it were you'd think Samsung would know about it by now.

> At first I couldn't get beyond 1680x1050 with a DVI cable. I then read on Samsung's tech support website, and other posts, that single-link DVI cable won't allow me past this resolution because of bandwidth limitations, so I hooked up an analog cable,It could be argued that it's not fit for purpose if it doesn't run at optimum resolution with DVI. Would consumer laws where you are permit you to return this? My 24" BenQ monitor works at 1920x1200 no problem with Ubuntu, Windows and Mac Mini, analogue or DVI, and through a KVM switch.

---

### Post by jellyfisharepretty on 2009-05-17
Thanks for your input, coffeecat.  I think the idea of trying the 173 driver is certainly worth a try.  Will report on my findings once I do that.

As for windows, I'll have to install XP on my second hard drive, and apply all the drivers and stuff... that will take time.  But I think I'll also try it if downgrading the Nvidia driver doesn't work.

I was certainly disappointed to learn Samsung did not include a dual-link DVI capability with this monitor, which effectively limits the resolution to 1920x1080 on DVI, according to what I have read.  Still, even this choice of resolution did not appear when I have a DVI cable connected.

I don't know if consumer laws would allow me to return this.  I suspect they would, since this monitor was advertised supporting a digital connection with a resolution of 1920x1200 (and clearly doesn't).  Personally, using the analog cable, as long as I can run at the monitor's native resolution, is an acceptable work-around for me.

---

### Post by coffeecat on 2009-05-17
Usual caveat - IANAL - but I understand that consumer law here in the UK means that if you buy from a distance seller (usually over the internet, delivered to your door) you have an absolute right to return the item within 30 days for a complete refund, no reason given. You are, I believe, liable for return carriage though.

Some suppliers try to wriggle out of this, of course. The better ones just accept this is part of their trading environment and don't quibble.

I don't know whether this is true in Canada, or just a UK quirk, but that might be worth checking out if you've had the monitor for only a short time.

---

### Post by jellyfisharepretty on 2009-05-18
Switching to the 173 drivers had no effect.  I still can get to 1920x1080 at most.  Will try with Windows next.

---

### Post by jellyfisharepretty on 2009-06-16
Update... I tried with windows by connecting my laptop (geforce 9500m) with an analog vga cable.  Still can't get to the native resolution, so this is beginning to look like some kind of hardware problem with my monitor I guess...

---

### Post by ghmerrill on 2009-06-18
It's  not a hardware problem with your monitor.  I just got a Lenovo Y 550 and put Ubuntu on it.  I have exactly the same problem with the T240.  I've posted in another thread asking for help as well, but no one seems to have a solution.

On my Dell laptop Windows system, Windows simply detects the monitor, the optimal resolution, and everything is fine.  On Linux, it just isn't happening.  It's a Linux problem of some sort.

I'm really impressed with Ubuntu Linux and am going back to using *NIX after a number of years.  But it still seems that one of the significant holes in Linux is hardware support.  It's a lot better now, but still problematic.

---

### Post by ghmerrill on 2009-06-18
This is particularly puzzling if you look at the thread "Samsung T240" how to enable 60 Hz where it appears that the correct resolution is achieved under Linux without a problem.  I wonder if it's a version problem.

Very frustrating.  I haven't experimented much with this yet, but no one seems to have any genuine insight into it.  We're seeing exactly the same problem on different laptops with different video cards -- and it works fine on Windows and apparently on at least one Linux install.

---

### Post by jellyfisharepretty on 2009-11-07
Resurrecting this thread from the dead...

I have found out what exactly might be wrong !  [This]("http://www.tomshardware.com/forum/262226-33-display-1920x1200-samsung-t240hd-asus-4850") thread led me to it.

The EDID my monitor provides seems to be the EDID of a 22in Samsung monitor of maximum resolution 1680x1050 (might be the EDID of the Samsung T220HD).  Here's what I got when I read the EDID off the monitor (Using the Monitor Asset Manager utility on Windows):

Monitor
  Model name............... SyncMaster
  Manufacturer............. Samsung
  Plug and Play ID......... SAM03F0
  Serial number............ HVLQC00122
  Manufacture date......... 2008, ISO week 50
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  **Screen size.............. 470 x 300 mm (22.0 in)**
  Power management......... Active off/sleep
  Extension blocs.......... None
  -------------------------
  DDC/CI................... Supported
  MCCS revison............. 2.0
  Display technology....... TFT
  Controller............... Mstar 0x1400
  Firmware revision........ 0.1
  Firmware flags........... 0x00000001
  Active power on time..... Not supported
  Power consumption........ Not supported
  Current frequency........ 65.54kHz, 0.00Hz

Color characteristics
  Default color space...... Non-sRGB
  Display gamma............ 2.20
  Red chromaticity......... Rx 0.640 - Ry 0.330
  Green chromaticity....... Gx 0.300 - Gy 0.600
  Blue chromaticity........ Bx 0.150 - By 0.060
  White point (default).... Wx 0.313 - Wy 0.329
  Additional descriptors... None

Timing characteristics
  Horizontal scan range.... 30-81kHz
  Vertical scan range...... 56-75Hz
  Video bandwidth.......... 150MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  **Native/preferred timing.. 1680x1050p at 60Hz (16:10)**
    **Modeline............... "1680x1050" 146.250 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync**

Standard timings supported
     720 x  400p at  70Hz - IBM VGA
     640 x  480p at  60Hz - IBM VGA
     640 x  480p at  67Hz - Apple Mac II
     640 x  480p at  72Hz - VESA
     640 x  480p at  75Hz - VESA
     800 x  600p at  56Hz - VESA
     800 x  600p at  60Hz - VESA
     800 x  600p at  72Hz - VESA
     800 x  600p at  75Hz - VESA
     832 x  624p at  75Hz - Apple Mac II
    1024 x  768p at  60Hz - VESA
    1024 x  768p at  70Hz - VESA
    1024 x  768p at  75Hz - VESA
    1280 x 1024p at  75Hz - VESA
    1152 x  870p at  75Hz - Apple Mac II
    1680 x 1050p at  60Hz - VESA STD
    1280 x 1024p at  60Hz - VESA STD
    1280 x  960p at  60Hz - VESA STD
    1152 x  864p at  75Hz - VESA STD

Now I can think of two solutions.

1) I try to contact Samsung so they can either replace the monitor or update its firmware so that it has the correct EDID.  It is a shame that Samsung does not make its firmware available as I could just as easily update it myself using the USB port at the back of the monitor and using the software update option in the monitor menu.

2) I somehow fool Ubuntu and the Nvidia drivers into not using EDID from the monitor, providing the information myself (in the form of lines in xorg.conf, or some other way ?).  As can be seen from my first post, I already tried doing this without much success.

Does anyone know of a way to specify the use of a different EDID (other than lines in xorg.conf - which didn't seem to work) ?

If anyone has a Samsung T240HD, can you post and attach your EDID file in binary format ?  This can be extracted using the read-edid package, probably by executing

[FONT="Courier New"]# sudo get-edid > edid.bin[/FONT]
[Edit] I don't think this is the right way of using get-edid.  In fact I don't think that command will work.  But am not sure how to use it.

or by using the Monitor Asset Manager utility on Windows.

Thanks!

---

### Post by vitorgr on 2009-11-18
Hello!!!
I have the same monitor. It is running ok in 1900X1200 with nvidia 185.18.36. However, I got low quality graphics. I think my problem is in -*hsync* +vsync configuration. You can find EDID file attached. I am looking for a manner to change -*hsync* +vsync configuration. Windows movements is tearing a lot.

---

### Post by jellyfisharepretty on 2009-11-18
Wow thanks a lot vitorgr !  I might be able to force ubuntu to use that EDID instead of mine.

I don't have the tearing problem though.  I made to sure to sync everything at 60 Hz.  If you use compiz, make sure to tell it your refresh frequency and set it to vsync.  That fixed the windows tearing problem for me a while back.

---

### Post by dash17291 on 2009-12-23
> **jellyfisharepretty said:**
> Resurrecting this thread from the dead...

I have found out what exactly might be wrong !  [This]("http://www.tomshardware.com/forum/262226-33-display-1920x1200-samsung-t240hd-asus-4850") thread led me to it.

The EDID my monitor provides seems to be the EDID of a 22in Samsung monitor of maximum resolution 1680x1050 (might be the EDID of the Samsung T220HD).  Here's what I got when I read the EDID off the monitor (Using the Monitor Asset Manager utility on Windows):

Monitor
  Model name............... SyncMaster
  Manufacturer............. Samsung
  Plug and Play ID......... SAM03F0
  Serial number............ HVLQC00122
  Manufacture date......... 2008, ISO week 50
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  **Screen size.............. 470 x 300 mm (22.0 in)**
  Power management......... Active off/sleep
  Extension blocs.......... None
  -------------------------
  DDC/CI................... Supported
  MCCS revison............. 2.0
  Display technology....... TFT
  Controller............... Mstar 0x1400
  Firmware revision........ 0.1
  Firmware flags........... 0x00000001
  Active power on time..... Not supported
  Power consumption........ Not supported
  Current frequency........ 65.54kHz, 0.00Hz

Color characteristics
  Default color space...... Non-sRGB
  Display gamma............ 2.20
  Red chromaticity......... Rx 0.640 - Ry 0.330
  Green chromaticity....... Gx 0.300 - Gy 0.600
  Blue chromaticity........ Bx 0.150 - By 0.060
  White point (default).... Wx 0.313 - Wy 0.329
  Additional descriptors... None

Timing characteristics
  Horizontal scan range.... 30-81kHz
  Vertical scan range...... 56-75Hz
  Video bandwidth.......... 150MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  **Native/preferred timing.. 1680x1050p at 60Hz (16:10)**
    **Modeline............... "1680x1050" 146.250 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync**

Standard timings supported
     720 x  400p at  70Hz - IBM VGA
     640 x  480p at  60Hz - IBM VGA
     640 x  480p at  67Hz - Apple Mac II
     640 x  480p at  72Hz - VESA
     640 x  480p at  75Hz - VESA
     800 x  600p at  56Hz - VESA
     800 x  600p at  60Hz - VESA
     800 x  600p at  72Hz - VESA
     800 x  600p at  75Hz - VESA
     832 x  624p at  75Hz - Apple Mac II
    1024 x  768p at  60Hz - VESA
    1024 x  768p at  70Hz - VESA
    1024 x  768p at  75Hz - VESA
    1280 x 1024p at  75Hz - VESA
    1152 x  870p at  75Hz - Apple Mac II
    1680 x 1050p at  60Hz - VESA STD
    1280 x 1024p at  60Hz - VESA STD
    1280 x  960p at  60Hz - VESA STD
    1152 x  864p at  75Hz - VESA STD

Now I can think of two solutions.

1) I try to contact Samsung so they can either replace the monitor or update its firmware so that it has the correct EDID.  It is a shame that Samsung does not make its firmware available as I could just as easily update it myself using the USB port at the back of the monitor and using the software update option in the monitor menu.

2) I somehow fool Ubuntu and the Nvidia drivers into not using EDID from the monitor, providing the information myself (in the form of lines in xorg.conf, or some other way ?).  As can be seen from my first post, I already tried doing this without much success.

Does anyone know of a way to specify the use of a different EDID (other than lines in xorg.conf - which didn't seem to work) ?

If anyone has a Samsung T240HD, can you post and attach your EDID file in binary format ?  This can be extracted using the read-edid package, probably by executing

[FONT=Courier New]# sudo get-edid > edid.bin[/FONT]
[Edit] I don't think this is the right way of using get-edid.  In fact I don't think that command will work.  But am not sure how to use it.

or by using the Monitor Asset Manager utility on Windows.

Thanks!


Hi there!

Please tell me if the following are working, or I won't install Ubuntu as a native OS. :confused:


Monitor #1 [Real-time 0x0051]
  Model name............... SyncMaster
  Manufacturer............. Samsung
  Plug and Play ID......... SAM0427
  Serial number............ n/a
  Manufacture date......... 2009, ISO week 15
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  Screen size.............. 160 x 90 mm (7,2 in)
  Power management......... Not supported
  Extension blocs.......... 1 (CEA-EXT)
  -------------------------
  DDC/CI................... Not supported

Color characteristics
  Default color space...... Non-sRGB
  Display gamma............ 2,20
  Red chromaticity......... Rx 0,650 - Ry 0,337
  Green chromaticity....... Gx 0,296 - Gy 0,604
  Blue chromaticity........ Bx 0,147 - By 0,074
  White point (default).... Wx 0,313 - Wy 0,329
  Additional descriptors... None

Timing characteristics
  Horizontal scan range.... 26-81kHz
  Vertical scan range...... 24-75Hz
  Video bandwidth.......... 230MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  Native/preferred timing.. 1920x1200p at 60Hz (16:9)
    Modeline............... "1920x1200" 154,000 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
  Detailed timing #1....... 1280x720p at 50Hz (16:9)
    Modeline............... "1280x720" 74,250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync

Standard timings supported
     720 x  400p at  70Hz - IBM VGA
     640 x  480p at  60Hz - IBM VGA
     640 x  480p at  67Hz - Apple Mac II
     640 x  480p at  72Hz - VESA
     640 x  480p at  75Hz - VESA
     800 x  600p at  56Hz - VESA
     800 x  600p at  60Hz - VESA
     800 x  600p at  72Hz - VESA
     800 x  600p at  75Hz - VESA
     832 x  624p at  75Hz - Apple Mac II
    1024 x  768p at  60Hz - VESA
    1024 x  768p at  70Hz - VESA
    1024 x  768p at  75Hz - VESA
    1280 x 1024p at  75Hz - VESA
    1152 x  870p at  75Hz - Apple Mac II
    1152 x  864p at  75Hz - VESA STD
    1280 x  960p at  60Hz - VESA STD
    1280 x 1024p at  60Hz - VESA STD
    1600 x 1200p at  60Hz - VESA STD

EIA/CEA-861 Information
  Revision number.......... 3
  DTV underscan............ Supported
  Basic audio.............. Supported
  YCbCr 4:4:4.............. Supported
  YCbCr 4:2:2.............. Supported
  Native formats........... 1
  Detailed timing #1....... 1920x1080i at 50Hz (16:9)
    Modeline............... "1920x1080" 74,250 1920 2448 2492 2640 1080 1084 1094 1124 interlace +hsync +vsync
  Detailed timing #2....... 1920x1080i at 60Hz (16:9)
    Modeline............... "1920x1080" 74,250 1920 2008 2052 2200 1080 1084 1094 1124 interlace +hsync +vsync
  Detailed timing #3....... 1280x720p at 60Hz (16:9)
    Modeline............... "1280x720" 74,250 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
  Detailed timing #4....... 720x576p at 50Hz (16:9)
    Modeline............... "720x576" 27,000 720 732 796 864 576 581 586 625 -hsync -vsync

CE video data (timings supported)
    1280 x  720p at  50Hz - HDTV (16:9, 1:1) [Native]
    1280 x  720p at  60Hz - HDTV (16:9, 1:1)
    1920 x 1080i at  60Hz - HDTV (16:9, 1:1)
    1920 x 1080i at  50Hz - HDTV (16:9, 1:1)
     720 x  480p at  60Hz - EDTV (16:9, 32:27)
     720 x  576p at  50Hz - EDTV (16:9, 64:45)
    1920 x 1080p at  60Hz - HDTV (16:9, 1:1)
    1920 x 1080p at  50Hz - HDTV (16:9, 1:1)
    1920 x 1080p at  24Hz - HDTV (16:9, 1:1)
    1920 x 1080p at  25Hz - HDTV (16:9, 1:1)
    1920 x 1080p at  30Hz - HDTV (16:9, 1:1)
    NB: NTSC refresh rate = (Hz*1000)/1001

---

### Post by jellyfisharepretty on 2009-12-23
Hi dash,

I'm sorry, I can't tell you if it will work for sure, but from the looks of it, it seems perfectly fine.v  I can see in your modelines that 1920x1200 is supported.

By the way, this issue is totally unrelated to the OS.  I can't run at this resolution on Windowd either.  It is purely a problem with my monitor.

So, I strongly recommend you give Ubuntu a try, you can install it along with Windows if you're not sure you want to switch over permanently.  I'm sure you'll like it :)

UPDATE about my problem: I've been trying and trying and trying to get Samsung to undertstand that it's not a driver, configuration or OS problem, but so far I haven't had any success with their tech support.  Seems like they won't replace my monitor.

---

### Post by Sidewinder1 on 2010-01-01
Just so that you know, (from a misery loves company standpoint :-)), I just acquired the exact same monitor with the exact same problem, although I don't know how to read the "EDID" info in ubuntu so I'm not sure how it's listed. Could you advise where this might be listed?
 Furthermore I can't get any higher than 1600X1200 @ 50 Hz which is the same as my old Viewsonic was using :-( . When I installed the new Samsung, Hardy automaticaly upgraded from the nvidia-glx driver to the nvidia-glx-new 169.12+2.6.24.18-26.3. 
I unplugged the DVI cable and am running the alalog only, rebooted, alas, to no avail.
I'll be watching this thread and thanks for all of your efforts; it's certainly frustrating to not be able to use a piece of hdw. to it's full extent.

Side

---

### Post by jellyfisharepretty on 2010-01-01
Hi Side, you're right, misery *does* love company!  Jokes aside I am glad someone else suffering from the same issue noticed this thread.

To get the EDID, the best way I have found is to use [Monitor Asset Manager]("http://www.entechtaiwan.com/util/moninfo.shtm").  That's a Windows program I'm afraid, so either try it in Wine or boot into Windows if you have it installed.  This program seems to give the most complete information about what the monitor EDID is saying.

In ubuntu, you can also use the program read-edid.  Just install it :
```
sudo apt-get install read-edid
```

Then :
```
sudo get-edid > edid.bin
cat edid.bin | parse-edid
```

Alternatively go to System -> Administration -> NVIDIA X Server Settings -> DFP-1 - (Samsung SyncMaster) -> Acquire EDID

Then save the bin file somewhere, and parse it using parse-edid as written above.  I don't know why but for me using get-edid doesn't work, so I have to go through the NVIDIA utility.  Anyway, with parse-edid you should be able to see what modeline your monitor is telling the computer to use.  Mine looks like this :

```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SyncMaster"
	VendorName "SAM"
	ModelName "SyncMaster"
	# Block type: 2:0 3:fd
	HorizSync 30-81
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 150 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1680x1050"	# vfreq 59.954Hz, hfreq 65.290kHz
		DotClock	146.250000
		HTimings	1680 1784 1960 2240
		VTimings	1050 1053 1059 1089
		Flags	"+HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
```

Strangely the output looks like what might go in xorg.conf, but, just to be clear, that is not what I have in my xorg.conf.

As soon as the holidays period is over I'm gonna contact Samsung again, and I'll update with what happens

---

### Post by Sidewinder1 on 2010-01-02
Jelly, thanks ever so much for the response and guidance. I semi-accomplished all of the above with somewhat spurious results. For your edification and anyone else following this thread:
First using Monitor Asset Mgr, keep in mind that since it's a win program running through win, where I can get the native 1920X1200@60Hz the output is not surprising: (BTW this is with the DVI cable unplugged, just analog connected)
```
Monitor 
  Model name............... SyncMaster 
  Manufacturer............. Samsung 
  Plug and Play ID......... SAM0424 
  Serial number............ HVZSA03197 
  Manufacture date......... 2009, ISO week 42 
  ------------------------- 
  EDID revision............ 1.3 
  Input signal type........ Analog 0.700,0.300 (1.0V p-p) 
  Sync input support....... Separate, Composite, Sync-on-green 
  Display type............. RGB color 
  Screen size.............. 520 x 320 mm (24.0 in) 
  Power management......... Active off/sleep 
  Extension blocs.......... None 
  ------------------------- 
  DDC/CI................... Supported 
  MCCS revison............. 2.0 
  Display technology....... TFT 
  Controller............... Mstar 0x1400 
  Firmware revision........ 0.1 
  Firmware flags........... 0x00000001 
  Active power on time..... Not supported 
  Power consumption........ Not supported 
  Current frequency........ 65.54kHz, 0.00Hz 
 
Color characteristics 
  Default color space...... Non-sRGB 
  Display gamma............ 2.20 
  Red chromaticity......... Rx 0.640 - Ry 0.330 
  Green chromaticity....... Gx 0.300 - Gy 0.600 
  Blue chromaticity........ Bx 0.150 - By 0.060 
  White point (default).... Wx 0.313 - Wy 0.329 
  Additional descriptors... None 
 
Timing characteristics 
  Horizontal scan range.... 30-81kHz 
  Vertical scan range...... 56-75Hz 
  Video bandwidth.......... 170MHz 
  CVT standard............. Not supported 
  GTF standard............. Not supported 
  Additional descriptors... None 
  Preferred timing......... Yes 
  Native/preferred timing.. 1920x1200p at 60Hz (16:10) 
    Modeline............... "1920x1200" 154.000 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync 
 
Standard timings supported 
     720 x  400p at  70Hz - IBM VGA 
     640 x  480p at  60Hz - IBM VGA 
     640 x  480p at  67Hz - Apple Mac II 
     640 x  480p at  72Hz - VESA 
     640 x  480p at  75Hz - VESA 
     800 x  600p at  56Hz - VESA 
     800 x  600p at  60Hz - VESA 
     800 x  600p at  72Hz - VESA 
     800 x  600p at  75Hz - VESA 
     832 x  624p at  75Hz - Apple Mac II 
    1024 x  768p at  60Hz - VESA 
    1024 x  768p at  70Hz - VESA 
    1024 x  768p at  75Hz - VESA 
    1280 x 1024p at  75Hz - VESA 
    1152 x  870p at  75Hz - Apple Mac II 
    1600 x 1200p at  60Hz - VESA STD 
    1280 x 1024p at  60Hz - VESA STD 
    1280 x  960p at  60Hz - VESA STD 
    1152 x  864p at  75Hz - VESA STD 
 
Report information 
  Date generated........... 1/2/2010 
  Software revision........ 2.43.0.822 
  Operating system......... 5.1.2600.2.Service Pack 2 
 
Raw data 
  00,FF,FF,FF,FF,FF,FF,00,4C,2D,24,04,34,32,44,54,2A,13,01,03,0E,34,20,78,2A,EE,91,A3,54,4C,99,26, 
  0F,50,54,BF,EF,80,A9,40,81,80,81,40,71,4F,01,01,01,01,01,01,01,01,28,3C,80,A0,70,B0,23,40,30,20, 
  36,00,06,44,21,00,00,1A,00,00,00,FD,00,38,4B,1E,51,11,00,0A,20,20,20,20,20,20,00,00,00,FC,00,53, 
  79,6E,63,4D,61,73,74,65,72,0A,20,20,00,00,00,FF,00,48,56,5A,53,41,30,33,31,39,37,0A,20,20,00,49 
```

Next is the output of read-edid after rebooting to Hardy:

```
 sudo get-edid > edid.bin
get-edid: get-edid version 1.4.1

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
de@de-desktop:~$ cat edid.bin | parse-edid
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

    # EDID version 255 revision 255
Section "Monitor"
    Identifier "___:ffff"
    VendorName "___"
    ModelName "___:ffff"
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
EndSection

```

Not sure why the error msgs above, packages downloaded and installed like a charm with no error msgs. The only anomaly I noticed during the install was
"Selecting previously deselected package read-edid." and I'm certain that I never installed this package before unless it was a dependency for something else that I have since uninstalled.
Perhaps you or anyone else may be able to glean something useful from the above.
Good luck and I'll continue the quest...
Side

---

### Post by jellyfisharepretty on 2010-01-02
Good news! I am typing this message in Ubuntu, running at 1920x1200@59.95Hz, on DVI cable :)  For me, this resolution does not even work in Windows.

Side: As I wrote before, I also had a bit of trouble using read-edid.  Use the nvidia-settings utility to get the EDID :

System -> Administration -> NVIDIA X Server Settings -> DFP-1 - (Samsung SyncMaster) -> Acquire EDID

Then you can use parse-edid to read the file.

Ok, so here's what I did to finally get my screen running at 1920x1200.  First I downloaded vitorgr's edid binary file (see a few post earlier in the thread).  Saved it as /home/jelly/t240hd.bin. He says he has the same monitor as us, but when I parse his EDID file, I get:
```
	HorizSync 26-81
	VertRefresh 24-75
```

While the T240HD manual from Samsung says it's rather 30 - 81 and 56 - 75.  I wanted to make sure I didn't bust anything, hardware-wise, so I forced the values the Samsung manual specifies.  I also calculated the correct DPI (94 x 95) for the T240HD and specified those values.  Here is the relevant portions of xorg.conf :

```
Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Samsung"
	ModelName      "T240HD"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView"       "FALSE"
        Option 	       "CustomEDID" 	"DFP:/home/jelly/t240hd.bin"
	Option         "UseEdidFreqs"   "FALSE"
	Option	       "UseEdidDpi"	"FALSE"
	Option	       "ModeDebug"	"TRUE"
	Option	       "DPI"	        "94 x 95"
	Option         "NoLogo"         "TRUE"
	Option         "Coolbits"       "TRUE"
	Option         "TripleBuffer"   "TRUE"
	DefaultDepth	24
EndSection
```

The option ModeDebug tells the nvidia driver to write all sorts of interesting information about mode validation in the X11 log file.  I found that in /var/log/xorg.0.log.  I highly recommend you activate it and have a look.  There is also a parsed version of the EDID in that log file.

"UseEdidFreqs" "FALSE" tells the driver to use my user-specified values in the monitor section rather than the EDID values.  "UseEdidDpi" "False" is the same but for the DPI setting.

"CustomEDID" tells the driver to use a specific file.  USE WITH CARE.  If you use the wrong file for your monitor it could damage it.  Change the path specified in the option to what you need.

I still don't understand why you can't get to 1920x1200 in Ubuntu, Side...  Hopefully with what I've written here, you can debug your problem.  Start by studying the X11 log file after setting Option "ModeDebug" "TRUE".

Now, all that's left is to find how to force these settings in Windows, so I can play games at 1920x1200 :)

I'll leave the thread status to UNSOLVED for now since you're still having problems. Good luck !

---

### Post by Sidewinder1 on 2010-01-03
Hey Jelly, congrats on your accomplishment and many thanks for your efforts on my behalf! It's due to people like you and the other useful posters on this forum (and the Mods whose tireless and totally voluntary efforts have *not* gone unnoticed) that I fell in love with ubuntu back in 2007 and have never looked back.
Since I'm running Hardy I don't have an "Nvidia X Server Setting" choice under System--->Administration, or anywhere else for that matter. While I am somewhat comfortable editing the xorg.conf file with the proper values, since: **A**: I'm currently getting 1600X1200 @50 Hz (which is the same res. I had with my old monitor and loved it) and **B**: I'm an old fart, currently viewing this screen with my "cheater", reading glasses and a smaller font would require my increasing the strength of said glasses and most importantly, **C:** (" USE WITH CARE.  If you use the wrong file for your monitor it could damage") I don't want to risk smokin' my new monitor. I'll try not to be a hog and just be satisfied with what I've got.
Again, thanks so much for your efforts and best of luck in all of your future endeavors!
Side

---

### Post by jellyfisharepretty on 2010-01-05
Ok then, I'll change the status to SOLVED. Hopefully this will help someone with the same problem.

Just know that you can use sudo nvidia-settings to get to the nvidia utility even if you don't have the System -> Administration -> ... way of getting to the shortcut.

jelly

---

### Post by Sidewinder1 on 2010-01-07
> **jellyfisharepretty said:**
> Ok then, I'll change the status to SOLVED. Hopefully this will help someone with the same problem.

Just know that you can use sudo nvidia-settings to get to the nvidia utility even if you don't have the System -> Administration -> ... way of getting to the shortcut.

jelly

That's certainly nice to know; in a month or so when everything's running smoothly and I'm feelin' a little frisky, I may just try that command. Again, many thanks!
Side

---

### Post by Sidewinder1 on 2010-01-07
Just for poops and giggles, this was the result of that command:
```
sudo: nvidia-settings: command not found
```
Guess it was just "not to be".
Side

---

### Post by jellyfisharepretty on 2010-01-14
Oops, looks like I may have misguided you...  But the command does work for me.  Probably since you're using an older version of Ubuntu, you also have an older version of the nvidia drivers which doesn't have the nvidia-settings utility?  Maybe somebody more familiar with the nvidia drivers could answer you.

---

### Post by AxlDLuffy on 2010-05-21
Hi Jelly, vitorgr and everybody else.
I have the same problem as you had, only my monitor is the Samsung P2370. 
Before I can be more detailed let me tell you this, Here's the thing with my monitor. Even in Windows I cannot achieve 1920x1080. 
To do that I have to install the Monitor driver found here ([http://bit.ly/aFULK6](http://bit.ly/aFULK6)). After the installation, 1920x1080@60 is available. I tried dozens of modifications to the xorg.conf with no result. The maximum resolution I can get is 1600x1200. Then I learned that Samsung does not support Linux. 

**Yeah, great work Samsung, but that's ok, just to be clear my next monitor WON'T be Samsung.** But anyway.

I've searched and searched google for similar problems but noone seemed to have the solution to the problem. Untill, **YOU CAME Jellyfish!!!** :D Seeing your updated post got my hopes up! So I'm begging you or anyone who has an idea, to help me solve this problem. The thing is that I'm an inexperienced Linux user, so I have a lot of data in my hands but I'm not sure how to use it... 

First things first. Here are the full specs of my monitor:

```
Model Name		SyncMaster P2370, P2370G
Size 			23 inch (58 cm)
Display area 		509.76 mm (H) x 286.74 mm (V)
Pixel Pitch 		0.2655 mm (H) x 0.2655 mm (V)

Synchronization

Horizontal		30 ~ 81 kHz
Vertical 		56 ~ 60 Hz

Display Color		16.7 M

Resolution
Optimum resolution 	1920x1080@60Hz
Maximum resolution 	1920x1080@60Hz

Input Signal, Terminated

DVI(Digital Visual Interface)- I
0.7 Vp-p ±5 %
Separate H/V sync, Composite, SOG
TTL level (V high ? 2.0 V, V low ? 0.8 V)

Maximum Pixel Clock
164MHz (Analog,Digital)

Dimensions (W x H x D) / Weight (Simple Stand)
571 x 364.5 x 47 mm / 22.5 x 14.4 x 1.9 inch (Without Stand)
571 x 423 x 190 mm / 22.5 x 16.7 x 7.5 inch (With Stand) / 4.1 kg / 9.0 Ibs

Preset Timing Modes
Display Mode 	 | Horizontal| Vertical | Pixel   | Polarity  		                Sync             | Frequency | Frequency| Clock   | (H/V)
		 | (Hz)	     |	(kHz)	| (MHz)	  | 	
VESA, 640 X 480  | 31.469    |  59.940 	|  25.175 |  -/-
VESA, 800 X 600  | 35.156    |  56.250 	|  36.000 |  +/+
VESA, 800 X 600  | 37.879    |  60.317 	|  40.000 |  +/+
VESA, 1024 X 768 | 48.363    |  60.004  |  65.000 |  -/-
VESA, 1280 X 800 | 49.702    |  59.810 	|  83.500 |  -/+
VESA, 1280 X 960 | 60.000    |  60.000 	|  108.000|  +/+
VESA, 1280 X 1024| 63.981    |  60.020  |  108.000|  +/+
VESA, 1440 X 900 | 55.935    |  59.887  |  106.500|  -/+
VESA, 1600 X 1200| 75.000    |  60.000 	|  162.000|  +/+
VESA, 1680 X 1050| 65.290    |  59.954 	|  146.250|  -/+
VESA, 1920 X 1080| 67.500    |  60.000 	|  148.500|  +/+
```

Here's my xorg.conf after a clean install of Ubuntu 10.04:

```
Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
EndSection
```

Also a fellow member in the Ubuntu-gr forums had the idea to open the inf file of the monitor driver so we can check the modelines which Samsung uses and force them into Ubuntu. That seemed a great idea only it didn't work, propably due to my inexperience. Here are the contents of the inf file: 

```
;==================================================

; SMP2370.inf 12/29/2008 ver. 3.0HC

;

; Copyright 2008 Samsung Electronics Corporation

;

; This is a Setup information file for Samsung Monitor. 

;==================================================



[Version]

signature="$CHICAGO$"

Class=Monitor

ClassGuid={4D36E96E-E325-11CE-BFC1-08002BE10318}

Provider=%Samsung%

CatalogFile=SMP2370.cat

DriverVer=12/29/2008,3.0



;--------------------------------------------------



[ControlFlags]

ExcludeFromSelect.nt=Monitor\SAM0529

ExcludeFromSelect.nt=Monitor\SAM052A



[ClassInstall32]

AddReg=ClassAddReg32



[ClassAddReg32]

HKR,,,,%MonitorClassName%

HKR,,Icon,,"-1"

HKR,,NoInstallClass,,1



[DestinationDirs]

DefaultDestDir = 11

SMP2370a.CopyFiles = 23

SMP2370d.CopyFiles = 23



[SourceDisksNames]

1=%DISK%,,,



[SourceDisksFiles]

SMP2370.icm=1



[Manufacturer]

%Samsung%=Samsung,NTx86,NTAMD64



; Manufacturer sections

;-----------------------------------------------------

[Samsung]

%SMP2370a%=SMP2370a.Install, Monitor\SAM0529

%SMP2370d%=SMP2370d.Install, Monitor\SAM052A



; Manufacturer sections

;-----------------------------------------------------

[Samsung.NTx86]

%SMP2370a%=SMP2370a.Install, Monitor\SAM0529

%SMP2370d%=SMP2370d.Install, Monitor\SAM052A



; Manufacturer sections

;-----------------------------------------------------

[Samsung.NTAMD64]

%SMP2370a%=SMP2370a.Install, Monitor\SAM0529

%SMP2370d%=SMP2370d.Install, Monitor\SAM052A



; Install Sections

;-----------------------------------------------------



[SMP2370a.Install]

DelReg=DEL_CURRENT_REG

AddReg=SMP2370a.AddReg, 1920, DPMS

CopyFiles=SMP2370a.CopyFiles



[SMP2370d.Install]

DelReg=DEL_CURRENT_REG

AddReg=SMP2370d.AddReg, 1920, DPMS

CopyFiles=SMP2370d.CopyFiles



; Addreg & DelReg sections

;-----------------------------------------------------



[DEL_CURRENT_REG]

HKR,MODES

HKR,,MaxResolution

HKR,,DPMS

HKR,,ICMProfile





[1920]

HKR,,MaxResolution,,"1920,1080"





[DPMS]

HKR,,DPMS,,1



; AddReg sections

;-----------------------------------------------------





[SMP2370a.AddReg]

HKR,"MODES\1920,1080",Mode1,,"30-81,56-61,+,+"

HKR,,ICMProfile,0,"SMP2370.icm"



[SMP2370d.AddReg]

HKR,"MODES\1920,1080",Mode1,,"30-81,56-61,+,+"

HKR,,ICMProfile,0,"SMP2370.icm"

;------------------------------------------------------



[SMP2370a.CopyFiles]

SMP2370.icm



[SMP2370d.CopyFiles]

SMP2370.icm



;------------------------------------------------------



[Strings]

DISK="Samsung Monitor Installation Disk"

MonitorClassName="Monitor"

Samsung="Samsung"

SMP2370a="SyncMaster P2370/P2370G(Analog)"

SMP2370d="SyncMaster P2370/P2370G(Digital)"
```

Any ideas of how to configure the xorg.conf to achieve 1920x1080 resolution? Please, I'm desperate...

Thank you in advance and excuse my poor english.
Greetings from Greece!

---

### Post by jellyfisharepretty on 2010-05-23
Hi Luffy,

Sorry for the delay in responding.  And don't worry about your English, I am not native English too :)

I have to say I'm not too happy with Samsung as well.  But regarding your problem, I wonder if it's really the same as mine.  I cannot even get to 1920x1200 in Windows using the Samsung driver for my monitor.  I can only get to that in Linux using the CustomEDID option of the NVIDIA drivers.  Strange thing to say, but I wish NVIDIA Windows' drivers were as good as their linux ones.

Anyway, here's what I would try if I were you:
[LIST=1]
[*]Try to find someone with the same monitor, but working at the correct resolution.  Maybe they can download the EDID (in binary format) and give it to you.  I was lucky, because someone in this thread replied with the EDID file for my monitor, so I used that.  That person could either use get-edid utility on Ubuntu to save the EDID to a file, or could use [_Monitor Asset Manager_]("http://www.entechtaiwan.com/util/moninfo.shtm") on Windows to do the same.
[*]Use [_Pheonix EDID designer_]("http://www.tucows.com/preview/329441") to make your own EDID.  That's a Windows program that I believe will allow you to write your own EDID.  You should be able to do it from the specs you posted.
[*] Assuming you have an NVIDIA card, force the drivers to use that EDID. See my [_earlier post_]("http://ubuntuforums.org/showpost.php?p=8598372&postcount=18").
[/LIST]

Just a word of caution, if you force the wrong EDID, with the wrong specs, it could damage your monitor, or so I've read, so please be extra careful.

Good luck and let me know how it turns out!

---

### Post by AxlDLuffy on 2010-05-23
> **jellyfisharepretty said:**
> Hi Luffy,

Sorry for the delay in responding.  And don't worry about your English, I am not native English too :)

I have to say I'm not too happy with Samsung as well.  But regarding your problem, I wonder if it's really the same as mine.  I cannot even get to 1920x1200 in Windows using the Samsung driver for my monitor.  I can only get to that in Linux using the CustomEDID option of the NVIDIA drivers.  Strange thing to say, but I wish NVIDIA Windows' drivers were as good as their linux ones.

Anyway, here's what I would try if I were you:
[LIST=1]
[*]Try to find someone with the same monitor, but working at the correct resolution.  Maybe they can download the EDID (in binary format) and give it to you.  I was lucky, because someone in this thread replied with the EDID file for my monitor, so I used that.  That person could either use get-edid utility on Ubuntu to save the EDID to a file, or could use [_Monitor Asset Manager_]("http://www.entechtaiwan.com/util/moninfo.shtm") on Windows to do the same.
[*]Use [_Pheonix EDID designer_]("http://www.tucows.com/preview/329441") to make your own EDID.  That's a Windows program that I believe will allow you to write your own EDID.  You should be able to do it from the specs you posted.
[*] Assuming you have an NVIDIA card, force the drivers to use that EDID. See my [_earlier post_]("http://ubuntuforums.org/showpost.php?p=8598372&postcount=18").
[/LIST]

Just a word of caution, if you force the wrong EDID, with the wrong specs, it could damage your monitor, or so I've read, so please be extra careful.

Good luck and let me know how it turns out!

Jelly thank you for your reply.

About the Monitor Asset Manager and Phoenix EDID Designer, my limited knowledge about monitors doesn't help me. Especially with PED, I don't want to try anything cause I'm too afraid of the consequences. 

Also I have an ATI card so would that be possible?

I guess I'm gonna try the first thing you suggested, to find someone with the same monitor and take from him the EDID in binary. I'm gonna start a new thread right now.

Thank you again for your time. :)

---

### Post by AxlDLuffy on 2010-05-27
I'm proud to announce that the problem is solved. Here's what I did:

```
$ xrandr
$ xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
$ xrandr --addmode CRT2 1920x1080_60.00
$ nano /etc/gdm/PreSession/Default
```

   and added in the end of the files these lines:

   ```
$ xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	$ xrandr --addmode CRT2 1920x1080_60.00
```

I used these sites:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)
[http://www.mythtv.org/wiki/Modeline_Database#CVT_modelines](http://www.mythtv.org/wiki/Modeline_Database#CVT_modelines)

Thank you all for your help!

---

### Post by kedar.mhaswade@gmail.com on 2010-08-06
So much of information on this topic. Thank you for the details.

When I encountered this problem, I too searched high and low. It was totally confusing why Ubuntu 10.04 wouldn't use the entire 24" screen real estate. It would annoyingly leave about 1.5" from both the right and left edges of my Samsung T240HD. 

I did everything suggested with EDID, nvidia-settings etc. but to no avail. 

Suddenly, I pressed the "Reset" button on the Remote control that came with the monitor. Voila! The windows expanded, resolution got fixed and I am a happy Samsung user now.

-Kedar

---

### Post by jellyfisharepretty on 2010-08-07
Hi Kedar,
Either way, I am glad you could solve your problem.  I don't believe I tried this reset button, so I'll give that a try, because I still can't run the monitor at 1920x1200 in windows, only in Ubuntu :)
Jelly

---

### Post by gUzAnO on 2010-08-31
Hi guys, i get here by googling a big headache with my gf's T240HD+CQ50-101 la+ GF 8200M on Ubuntu 9.10.

First of all i read all the threads "trying" to understand something, i'm new to Ubuntu, and understand some basics of linux platform. So i hope you can help me, guiding me to solve this nasty problem, so far i know this:

Laptop CQ50-101la
GeForce 8200M
T240HD
She uses VGA Analog cable only.

What we want to do is basically to get the HD resolution to watch HD Movies, she now uses it as a single TV, BTW we live in SouthAmerica, in Chile to be more specific, now here's the problem:

When switching to the T240HD, the image gets cropped so i can't fully see the whole desktop on it, but when aiming the mouse to the "cropped area" the whole image moves, as if you were using Windows Augment Lens app.

How can we get the T240HD to work properly and watch movies in HD Format? Please be patient and simple on your explanations, hope not to trouble you too much, and i'm terribly sorry if my english isn't very accurate :D hope you guys're doing well


greetz!

---

### Post by jellyfisharepretty on 2010-09-04
Hey guzano,

Sorry that I reply so late after your message.  The cropped area effect (windows augment) I what I have seen in windows when the OS determines that the resolution attempted by the video card is larger than what the monitor supports.

This happened, in my case, because my T240HD was "telling" windows it supports a maximum of 1680x1050, yet I was forcing the nvidia driver to try a resolution of 1920x1200.  So the cropped area effect -- or panning as I call it -- happened.

I've never seen it under Ubuntu though.  Please tell me if you can at least run your T240HD at 1920x1200 in windows.  If you want, try the following commands, and post the results:

Go to System -> Administration -> NVIDIA X Server Settings -> DFP-1 - (Samsung SyncMaster) -> Acquire EDID

(make sure you are using nvidia binary drivers under Ubuntu)

Save the file as edid.bin (say, in your home directory), then read it using these commands in a terminal window

```
cd
sudo apt-get install read-edid
cat edid.bin | parse-edid
```

Good luck and ):P from Canada

---

### Post by frenzy3 on 2012-01-29
none of this worked for me 

/ # xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

---

