---
title: "Resolution issues"
date: 2012-06-22
forum: Hardware
---

### Post by mathew.s.hanley on 2012-06-22
Okay so I broke my laptop screen and since using it on my TV I don't want to get it fixed the only issue I have is when using ubuntu is I can't set my resolution correctly in windows its 1280x720 and it fits perfectly but in ubuntu I'm missing the edges. Everything else works. I'm using a packard bell tk-37 and my tv is a samsung 32 inch 720 HD

[IMG]https://lh5.googleusercontent.com/-XtCgHP5Pct4/T-TN2gZyT2I/AAAAAAAAC-U/cVwZEMcI_iM/s660/Capture.PNG[/IMG]

[IMG]https://lh6.googleusercontent.com/-KAcs0eJYqdY/T-Tzfy22pBI/AAAAAAAADAI/u4SeLEHofj4/s709/IMG_20120622_232834.jpg[/IMG]


Think I'm going to struggle to install this...

---

### Post by papibe on 2012-06-22
Hi mathew.s.hanley. Welcome to the forums!

Could you restart your computer with the TV connected, and then post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by mathew.s.hanley on 2012-06-22
> **papibe said:**
> Hi mathew.s.hanley. Welcome to the forums!

Could you restart your computer with the TV connected, and then post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```Please paste them separately here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/), and then post back the links here.

Regards.

Will do, I forgot to say I don't have ubuntu right now, I un-installed and just said I'd cope with windows but it's really annoying me, so I'll re-install asap!

Thanks!

---

### Post by papibe on 2012-06-22
Since you are on Windows right now, try getting the EDID info (in text format) from Windows using "[Phoenix EDID Designer]("http://www.tucows.com/preview/329441/Phoenix-EDID-Designer?q=Phoenix+EDID+Designer")".

You are looking for something like this:
```
EDID BYTES:
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 3A C4 00 04 00 00 00 00
10 | 2D 0C 01 03 80 20 18 00 EA A8 E0 99 57 4B 92 25
20 | 1C 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
30 | 01 01 01 01 01 01 48 3F 40 30 62 B0 32 40 4C C0
40 | 13 00 42 F3 10 00 00 1E 00 00 00 FC 00 4E 76 69
50 | 64 69 61 20 44 65 66 61 75 6C 00 00 00 FC 00 74
60 | 20 46 6C 61 74 20 50 61 6E 65 6C 00 00 00 00 FD
70 | 00 00 3C 1D 4C 11 00 00 20 20 20 20 20 00 00 9C
```

This data might be very useful later.
Regards.

---

### Post by mathew.s.hanley on 2012-06-22
It gave me a few different options but I'm going to assume it was for the one called "sam" something, since my tv is samsung  

```

EDID BYTES:
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 4C 2D 00 02 00 00 00 00
10 | 03 11 01 03 80 10 09 8C 0A E2 BD A1 5B 4A 98 24
20 | 15 47 4A 20 00 00 01 01 01 01 01 01 01 01 01 01
30 | 01 01 01 01 01 01 01 1D 00 72 51 D0 1E 20 6E 28
40 | 55 00 A0 5A 00 00 00 1E 01 1D 00 BC 52 D0 1E 20
50 | B8 28 55 40 A0 5A 00 00 00 1E 00 00 00 FD 00 32
60 | 3D 0F 2E 08 00 0A 20 20 20 20 20 20 00 00 00 FC
70 | 00 53 41 4D 53 55 4E 47 0A 20 20 20 20 20 01 D4

```

---

### Post by papibe on 2012-06-22
It looks good. This is the data converted to binary and read by a edid parser:
```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SAMSUNG"
	VendorName "SAM"
	ModelName "SAMSUNG"
	# Block type: 2:0 3:fd
	HorizSync 15-46
	VertRefresh 50-61
	# Max dot clock (video bandwidth) 80 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1280x720"	# vfreq 60.000Hz, hfreq 45.000kHz
		DotClock	74.250000
		HTimings	1280 1390 1430 1650
		VTimings	720 725 730 750
		Flags	"+HSync" "+VSync"
	EndMode
	Mode 	"1280x720"	# vfreq 50.000Hz, hfreq 37.500kHz
		DotClock	74.250000
		HTimings	1280 1464 1504 1980
		VTimings	720 725 730 750
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

```

---

### Post by mathew.s.hanley on 2012-06-22
> **papibe said:**
> It looks good. This is the data converted to binary and read by a edid parser:
```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
    Identifier "SAMSUNG"
    VendorName "SAM"
    ModelName "SAMSUNG"
    # Block type: 2:0 3:fd
    HorizSync 15-46
    VertRefresh 50-61
    # Max dot clock (video bandwidth) 80 MHz
    # Block type: 2:0 3:fc
    # DPMS capabilities: Active off:no  Suspend:no  Standby:no

    Mode     "1280x720"    # vfreq 60.000Hz, hfreq 45.000kHz
        DotClock    74.250000
        HTimings    1280 1390 1430 1650
        VTimings    720 725 730 750
        Flags    "+HSync" "+VSync"
    EndMode
    Mode     "1280x720"    # vfreq 50.000Hz, hfreq 37.500kHz
        DotClock    74.250000
        HTimings    1280 1464 1504 1980
        VTimings    720 725 730 750
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
EndSection

```

Great! Just got to wait for it to download 500kbp/s (don't move to UK) about 13 minutes left..

---

### Post by papibe on 2012-06-22
I see that you are having trouble with the resolution while installing it.

Try this:
[LIST]
[*]Boot into the installation media (CD or USB).
[*]Choose 'Try Ubuntu' instead of install.
[*]When you get into the desktop open a terminal and run this:
```
xrandr --newmode "1280x720_60.00"  74.25  1280 1390 1430 1650  720 725 730 750  +HSync +VSync
```
[*]And then:
```
xrandr --addmode CRT-0 "1280x720_60.00"
```
[/LIST]
If that does not work, please post the result of this command:
```
xrandr
```
Tell us how it goes.
Regards.

---

### Post by mathew.s.hanley on 2012-06-22
Nothing changed and I couldn't see about half my screen 

```

ubuntu@ubuntu:~$  xrandr --newmode"1280x720_60.00" 74.25 1280 1390 1430 1650 720725 730 750 +HSync +VSync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
ubuntu@ubuntu:~$ xrandr --addmode CRT-0 @1280x720_60.00@
xrandr: cannot find output "CRT-0"
ubuntu@ubuntu:~$ xrandr --addmode CRT-0m"1280x720_60.00"
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 8192 x 8192
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9* 
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 640x480+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       60.0 +   50.0  
   640x480        60.0* 
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)



```

---

### Post by papibe on 2012-06-22
Somehow you are **not** running the command that I gave you on post #8, but you are pasting options together so it gives you syntax error.

Regards.

EDIT: change CRT-0 for HDMI1 on the second command.

---

### Post by mathew.s.hanley on 2012-06-22
> **papibe said:**
> Somehow you are **not** running the command that I gave you on post #8, but you are pasting options together so it gives you syntax error.

Regards.

My mistake, I can't see half my screen so easy mistake to make I'll try again! Cheers for pointing it out!

---

### Post by papibe on 2012-06-22
Once you run successfully the first command, try adding the mode to both HDMI1 and LVDS1.

For example, this:
```
xrandr --addmode HDMI1 "1280x720_60.00"
```
or this:
```
xrandr --addmode LVDS1 "1280x720_60.00"
```

Regards.

---

### Post by mathew.s.hanley on 2012-06-22
```

ubuntu@ubuntu:~$ xrandr --newmode "1280x720_60.00" 74.25 1280 1390 1430 1650 720 725 730 750 +HSync +VSync
ubuntu@ubuntu:~$ xrandr --addmode CRT-0 "1280x720_60.00"
xrandr: cannot find output "CRT-0"
ubuntu@ubuntu:~$ xrandr --addmode HDMI1 "1280x720_60.00"
ubuntu@ubuntu:~$ xrandr --addmode LVDS1 "1280x720_60.00"
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 8192 x 8192
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9* 
   1280x720_60.00   60.0  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 640x480+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       60.0 +   50.0  
   640x480        60.0* 
   1280x720_60.00   60.0  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
ubuntu@ubuntu:~$ 


```

Still nothing...

---

### Post by papibe on 2012-06-22
Ok. The new 1280x720_60.00 is defined, and added.

Now try to set it this way:
```
xrandr --output HDMI1 --mode "1280x720_60.00"
```
or this:
```
xrandr --output LVDS1 --mode "1280x720_60.00"
```
Tell us how it goes.
Regards.

---

### Post by mathew.s.hanley on 2012-06-22
Success, almost

[IMG]https://lh6.googleusercontent.com/-_aV0bR6qvQk/T-UgvAyE2pI/AAAAAAAADBQ/epa3QSzuum8/s613/IMG_20120623_024431.jpg[/IMG]

It cuts the edges of the screen off, this was my original issue how do I fix this? I've tried to alter my tv settings and it only makes it worse so what can I do? I don't have this issue in windows...

---

### Post by papibe on 2012-06-22
):P getting closer!

That looks like [Overscan]("http://en.wikipedia.org/wiki/Overscan")

You have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet (some models need an undocumented procedure to disable it).

Second: I know you can solve this using the command xrandr itself.

Tell us how it goes,
Regards.

---

### Post by mathew.s.hanley on 2012-06-22
> **papibe said:**
> ):P getting closer!

That looks like [Overscan]("http://en.wikipedia.org/wiki/Overscan")

You have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet (some models need an undocumented procedure to disable it).

Second: I know you can solve this using the command xrandr itself.

Tell us how it goes,
Regards.

Nope nothing I can do on my tv to change it with windows there was something in the intel setting that allowed me to stretch and shrink the image I had to use that to get rid of it but since I did that it was fine on windows but even on boot and device selection menu at boot I have over scan, what's the xrandr command?

---

### Post by papibe on 2012-06-22
> **mathew.s.hanley said:**
> what's the xrandr command?

I'm not exactly sure. I don't much experience doing that since most of my experience is with Nvidia cards. Their driver has an easy-to-set-GUI option to correct overscan.

I found 3 ways people use to fix overscan using xrandr: [here]("http://forums.freebsd.org/archive/index.php/t-20987.html"), [here]("http://ubuntuforums.org/showthread.php?t=1849599&highlight=intel+overscan+xrandr&page=2"), and [here]("http://forums.overclockers.com.au/showthread.php?t=862388&page=10").

The second one looks promising. First let's say that the amount of pixels being "eaten" by overscan is 16 pixels in all directions.

Then to calculate the viewable size of the screen would be:```

1280 - 16 = 1264
720  - 16 = 704
```
Then you would do:
```
xrandr --output HDMI1 --fb 1264x704
xrandr --output HDMI1 --pos 16x16
```

Try that and let us know.
Regards.

---

