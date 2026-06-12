---
title: "M1300 Display rotation problem"
date: 2010-12-16
forum: Hardware
---

### Post by flaquito on 2010-12-16
I just installed Ubuntu 10.10 on a MotionComputing M1300 tablet. To my surprise, almost everything worked perfectly out-of-the-box, including the Wacom pen. However, I'm having problems getting the display rotation working. Here's what I've done:

-I created an xorg.conf file to load the intel xorg driver according to the instructions here: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

-I created a script to rotate the screen to the right based on the script here: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9920838&postcount=6](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9920838&postcount=6) (but modified to rotate 90 degrees).

When the script is run, the display rotates 90 degrees to the right, as it should. The pen and mouse inputs also rotate correctly. However, the display is shifted up about 256 pixels off the top of the screen. xrandr says that the resolution is 768x1024, which is what it should be. The cursor tracks correctly with the pen, but the logical pointer location is also shifted up by the same amount.

Any suggestions?

---

### Post by Favux on 2010-12-16
Hi flaquito,

Welcome to Ubuntu forums!

Could I see the rotation script you are using?  Also do you have Compiz enabled?

---

### Post by flaquito on 2010-12-16
> **Favux said:**
> Could I see the rotation script you are using?  Also do you have Compiz enabled?

Certainly. Here's the script:

```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet" Rotate CW
    xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
    xsetwacom set "Serial Wacom Tablet touch" Rotate CW
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
    /usr/bin/xmodmap -e "keycode 114 = Up NoSymbol Up NoSymbol Up"
    /usr/bin/xmodmap -e "keycode 111 = Left NoSymbol Left NoSymbol Left"
    /usr/bin/xmodmap -e "keycode 116 = Right NoSymbol Right NoSymbol Right"
    /usr/bin/xmodmap -e "keycode 113 = Down NoSymbol Down NoSymbol Down"
else
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" Rotate None
    xsetwacom set "Serial Wacom Tablet eraser" Rotate None
    xsetwacom set "Serial Wacom Tablet touch" Rotate None
    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
    /usr/bin/xmodmap -e "keycode 111 = Up NoSymbol Up NoSymbol Up"
    /usr/bin/xmodmap -e "keycode 113 = Left NoSymbol Left NoSymbol Left"
    /usr/bin/xmodmap -e "keycode 114 = Right NoSymbol Right NoSymbol Right"
    /usr/bin/xmodmap -e "keycode 116 = Down NoSymbol Down NoSymbol Down"
fi
```

I don't think that I have Compiz running -- my visual effects are set to normal.

---

### Post by flaquito on 2010-12-16
I thought it might be helpful to include a screenshot of the problem. Note that I left the cursor at the end of making that selection in Vim.

---

### Post by Favux on 2010-12-17
OK, then it isn't Compiz.  Let's get rid of touch.  Have you tried it without the panel resizing?
```
orientation=`xrandr --query | grep LVDS | awk '{print $4}'`

if [ "$orientation" = "(normal" ]; then
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet" Rotate CW
    xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
#    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 50
#    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 50
    /usr/bin/xmodmap -e "keycode 114 = Up NoSymbol Up NoSymbol Up"
    /usr/bin/xmodmap -e "keycode 111 = Left NoSymbol Left NoSymbol Left"
    /usr/bin/xmodmap -e "keycode 116 = Right NoSymbol Right NoSymbol Right"
    /usr/bin/xmodmap -e "keycode 113 = Down NoSymbol Down NoSymbol Down"
else
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" Rotate None
    xsetwacom set "Serial Wacom Tablet eraser" Rotate None
#    gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer 25
#    gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer 25
    /usr/bin/xmodmap -e "keycode 111 = Up NoSymbol Up NoSymbol Up"
    /usr/bin/xmodmap -e "keycode 113 = Left NoSymbol Left NoSymbol Left"
    /usr/bin/xmodmap -e "keycode 114 = Right NoSymbol Right NoSymbol Right"
    /usr/bin/xmodmap -e "keycode 116 = Down NoSymbol Down NoSymbol Down"
fi
```

---

### Post by flaquito on 2010-12-17
No difference. I actually had those lines commented out before I reformatted the code to paste it here. It does the same thing either way. (I just commented them out again to verify.) Getting rid of touch doesn't do anything, either.

---

### Post by Favux on 2010-12-17
Sounding like it's the video.  Which Intel chipset do you have?  What's your xorg.conf look like?  Let's look at your output of:
```
xrandr -q --verbose
```

---

### Post by flaquito on 2010-12-17
Graphics chipset is: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

xorg.conf is:
```
brent@ubuntu:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "RandRRotation" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Here's the output with the display in normal mode:
```
brent@ubuntu:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  13832602
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1024x768+0+0 (0x44) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x42
	Timestamp:  13832602
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	BACKLIGHT: 10 (0x0000000a)	range:  (0,10)
	Backlight: 10 (0x0000000a)	range:  (0,10)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1024x768 (0x43)   65.0MHz -HSync -VSync +preferred
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x768 (0x44)   94.5MHz +HSync +VSync *current
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x45)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x46)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x43)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x47)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x48)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x49)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x4a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4c)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4d)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x4e)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x4f)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x50)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x51)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x52)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x53)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
```

Here's the output when rotated:
```
brent@ubuntu:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 768 x 1024, maximum 2048 x 2048
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  14196850
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 768x1024+0+0 (0x44) right (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x42
	Timestamp:  14196850
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	BACKLIGHT: 10 (0x0000000a)	range:  (0,10)
	Backlight: 10 (0x0000000a)	range:  (0,10)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1024x768 (0x43)   65.0MHz -HSync -VSync +preferred
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x768 (0x44)   94.5MHz +HSync +VSync *current
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x45)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x46)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x43)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x47)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x48)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x49)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x4a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4c)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4d)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x4e)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x4f)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x50)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x51)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x52)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x53)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
```

---

### Post by Favux on 2010-12-17
Sure, it has to be the "nightmare" Intel chipset, doesn't it?  You could try a different set of lines like in method 1 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  As I recall without the verbose switch you can't quite count on the output.

But it's probably the video.  I vaguely recall a couple of lines we could try.  Was it the Intel that had something about buffer or memory allocation?

---

### Post by flaquito on 2010-12-17
Yeah, I don't think any of those other lines in that how-to will make much difference, since the script is executing properly.

I don't know anything about intel linux drivers... in the past I've always used ATI or NVidia. I haven't downloaded any third-party drivers -- are there others that I should try instead of the packaged drivers? Are there tweaks that I can make to this driver to make it work correctly?

Thanks for all your help, Favux.

---

### Post by Favux on 2010-12-17
Sure.  Well I'm not a video expert and I don't really know how things are in Maverick for the Intel.  I have a bunch of bookmarks, but they're dated.  Here's a few:

[http://ubuntuforums.org/showpost.php?p=7104256&postcount=1](http://ubuntuforums.org/showpost.php?p=7104256&postcount=1)  you might try the "MigrationHeuristic" "greedy" option for example.  Be sure to back up your xorg.conf and be prepared to restore it from the command line if you break X.

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver)

[http://ubuntuforums.org/showthread.php?t=1464239](http://ubuntuforums.org/showthread.php?t=1464239)

There was a good Motion thread.  1300 or 1400?  Not much activity lately.  I'll see if I can dig it up and if it has anything relevant.

---

### Post by Favux on 2010-12-17
Alright, priegog's thread on the Motion 1300 was the best:  [http://ubuntuforums.org/showthread.php?t=796359](http://ubuntuforums.org/showthread.php?t=796359)  But the thread didn't go past the ACPI breakage Jaunty caused.

---

### Post by flaquito on 2010-12-17
> **Favux said:**
> Alright, priegog's thread on the Motion 1300 was the best:  [http://ubuntuforums.org/showthread.php?t=796359](http://ubuntuforums.org/showthread.php?t=796359)  But the thread didn't go past the ACPI breakage Jaunty caused.

Genius! I had seen that thread, but somehow missed section 4.1. The Device section in my xorg.conf now looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"Intel"
	Option		"RandRRotation"	"on"
	Option		"NvAGP" 	"1"
	Option		"DRI"		"false"
EndSection
```

And it works!

Favux, thanks again for all of your help and your incredibly quick responses. I appreciate it.

-Brent

---

