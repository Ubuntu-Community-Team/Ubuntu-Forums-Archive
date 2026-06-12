---
title: "How do I get 5120 1440 resolution on Samsung CRG90 over DisplayPort or HDMI ?"
date: 2019-10-31
forum: Hardware
---

### Post by rshetye2 on 2019-10-31
Hi,

MX Linux 18.3 is able to do 5120 x 1440 out of the box on the Samsung 49 inch CRG90 monitor. MX Linux 19, Kubuntu 19.10, and Manjaro 18.1.1 are not able to do 5120 x 1440, they can only do 3840 x 1080. Has anyone figured out why ? Windows (from a laptop) and MX Linux 18.3 (from the same box as Ubuntu) do the 5120 flawlessly over DisplayPort.

```

# xrandr --delmode DP-2 "5120x1440_30.00"
xrandr --newmode "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
xrandr --addmode DP-2 "5120x1440_30.00"
xrandr --output DP-2 --mode "5120x1440_30.00"

```

I've tried over Display Port and over HDMI.

I've tried the cvt settings and xrandr but it comes back with an error. (I'll post the error once I log into the Ubuntu box)

> xrandr: Configure crtc 0 failed


Output on Kubuntu 19.10
> 
+ export rate=30
+ [ 1 -gt 0 ]
+ export rate=30
+ echo rate=30
rate=30
+ export RESOLUTION=5120 1440 30
+ OUTPUT=DP-2
+ xrandr --current
+ grep -i DP-2
+ cut -f2 -d 
+ CONNECTED=connected
+ [ connected = connected ]
+ cvt 5120 1440 30
+ tail -n +2
+ MODELINE=Modeline "5120x1440_30.00"  292.75  5120 5360 5888 6656  1440 1443 1453 1468 -hsync +vsync
+ echo Modeline "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
+ cut -f 3- -d 
+ MODEDATA=292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
+ echo Modeline "5120x1440_30.00" 292.75 5120 5360 5888+  6656 1440 1443cut 1453 -f2 1468 -d  -hsync +vsync


+ MODENAME="5120x1440_30.00"
+ echo Deleting mode -  "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
Deleting mode -  "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
+ xrandr --delmode DP-2 "5120x1440_30.00"
+ echo Adding mode -  "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
Adding mode -  "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
+ xrandr --newmode "5120x1440_30.00" 292.75 5120 5360 5888 6656 1440 1443 1453 1468 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  34
  Current serial number in output stream:  34
+ xrandr --addmode DP-2 "5120x1440_30.00"
+ xrandr --output DP-2 --mode "5120x1440_30.00"
xrandr: Configure crtc 0 failed


thanks!

---

### Post by Skaperen on 2019-10-31
if you type the command:```
xrandr|head -n1
```do you get a maximum size info?

---

### Post by Holger_Gehrke on 2019-11-01
Did you check whether the display announces its capabilities in the Extended Display Information Data (EDID) ? A simple 'get-edid|parse-edid' should tell you whether the display tells the system what it can do. Since EDID is transmitted through the i2c-bus that's part of all modern display connectors you might need to either be a member of the group 'i2c' or use sudo for the first command of that pipe.

Holger

---

### Post by rshetye2 on 2019-11-02
Hi, here's the output for ```
xrandr | head -n1
```

> Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384


> **Skaperen said:**
> if you type the command:```
xrandr|head -n1
```do you get a maximum size info?

---

### Post by rshetye2 on 2019-11-02
Hi, here's the output. There is no i2c group. Is that ok ? Normal ?

Also, I think you might be on to something. There's a warning at the end of command output:
> You seem to have too many extension blocks. Will not continue to parse
Something strange happened. Please contact the author,
Matthew Kern at <pyrophobicman@gmail.com>


```
sudo get-edid | parse-edid

```

full output:
> This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 6
2 potential busses found: 0 5
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 5
Looks like i2c was successful. Have a good day.
You seem to have too many extension blocks. Will not continue to parse
Something strange happened. Please contact the author,
Matthew Kern at <pyrophobicman@gmail.com>


I installed i2c-tools and then I got the following:
> 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
Problem requesting slave address: Device or resource busy
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
Problem requesting slave address: Device or resource busy
No EDID on bus 6
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful


	VBE version 300
	VBE string at 0xc94bc "Intel(R) SKL/KBL Mobile/Desktop Graphics Chipset Accelerated VGA BIOS"


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
	Call successful


EDID claims 2 more blocks left




*********** Something special has happened!
This happens a lot with TV's, and other devices
with extension blocks. If you have a TV, don't bother.
Odds are good that I2C will work for you. Try 'modprobe i2c-dev'.
Otherwise, please contact the author, Matthew Kern
E-mail: [email]pyrophobicman@gmail.com[/email]
Please include full output from this program (especially that to stderr)






Reading next EDID block


VBE/DDC service about to be called
	Read EDID


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful


EDID claims 2 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
Reading next EDID block


VBE/DDC service about to be called
	Read EDID


	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful


EDID claims 2 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
Looks like VBE was successful. Have a good day.
You seem to have too many extension blocks. Will not continue to parse
Something strange happened. Please contact the author,
Matthew Kern at <pyrophobicman@gmail.com>


---

