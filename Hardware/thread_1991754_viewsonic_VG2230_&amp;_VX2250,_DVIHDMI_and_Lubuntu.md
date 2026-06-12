---
title: "viewsonic VG2230 &amp; VX2250, DVI/HDMI and Lubuntu not working"
date: 2012-05-30
forum: Hardware
---

### Post by crazyJay648 on 2012-05-30
Here's the problem:
I cannot get lubuntu to work with either a viewsonic VG2230 or Vx2250 through my PCs HDMI port. It does work through the VGA though. I'm still not 100% if the problem is lubuntu, the viewsonic monitors or my PC.

Here's the troubleshooting I've done thus far:
- The PC is a Foxconn nettop. It has a VGA port and a HDMI port. ([http://www.newegg.com/Product/Product.aspx?Item=N82E16856119056](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119056))
- I'm using a HDMI -> DVI adapter to connect it to the VG2230, and I have the VX2250 on VGA.
- I confirmed that the HDMI-DVI adapter works by connecting a windows laptop with HDMI out to the VG2230 and even the VX2250, and it works just fine.
- I connect the PC running lubuntu to a TV through the HDMI with no HDMI->DVI adapter (straight HDMI). That works just fine. I was able to turn my TV into a second monitor.
- However, when I connect any of these viewsonic monitors to the PC with the HDMI->DVI adapter, they don't work. Only the VGA connection works.

It's like this particular PC and these particular monitors just don't like each other. Any ideas?

Here is a description of the hardware I'm running:
-Computer-
Processor        : 4x Intel(R) Atom(TM) CPU D525   @ 1.80GHz
Memory        : 4040MB (324MB used)
Operating System        : Ubuntu 12.04 LTS
Date/Time        : Wed 30 May 2012 09:37:01 PM CDT
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 HOLTEK Evoluent VM3 Wireless
 No brand 2Port KVMSwicther
 Microsoft Natural® Ergonomic Keyboard 4000
 Microsoft Natural® Ergonomic Keyboard 4000
 HDA Intel Mic
 HDA Intel Front Headphone
 HDA Intel Line-Out
-Printers (CUPS)-
Brother_MFC-495CW        : <i>Default</i>
-SCSI Disks-
ATA Corsair Accelera

OS info:
-Version-
Kernel        : Linux 3.2.0-24-generic (x86_64)
Compiled        : #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012
C Library        : Unknown
Default C Compiler        : Unknown
Distribution        : Ubuntu 12.04 LTS
-Current Session-
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 25 minutes
Load Average        : 1.11, 0.94, 0.67

Display info:
-Display-
Resolution        : 1920x1080 pixels
Vendor        : The X.Org Foundation
Version        : 1.11.3
-Monitors-
Monitor 0        : 1920x1080 pixels
Monitor 1        : 1366x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No

---

### Post by crazyJay648 on 2012-05-30
Just an update:

When I connect the monitor with the HDMI->DVI adapter, the monitor doesn't say "No signal" or "Out of range." IT looks like it does detect something, because once I unplug the HDMI cable it then say's "no signal."

Also, I'm using an actually HDMI-DVI cable, not an adapter that takes a HDMI cable and converts it to DVI.

---

### Post by crazyJay648 on 2012-05-31
Here's another update:

When I run xrandr I get this:

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.4*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  


It looks like the display is set to a size of 0mm by 0mm. It's not clear how I can change this. Any ideas?

---

### Post by marinara on 2012-05-31
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Can.27t_Change_to_Screen_Resolution_I_need_For_My_Monitor_or_Laptop_Screen](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Can.27t_Change_to_Screen_Resolution_I_need_For_My_Monitor_or_Laptop_Screen)

sorry i can't help more

---

### Post by crazyJay648 on 2012-05-31
Thanks for the help. Yea, all that stuff doesn't really talk about how to get the display to not be 0mm x 0mm. I'm wondering if maybe this just isn't possible with my monitor. >=\

---

### Post by crazyJay648 on 2012-05-31
I officially give up. I'm going to sell the VG2230, never buy Viewsonic monitors and never buy foxconn nettop boxes. :(

---

### Post by poikiloid on 2012-06-02
Hello crazyJay648,

I am having the same problem as you.

I recently got a viewsonic VX2336S-LED monitor after upgrading to ubuntu 12.04. This monitor has VGA and DVI input. I am using a system76 pangolin (panp5) laptop specially made for ubuntu. This laptop has only VGA and HDMI.

The VGA cable input works well.

The HDMI-DVI cable input at first wouldn't work, then suddenly it worked for a while until I restarted laptop, and since then will not work anymore at all. It is a brand new cable, so I don't think it is bad, but I have no other way of testing it. Ubuntu KNOWS that a viewsonic 23" monitor is connected, because it shows it in the "Displays" manager. However, nothing shows up on the external screen.

Very frustrating!!!!

It may be something wrong with Ubuntu itself however, because this person appears to be having the same problem as we are, with an HDMI-DVI cable setup: [http://ubuntuforums.org/showthread.php?t=1933078](http://ubuntuforums.org/showthread.php?t=1933078)

---

### Post by crazyJay648 on 2012-06-03
I see,

Well, it's nice to know I'm not alone in this. lol. I will post if I discover anything that fixes this.

---

