---
title: "installing ATI drivers"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by spa79 on 2006-11-19
Hi,

I have had many problems to get the ATI X1300 drivers (using xorg) working on Edgy and have followed many instructions on the web. I guess I am close to get it working, but for the following issue:

The "glxinfo" and "fglrxinfo" outputs seem to be fine. However, when I run "glxgears" or "fgl_glxgears", I don't actually see the gears spinning. What would that mean ?

>glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
...
...
...

>flgrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6011 (8.28.8)

>fgl_glxgears
Using GLX_SGIX_pbuffer
2945 frames in 5.0 seconds = 589.000 FPS
...
...

>modprobe fglrx
does not give any output.

> lsmod | grep fglrx
fglrx     406988  8 
agpgart    34888  2 fglrx,intel_agp


Please kindly advice.

Thanks much,

---

### Post by chaosgeisterchen on 2006-11-19
Did you already try out [this HowTo](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)?

---

### Post by spa79 on 2006-11-20
Yes, I did try method 1.

---

### Post by spa79 on 2006-11-20
Here is some information (from the same link: method 1). I don't understand the cause of the *ERROR*:

> dmesg | grep fglrx
[17179585.204000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179585.204000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[17179585.204000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179594.324000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[17179594.328000] [fglrx] total      GART = 134217728
[17179594.328000] [fglrx] free       GART = 118226944
[17179594.328000] [fglrx] max single GART = 118226944
[17179594.328000] [fglrx] total      LFB  = 124305408
[17179594.328000] [fglrx] free       LFB  = 108843008
[17179594.328000] [fglrx] max single LFB  = 108843008
[17179594.328000] [fglrx] total      Inv  = 0
[17179594.328000] [fglrx] free       Inv  = 0
[17179594.328000] [fglrx] max single Inv  = 0
[17179594.328000] [fglrx] total      TIM  = 0

---

### Post by DonKyot on 2006-12-09
Hi,
I'm getting exactly that also.
Anyone know why?

Trying to get ATI/x1300pro working properly on a Dell Dimension 9200.
I've tried everything (i.e both fglrx & ATIs drivers) in 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
still no good :(

Just a thaught.
Could this be a 32/64 bit problem?
If I do 'sudo lspci -v' I get:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183 (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at dc00 [size=256]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
        Subsystem: Dell Unknown device 0303
        Flags: bus master, fast devsel, latency 0
        Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0


```
so maybe I should install the 64 bit ATI drivers?

---

### Post by Patrick-Ruff on 2006-12-09
worth a try I guess.

---

### Post by Choxo on 2006-12-11
Did it help?
I've got the same problem here with a Dimension 9200.

fglrxinfo
```

spitz@desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6011 (8.28.8)

```


lspci -v
```

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183 (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at dc00 [size=256]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
        Subsystem: Dell Unknown device 0303
        Flags: bus master, fast devsel, latency 0
        Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0

```


 dmesg | grep fglrx
```

[17179607.076000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179607.080000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[17179607.080000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17180942.228000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[17180942.232000] [fglrx] total      GART = 134217728
[17180942.232000] [fglrx] free       GART = 118226944
[17180942.232000] [fglrx] max single GART = 118226944
[17180942.232000] [fglrx] total      LFB  = 260960256
[17180942.232000] [fglrx] free       LFB  = 250474496
[17180942.232000] [fglrx] max single LFB  = 250474496
[17180942.232000] [fglrx] total      Inv  = 0
[17180942.232000] [fglrx] free       Inv  = 0
[17180942.232000] [fglrx] max single Inv  = 0
[17180942.232000] [fglrx] total      TIM  = 0
[17181436.536000] [fglrx:firegl_rmmap] *ERROR* map 0xf77e85d0 still in use (map_count=1)
[17181436.536000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf77e85c0 still mapped (user_handle = 0x00016000)
[17181436.540000] [fglrx:firegl_rmmap] *ERROR* map 0xf77e85d0 still in use (map_count=1), force it to be removed anyway
[17181436.540000] [fglrx:firegl_rmmap] *ERROR* map 0xf61b8650 still in use (map_count=1)
[17181436.540000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf61b8640 still mapped (user_handle = 0x00015000)
[17181436.540000] [fglrx:firegl_rmmap] *ERROR* map 0xf61b8650 still in use (map_count=1), force it to be removed anyway
[17181438.424000] [fglrx:firegl_rmmap] *ERROR* map 0xf61b84d0 still in use (map_count=1)
[17181438.424000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf61b84c0 still mapped (user_handle = 0x00012000)
[17181438.652000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17181438.692000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17181478.784000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[17181478.788000] [fglrx] total      GART = 134217728
[17181478.788000] [fglrx] free       GART = 118226944
[17181478.788000] [fglrx] max single GART = 118226944
[17181478.788000] [fglrx] total      LFB  = 260960256
[17181478.788000] [fglrx] free       LFB  = 250474496
[17181478.788000] [fglrx] max single LFB  = 250474496
[17181478.788000] [fglrx] total      Inv  = 0
[17181478.788000] [fglrx] free       Inv  = 0
[17181478.788000] [fglrx] max single Inv  = 0
[17181478.788000] [fglrx] total      TIM  = 0


```

glxgears doesn"t give anything gl_glxgears does give some output, but the screen is rather strange.
*Edit* glxgears -printfps does give now some fps scores in console, but i still doesn't see anything in the window that opens.
```
spitz@desktop:~$ glxgears -printfps
39369 frames in 5.0 seconds = 7868.958 FPS
1246 frames in 5.0 seconds = 249.184 FPS
1250 frames in 5.0 seconds = 249.984 FPS
38127 frames in 5.0 seconds = 7625.398 FPS
63081 frames in 5.0 seconds = 12616.117 FPS
62000 frames in 5.0 seconds = 12399.988 FPS
36057 frames in 5.0 seconds = 7209.654 FPS

```
```

spitz@desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
4138 frames in 5.0 seconds = 827.600 FPS
5002 frames in 5.0 seconds = 1000.400 FPS

```
glxgears opens a window but doesn't write anything in console.

This is my xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "be"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

Thanks!

---

### Post by DonKyot on 2006-12-11
> **Choxo said:**
> Did it help?
I've got the same problem here with a Dimension 9200.

Thanks!
I didn't try - Not comfortable that it's 'safe'.

You're "dmesg | grep fglrx" is even worse than mine (which is as spa79) & like you, I don't always get 'gears' output.

I did find this in /var/log/Xorg.0.log
> 
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON X1300 (RV516 7183) found
...
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

and searching for 'stuff' seems to show that the problem may be more than just faffing around with some parameters here and there...

... but I admit, I'm lost.


Maybe this is needed?
[http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)

---

### Post by fedecarra on 2006-12-12
same problem for me.

i have a dell dimension 9200, 4 gb ram, core 2 duo E6600, Chipset Intel®965, and ATI radeon x1300 256 mb, and ubuntu edgy 64bit.

i have correctly installed ati driver (i have tried all available versions and all installation methods), fglrxinfo works fine, 2d acceleration works fine, but **3d acceleration simply doesn't work**.

**fgl_glxgears and glxgears show correct output on the console, but black screen on the graphic window**.

i have also tried to install ubuntu edgy 32bit version, but the situation was the same.

after lot of searches, i found this issue:
if i write on a console:
# cat /proc/mtrr
reg00: base=0x00000000 ( 0MB), size=65536MB: write-back, count=1
reg01: base=0xbff00000 (3071MB), size= 1MB: uncachable, count=1
reg02: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1

here everything is wrong: the ram (i have 4gb not 64!!!), the video ram (256mb) etc.

it seems that the dell motherboard bios is not able to tell linux kernel the correct amount of ram (in spite of 4gb it reports exactly 16 times the amount: 64gb), and so the kernel is not able to handle agp aperture and graphic card amount of ram, disabling, as an issue, 3d rendering.
i flashed bios with latest version from dell, but nothing...

on google i found a lot of workarounds for this problem, but none seems to work with my dell hardware:
[http://www.rage3d.com/board/showpost.php?p=1333981360&postcount=18](http://www.rage3d.com/board/showpost.php?p=1333981360&postcount=18)
[http://www.rage3d.com/board/showthread.php?t=33867702](http://www.rage3d.com/board/showthread.php?t=33867702)
[http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)
[http://www.google.it/search?q=MTRR_END_BIT&ie=utf-8&oe=utf-8&rls=com.ubuntu:http://www.google.it/search?q=MTRR_END_BIT&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-aen-US:official&client=firefox-a](http://www.google.it/search?q=MTRR_END_BIT&ie=utf-8&oe=utf-8&rls=com.ubuntu:http://www.google.it/search?q=MTRR_END_BIT&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-aen-US:official&client=firefox-a)


I TRIED EVERYTHING!!!!


hope someone of you has some good idea to solve this problem.

](*,) 

federico

---

### Post by DonKyot on 2006-12-12
> **fedecarra said:**
> 
after lot of searches, i found this issue:
if i write on a console:
# cat /proc/mtrr
reg00: base=0x00000000 ( 0MB), size=65536MB: write-back, count=1
reg01: base=0xbff00000 (3071MB), size= 1MB: uncachable, count=1
reg02: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1

here everything is wrong: the ram (i have 4gb not 64!!!), the video ram (256mb) etc.
interesting - although I don't understand what the different fields mean.
for info.
I get, for 2Gig ram:
```
reg00: base=0x00000000 (   0MB), size=65536MB: write-back, count=1
reg01: base=0x7ff00000 (2047MB), size=   1MB: uncachable, count=1
reg02: base=0x80000000 (2048MB), size=2048MB: uncachable, count=1

```


Is this the same or different problem? Or an overlapping problem?

I tried the fix in:
[http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)

but it doesn't fix the grafix prolem :(

---

### Post by fedecarra on 2006-12-12
here is some more explanations about what mtrr fields mean:

[http://www.rage3d.com/board/showthread.php?t=33821469](http://www.rage3d.com/board/showthread.php?t=33821469)
[http://www.rage3d.com/board/showthread.php?threadid=33736241](http://www.rage3d.com/board/showthread.php?threadid=33736241)

as i said, i tried everything, and nothing worked, but if you want to give a try and get some results, please, let me know!!! i need 3d acceleration on my machine!

federico

---

### Post by Choxo on 2006-12-26
Ok guys,

I managed to get this in console when I hit cat /proc/mtrr ( I've got Dell Dimension 9200 with 2gig ram and Radeon X1300 with 256mb of RAM)
```

reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0xc0000000 (3072MB), size= 256MB: write-combining, count=5

```

Now, to be truly honest, I don't know if it is ok like this, but it seems much better than what I normally got:
```

eg00: base=0x00000000 (   0MB), size=65536MB: write-back, count=1
reg01: base=0x7ff00000 (2047MB), size=   1MB: uncachable, count=1
reg02: base=0x80000000 (2048MB), size=2048MB: uncachable, count=1

```

Now, for those who are still interested ( ** because it doesn't fix glxgears or other problems as far as I know ** ), this is the whay I did it:

First create script
```

sudo gedit /etc/init.d/fix_mtrr

```

Paste there the following :
```

#!/bin/sh
# Fix wrong MTRR setting
#Empty File  
echo "disable=0" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr 
echo "disable=2" >| /proc/mtrr 
#Set Correct settings:
#Possible Values:
#0x08000000 = 128Mb
#0x10000000 = 256Mb
#0x40000000 = 1Gb
#0x60000000 = 1.5Gb
#0x80000000 = 2Gb
# First Line : Main Memory ( my Case 2gb)
# Second Line : Video Card Mem  ( my case 256 mb)
# don't edit base=.... !!! 
echo "base=0x0 size=0x80000000 type=write-back" >| /proc/mtrr
echo 'base=0xd0000000 size=0x10000000 type=write-combining' >| /proc/mtrr

```

Save & Exit

give file exec permissions:
```

sudo chmod +x /etc/init.d/fix_mtrr

```

Last, create symlink:
```

sudo ln -s /etc/init.d/fix_mtrr /etc/rcS.d/S02fix_mtrr

```

Reboot system:
```

sudo shutdown -r now

```

Check if it worked with cat /proc/mtrr

Thanks to Rage 3D forums, I made this script copy pasting snipplets here & there on the forums...

Let me now if it worked for you...

( I'm tempering my hate against Dell for a while ;))

---

### Post by zolly on 2006-12-26
see [http://ubuntuforums.org/showthread.php?t=324794&highlight=acer](http://ubuntuforums.org/showthread.php?t=324794&highlight=acer)

---

### Post by Choxo on 2006-12-27
I can't see what's so different with other solutions?
I think I tried that solution for a xxx times...


Thanks anyway though...

---

### Post by DonKyot on 2006-12-27
well. Seems there are a few of us in the same situation. Which is reassuring in a way...

---

### Post by Choxo on 2006-12-27
I don't know...

I like ubuntu very much,
But the fact that I can't use my system for the 100% and there is really no Photoshop equivalent,
makes me look more and more direction Vista.
I know Compiz/Beryl & all the Eye Candy isn't necessary, but I don't buy a Dual Core with 2 gb to only have 2D Accelation, am I?
I want to be possible to run all applications, having a Dell or not...

I'm a bit frustrated as it seems that only a few ( maybe 5/6 persons) are suffering these problems...

Is there any indication that this problem will be solved in Feisty? And than I mean that the Generic Kernel is used standerd ( First I were not aware that I was using only 1 proc!) that I don't need to write scripts to overwrite mtrr values, that the radeon open source driver just works for X1300 ( why does it not work in fact?) and that I can use Compiz to make my ubuntu feel modern...

---

### Post by nikdc5 on 2006-12-27
i'm also having this problem :(

---

### Post by jewo on 2007-01-01
I  have the same problem: Dell Dimension E520 with Ati X1300 256mb. 
The mtrr fix freezes my system.

---

### Post by jewo on 2007-01-02
Adding these options in the "Device" section should solve the problem :) :
 
 Driver      "fglrx"
 Option      "mtrr"              "off" 
 Option      "UseFastTLS" "2"
 Option      "EnablePrivateBackZ" "on" # Gentoo Ati Driver Howto recommends this for X1300
 Option      "UseInternalAGPGART" "no" # allow xorg to use the intel_agp module

Also you have to add:

Section "Extensions"
        Option  "Composite" "false"
EndSection

Good luck!

---

### Post by DonKyot on 2007-01-03
> **jewo said:**
> Adding these options in the "Device" section should solve the problem :) :
 
 Driver      "fglrx"
 Option      "mtrr"              "off" 
 Option      "UseFastTLS" "2"
 Option      "EnablePrivateBackZ" "on" # Gentoo Ati Driver Howto recommends this for X1300
 Option      "UseInternalAGPGART" "no" # allow xorg to use the intel_agp module

Also you have to add:

Section "Extensions"
        Option  "Composite" "false"
EndSection

Good luck!

with that I get 674 FPS fgl_glxgears and can see them - is that good / expected?

But more importantly I can see googleerth!!!! which if fab!!!

Thanks :KS

---

### Post by nikdc5 on 2007-01-03
This has worked for me too.  Many many thanks... now to get xgl working :)

---

### Post by fedecarra on 2007-01-05
hi all,

I just tried the jewo suggestion:

> Adding these options in the "Device" section should solve the problem  :

Driver "fglrx"
Option "mtrr" "off"
Option "UseFastTLS" "2"
Option "EnablePrivateBackZ" "on" # Gentoo Ati Driver Howto recommends this for X1300
Option "UseInternalAGPGART" "no" # allow xorg to use the intel_agp module

Also you have to add:

Section "Extensions"
Option "Composite" "false"
EndSection

Good luck!

now I have glxgears and fgl_glxgears showing correctly rotating cubes BUT:

- no OpenGL screen saver running (they use CPU rendering, and after a while X crashes)
- glxgears and fgl_glxgears run smoothly, but CPU is 100% busy too

i've not tried yet Beryl, Xgl & c.

someone has good news?

thanx

---

### Post by mattgy on 2007-01-07
This solution worked for me - thanks!  Weeks of trying to figure it out...

I have a Radeon X1300 on a Dell Dimension 9200.

Thanks again,
Matt

---

### Post by DonKyot on 2007-01-07
Anyone any luck with Beryl?
Not that I really *need* it...

I get in Xorg.1.log:
> (EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

(EE) AIGLX: Screen 0 is not DRI capable

even though I'm not meant to be using AIGLX :-k

---

### Post by jewo on 2007-01-13
I've got XGL/Beryl SVN working with ATI Driver 8.33.6 and some modifications in my xorg.conf:

In Section "Device" change EnablePrivateBackZ to "no"

```
  Option   "EnablePrivateBackZ" "no"
```

and add these options to your "Extensions" section :

```
 
Section "Extensions"
        Option  "Composite" "false"
        Option  "XVideo" "Enable"
        Option "DAMAGE" "no"
EndSection

```

---

### Post by Gizmocool on 2007-01-18
Hi, I've the same problem as you.
I tried the jewo's solution. And my glxgears works now, but XGL/Beryl don't work...

If I change EnablePrivateBackZ to "no", my glxgears come black, but, if I left "on", my XGL session freeze when I log in...

Have you an issue ?

Thanks for the replies. ;)

---

### Post by tbeld on 2007-01-18
Everything seems to be working fine for me. I have an ATI X1300 as well. I tried and tried under Dapper to no avail and again upon upgrade to Edgy. Then after a clean install of Edgy and following the instructions at: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
Everything worked as expected **except that I only have direct rendering on screen 0 (dual-head setup- [B]anyone know how to fix this?**).
lspci -v
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300] (prog-if 00 [VGA])
        Subsystem: VISIONTEK Unknown device 1930
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 169
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at ff5f0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at d000 [size=256]
        Expansion ROM at ff5c0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
        Subsystem: VISIONTEK Unknown device 1931
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at ff5e0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```
fglrxinfo
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

glxgears outputs the turning colored gears

cat xorg.conf
```
Section "Monitor"
        Identifier   "DELL 1901FP"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "DELL 1901FP"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "false"
EndSection

```

I'm new so I don't have any specific suggestions but I'd be happy to provide any info you think might help...

---

### Post by Gizmocool on 2007-01-18
Do you have a Dell Computer ? And if yes what is it ? A Dimension ?

---

### Post by Gizmocool on 2007-01-19
But, now that we know the problem. What does fix it ? A new version of ATI drivers ? Or a new version of Ubuntu ? Or a new version of Dell bios ?

Because we can't use XGL/Beryl... Anyone have a solution ?

---

### Post by tbeld on 2007-01-19
> **Gizmocool said:**
> Do you have a Dell Computer ? And if yes what is it ? A Dimension ?

No, I built my computer. 

I know xgl+beryl with ATI can be done in Dapper as well. I just wasn't successful because I mucked around to much- had Gnome, KDE, Enlightenment, various drivers, partially finished beryl guides, many retries etc.

After a week or so of frustration I dit the clean install of Edgy and followed the above guide and within an hour had it working. I wish I would have done it sooner.

The same guy wrote a guide for Dapper. Maybe it will help. [http://lhansen.blogspot.com/2006/10/...-with-ati.html](http://lhansen.blogspot.com/2006/10/...-with-ati.html)

Good luck!

---

### Post by Gizmocool on 2007-01-19
Thanks :)

But the problem is that with Dell computers, especially Dimension, ATI drivers aren't recognized. Until now, nobody find correct solutions... ](*,)

---

### Post by datakid on 2007-01-24
Cheers Jewo - worked for me too.

I'm not sure what all this glxgears is that people are talking about, but a new x seesion gave me all the prettiness that I've been seeing in the youtube clips - wavy terminals, crazy block desktops and lots of nice movement.

I'm running edgy 6.10 on the dell dimension 9200 with 256M ATI X1300 on flgrx drivers.

One thing - I did get a bug report pop up and response with that was slow. I don't know where to post it? Should it go here, in the ubuntu bugtracker or the beryl bug tracker?

   please find report attached if you can help me help us?

---

### Post by fedecarra on 2007-01-26
now it works: problem solved with fglrx ati drivers version 8.33.6!!!!!!
xgl + beryl on dell dimension 9200 and ati radeon x1300 :-)

---

### Post by Gizmocool on 2007-01-28
For me, 8.33.6 drivers crash my X server. The only solution is to install 8.32.5 drivers and modify my xorg.conf like Jewo. I'm on a Dell Dimension E521, have you a solution?

I precise that i'm on Ubuntu (32 bits) Edgy Eft.

---

### Post by dp_wiz on 2007-02-14
The best results i can work out of feisty on dell 6400 / ati x1300 is DRI-disabled (somewhat) stable and DRI/Accel enabled, but messy screen and looong session loading. Any success stories of this configuration?

---

### Post by Gizmocool on 2007-02-21
New drivers (8.34.8 ) are released but crash my X server again ! I stay with my 8.32.5 and the jewo's config. :(

---

### Post by gauchozh on 2007-02-26
Hallo everybody!

I buy a new Dell Dimension E521 and I'm triyng to configure the 3d graphic card (Ati X1300) since a couple of days and i can't bring it to work.
Could some of them which also have this computer post their xorg.conf and if possible some information about the driver used?

Thanks!

---

### Post by Gizmocool on 2007-02-27
Hi. First, sorry for my bad english but this is not my native language...

I use fglrx driver version 8.32.5 and this is my xorg.conf : 

```
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Carte vidéo générique"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	Option		"EnablePrivateBackZ" "on"
	Option		"mtrr" "off"
	Option		"UseFastTLS" "2"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Carte vidéo générique"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

I've the same computer as you (a Dimension E521) and currently, this version (8.32.5) is the last version which works with Dimension E521. Moreover, you must to add this line (thanks jewo :) ) to your xorg.conf to enable the 3D acceleration : 

```
Option		"EnablePrivateBackZ" "on"
```

The next drivers (8.33.6 & 8.34.8) freeze the X server when you use them. If anyone has a solution...

---

### Post by nabmaz on 2007-03-01
Hi all,

I have Dell 520 ubuntu edgy 6.10 latest drivers

all seems run eprfectly but when i use 3d drivers for gaming (World of Warcraft) I do not have same performances as in windows.

So I have read your post and see that I have almost same symptoms.


```
 nab@nab-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
 
```

```
 01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183 (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at dc00 [size=256]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
        Subsystem: Dell Unknown device 0303
        Flags: bus master, fast devsel, latency 0
        Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
 
```

```
 nab@nab-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)
 
```

```
 nab@nab-desktop:~$ glxgears -printfps
23618 frames in 5.0 seconds = 4723.465 FPS
23601 frames in 5.0 seconds = 4720.102 FPS
23601 frames in 5.0 seconds = 4720.122 FPS
23551 frames in 5.0 seconds = 4710.157 FPS
 
```

but:

```
 nab@nab-desktop:~$ dmesg | grep fglrx
[17179615.832000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179615.832000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[17179617.188000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[17179617.188000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[17179617.196000] [fglrx] total      GART = 130023424
[17179617.196000] [fglrx] free       GART = 114032640
[17179617.196000] [fglrx] max single GART = 114032640
[17179617.196000] [fglrx] total      LFB  = 268304384
[17179617.196000] [fglrx] free       LFB  = 250474496
[17179617.196000] [fglrx] max single LFB  = 250474496
[17179617.196000] [fglrx] total      Inv  = 0
[17179617.196000] [fglrx] free       Inv  = 0
[17179617.196000] [fglrx] max single Inv  = 0
[17179617.196000] [fglrx] total      TIM  = 0
 
```


Strange no ?

If anyone can help it will be really cool

Also my 


```
 
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option      "Capabilities" "0x00000800"
        Option      "UseFastTLS" "off"
        Option      "KernelModuleParm" "locked-userpages=0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

 
```

ooops i forget my log when i launch World of warcraft + wine manually:


[/CODE]

nab@nab-desktop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

[/CODE]

otherwise all is oki google earth and other 3d apps

Bye all !

---

### Post by carsena on 2007-03-23
> **Gizmocool said:**
> Thanks :)

But the problem is that with Dell computers, especially Dimension, ATI drivers aren't recognized. Until now, nobody find correct solutions... ](*,)

I think I am having this problem. You say that ATI drivers are not recognized? Where did you get this information? Until now you say....what is that correct solution?

I'm gathering information to help me deal with dell tech support.

---

### Post by Gizmocool on 2007-03-28
Hi :)

I've a Dimension E521 and today, new drivers was released... 8.35.5

They crash my system again ! ](*,) 

The only driver which work is 8.32.5 .

I hope you can find a solution with Dell technical support.

You can found informations here : [http://ati.cchtml.com/show_bug.cgi?id=567]("http://ati.cchtml.com/show_bug.cgi?id=567").

:) Good night !

---

### Post by josvazg on 2007-04-28
I just got an Dell E512 with a AMD x2 and an ATI X1300.

I haven't got further that to lookup the display everytime I try something different to the VESA driver.

Everybody here says that ATI deriver vesion 8.32 is the best option for the time being, but I can only download versions 8.34, 8.35 and 8.36. 

All links go to ATI and ATI only allows you to download the latest version (8.36). Where can I download the good old 8.32 from?

Can anyone get 3D work on this version 8.32?

Another question, has anyone manage something to get the system recognize the ATI card model on this Dell Model?
lspci tells me 'unknown device'

---

### Post by josvazg on 2007-04-28
I forgot to say that my software is a Kubuntu Feisty Fawn with X.org 7.2.

All works fine, even the SD card reader, but the graphics, still in VESA mode 1024x768. It even adds Vista in the Grub menu manually (think Edgy didn't)

---

### Post by josvazg on 2007-04-28
I got this link by changing the link:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run)

I think this will also work for a 8.33:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.33.5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.33.5-x86.x86_64.run)

This link may not last long, though.

---

### Post by josvazg on 2007-04-28
Version 8.32 refuses to install on my Feisty... great!

---

### Post by josvazg on 2007-04-30
Hi all!

Partial success thanks to this thread's help!

I am on Edgy now with 3D working "fine" but no AIGLX nor XGL to use Beryl with. 
glxgears seems to fgl_glxgears shows about 730fps (which I think its poor for this card) and lspci and fglrxinfo don't know the x1300 model:
```

$ lspci
...
01:00.0 Multimedia video controller: Unknown device 18c3:0720
03:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
03:00.1 Display controller: ATI Technologies Inc Unknown device 71a3

```
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

Am on a Dell E521 with ATI x1300 pro
Edgy + x.org 7.1 + ATI drivers 8.32.5 + jewo xorg.conf tips
(I want to try on a Feisty, but I guess x.org 7.2 will complain)

You may be interested in signing this petition for better ATI drivers:
[http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html)
(fund here [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide))

Anyone got Beryl working? on XGL or via AIGLX? how?

---

### Post by etano on 2007-06-28
Got it working with Dapper on Dell E521 with ATI X1300 Pro 256mb.  I was so grateful I made a tutorial.  It should work for Edgy too.  Here it is:

[click here]("http://etano.net/2007/06/28/ubuntu-dapper-dell-e521-and-ati-x1300/")

Note: by working, I mean pretty much exactly the setup josvazg has, only dapper

---

