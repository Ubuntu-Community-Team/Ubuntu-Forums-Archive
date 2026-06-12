---
title: "Lubuntu screen resolution problem, Acer monitor"
date: 2015-11-11
forum: Hardware
---

### Post by LostInUA on 2015-11-11
Hi,

I've been using Lubuntu on an older desktop machine pretty happily for about six months now (previously used Kubuntu on my laptop). Recently I've run into a frustrating, and really flaky issue with xrandr. From time to time upon logging in I find that my screen resolution has changed. My monitor looks best with a 5:4 aspect ratio, so I use 1280x1024. Thing is, when I go to set my resolution back to the previous setting, that choice isn't there in the Monitor Settings! So I'm stuck with the next best choice - 1152x864 - which is ok, but just a tiny bit vertically stretched. After some amount of time (days, hours) 1280x1024 reappears as a choice in the Monitor Settings. Weird huh? 

So far I've tried editing my autostart file:

```
@xrandr --auto --output VGA-0 --primary --mode 1280x1024
```

... No luck. 

Any ideas?

---

### Post by LostInUA on 2015-11-17
Nothin'?

---

### Post by blm-ubunet on 2015-11-17
That flakyness from time to time .. is that just logging from screensaver or cold reboot & login?
If you log out (to the greeter) & login does this fix the problem or create one?

VGA, DVI & HDMI use a serial connection for DDC/EDID. AFAIK Historically this has been unreliable over VGA for some h/w.
You could remove the --auto from your xrandr command but think it is harmless..

What's the output from "xrandr" with no options?
If "1280x1024" is not in the video mode pool for that port then you can't select it as the active mode.
```
xrandr --addmode VGA-0 1280x1024
xrandr --output VGA-0 --mode 1280x1024 --primary
```
Post your /var/log/Xorg.0.log as attachment.

Which desktop manager do you run?
Gnome's gdm performs lots of messing around with "xrandr --auto" at points in greeter/login stage.

---

### Post by LostInUA on 2015-11-20
> **blm-ubunet said:**
> That flakyness from time to time .. is that just logging from screensaver or cold reboot & login?
If you log out (to the greeter) & login does this fix the problem or create one?

I can't say for sure, but I'm pretty sure it's just logging in/out (not a cold start + login). At this point I've been stuck with 1152x864 as the next best thing for over a week. 

> **blm-ubunet said:**
> What's the output from "xrandr" with no options?
If "1280x1024" is not in the video mode pool for that port then you can't select it as the active mode.
```
xrandr --addmode VGA0 1280x1024
xrandr --output VGA0 --mode 1280x1024 --primary
```
Post your /var/log/Xorg.0.log as attachment.

Which desktop manager do you run?
Gnome's gdm performs lots of messing around with "xrandr --auto" at points in greeter/login stage.

Here's my xrandr output: 

```
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96    59.80  
   1152x864      60.00* 
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
```

As you can see 1280x1024 isn't there at the moment. I am also getting a totally different resolution at the login screen (looks like 800x600). The switch to the desktop environment settings is pretty noticeable. I'm not really sure what desktop manager I'm running - I suppose whatever is included by default in the latest release.

Thanks!

---

### Post by blm-ubunet on 2015-11-20
Likely your monitor is a cheap HD-ready 16:9 TV panel so resolution could be 1360x768 or 1366x768 or 1368x768 with unusual pixel aspect ratio.
```
xrandr --output VGA-0 --mode 1360x768 --primary
```
Possible the display does not allow native resolution over VGA (common TV trick).
To be sure, need to see the Xorg log file...

---

### Post by LostInUA on 2015-11-20
Having trouble uploading Xorg.0.log - the uploader keeps telling me it's an invalid file. Can you tell me what I should look for in there?

---

### Post by blm-ubunet on 2015-11-20
These silly forums only understand windows file types by extensions (dangerous/primitive & ironic?). You need to rename the file "Xorg.0.log.txt".

Note that my code example has correct name "VGA-0" & not "VGA0".
did you try that?

---

### Post by LostInUA on 2015-11-20
> **blm-ubunet said:**
> These silly forums only understand windows file types by extensions (dangerous/primitive & ironic?). You need to rename the file "Xorg.0.log.txt".

Note that my code example has correct name "VGA-0" & not "VGA0".
did you try that?

I re-named the file as you suggested - it's over the 19KB attachment limit for that file type at 44.3KB, yeesh. This forum is odd :rolleyes:

I tried that code you put up, but got:  
```
xrandr: cannot find mode "1280X1024"
``` 
It would seem my monitor doesn't support 1280x1024, but it does... Just not all the time for some reason.

---

### Post by blm-ubunet on 2015-11-20
I did not put up any code suggesting/using 1280x1024 video mode or "1280X1024" video mode name (capital "X").
Native resolution (& 4:4:4 video) is the only way to use a DFP display on a computer, if the aspect ratio is then odd/wrong then you fix it with another setting.

---

### Post by LostInUA on 2015-11-20
> **blm-ubunet said:**
> I did not put up any code suggesting/using 1280x1024 video mode or "1280X1024" video mode name (capital "X").
Native resolution (& 4:4:4 video) is the only way to use a DFP display on a computer, if the aspect ratio is then odd/wrong then you fix it with another setting.

Woops, I meant 1280x1024 with a lower case x.

Anyways, I got back to 1280x1024 by resetting the monitor manually - 1280x1024 just reappeared as an option in monitor settings after reset. Now xrandr gives me this: 

```
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 8192 x 8192DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00    60.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
``` 

Now we'll see how long it lasts this time. So far it's made it through a reboot and logout/login. I'd still like to get to the root of the problem, but I have a feeling it's got something to do with the monitor, and less to do with xrandr/lubuntu.

---

### Post by blm-ubunet on 2015-11-20
A 4:3 15" LCD display from 10years ago might be expected to be 1280x1024..
Is your display that old?

Possible reasons for the wrong mode (1280x1024):
- vesa driver (max res.)
- limited function VGA input on TV (or not set to PC input mode)
- monitor is old 4:3 14" or 15" CRT or LCD.

The Xorg log file clarifies kernel/kernel-options/Xorg/display/EDID-probing etc..

---

### Post by LostInUA on 2015-11-21
I think this display could easily be that old - it's been traded around the family for awhile. We live in Ukraine, so you never know - it could just be something cheap they made to sell in developing markets ;) It's basically an almost-but-not-quite-square 17 in. panel.

This set of messages shows up in Xorg.0.log a couple of times:

```
[  2140.779] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display[  2140.779] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[  2140.779] (**) NVIDIA(0):     all display devices.)
[  2140.863] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-1 is invalid: the
[  2140.863] (WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
[  2140.863] (--) NVIDIA(GPU-0): 
[  2140.863] (--) NVIDIA(GPU-0): Raw EDID bytes:
[  2140.863] (--) NVIDIA(GPU-0): 
[  2140.863] (--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  04 72 49 ad 7d 5f 32 81
[  2140.863] (--) NVIDIA(GPU-0):   0d 12 01 03 68 26 1e 6b  2a 67 60 a2 5a 49 9e 23
[  2140.863] (--) NVIDIA(GPU-0):   13 50 54 bf ef 00 81 8f  81 80 71 4f 71 40 61 4f
[  2140.863] (--) NVIDIA(GPU-0):   61 40 76 4f 45 40 30 2a  00 98 51 00 2a 40 30 70
[  2140.863] (--) NVIDIA(GPU-0):   13 00 78 2d 11 00 00 1e  00 00 00 ff 00 4c 34 39
[  2140.863] (--) NVIDIA(GPU-0):   30 38 36 30 34 34 32 48  4d 0a 00 00 00 fd 00 37
[  2140.863] (--) NVIDIA(GPU-0):   4b 1e 53 0e 00 0a 20 20  20 20 20 20 00 00 00 fc
[  2140.863] (--) NVIDIA(GPU-0):   00 41 63 65 72 20 41 4c  31 39 31 36 0a 20 00 af
[  2140.863] (--) NVIDIA(GPU-0): 
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  2140.863] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
```

looking at the end of the file there are lot of messages like this:

```
[   794.928] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   794.928] (**) NVIDIA(0):     device Acer AL1916 (CRT-1) (Using EDID frequencies has
[   794.928] (**) NVIDIA(0):     been enabled on all display devices.)
[   795.097] (II) NVIDIA(GPU-0): Display (Acer AL1916 (CRT-1)) does not support NVIDIA 3D
[   795.097] (II) NVIDIA(GPU-0):     Vision stereo.
```

And the very last set of entries:

```
[  1182.684] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1182.684] (**) NVIDIA(0):     device Acer AL1916 (CRT-1) (Using EDID frequencies has
[  1182.684] (**) NVIDIA(0):     been enabled on all display devices.)
```

---

### Post by blm-ubunet on 2015-11-21
You're right it is that old & 4:3 aspect & its native resolution is 1280x1024.
But it is reliable!

Probably the thing that will stop it working (eventually) is failure of electrolytic capacitors in the SMPS.
[https://www.ifixit.com/Guide/Acer+AL1916+Power+Supply+Board+Replacement/6762](https://www.ifixit.com/Guide/Acer+AL1916+Power+Supply+Board+Replacement/6762)

When you said "reset the monitor manually" is that by using the monitor OSD/menu or power cycling?

Notice the nvidia driver calls the connected monitor/port CRT-1 but your xrandr calls it VGA-0.
I recall that older nvidia graphics cards had unreliable EDID probing over VGA. Maybe it was drivers or the hardware..

I made an error in Post#3 where I used "VGA0" instead of "VGA-0".
Your xrandr reports the monitors as LVDS-1, VGA-0 etc.
My intel GPU PC xrandr reports them as LVDS1, VGA0.

So you needed to use this:
```
xrandr --addmode VGA-0 1280x1024
xrandr --output VGA-0 --mode 1280x1024 --primary
```

---

### Post by LostInUA on 2015-11-24
As far as monitors go there's really nothing wrong with it :) it's the right size for the spot where it stands, and it always works. Just a bit of a strange problem with the resolution setting. When I said "reset the monitor" I meant by using the OSD, not a power cycle. I guess that wasn't clear. 

Regarding the Nvidia drivers, I'm currently using version 304.131, and I have a GeForce 210 graphics card. 

BTW - that monitor in the link you posted is exactly the same one I've got.

blm-ubunet - thanks for your help figuring this out!

---

