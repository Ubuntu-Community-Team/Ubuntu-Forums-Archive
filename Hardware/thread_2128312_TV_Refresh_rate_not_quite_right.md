---
title: "TV Refresh rate not quite right"
date: 2013-03-22
forum: Hardware
---

### Post by sugarat on 2013-03-22
Hi Everyone!

I am very pleased with my new ubuntu desktop. There is just one thing I need to get working for it to be perfect.

I have a Dell XPS One 27 with HDMI out.  When I connect my Amp / TV to it, it does indeed show up in the displays program.  It works, but not at the native resolution of the plasma display. 

When I click 1920x1080, the TV goes blank.  I am convinced that the refresh rate being fed to it, is not quite right.  

How would I change the refresh rate, so that I know I am outputting 1920x1080 at the right refresh? 

Many thanks

---

### Post by papibe on 2013-03-22
Hi sugarat.

If it works fine while connected directly from the TV (not amp, not receiver). It may be possible to hard code the TV timings, so that are not lost in the case of a intrusive receiver in the middle.

Let us know how it goes.
Regards.

---

### Post by sugarat on 2013-03-22
Hi Papibe, 

 Many thanks for your quick response.  I have plugged in the TV directly, and can confirm that it *does* work when the amp is taken out of the equation.

Many thanks

---

### Post by papibe on 2013-03-22
Install this package:
```
sudo apt-get install read-edid
```
Then, check if you can get, and parse the TV's EDID information by doing:
```
sudo get-edid | parse-edid
```
If you are getting all the relevant information, save it to a file:
```
sudo get-edid > edid.bin
```
Now we have to create a custom xorg.conf file to point to that information. 

What is your graphic cards?
Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by sugarat on 2013-03-23
Hmm.  I've turned the TV on, but after parsing the EDID information, I don't see anything relating to it.  Only the flat panel on the PC:

```

get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
parse-edid: parse-edid version 2.0.0
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
	Call successful

EDID claims 1 more blocks left


*********** Something special has happened!
Please contact the author, Matthew Kern
E-mail: pyrophobicman@gmail.com
Please include full output from this program (especially that to stderr)



Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

EDID claims 1 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum passed.

	# EDID version 1 revision 4
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "XPS One 2710"
	VendorName "@@@"
	ModelName "XPS One 2710"
	# Block type: 2:0 3:fd
	HorizSync 15-99
	VertRefresh 55-65
	# Max dot clock (video bandwidth) 90 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"2560x1440"	# vfreq 59.951Hz, hfreq 88.787kHz
		DotClock	241.500000
		HTimings	2560 2608 2640 2720
		VTimings	1440 1443 1448 1481
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection

```

As far as I can figure out, the system is always using the Intel graphics card:

```

root@adam-PC:~# lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
	Subsystem: Dell Device [1028:054b]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640M] [10de:0fd2] (rev a1)
	Subsystem: Dell Device [1028:054b]
	Kernel modules: nouveau, nvidiafb

```

---

### Post by sugarat on 2013-03-27
Can someone please advise how to simply set the refresh rate of an external display?

Many thanks

---

### Post by papibe on 2013-03-27
Try running the commands from terminals opened on the TV.

Also, please do the same with this commands:
```
xrandr

xvidtune -show
```
Regards.

BTW, I'm very confused by the output of lspci. It has the same output as a laptop running [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html").

---

### Post by sugarat on 2013-03-27
Hi Papibe, 

 Here is the output from running in a terminal on the TV (directly connected to HDMI)

```

m@adam-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 4480 x 1440, maximum 8192 x 8192
eDP1 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440      60.0*+
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   2048x1152      60.0  
   1920x1200      59.9     60.0  
   1920x1080      50.0     59.9  
   1600x1200      60.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0     59.8     60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0     50.0  
   1024x768       60.0  
   1024x576       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+2560+360 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      59.9*+   50.0     60.0     24.0     30.0     25.0     30.0  
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      59.9  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       59.9  
   1280x768       60.0  
   1280x720       60.0     50.0  
   1440x576       25.0  
   1024x768       60.0  
   1024x576       60.0  
   800x600        60.3  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        60.0     59.9  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)

```

```

@adam-PC:~$ xvidtune -show
"1920x1080"   138.50   1920 1968 2000 2080   1080 1083 1088 1111 +hsync -vsync

```

I'm not surprised it looks like a laptop. No doubt many parts of this machine are mobile based due to it's thin nature. It has an Intel chip, and an Nvidia chip.

Many thanks

---

### Post by papibe on 2013-03-27
That sounds more promising. 

Since we couldn't get the TV's EDID into a file, I'm thinking going another route with this information:
```
"1920x1080"   138.50   1920 1968 2000 2080   1080 1083 1088 1111 +hsync -vsync
```
Take a look at this [tutorial]("http://askubuntu.com/questions/271801/configure-modeline-ubuntu-12-04") on how to use the command 'xrandr' to set a resolution that is not apparently available.

Try the steps while connected to your amp, to see if you can set the correct resolution (use the your own modeline above).

Let us know how it goes.
Regards.

---

### Post by sugarat on 2013-03-27
Ok, I have done the following with the amp between the PC and TV:

```

xrandr --newmode "1920x1080_60"   138.50   1920 1968 2000 2080   1080 1083 1088 1111 +hsync -vsync
xrandr --addmode HDMI1 1920x1080_60
xrandr --output HDMI1 --mode 1920x1080_60

```

The TV is still refusing to display anything. 

Output of xrandr at this stage is

```

adam@adam-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 4480 x 1440, maximum 8192 x 8192
eDP1 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440      60.0*+
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   2048x1152      60.0  
   1920x1200      59.9     60.0  
   1920x1080      50.0     59.9  
   1600x1200      60.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0     59.8     60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0     50.0  
   1024x768       60.0  
   1024x576       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+2560+360 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      59.9*+   50.0     60.0     24.0     30.0     25.0     30.0  
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      59.9  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       59.9  
   1280x768       60.0  
   1280x720       60.0     50.0  
   1440x576       25.0  
   1024x768       60.0  
   1024x576       60.0  
   800x600        60.3  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        60.0     59.9  
   720x400        70.1  
   1920x1080_60   59.9  
DP1 disconnected (normal left inverted right x axis y axis)

```

Presuming that the * signifies what mode is currently in use.  I don't get this 59.9 business. It should be 60.  I think this could be something to do with the issue..?

---

### Post by papibe on 2013-03-27
How about constructing a different modeline with either with 'cvt' ot 'gtf':
```
cvt 1920 1080 60

gtf 1920 1080 60
```
Regards.

---

### Post by sugarat on 2013-03-28
I could not get any of the new modelines to work either... 

 ..BUT..  Type the following in, and BAM, the TV comes alive!

```

xrandr --output HDMI1 --mode 1920x1080 --rate 60

```

I have no idea why it is using the refresh rate called 59.9 by default?  This has now set it to 60Hz and the screen works!

Thanks for all your help

---

### Post by sugarat on 2013-03-29
Can we identify where the core fault lies in this case?  If we can figure out what was going wrong, we can get it fixed for other people in future.   Whenever I use the display configuration control it again overwrites the refresh rate and I now have to run a little script to fix it.  Can we get this display program fixed so that the actual problem won't be seen again..?

---

