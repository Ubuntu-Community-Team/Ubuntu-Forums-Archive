---
title: "Screen rotation HP Touchsmart TX2-1224ca"
date: 2010-09-17
forum: Hardware
---

### Post by fearless.75 on 2010-09-17
Hi,
 I have an HP Touchsmart TX2-1224ca and stylus and touchscreen is  working right out of the box. I found several tips to make  a screen rotation  including magick-rotation program. Rotation works great, but when screen  is rotated the mouse / stylus / touchscreen is still on the landscape  assignment. I have to mention I'm using a 64 bits release.

Here's the script I'm using. You may see I've  changed names of the stylus and touchscreen to match the name of the  N-trig hardware.
[INDENT]#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr  -q --verbose | grep 'connected' | egrep -o  '\)  (normal|left|inverted|right) \(' | egrep -o  '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set pen rotate CCW 
    xsetwacom set touchscreen rotate CCW 
    xsetwacom set eraser rotate CCW 
    ;; 
    left) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set pen rotate HALF 
    xsetwacom set touchscreen rotate HALF 
    xsetwacom set eraser rotate HALF 
    ;; 
    inverted) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set pen rotate  CW 
    xsetwacom set touchscreen rotate CW 
    xsetwacom set eraser rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set pen rotate NONE 
    xsetwacom set touchscreen rotate NONE 
    xsetwacom set eraser rotate NONE 
    ;; 
esac


[/INDENT][LEFT]After I found that if I'm trying only one xwacom commande line I have an error message :
When I type:
xsetwacom set "N-Trig Pen" rotate CCW

I get :
xsetwacom set "N-Trig Pen" rotate CCW

This problem is making me crazy because when I do axinput --listI get 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                           id=12    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=16    [slave  keyboard (3)]

The annoying thing is if I try to xsetwacom --list, nothing appears

I tried to put on the script the full name, the ID number and same result.

Does anyone have an idea ?

Please helllllppppp !


[/LEFT]

---

### Post by Ayuthia on 2010-09-17
Welcome to the Forums!

The xsetwacom --list might not be working because either the Wacom driver does not recognize the device or else the evdev driver is taking the devices.  You can either check or post the results of:
```

xinput list-props 12
xinput list-props 11

```
That will help us see which driver you are using.  You should see some properties that will either show Wacom or else evdev.

The other place to check is /var/log/Xorg.0.log to see if there are any errors coming from the Wacom driver.

---

### Post by fearless.75 on 2010-09-19
Here's the answers for 
xinput list-props 12

> Device 'N-Trig Pen':
    Device Enabled (147):    1
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    10.000000
    Evdev Reopen Attempts (263):    10
    Evdev Axis Inversion (272):    0, 0
    Evdev Axis Calibration (273):    <no items>
    Evdev Axes Swap (274):    0
    Axis Labels (275):    "Abs X" (265), "Abs Y" (266), "Abs Pressure" (286)
    Button Labels (276):    "Button 0" (285), "Button Unknown" (264), "Button Unknown" (264), "Button Wheel Up" (151), "Button Wheel Down" (152)
    Evdev Middle Button Emulation (277):    2
    Evdev Middle Button Timeout (278):    50
    Evdev Wheel Emulation (279):    0
    Evdev Wheel Emulation Axes (280):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (281):    10
    Evdev Wheel Emulation Timeout (282):    200
    Evdev Wheel Emulation Button (283):    4
    Evdev Drag Lock Buttons (284):    0and for xinput list-props 11

> Device 'N-Trig Touchscreen':
    Device Enabled (147):    1
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    10.000000
    Evdev Reopen Attempts (263):    10
    Evdev Axis Inversion (272):    0, 0
    Evdev Axis Calibration (273):    <no items>
    Evdev Axes Swap (274):    0
    Axis Labels (275):    "Abs X" (265), "Abs Y" (266), "None" (0), "None" (0)
    Button Labels (276):    "Button Unknown" (264), "Button Unknown" (264), "Button Unknown" (264), "Button Wheel Up" (151), "Button Wheel Down" (152)
    Evdev Middle Button Emulation (277):    2
    Evdev Middle Button Timeout (278):    50
    Evdev Wheel Emulation (279):    0
    Evdev Wheel Emulation Axes (280):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (281):    10
    Evdev Wheel Emulation Timeout (282):    200
    Evdev Wheel Emulation Button (283):    4
    Evdev Drag Lock Buttons (284):    0Does this helps you tofind out what's wrong ?

---

### Post by Ayuthia on 2010-09-19
Ok.  What is happening is that both your pen and touchscreen are using the evdev driver instead of the Wacom driver.  If you are using Lucid, the recommendation is to have the pen run with Wacom and the touchscreen use evdev.

I am going to assume that you are currently using Lucid.  If you are not, please let us know and will will give you updated information because it might be different.

To get the pen to use the Wacom driver, you will need to check and see if there is a file already out there in /etc/X11/xorg.conf for your device.  If there are files out there and you are not sure, please post them so that we can review and verify that they don't contain anything that might block out our changes.

If you are confident that there is nothing out there, you will need to follow the steps in 1b from this [guide]("http://ubuntuforums.org/showthread.php?t=1252492").

In order to get the evdev driver to rotate, you might try using this [script]("http://ubuntuforums.org/showpost.php?p=9842541&postcount=1193").  You will need to verify that you have zsh installed so that the script will run.

You will then need to restart X or reboot for the changes to take effect.

---

### Post by fearless.75 on 2010-09-19
I use 10.04 indeed.

I first did the trick for 10-wacom.conf and rebooted.

I just checked after your xinput list-props 12 and then 11. i just realized the ID 11 is now attribued to an Eraser I don't have. I don't know if this is important or not. Anyway, doing a xinput list tell me the 11 ID is now the 14. I checked both and now the pen is Wacom and Touchscreen is evdev.

I then installed zsh and tried the script. Just to be sure I'm doing the right way. I making an script,copy and paste the script, save it and make it executable doing chmod a+x script_name.sh. Am I doing well here ? I'm asking this because when trying to launch this script, nothing happens.

Any idea ?

---

### Post by Favux on 2010-09-19
Hi fearless.75,

I believe it requires the extended shell zsh so "apt-get install zsh".

---

### Post by fearless.75 on 2010-09-19
I've just run new test without doing more I've explained on this post. 
So I've just tested magic rotation and it works almost ! When I twist the screen, the swivel down, then the screen is rotating and it works perfectly with the stylus but not with the touchscreen. Wallpaper is removed at this point and if I put back my wallpaper and retwist the screen, wallpaper is off again (black screen).

I still would like to have a script to make the screen rotate when I just activate it, and magic rotate would also great to have.

Your help would be very helpful

---

### Post by fearless.75 on 2010-09-19
> **Favux said:**
> Hi fearless.75,

I believe it requires the extended shell zsh so "apt-get install zsh".

Already done. I also checked in Synaptics and I can see it. Strange problem isn't it ?

---

### Post by Favux on 2010-09-19
Did you remember to make the script executable?

---

### Post by fearless.75 on 2010-09-19
Yes, like I said in one of my previous post.

If I'm launching the script manually in a terminal I get :
 rotate_test.sh: 4: Syntax error: "(" unexpected

Any idea what's wrong ?

---

### Post by Favux on 2010-09-19
Well, the script is for Maverick.  Let's try Rafi's original script for Lucid that it's based on:  [http://ofb.net/~rafi/xrotate.zsh](http://ofb.net/~rafi/xrotate.zsh)  That's linked in "4 b) Using evdev for touch and the Wacom drivers for the stylus" in the HOW TO.

---

### Post by fearless.75 on 2010-09-19
zsh script not working. Still same error message when lauching script in terminal. I tried the hid-ntrig.ko andafter reboot no more stylus or touch working. Getting worse now !

---

### Post by Favux on 2010-09-19
Hmmm.  Now that's getting word.  The script and extended shell shouldn't have anything to do with the hid-ntrig.ko.  Did you let a kernel update happen?

---

### Post by Ayuthia on 2010-09-20
Can you post your /var/log/Xorg.0.log file?  It sounds like the device is not passing the rules for some reason.

---

### Post by fearless.75 on 2010-09-21
Hi,

Sorry for the delay of my answer. I was far from an Internet connection.

SoI just restored my OS to original state (before pen and screen not working anymore). I just changed the fdi to have the wacom and evdev drivers.

Here's now the  /var/log/Xorg.0.log result :


```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux corley-TX2-1224 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=e5bc4a3a-bb34-4dbc-8a64-493c664100a9 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 21 08:41:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9612:103c:3045 ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xc0000000/268435456, 0xd2300000/65536, 0xd2200000/1048576, I/O @ 0x00005000/256
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9612) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0xe1a7e0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 10, (OK)
ukiOpenByBusid: ukiOpenMinor returns 10
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics " (Chipset = 0x9612)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3045)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd2300000
(--) fglrx(0): I/O port at 0x00005000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780M
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 327680 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x14000000)
(II) fglrx(0): Interrupt handler installed at IRQ 29.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: LCD on internal LVDS [lvds]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CMO  Model: 1233  Serial#: 0
(II) fglrx(0): Year: 2008  Week: 45
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 26  vert.: 17
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.560 redY: 0.350   greenX: 0.340 greenY: 0.560
(II) fglrx(0): blueX: 0.159 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 69.3 MHz   Image Size:  260 x 170 mm
(II) fglrx(0): h_active: 1280  h_sync: 1320  h_sync_end 1346 h_blank_end 1412 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 807 v_blanking: 818 v_border: 0
(II) fglrx(0):  N121IB-L06
(II) fglrx(0):  CMO
(II) fglrx(0):  N121IB-L06
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff000daf331200000000
(II) fglrx(0):     2d120103801a11780a61c58f59578f28
(II) fglrx(0):     23505400000001010101010101010101
(II) fglrx(0):     010101010101121b008450201230281a
(II) fglrx(0):     340004aa10000018000000fe004e3132
(II) fglrx(0):     3149422d4c30360a2020000000fe0043
(II) fglrx(0):     4d4f0a202020202020202020000000fe
(II) fglrx(0):     004e31323149422d4c30360a202000c4
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output LVDS has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output TV has no monitor section
(II) fglrx(0): Output COMPONENT_VIDEO has no monitor section
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output TV disconnected
(II) fglrx(0): Output COMPONENT_VIDEO disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output LVDS using initial mode 1280x800
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 3200 Graphics  has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 15, (OK)
ukiOpenByBusid: ukiOpenMinor returns 15
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f4174748000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-21-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd2ff7000 FBMappedSize: 0x01004000
(II) fglrx(0): Reserved 0x02500000 bytes of sideport memory for power saving
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1280) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2000
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid Horizontal and Vertical Lines
    Driver provided ScreenToScreenBitBlt replacement
    Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
(II) fglrx(0): Cannot set TV horizontal size.
(II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
(II) fglrx(0): Cannot set TV horizontal position.
(II) fglrx(0): Cannot set TV vertical position.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) XKB: reuse xkmfile /var/lib/xkb/server-3BCFF748FFB6BCDACC88715CBF6A9DF905CD3181.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) config/udev: Adding input device Lid Switch (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) config/udev: Adding input device HP Webcam (/dev/input/event10)
(**) HP Webcam: Applying InputClass "evdev keyboard catchall"
(**) HP Webcam: always reports core events
(**) HP Webcam: Device: "/dev/input/event10"
(II) HP Webcam: Found keys
(II) HP Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig Pen (/dev/input/event7)
(**) N-Trig Pen: Applying InputClass "evdev tablet catchall"
(**) N-Trig Pen: Applying InputClass "Wacom N-Trig class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event7"
(II) N-Trig Pen: type not specified, assuming 'stylus'.
(II) N-Trig Pen: other types will be automatically added.
(**) N-Trig Pen: always reports core events
(**) Option "Button2" "3"
(II) N-Trig Pen: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event7"
(**) N-Trig Pen eraser: always reports core events
(**) Option "Button2" "3"
(II) XINPUT: Adding extended input device "N-Trig Pen eraser" (type: ERASER)
(--) N-Trig Pen eraser: using pressure threshold of 15 for button 1
(--) N-Trig Pen eraser: Wacom USB TabletPC tablet speed=38400 maxX=9600 maxY=7200 maxZ=256 resX=934 resY=1122  tilt=disabled
(--) N-Trig Pen eraser: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
(II) N-Trig Pen: hotplugging completed.
(II) XINPUT: Adding extended input device "N-Trig Pen" (type: STYLUS)
(--) N-Trig Pen: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
(II) config/udev: Adding input device N-Trig Pen (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig MultiTouch (/dev/input/event8)
(**) N-Trig MultiTouch: Applying InputClass "evdev touchscreen catchall"
(**) N-Trig MultiTouch: always reports core events
(**) N-Trig MultiTouch: Device: "/dev/input/event8"
(II) N-Trig MultiTouch: Found absolute axes
(II) N-Trig MultiTouch: Found x and y absolute axes
(II) N-Trig MultiTouch: Found absolute touchscreen
(II) N-Trig MultiTouch: Configuring as touchscreen
(**) N-Trig MultiTouch: YAxisMapping: buttons 4 and 5
(**) N-Trig MultiTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "N-Trig MultiTouch" (type: TOUCHSCREEN)
(II) N-Trig MultiTouch: initialized for absolute axes.
(II) config/udev: Adding input device N-Trig MultiTouch (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/event9)
(**) N-Trig Touchscreen: Applying InputClass "evdev touchscreen catchall"
(**) N-Trig Touchscreen: always reports core events
(**) N-Trig Touchscreen: Device: "/dev/input/event9"
(II) N-Trig Touchscreen: Found absolute axes
(II) N-Trig Touchscreen: Found x and y absolute axes
(II) N-Trig Touchscreen: Found absolute touchscreen
(II) N-Trig Touchscreen: Configuring as touchscreen
(**) N-Trig Touchscreen: YAxisMapping: buttons 4 and 5
(**) N-Trig Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "N-Trig Touchscreen" (type: TOUCHSCREEN)
(II) N-Trig Touchscreen: initialized for absolute axes.
(II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ca"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event12"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
```

---

### Post by Ayuthia on 2010-09-21
Have you installed zsh:
```

sudo apt-get install zsh

```

---

### Post by fearless.75 on 2010-09-21
Well, since my Ghost restore , I did not reinstall zsh. I'll try this but I don't think the script is going to work and I guess it will make the same error message I described when launching it in terminal.

Anyway, I think the problem might me else where, because using magick-rotate does the job of rotating, but X and Y abciss are not correct on portrait mode. So I don't think there's a link here. But this is only my opinion.


Tested with reinstallation of zsh and still no effect with the script.

---

### Post by Ayuthia on 2010-09-21
> **fearless.75 said:**
> Well, since my Ghost restore , I did not reinstall zsh. I'll try this but I don't think the script is going to work and I guess it will make the same error message I described when launching it in terminal.

Anyway, I think the problem might me else where, because using magick-rotate does the job of rotating, but X and Y abciss are not correct on portrait mode. So I don't think there's a link here. But this is only my opinion.


Tested with reinstallation of zsh and still no effect with the script.

Right now, the magick-rotate should be able to adjust the pen to the correct position, but the touch should be off since it is using the evdev driver.  Is this correct?  If it is not, can you describe what happens with the rotation for the pen?  Is it going in the opposite direction, or is it 90 degrees off, or is it doing something entirely different?

As for the zsh script, you say that it has no effect.  Does that mean that you are still getting the error message or is not not doing anything?

One other request, can you post the results of 'xinput list-props' for the pen and touch?  I am going to try to create a python script to handle this and possibly add some debugging so that we can see what is happening.

---

### Post by fearless.75 on 2010-09-21
When rotating with magick-rotate, the screen is rotating correctly. Pen and touch are active. With the pen and if i keep the laptop in landscape mode (meaning i just rotated the screen and did not moved the laptop in portrait mode), here's what's happening :
- down  is going to the left
- right is going down
- top is going right
- left is going top

For zsh script, If I double click it, and choose run, nothing happens. If I launching it in terminal I get :
rotate-zsh.sh: 4: Syntax error: "(" unexpected

Result for xinput list-props 11 (Touchscreen)

```
Device 'N-Trig Touchscreen':
    Device Enabled (147):    1
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    10.000000
    Evdev Reopen Attempts (263):    10
    Evdev Axis Inversion (272):    0, 0
    Evdev Axis Calibration (273):    <no items>
    Evdev Axes Swap (274):    0
    Axis Labels (275):    "Abs X" (265), "Abs Y" (266), "None" (0), "None" (0)
    Button Labels (276):    "Button Unknown" (264), "Button Unknown" (264), "Button Unknown" (264), "Button Wheel Up" (151), "Button Wheel Down" (152)
    Evdev Middle Button Emulation (277):    2
    Evdev Middle Button Timeout (278):    50
    Evdev Wheel Emulation (279):    0
    Evdev Wheel Emulation Axes (280):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (281):    10
    Evdev Wheel Emulation Timeout (282):    200
    Evdev Wheel Emulation Button (283):    4
    Evdev Drag Lock Buttons (284):    0

```Result for xinput list-props 13 (Pen)

```
Device 'N-Trig Pen':
    Device Enabled (147):    1
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    10.000000
    Wacom Tablet Area (290):    0, 0, 9600, 7200
    Wacom Rotation (291):    0
    Wacom Pressurecurve (292):    0, 0, 100, 100
    Wacom Serial IDs (293):    1, 0, 2, 0
    Wacom TwinView Resolution (294):    0, 0, 0, 0
    Wacom Display Options (295):    -1, 0, 1
    Wacom Screen Area (296):    0, 0, 1280, 800
    Wacom Proximity Threshold (297):    42
    Wacom Capacity (298):    -1
    Wacom Pressure Threshold (299):    15
    Wacom Sample and Suppress (300):    2, 4
    Wacom Enable Touch (301):    0
    Wacom Hover Click (302):    1
    Wacom Tool Type (303):    "STYLUS" (305)
    Wacom Button Actions (304):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

---

### Post by Ayuthia on 2010-09-22
Can you try this rotation script?  To extract it:
```
tar -xvjf xrotate.tar.bz2
```
To run it you can have it do a normal rotation:
```

./xrotate.py

```
or to give it a direction (normal, left, inverted, right):
```

./xrotate.py inverted

```
You can also run it by:
```

python xrotate.py inverted

```

It should rotate all wacom and evdev devices at this point.

---

### Post by fearless.75 on 2010-09-22
I just two tests and here are the results :

1- Trying to use your pyhton scrip by double clicking in on my desktop and choosing "run". Works alsmot perfect : the cursor is not exactly under the stylus. Same for touch

2- Trying to use your python script in terminal. Works perfect ! Nothing to say more than perfect.

My question is then what the difference when doing in terminal and double clinking on it ? Can i make magick-rotation to use this python script ?

---

### Post by Ayuthia on 2010-09-22
> **fearless.75 said:**
> I just two tests and here are the results :

1- Trying to use your pyhton scrip by double clicking in on my desktop and choosing "run". Works alsmot perfect : the cursor is not exactly under the stylus. Same for touch

2- Trying to use your python script in terminal. Works perfect ! Nothing to say more than perfect.

My question is then what the difference when doing in terminal and double clinking on it ? Can i make magick-rotation to use this python script ?
Thanks for testing it!

That is odd about the clicking vs. running it from the terminal.  There should not be a difference because they are essentially doing the same thing.  I will test it out over here to see if I can see anything.

As for the magick-rotation, I am currently working make some updates for it so that this change will be incorporated.  However, due to some time constraints on my end, I might check and see how difficult it would be to slip this code into the current magick-rotation.

---

### Post by fearless.75 on 2010-09-22
if you need me to make some tests, please feel free to ask me !

I'd like to thank you very much for your help,and the time you're taking to make my tablet PC working like a charm.

I'm really happy with this ! Of course, if you can compile to a new version of magick-rotation, this would be great.

A new test while I was writing down this post : If I run the script by double-clicking it, and then launch the xournal application, problem of the cursor not being exactly under the stylus is solved. Hope this helps !

Thanks again !

---

### Post by Ayuthia on 2010-09-22
> **fearless.75 said:**
> if you need me to make some tests, please feel free to ask me !

I'd like to thank you very much for your help,and the time you're taking to make my tablet PC working like a charm.

I'm really happy with this ! Of course, if you can compile to a new version of magick-rotation, this would be great.

A new test while I was writing down this post : If I run the script by double-clicking it, and then launch the xournal application, problem of the cursor not being exactly under the stylus is solved. Hope this helps !

Thanks again !

I am glad that it is working for you!  I will let you know if I come up with anything with the double-click or magick-rotation.

---

### Post by fearless.75 on 2010-09-22
Just a quick try using the Tablet in portrait mode and using xournal make me realize that the best solution for this script would be the turn off the touch only when the application Xournal is opened. That way this Tablet could be used with both sytlus and fingers and only fingers when a annotator program is launched.

Do you think it could be possible to add such exception to your incredible python script ?

---

### Post by Ayuthia on 2010-09-23
> **fearless.75 said:**
> Just a quick try using the Tablet in portrait mode and using xournal make me realize that the best solution for this script would be the turn off the touch only when the application Xournal is opened. That way this Tablet could be used with both sytlus and fingers and only fingers when a annotator program is launched.

Do you think it could be possible to add such exception to your incredible python script ?

For something like Xournal, you might create a file like myxournal and have it contain:
```

#!/bin/bash
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 0
xournal
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 1

```
and save it.  To make it executable:
```

chmod 744 myxournal

```
You can then just click on that icon and it will automatically turn off your touch, run xournal, and then once you are done, it will turn it back on again.
Hopefully that will suit your needs.

---

### Post by SaintDanBert on 2010-09-23
Karl Hegbloom has a package at his PPA that does all of this without all of the hacking about.

~~~ 0;-Dan

---

### Post by Ayuthia on 2010-09-23
> **SaintDanBert said:**
> Karl Hegbloom has a package at his PPA that does all of this without all of the hacking about.

~~~ 0;-Dan

His PPA package info looks like it is for the Thinkpad.  The rotation information is different in the HP than it is for the Thinkpads.  Do you know if this covers more than just the Thinkpad?

---

### Post by fearless.75 on 2010-09-23
> **Ayuthia said:**
> For something like Xournal, you might create a file like myxournal and have it contain:
```

#!/bin/bash
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 0
xournal
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 1

```and save it.  To make it executable:
```

chmod 744 myxournal

```You can then just click on that icon and it will automatically turn off your touch, run xournal, and then once you are done, it will turn it back on again.
Hopefully that will suit your needs.

The best would be that this happens when your python script is launched. Here I would have to launch your script, then this new script. Note this is very good solution, but a "one does all" would be excellent !

---

### Post by Ayuthia on 2010-09-23
> **fearless.75 said:**
> The best would be that this happens when your python script is launched. Here I would have to launch your script, then this new script. Note this is very good solution, but a "one does all" would be excellent !

So when you want to run xournal, you want the screen to automatically go into tablet mode and turn off touch.  When xournal is done, you want it to rotate back to laptop mode and turn on touch.  Is that correct?

If so:
```

#!/bin/bash
~/xrotate.py right
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 0
xournal
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 1
~/xrotate.py normal

```
should work assuming that the xrotate.py script is in your home directory.

---

### Post by fearless.75 on 2010-09-23
Almost perfect here.What about when running the python rotation script and when xournal is launched it disable automatically the touchscreen and enable it back when xournal is closed. Is this possible ? If not, then I'll take your last solution !

---

### Post by fearless.75 on 2010-09-23
> **fearless.75 said:**
> The best would be that this happens when your python script is launched. Here I would have to launch your script, then this new script. Note this is very good solution, but a "one does all" would be excellent !

I just tried this script and the touchscreen is never disabled ! What's wrong ?

---

### Post by Ayuthia on 2010-09-23
How about trying the following:
```

#!/bin/bash
~/xrotate.py right
xinput set-prop 'N-Trig MultiTouch' 'Device Enabled' 0
xournal
xinput set-prop 'N-Trig MultiTouch' 'Device Enabled' 1
~/xrotate.py normal

```

I did not see that you had an N-Trig MultiTouch device.  Most likely that is why it is still working.  All you really need to do is replace the 'N-Trig Touchscreen' with 'N-Trig MultiTouch'.

Hopefully that will take care of it.

---

### Post by fearless.75 on 2010-09-23
Is there something you don't have the answer ? You're an incredible knowledge base !

It works now perfectly. Many thanks !

---

### Post by Favux on 2010-09-25
Hi fearless.75,

The [**Magick Rotation 0.5**]("http://ubuntuforums.org/showpost.php?p=9888796&postcount=528") applet now supports evdev, along with Wacom, rotation.  So you can use it now if you want to.

---

### Post by fearless.75 on 2010-09-28
Hi,

I just tested this new version and it does not rotate. In fact, there's the message saying it's in tablet mode or back to normal, but it's not launching the xrotate.py. Note the cellwriter is lauching correctly. I also found a new file created called "xrotate.pyc".

Any ideas ?

---

### Post by Favux on 2010-09-28
Hi fearless.75,

> In fact, there's the message saying it's in tablet mode or back to normal, but it's not launching the xrotate.py. 
Can you show me the exact message?

The xrotate.py file is what adds support for evdev rotation as you know.  And xrotate.pyc should appear in the folder after it's run the first time.  So it looks good up to there.

Do you still have the original xrotate.py rotation script you tested for Ayuthia active?

---

### Post by fearless.75 on 2010-09-28
Showing you the message is impossible as it's the notification balloon. 

If I launch the xrotate.py from the magic-rotation script, it works well. But it's not working when using the magic-rotation application despite the notification balloons and the cellwriter launching.

---

### Post by Favux on 2010-09-28
OK, we probably need Ayuthia to debug it.  I'll probably just waste your time if I try.  You're in Lucid right?

---

### Post by fearless.75 on 2010-09-28
correct !

---

### Post by Ayuthia on 2010-09-28
Can you try running the magick-rotation-0.5 script with the debug log turned on?  There should be an option in the setup screen for it.  Once it is on, flip the lid to tablet mode and back to normal mode.  Then, please attach the log.

I am thinking that if everything seems to be working, but the rotation portion (does the pen/touch get rotated?) then the call the to rotate script is not being called correctly.  The log should be able to report that for us.

---

### Post by fearless.75 on 2010-10-01
Hi. Sorry for the time it took to respond. Here's the log created by magick-rotate. Please note this has been done with an HP TX2525nr and not the TX2-1224ca. Rotation python script works as well on this TX2525nr, but not automatically with magic-rotation.

> 
2010-10-01 13:08:43: ---- Debugging Tool Started ----
2010-10-01 13:08:43: checking for rotation
2010-10-01 13:08:43: opening status file
2010-10-01 13:08:43: file opened successfully
2010-10-01 13:08:43: cur_state: 0
 
2010-10-01 13:08:43: old_state: 0
 
2010-10-01 13:08:43: checking for rotation
2010-10-01 13:08:43: opening status file
2010-10-01 13:08:43: file opened successfully
2010-10-01 13:08:43: cur_state: 0
 
2010-10-01 13:08:43: old_state: 0
 
2010-10-01 13:08:44: checking for rotation
2010-10-01 13:08:44: opening status file
2010-10-01 13:08:44: file opened successfully
2010-10-01 13:08:44: cur_state: 0
 
2010-10-01 13:08:44: old_state: 0
 
2010-10-01 13:08:44: checking for rotation
2010-10-01 13:08:44: opening status file
2010-10-01 13:08:44: file opened successfully
2010-10-01 13:08:44: cur_state: 0
 
2010-10-01 13:08:44: old_state: 0
 
2010-10-01 13:08:44: checking for rotation
2010-10-01 13:08:44: opening status file
2010-10-01 13:08:44: file opened successfully
2010-10-01 13:08:44: cur_state: 0
 
2010-10-01 13:08:44: old_state: 0
 
2010-10-01 13:08:44: checking for rotation
2010-10-01 13:08:45: opening status file
2010-10-01 13:08:45: file opened successfully
2010-10-01 13:08:45: cur_state: 0
 
2010-10-01 13:08:45: old_state: 0
 
2010-10-01 13:08:45: checking for rotation
2010-10-01 13:08:45: opening status file
2010-10-01 13:08:45: file opened successfully
2010-10-01 13:08:45: cur_state: 0
 
2010-10-01 13:08:45: old_state: 0
 
2010-10-01 13:08:45: checking for rotation
2010-10-01 13:08:45: opening status file
2010-10-01 13:08:45: file opened successfully
2010-10-01 13:08:45: cur_state: 0
 
2010-10-01 13:08:45: old_state: 0
 
2010-10-01 13:08:45: checking for rotation
2010-10-01 13:08:45: opening status file
2010-10-01 13:08:45: file opened successfully
2010-10-01 13:08:45: cur_state: 0
 
2010-10-01 13:08:45: old_state: 0
 
2010-10-01 13:08:46: checking for rotation
2010-10-01 13:08:46: opening status file
2010-10-01 13:08:46: file opened successfully
2010-10-01 13:08:46: cur_state: 0
 
2010-10-01 13:08:46: old_state: 0
 
2010-10-01 13:08:46: checking for rotation
2010-10-01 13:08:46: opening status file
2010-10-01 13:08:46: file opened successfully
2010-10-01 13:08:46: cur_state: 0
 
2010-10-01 13:08:46: old_state: 0
 
2010-10-01 13:08:46: checking for rotation
2010-10-01 13:08:46: opening status file
2010-10-01 13:08:46: file opened successfully
2010-10-01 13:08:46: cur_state: 0
 
2010-10-01 13:08:46: old_state: 0
 
2010-10-01 13:08:47: checking for rotation
2010-10-01 13:08:47: opening status file
2010-10-01 13:08:47: file opened successfully
2010-10-01 13:08:47: cur_state: 0
 
2010-10-01 13:08:47: old_state: 0
 
2010-10-01 13:08:47: checking for rotation
2010-10-01 13:08:47: opening status file
2010-10-01 13:08:47: file opened successfully
2010-10-01 13:08:47: cur_state: 0
 
2010-10-01 13:08:47: old_state: 0
 
2010-10-01 13:08:47: checking for rotation
2010-10-01 13:08:47: opening status file
2010-10-01 13:08:47: file opened successfully
2010-10-01 13:08:47: cur_state: 0
 
2010-10-01 13:08:47: old_state: 0
 
2010-10-01 13:08:47: checking for rotation
2010-10-01 13:08:47: opening status file
2010-10-01 13:08:47: file opened successfully
2010-10-01 13:08:47: cur_state: 0
 
2010-10-01 13:08:47: old_state: 0
 
2010-10-01 13:08:48: checking for rotation
2010-10-01 13:08:48: opening status file
2010-10-01 13:08:48: file opened successfully
2010-10-01 13:08:48: cur_state: 0
 
2010-10-01 13:08:48: old_state: 0
 
2010-10-01 13:08:48: checking for rotation
2010-10-01 13:08:48: opening status file
2010-10-01 13:08:48: file opened successfully
2010-10-01 13:08:48: cur_state: 0
 
2010-10-01 13:08:48: old_state: 0
 
2010-10-01 13:08:48: checking for rotation
2010-10-01 13:08:48: opening status file
2010-10-01 13:08:48: file opened successfully
2010-10-01 13:08:48: cur_state: 0
 
2010-10-01 13:08:48: old_state: 0
 
2010-10-01 13:08:49: checking for rotation
2010-10-01 13:08:49: opening status file
2010-10-01 13:08:49: file opened successfully
2010-10-01 13:08:49: cur_state: 0
 
2010-10-01 13:08:49: old_state: 0
 
2010-10-01 13:08:49: checking for rotation
2010-10-01 13:08:49: opening status file
2010-10-01 13:08:49: file opened successfully
2010-10-01 13:08:49: cur_state: 0
 
2010-10-01 13:08:49: old_state: 0
 
2010-10-01 13:08:49: checking for rotation
2010-10-01 13:08:49: opening status file
2010-10-01 13:08:49: file opened successfully
2010-10-01 13:08:49: cur_state: 0
 
2010-10-01 13:08:49: old_state: 0
 
2010-10-01 13:08:49: checking for rotation
2010-10-01 13:08:49: opening status file
2010-10-01 13:08:49: file opened successfully
2010-10-01 13:08:49: cur_state: 0
 
2010-10-01 13:08:49: old_state: 0
 
2010-10-01 13:08:50: checking for rotation
2010-10-01 13:08:50: opening status file
2010-10-01 13:08:50: file opened successfully
2010-10-01 13:08:50: cur_state: 0
 
2010-10-01 13:08:50: old_state: 0
 
2010-10-01 13:08:50: checking for rotation
2010-10-01 13:08:50: opening status file
2010-10-01 13:08:50: file opened successfully
2010-10-01 13:08:50: cur_state: 0
 
2010-10-01 13:08:50: old_state: 0
 
2010-10-01 13:08:50: checking for rotation
2010-10-01 13:08:50: opening status file
2010-10-01 13:08:50: file opened successfully
2010-10-01 13:08:50: cur_state: 0
 
2010-10-01 13:08:50: old_state: 0
 
2010-10-01 13:08:51: checking for rotation
2010-10-01 13:08:51: opening status file
2010-10-01 13:08:51: file opened successfully
2010-10-01 13:08:51: cur_state: 0
 
2010-10-01 13:08:51: old_state: 0
 
2010-10-01 13:08:51: checking for rotation
2010-10-01 13:08:51: opening status file
2010-10-01 13:08:51: file opened successfully
2010-10-01 13:08:51: cur_state: 0
 
2010-10-01 13:08:51: old_state: 0
 
2010-10-01 13:08:51: checking for rotation
2010-10-01 13:08:51: opening status file
2010-10-01 13:08:51: file opened successfully
2010-10-01 13:08:51: cur_state: 0
 
2010-10-01 13:08:51: old_state: 0
 
2010-10-01 13:08:51: checking for rotation
2010-10-01 13:08:51: opening status file
2010-10-01 13:08:51: file opened successfully
2010-10-01 13:08:51: cur_state: 0
 
2010-10-01 13:08:51: old_state: 0
 
2010-10-01 13:08:52: checking for rotation
2010-10-01 13:08:52: opening status file
2010-10-01 13:08:52: file opened successfully
2010-10-01 13:08:52: cur_state: 0
 
2010-10-01 13:08:52: old_state: 0
 
2010-10-01 13:08:52: checking for rotation
2010-10-01 13:08:52: opening status file
2010-10-01 13:08:52: file opened successfully
2010-10-01 13:08:52: cur_state: 0
 
2010-10-01 13:08:52: old_state: 0
 
2010-10-01 13:08:52: checking for rotation
2010-10-01 13:08:52: opening status file
2010-10-01 13:08:52: file opened successfully
2010-10-01 13:08:52: cur_state: 0
 
2010-10-01 13:08:52: old_state: 0
 
2010-10-01 13:08:53: checking for rotation
2010-10-01 13:08:53: opening status file
2010-10-01 13:08:53: file opened successfully
2010-10-01 13:08:53: cur_state: 0
 
2010-10-01 13:08:53: old_state: 0
 
2010-10-01 13:08:53: checking for rotation
2010-10-01 13:08:53: opening status file
2010-10-01 13:08:53: file opened successfully
2010-10-01 13:08:53: cur_state: 0
 
2010-10-01 13:08:53: old_state: 0
 
2010-10-01 13:08:53: checking for rotation
2010-10-01 13:08:53: opening status file
2010-10-01 13:08:53: file opened successfully
2010-10-01 13:08:53: cur_state: 0
 
2010-10-01 13:08:53: old_state: 0
 
2010-10-01 13:08:53: checking for rotation
2010-10-01 13:08:53: opening status file
2010-10-01 13:08:53: file opened successfully
2010-10-01 13:08:53: cur_state: 0
 
2010-10-01 13:08:53: old_state: 0
 
2010-10-01 13:08:54: checking for rotation
2010-10-01 13:08:54: opening status file
2010-10-01 13:08:54: file opened successfully
2010-10-01 13:08:54: cur_state: 0
 
2010-10-01 13:08:54: old_state: 0
 
2010-10-01 13:08:54: checking for rotation
2010-10-01 13:08:54: opening status file
2010-10-01 13:08:54: file opened successfully
2010-10-01 13:08:54: cur_state: 0
 
2010-10-01 13:08:54: old_state: 0
 
2010-10-01 13:08:54: checking for rotation
2010-10-01 13:08:54: opening status file
2010-10-01 13:08:54: file opened successfully
2010-10-01 13:08:54: cur_state: 0
 
2010-10-01 13:08:54: old_state: 0
 
2010-10-01 13:08:55: checking for rotation
2010-10-01 13:08:55: opening status file
2010-10-01 13:08:55: file opened successfully
2010-10-01 13:08:55: cur_state: 0
 
2010-10-01 13:08:55: old_state: 0
 
2010-10-01 13:08:55: checking for rotation
2010-10-01 13:08:55: opening status file
2010-10-01 13:08:55: file opened successfully
2010-10-01 13:08:55: cur_state: 0
 
2010-10-01 13:08:55: old_state: 0
 
2010-10-01 13:08:55: checking for rotation
2010-10-01 13:08:55: opening status file
2010-10-01 13:08:55: file opened successfully
2010-10-01 13:08:55: cur_state: 0
 
2010-10-01 13:08:55: old_state: 0
 
2010-10-01 13:08:55: checking for rotation
2010-10-01 13:08:55: opening status file
2010-10-01 13:08:55: file opened successfully
2010-10-01 13:08:55: cur_state: 0
 
2010-10-01 13:08:55: old_state: 0
 
2010-10-01 13:08:56: checking for rotation
2010-10-01 13:08:56: opening status file
2010-10-01 13:08:56: file opened successfully
2010-10-01 13:08:56: cur_state: 0
 
2010-10-01 13:08:56: old_state: 0
 
2010-10-01 13:08:56: checking for rotation
2010-10-01 13:08:56: opening status file
2010-10-01 13:08:56: file opened successfully
2010-10-01 13:08:56: cur_state: 0
 
2010-10-01 13:08:56: old_state: 0
 
2010-10-01 13:08:56: checking for rotation
2010-10-01 13:08:56: opening status file
2010-10-01 13:08:56: file opened successfully
2010-10-01 13:08:56: cur_state: 1
 
2010-10-01 13:08:56: old_state: 0
 
2010-10-01 13:08:56: calling cellwriter --show-window
2010-10-01 13:08:56: Change to Tablet mode
2010-10-01 13:08:57: checking for rotation
2010-10-01 13:08:57: opening status file
2010-10-01 13:08:57: file opened successfully
2010-10-01 13:08:57: cur_state: 1
 
2010-10-01 13:08:57: old_state: 1
 
2010-10-01 13:08:57: checking for rotation
2010-10-01 13:08:57: opening status file
2010-10-01 13:08:57: file opened successfully
2010-10-01 13:08:57: cur_state: 1
 
2010-10-01 13:08:57: old_state: 1
 
2010-10-01 13:08:57: checking for rotation
2010-10-01 13:08:57: opening status file
2010-10-01 13:08:57: file opened successfully
2010-10-01 13:08:57: cur_state: 1
 
2010-10-01 13:08:57: old_state: 1
 
2010-10-01 13:08:58: checking for rotation
2010-10-01 13:08:58: opening status file
2010-10-01 13:08:58: file opened successfully
2010-10-01 13:08:58: cur_state: 1
 
2010-10-01 13:08:58: old_state: 1
 
2010-10-01 13:08:58: checking for rotation
2010-10-01 13:08:58: opening status file
2010-10-01 13:08:58: file opened successfully
2010-10-01 13:08:58: cur_state: 1
 
2010-10-01 13:08:58: old_state: 1
 
2010-10-01 13:08:58: checking for rotation
2010-10-01 13:08:58: opening status file
2010-10-01 13:08:58: file opened successfully
2010-10-01 13:08:58: cur_state: 1
 
2010-10-01 13:08:58: old_state: 1
 
2010-10-01 13:08:58: checking for rotation
2010-10-01 13:08:58: opening status file
2010-10-01 13:08:58: file opened successfully
2010-10-01 13:08:58: cur_state: 1
 
2010-10-01 13:08:58: old_state: 1
 
2010-10-01 13:08:59: checking for rotation
2010-10-01 13:08:59: opening status file
2010-10-01 13:08:59: file opened successfully
2010-10-01 13:08:59: cur_state: 1
 
2010-10-01 13:08:59: old_state: 1
 
2010-10-01 13:08:59: checking for rotation
2010-10-01 13:08:59: opening status file
2010-10-01 13:08:59: file opened successfully
2010-10-01 13:08:59: cur_state: 0
 
2010-10-01 13:08:59: old_state: 1
 
2010-10-01 13:08:59: calling cellwriter --hide-window
2010-10-01 13:08:59: Change to normal state
2010-10-01 13:08:59: checking for rotation
2010-10-01 13:08:59: opening status file
2010-10-01 13:08:59: file opened successfully
2010-10-01 13:09:00: cur_state: 0
 
2010-10-01 13:09:00: old_state: 0
 
2010-10-01 13:09:00: checking for rotation
2010-10-01 13:09:00: opening status file
2010-10-01 13:09:00: file opened successfully
2010-10-01 13:09:00: cur_state: 0
 
2010-10-01 13:09:00: old_state: 0
 
2010-10-01 13:09:00: checking for rotation
2010-10-01 13:09:00: opening status file
2010-10-01 13:09:00: file opened successfully
2010-10-01 13:09:00: cur_state: 0
 
2010-10-01 13:09:00: old_state: 0
 
2010-10-01 13:09:00: checking for rotation
2010-10-01 13:09:00: opening status file
2010-10-01 13:09:00: file opened successfully
2010-10-01 13:09:00: cur_state: 0
 
2010-10-01 13:09:00: old_state: 0
 
2010-10-01 13:09:01: checking for rotation
2010-10-01 13:09:01: opening status file
2010-10-01 13:09:01: file opened successfully
2010-10-01 13:09:01: cur_state: 0
 
2010-10-01 13:09:01: old_state: 0
 
2010-10-01 13:09:01: checking for rotation
2010-10-01 13:09:01: opening status file
2010-10-01 13:09:01: file opened successfully
2010-10-01 13:09:01: cur_state: 0
 
2010-10-01 13:09:01: old_state: 0
 
2010-10-01 13:09:01: checking for rotation
2010-10-01 13:09:01: opening status file
2010-10-01 13:09:01: file opened successfully
2010-10-01 13:09:01: cur_state: 0
 
2010-10-01 13:09:01: old_state: 0
 
2010-10-01 13:09:02: checking for rotation
2010-10-01 13:09:02: opening status file
2010-10-01 13:09:02: file opened successfully
2010-10-01 13:09:02: cur_state: 0
 
2010-10-01 13:09:02: old_state: 0
 
2010-10-01 13:09:02: checking for rotation
2010-10-01 13:09:02: opening status file
2010-10-01 13:09:02: file opened successfully
2010-10-01 13:09:02: cur_state: 0
 
2010-10-01 13:09:02: old_state: 0
 
2010-10-01 13:09:02: checking for rotation
2010-10-01 13:09:02: opening status file
2010-10-01 13:09:02: file opened successfully
2010-10-01 13:09:02: cur_state: 0
 
2010-10-01 13:09:02: old_state: 0
 
2010-10-01 13:09:02: checking for rotation
2010-10-01 13:09:02: opening status file
2010-10-01 13:09:02: file opened successfully
2010-10-01 13:09:02: cur_state: 0
 
2010-10-01 13:09:02: old_state: 0
 
2010-10-01 13:09:03: checking for rotation
2010-10-01 13:09:03: opening status file
2010-10-01 13:09:03: file opened successfully
2010-10-01 13:09:03: cur_state: 0
 
2010-10-01 13:09:03: old_state: 0
 
2010-10-01 13:09:03: checking for rotation
2010-10-01 13:09:03: opening status file
2010-10-01 13:09:03: file opened successfully
2010-10-01 13:09:03: cur_state: 0
 
2010-10-01 13:09:03: old_state: 0
 
2010-10-01 13:09:03: checking for rotation
2010-10-01 13:09:03: opening status file
2010-10-01 13:09:03: file opened successfully
2010-10-01 13:09:03: cur_state: 0
 
2010-10-01 13:09:03: old_state: 0
 
2010-10-01 13:09:04: checking for rotation
2010-10-01 13:09:04: opening status file
2010-10-01 13:09:04: file opened successfully
2010-10-01 13:09:04: cur_state: 0
 
2010-10-01 13:09:04: old_state: 0
 
2010-10-01 13:09:04: checking for rotation
2010-10-01 13:09:04: opening status file
2010-10-01 13:09:04: file opened successfully
2010-10-01 13:09:04: cur_state: 0
 
2010-10-01 13:09:04: old_state: 0
 
2010-10-01 13:09:04: checking for rotation
2010-10-01 13:09:04: opening status file
2010-10-01 13:09:04: file opened successfully
2010-10-01 13:09:04: cur_state: 0
 
2010-10-01 13:09:04: old_state: 0
 
2010-10-01 13:09:04: checking for rotation
2010-10-01 13:09:04: opening status file
2010-10-01 13:09:04: file opened successfully
2010-10-01 13:09:04: cur_state: 0
 
2010-10-01 13:09:04: old_state: 0
 
2010-10-01 13:09:05: checking for rotation
2010-10-01 13:09:05: opening status file
2010-10-01 13:09:05: file opened successfully
2010-10-01 13:09:05: cur_state: 0
 
2010-10-01 13:09:05: old_state: 0
 
2010-10-01 13:09:05: checking for rotation
2010-10-01 13:09:05: opening status file
2010-10-01 13:09:05: file opened successfully
2010-10-01 13:09:05: cur_state: 0
 
2010-10-01 13:09:05: old_state: 0
 
2010-10-01 13:09:05: checking for rotation
2010-10-01 13:09:05: opening status file
2010-10-01 13:09:05: file opened successfully
2010-10-01 13:09:05: cur_state: 0
 
2010-10-01 13:09:05: old_state: 0
 
2010-10-01 13:09:06: checking for rotation
2010-10-01 13:09:06: opening status file
2010-10-01 13:09:06: file opened successfully
2010-10-01 13:09:06: cur_state: 0
 
2010-10-01 13:09:06: old_state: 0
 
2010-10-01 13:09:06: checking for rotation
2010-10-01 13:09:06: opening status file
2010-10-01 13:09:06: file opened successfully
2010-10-01 13:09:06: cur_state: 0
 
2010-10-01 13:09:06: old_state: 0
 
2010-10-01 13:09:06: checking for rotation
2010-10-01 13:09:06: opening status file
2010-10-01 13:09:06: file opened successfully
2010-10-01 13:09:06: cur_state: 0
 
2010-10-01 13:09:06: old_state: 0
 
2010-10-01 13:09:06: checking for rotation
2010-10-01 13:09:06: opening status file
2010-10-01 13:09:06: file opened successfully
2010-10-01 13:09:06: cur_state: 0
 
2010-10-01 13:09:06: old_state: 0
 
2010-10-01 13:09:07: checking for rotation
2010-10-01 13:09:07: opening status file
2010-10-01 13:09:07: file opened successfully
2010-10-01 13:09:07: cur_state: 0
 
2010-10-01 13:09:07: old_state: 0
 
2010-10-01 13:09:07: checking for rotation
2010-10-01 13:09:07: opening status file
2010-10-01 13:09:07: file opened successfully
2010-10-01 13:09:07: cur_state: 0
 
2010-10-01 13:09:07: old_state: 0
 
2010-10-01 13:09:07: checking for rotation
2010-10-01 13:09:07: opening status file
2010-10-01 13:09:07: file opened successfully
2010-10-01 13:09:07: cur_state: 0
 
2010-10-01 13:09:07: old_state: 0
 
2010-10-01 13:09:08: checking for rotation
2010-10-01 13:09:08: opening status file
2010-10-01 13:09:08: file opened successfully
2010-10-01 13:09:08: cur_state: 0
 
2010-10-01 13:09:08: old_state: 0
 
2010-10-01 13:09:08: checking for rotation
2010-10-01 13:09:08: opening status file
2010-10-01 13:09:08: file opened successfully
2010-10-01 13:09:08: cur_state: 0
 
2010-10-01 13:09:08: old_state: 0
 
2010-10-01 13:09:08: checking for rotation
2010-10-01 13:09:08: opening status file
2010-10-01 13:09:08: file opened successfully
2010-10-01 13:09:08: cur_state: 0
 
2010-10-01 13:09:08: old_state: 0
 
2010-10-01 13:09:08: checking for rotation
2010-10-01 13:09:08: opening status file
2010-10-01 13:09:08: file opened successfully
2010-10-01 13:09:08: cur_state: 0
 
2010-10-01 13:09:09: old_state: 0
 
2010-10-01 13:09:09: checking for rotation
2010-10-01 13:09:09: opening status file
2010-10-01 13:09:09: file opened successfully
2010-10-01 13:09:09: cur_state: 0
 
2010-10-01 13:09:09: old_state: 0
 
2010-10-01 13:09:09: checking for rotation
2010-10-01 13:09:09: opening status file
2010-10-01 13:09:09: file opened successfully
2010-10-01 13:09:09: cur_state: 0
 
2010-10-01 13:09:09: old_state: 0
 
2010-10-01 13:09:09: checking for rotation
2010-10-01 13:09:09: opening status file
2010-10-01 13:09:09: file opened successfully
2010-10-01 13:09:09: cur_state: 0
 
2010-10-01 13:09:09: old_state: 0
 
2010-10-01 13:09:10: checking for rotation
2010-10-01 13:09:10: opening status file
2010-10-01 13:09:10: file opened successfully
2010-10-01 13:09:10: cur_state: 0
 
2010-10-01 13:09:10: old_state: 0
 
2010-10-01 13:09:10: checking for rotation
2010-10-01 13:09:10: opening status file
2010-10-01 13:09:10: file opened successfully
2010-10-01 13:09:10: cur_state: 0
 
2010-10-01 13:09:10: old_state: 0
 
2010-10-01 13:09:10: checking for rotation
2010-10-01 13:09:10: opening status file
2010-10-01 13:09:10: file opened successfully
2010-10-01 13:09:10: cur_state: 0
 
2010-10-01 13:09:10: old_state: 0
 
2010-10-01 13:09:10: checking for rotation
2010-10-01 13:09:10: opening status file
2010-10-01 13:09:10: file opened successfully
2010-10-01 13:09:10: cur_state: 0
 
2010-10-01 13:09:10: old_state: 0
 
2010-10-01 13:09:11: checking for rotation
2010-10-01 13:09:11: opening status file
2010-10-01 13:09:11: file opened successfully
2010-10-01 13:09:11: cur_state: 0
 
2010-10-01 13:09:11: old_state: 0
 
2010-10-01 13:09:11: checking for rotation
2010-10-01 13:09:11: opening status file
2010-10-01 13:09:11: file opened successfully
2010-10-01 13:09:11: cur_state: 0
 
2010-10-01 13:09:11: old_state: 0
 
2010-10-01 13:09:11: checking for rotation
2010-10-01 13:09:11: opening status file
2010-10-01 13:09:11: file opened successfully
2010-10-01 13:09:11: cur_state: 0
 
2010-10-01 13:09:11: old_state: 0
 
2010-10-01 13:09:12: checking for rotation
2010-10-01 13:09:12: opening status file
2010-10-01 13:09:12: file opened successfully
2010-10-01 13:09:12: cur_state: 0
 
2010-10-01 13:09:12: old_state: 0
 
2010-10-01 13:09:12: checking for rotation
2010-10-01 13:09:12: opening status file
2010-10-01 13:09:12: file opened successfully
2010-10-01 13:09:12: cur_state: 0
 
2010-10-01 13:09:12: old_state: 0
 
2010-10-01 13:09:12: checking for rotation
2010-10-01 13:09:12: opening status file
2010-10-01 13:09:12: file opened successfully
2010-10-01 13:09:12: cur_state: 0
 
2010-10-01 13:09:12: old_state: 0
 
2010-10-01 13:09:12: checking for rotation
2010-10-01 13:09:12: opening status file
2010-10-01 13:09:12: file opened successfully
2010-10-01 13:09:12: cur_state: 0
 
2010-10-01 13:09:12: old_state: 0
 
2010-10-01 13:09:13: checking for rotation
2010-10-01 13:09:13: opening status file
2010-10-01 13:09:13: file opened successfully
2010-10-01 13:09:13: cur_state: 0
 
2010-10-01 13:09:13: old_state: 0
 
2010-10-01 13:09:13: checking for rotation
2010-10-01 13:09:13: opening status file
2010-10-01 13:09:13: file opened successfully
2010-10-01 13:09:13: cur_state: 0
 
2010-10-01 13:09:13: old_state: 0
 
2010-10-01 13:09:13: checking for rotation
2010-10-01 13:09:13: opening status file
2010-10-01 13:09:13: file opened successfully
2010-10-01 13:09:13: cur_state: 0
 
2010-10-01 13:09:13: old_state: 0
 
2010-10-01 13:09:14: checking for rotation
2010-10-01 13:09:14: opening status file
2010-10-01 13:09:14: file opened successfully
2010-10-01 13:09:14: cur_state: 0
 
2010-10-01 13:09:14: old_state: 0
 
2010-10-01 13:09:14: checking for rotation
2010-10-01 13:09:14: opening status file
2010-10-01 13:09:14: file opened successfully
2010-10-01 13:09:14: cur_state: 0
 
2010-10-01 13:09:14: old_state: 0
 
2010-10-01 13:09:14: checking for rotation
2010-10-01 13:09:14: opening status file
2010-10-01 13:09:14: file opened successfully
2010-10-01 13:09:14: cur_state: 0
 
2010-10-01 13:09:14: old_state: 0
 
2010-10-01 13:09:14: checking for rotation
2010-10-01 13:09:14: opening status file
2010-10-01 13:09:15: file opened successfully
2010-10-01 13:09:15: cur_state: 0
 
2010-10-01 13:09:15: old_state: 0
 
2010-10-01 13:09:15: checking for rotation
2010-10-01 13:09:15: opening status file
2010-10-01 13:09:15: file opened successfully
2010-10-01 13:09:15: cur_state: 0
 
2010-10-01 13:09:15: old_state: 0
 
2010-10-01 13:09:15: checking for rotation
2010-10-01 13:09:15: opening status file
2010-10-01 13:09:15: file opened successfully
2010-10-01 13:09:15: cur_state: 0
 
2010-10-01 13:09:15: old_state: 0
 
2010-10-01 13:09:15: checking for rotation
2010-10-01 13:09:15: opening status file
2010-10-01 13:09:15: file opened successfully
2010-10-01 13:09:15: cur_state: 0
 
2010-10-01 13:09:15: old_state: 0
 
2010-10-01 13:09:16: checking for rotation
2010-10-01 13:09:16: opening status file
2010-10-01 13:09:16: file opened successfully
2010-10-01 13:09:16: cur_state: 0
 
2010-10-01 13:09:16: old_state: 0
 
2010-10-01 13:09:16: checking for rotation
2010-10-01 13:09:16: opening status file
2010-10-01 13:09:16: file opened successfully
2010-10-01 13:09:16: cur_state: 0
 
2010-10-01 13:09:16: old_state: 0
 
2010-10-01 13:09:16: checking for rotation
2010-10-01 13:09:16: opening status file
2010-10-01 13:09:16: file opened successfully
2010-10-01 13:09:16: cur_state: 0
 
2010-10-01 13:09:16: old_state: 0
 
2010-10-01 13:09:17: checking for rotation
2010-10-01 13:09:17: opening status file
2010-10-01 13:09:17: file opened successfully
2010-10-01 13:09:17: cur_state: 0
 
2010-10-01 13:09:17: old_state: 0
 
2010-10-01 13:09:17: checking for rotation
2010-10-01 13:09:17: opening status file
2010-10-01 13:09:17: file opened successfully
2010-10-01 13:09:17: cur_state: 0
 
2010-10-01 13:09:17: old_state: 0
 
2010-10-01 13:09:17: checking for rotation
2010-10-01 13:09:17: opening status file
2010-10-01 13:09:17: file opened successfully
2010-10-01 13:09:17: cur_state: 0
 
2010-10-01 13:09:17: old_state: 0
 
2010-10-01 13:09:17: checking for rotation
2010-10-01 13:09:17: opening status file
2010-10-01 13:09:17: file opened successfully
2010-10-01 13:09:17: cur_state: 0
 
2010-10-01 13:09:17: old_state: 0
 
2010-10-01 13:09:18: checking for rotation
2010-10-01 13:09:18: opening status file
2010-10-01 13:09:18: file opened successfully
2010-10-01 13:09:18: cur_state: 0
 
2010-10-01 13:09:18: old_state: 0
 
2010-10-01 13:09:18: checking for rotation
2010-10-01 13:09:18: opening status file
2010-10-01 13:09:18: file opened successfully
2010-10-01 13:09:18: cur_state: 0
 
2010-10-01 13:09:18: old_state: 0
 
2010-10-01 13:09:18: checking for rotation
2010-10-01 13:09:18: opening status file
2010-10-01 13:09:18: file opened successfully
2010-10-01 13:09:18: cur_state: 0
 
2010-10-01 13:09:18: old_state: 0
 
2010-10-01 13:09:19: checking for rotation
2010-10-01 13:09:19: opening status file
2010-10-01 13:09:19: file opened successfully
2010-10-01 13:09:19: cur_state: 0
 
2010-10-01 13:09:19: old_state: 0
 
2010-10-01 13:09:19: checking for rotation
2010-10-01 13:09:19: opening status file
2010-10-01 13:09:19: file opened successfully
2010-10-01 13:09:19: cur_state: 0
 
2010-10-01 13:09:19: old_state: 0
 
2010-10-01 13:09:19: checking for rotation
2010-10-01 13:09:19: opening status file
2010-10-01 13:09:19: file opened successfully
2010-10-01 13:09:19: cur_state: 0
 
2010-10-01 13:09:19: old_state: 0
 
2010-10-01 13:09:19: checking for rotation
2010-10-01 13:09:19: opening status file
2010-10-01 13:09:19: file opened successfully
2010-10-01 13:09:19: cur_state: 0
 
2010-10-01 13:09:19: old_state: 0
 
2010-10-01 13:09:20: checking for rotation
2010-10-01 13:09:20: opening status file
2010-10-01 13:09:20: file opened successfully
2010-10-01 13:09:20: cur_state: 0
 
2010-10-01 13:09:20: old_state: 0
 
2010-10-01 13:09:20: checking for rotation
2010-10-01 13:09:20: opening status file
2010-10-01 13:09:20: file opened successfully
2010-10-01 13:09:20: cur_state: 0
 
2010-10-01 13:09:20: old_state: 0
 
2010-10-01 13:09:20: checking for rotation
2010-10-01 13:09:20: opening status file
2010-10-01 13:09:20: file opened successfully
2010-10-01 13:09:20: cur_state: 0
 
2010-10-01 13:09:20: old_state: 0
 
2010-10-01 13:09:21: checking for rotation
2010-10-01 13:09:21: opening status file
2010-10-01 13:09:21: file opened successfully
2010-10-01 13:09:21: cur_state: 0
 
2010-10-01 13:09:21: old_state: 0
 
2010-10-01 13:09:21: checking for rotation
2010-10-01 13:09:21: opening status file
2010-10-01 13:09:21: file opened successfully
2010-10-01 13:09:21: cur_state: 0
 
2010-10-01 13:09:21: old_state: 0
 
2010-10-01 13:09:21: checking for rotation
2010-10-01 13:09:21: opening status file
2010-10-01 13:09:21: file opened successfully
2010-10-01 13:09:21: cur_state: 0
 
2010-10-01 13:09:21: old_state: 0
 
2010-10-01 13:09:21: checking for rotation
2010-10-01 13:09:21: opening status file
2010-10-01 13:09:21: file opened successfully
2010-10-01 13:09:21: cur_state: 0
 
2010-10-01 13:09:21: old_state: 0
 
2010-10-01 13:09:22: checking for rotation
2010-10-01 13:09:22: opening status file
2010-10-01 13:09:22: file opened successfully
2010-10-01 13:09:22: cur_state: 0
 
2010-10-01 13:09:22: old_state: 0
 
2010-10-01 13:09:22: checking for rotation
2010-10-01 13:09:22: opening status file
2010-10-01 13:09:22: file opened successfully
2010-10-01 13:09:22: cur_state: 0
 
2010-10-01 13:09:22: old_state: 0
 
2010-10-01 13:09:22: checking for rotation
2010-10-01 13:09:22: opening status file
2010-10-01 13:09:22: file opened successfully
2010-10-01 13:09:22: cur_state: 0
 
2010-10-01 13:09:22: old_state: 0
 
2010-10-01 13:09:23: checking for rotation
2010-10-01 13:09:23: opening status file
2010-10-01 13:09:23: file opened successfully
2010-10-01 13:09:23: cur_state: 0
 
2010-10-01 13:09:23: old_state: 0
 
2010-10-01 13:09:23: checking for rotation
2010-10-01 13:09:23: opening status file
2010-10-01 13:09:23: file opened successfully
2010-10-01 13:09:23: cur_state: 0
 
2010-10-01 13:09:23: old_state: 0
 
2010-10-01 13:09:23: checking for rotation
2010-10-01 13:09:23: opening status file
2010-10-01 13:09:23: file opened successfully
2010-10-01 13:09:23: cur_state: 0
 
2010-10-01 13:09:23: old_state: 0
 
2010-10-01 13:09:23: checking for rotation
2010-10-01 13:09:23: opening status file
2010-10-01 13:09:23: file opened successfully
2010-10-01 13:09:23: cur_state: 0
 
2010-10-01 13:09:23: old_state: 0
 
2010-10-01 13:09:24: checking for rotation
2010-10-01 13:09:24: opening status file
2010-10-01 13:09:24: file opened successfully
2010-10-01 13:09:24: cur_state: 0
 
2010-10-01 13:09:24: old_state: 0
 
2010-10-01 13:09:24: checking for rotation
2010-10-01 13:09:24: opening status file
2010-10-01 13:09:24: file opened successfully
2010-10-01 13:09:24: cur_state: 0
 
2010-10-01 13:09:24: old_state: 0
 
2010-10-01 13:09:24: checking for rotation
2010-10-01 13:09:24: opening status file
2010-10-01 13:09:24: file opened successfully
2010-10-01 13:09:24: cur_state: 0
 
2010-10-01 13:09:24: old_state: 0
 
2010-10-01 13:09:24: checking for rotation
2010-10-01 13:09:25: opening status file
2010-10-01 13:09:25: file opened successfully
2010-10-01 13:09:25: cur_state: 0
 
2010-10-01 13:09:25: old_state: 0
 
2010-10-01 13:09:25: checking for rotation
2010-10-01 13:09:25: opening status file
2010-10-01 13:09:25: file opened successfully
2010-10-01 13:09:25: cur_state: 0
 
2010-10-01 13:09:25: old_state: 0
 
2010-10-01 13:09:25: checking for rotation
2010-10-01 13:09:25: opening status file
2010-10-01 13:09:25: file opened successfully
2010-10-01 13:09:25: cur_state: 0
 
2010-10-01 13:09:25: old_state: 0
 
2010-10-01 13:09:25: checking for rotation
2010-10-01 13:09:25: opening status file
2010-10-01 13:09:25: file opened successfully
2010-10-01 13:09:25: cur_state: 0
 
2010-10-01 13:09:25: old_state: 0
 
2010-10-01 13:09:26: checking for rotation
2010-10-01 13:09:26: opening status file
2010-10-01 13:09:26: file opened successfully
2010-10-01 13:09:26: cur_state: 0
 
2010-10-01 13:09:26: old_state: 0
 
2010-10-01 13:09:26: checking for rotation
2010-10-01 13:09:26: opening status file
2010-10-01 13:09:26: file opened successfully
2010-10-01 13:09:26: cur_state: 0
 
2010-10-01 13:09:26: old_state: 0
 
2010-10-01 13:09:26: checking for rotation
2010-10-01 13:09:26: opening status file
2010-10-01 13:09:26: file opened successfully
2010-10-01 13:09:26: cur_state: 0
 
2010-10-01 13:09:26: old_state: 0
 
2010-10-01 13:09:27: checking for rotation
2010-10-01 13:09:27: opening status file
2010-10-01 13:09:27: file opened successfully
2010-10-01 13:09:27: cur_state: 0
 
2010-10-01 13:09:27: old_state: 0
 
2010-10-01 13:09:27: checking for rotation
2010-10-01 13:09:27: opening status file
2010-10-01 13:09:27: file opened successfully
2010-10-01 13:09:27: cur_state: 0
 
2010-10-01 13:09:27: old_state: 0
 
2010-10-01 13:09:27: checking for rotation
2010-10-01 13:09:27: opening status file
2010-10-01 13:09:27: file opened successfully
2010-10-01 13:09:27: cur_state: 0
 
2010-10-01 13:09:27: old_state: 0
 
2010-10-01 13:09:27: checking for rotation
2010-10-01 13:09:27: opening status file
2010-10-01 13:09:27: file opened successfully
2010-10-01 13:09:27: cur_state: 0
 
2010-10-01 13:09:27: old_state: 0
 
2010-10-01 13:09:28: checking for rotation
2010-10-01 13:09:28: opening status file
2010-10-01 13:09:28: file opened successfully
2010-10-01 13:09:28: cur_state: 0
 
2010-10-01 13:09:28: old_state: 0
 
2010-10-01 13:09:28: checking for rotation
2010-10-01 13:09:28: opening status file
2010-10-01 13:09:28: file opened successfully
2010-10-01 13:09:28: cur_state: 0
 
2010-10-01 13:09:28: old_state: 0
 
2010-10-01 13:09:28: checking for rotation
2010-10-01 13:09:28: opening status file
2010-10-01 13:09:28: file opened successfully
2010-10-01 13:09:28: cur_state: 0
 
2010-10-01 13:09:28: old_state: 0
 
2010-10-01 13:09:29: checking for rotation
2010-10-01 13:09:29: opening status file
2010-10-01 13:09:29: file opened successfully
2010-10-01 13:09:29: cur_state: 0
 
2010-10-01 13:09:29: old_state: 0
 
2010-10-01 13:09:29: checking for rotation
2010-10-01 13:09:29: opening status file
2010-10-01 13:09:29: file opened successfully
2010-10-01 13:09:29: cur_state: 0
 
2010-10-01 13:09:29: old_state: 0
 
2010-10-01 13:09:29: checking for rotation
2010-10-01 13:09:29: opening status file
2010-10-01 13:09:29: file opened successfully
2010-10-01 13:09:29: cur_state: 0
 
2010-10-01 13:09:29: old_state: 0
 
2010-10-01 13:09:29: checking for rotation
2010-10-01 13:09:29: opening status file
2010-10-01 13:09:29: file opened successfully
2010-10-01 13:09:29: cur_state: 0
 
2010-10-01 13:09:29: old_state: 0
 
2010-10-01 13:09:30: checking for rotation
2010-10-01 13:09:30: opening status file
2010-10-01 13:09:30: file opened successfully
2010-10-01 13:09:30: cur_state: 0
 
2010-10-01 13:09:30: old_state: 0
 
2010-10-01 13:09:30: checking for rotation
2010-10-01 13:09:30: opening status file
2010-10-01 13:09:30: file opened successfully
2010-10-01 13:09:30: cur_state: 0
 
2010-10-01 13:09:30: old_state: 0
 
2010-10-01 13:09:30: checking for rotation
2010-10-01 13:09:30: opening status file
2010-10-01 13:09:30: file opened successfully
2010-10-01 13:09:30: cur_state: 0
 
2010-10-01 13:09:30: old_state: 0
 

Moreover, with this TX2525nr I miss the right click with the stylus. Any ideas ?

---

### Post by Ayuthia on 2010-10-01
> **fearless.75 said:**
> Hi. Sorry for the time it took to respond. Here's the log created by magick-rotate. Please note this has been done with an HP TX2525nr and not the TX2-1224ca. Rotation python script works as well on this TX2525nr, but not automatically with magic-rotation.


 

Moreover, with this TX2525nr I miss the right click with the stylus. Any ideas ?

I found the issue.  There was an extra tab where there should not have been.  In magick-rotation-0.5 at line 257, the code should look like this:
```

# this exec array, needed for rotation and post exec
#def exec_array(arr):
def exec_array(is_normal):
    r = rotate()
    if is_normal:
        rot_mod=['normal', 'none']
        afexec=run_normal
        beexec=run_normal_before
    else:
        rot_mod=rotate_mode
        afexec=run_tablet
        beexec=run_tablet_before
    if beexec:
        debug("calling %s" % beexec)
        os.system(beexec + "&")

[B]    debug("calling xrotate %s" % rot_mod[0])
    r.rotate(rot_mod[0])[/B]

    if afexec:
        debug("calling %s" % afexec)
        os.system(afexec + "&")
#   for i in arr:
#       if ( i != ""):
#           debug("calling %s" % i)
#           os.system(i + "&")

```

Can you try this attached version?

As for the right-click, I think that you will need to go into /usr/lib/X11/xorg.conf.d/10-wacom.conf and have it contain the following:
```

Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        Option "Button 2" "3"
EndSection

```

Favux, if you happen to be reading this, please let us know if it is incorrect.

---

### Post by fearless.75 on 2010-10-01
Impossible to uncompress your file. Can you repost it ?

For right click I don not have the "10-wacom.conf" file. Do i need to create it with the code you gave ?

---

### Post by Favux on 2010-10-01
You can't uncompress it from the gui.  Use the terminal:
```
tar xvf /home/yourusername/Desktop/Magick_Rotation_0.5.tar.gz

```
From the HOW TO:
```
 Section "InputClass"
     Identifier "Wacom N-Trig class"
     MatchProduct "HID 1b96:0001|N-Trig Pen"
     MatchDevicePath "/dev/input/event*"
     Driver "wacom"
     Option "Button2" "3"
 EndSection
```
To put stylus on linuxwacom, touch on evdev, and get right click.

---

### Post by Ayuthia on 2010-10-01
> **fearless.75 said:**
> Impossible to uncompress your file. Can you repost it ?

For right click I don not have the "10-wacom.conf" file. Do i need to create it with the code you gave ?

I have reloaded the file in the above post.  Please let me know if:
```

tar -xvf Magick_Rotation_0.5.tar.gz

```
does not work.

---

### Post by Ayuthia on 2010-10-01
> **Favux said:**
> You can't uncompress it from the gui.  Use the terminal:
```
tar xvf /home/yourusername/Desktop/Magick_Rotation_0.5.tar.gz

```
From the HOW TO:
```
 Section "InputClass"
     Identifier "Wacom N-Trig class"
     MatchProduct "HID 1b96:0001|N-Trig Pen"
     MatchDevicePath "/dev/input/event*"
     Driver "wacom"
     Option "Button2" "3"
 EndSection
```
To put stylus on linuxwacom, touch on evdev, and get right click.

Favux, the right-click portion is for the TX2525nr.  That one is not an N-Trig device, right?

---

### Post by Favux on 2010-10-01
The terminal command will work.  As you recall we went through this once before given your habit of compressing from the command line.  Your syntax isn't quite right for the gui.  So I've had to do this on all your gz's lately.

And you know what a burden it is for me to not use the gui and have to do it from the command line.  Notice this time I have borne it in stoic silence!

The:
```
Option "Button2" "3"

```
Should work on any stylus with buttons that is on the linuxwacom driver.  It's a wacom option.

---

### Post by fearless.75 on 2010-10-01
now magick-rotation works, but on this tablet (TX2525nr) the stylus is not working properly.

For this code, where should I put it ? In other words, what is the file I have to edit ?

 Section "InputClass"      Identifier "Wacom N-Trig class"      MatchProduct "HID 1b96:0001|N-Trig Pen"      MatchDevicePath "/dev/input/event*"      Driver "wacom"      Option "Button2" "3"  EndSection

---

### Post by Ayuthia on 2010-10-01
> **Favux said:**
> The terminal command will work.  As you recall we went through this once before given your habit of compressing from the command line.  Your syntax isn't quite right for the gui.  So I've had to do this on all your gz's lately.

And you know what a burden it is for me to not use the gui and have to do it from the command line.  Notice this time I have borne it in stoic silence!

The:
```
Option "Button2" "3"

```
Should work on any stylus with buttons that is on the linuxwacom driver.  It's a wacom option.

Oops.  I do recall the conversation about the compression.  I will have to install Ubuntu back on my machine and get the compression right.  By the way, what is GUI?  :)

The reason for my question about it being a non N-trig device is because of the MatchProduct line that you provided.  I was thinking that it might skip the Wacom device in configuring the device.

---

### Post by Favux on 2010-10-01
No, because it's matching to the wacom driver line.  And since it's the wacom driver you can use the wacom option.

GUI = graphical user interface  :)

---

### Post by fearless.75 on 2010-10-01
The TX2-1224ca (that I don't have for the moment) is the NTrig

The TX2525nr is the wacom one. When I create a file in /usr/lib/X11/xorg.conf.d/10-wacom.conf

and adding

> Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class identifiers"
    MatchProduct "WACf|FUJ02e5|FUJ02e7"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

 Section "InputClass"
     Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
     MatchDevicePath "/dev/input/event*"
     Driver "wacom"
    Option "Button2" "3"
 EndSection

the stylus and touchpad are not working at all.

---

### Post by Favux on 2010-10-01
Sorry fearless.75, I completely missed you had changed tablets.  Oops.  So Ayuthia was right, and I was wrong, wrong, wrong!  You want to add:
```
Option "Button2" "3"
```
to the wacom usb snippet:
```
Section "InputClass"
Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
# MatchProduct "Wacom|WALTOP|WACOM"
MatchProduct "Wacom|WACOM"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
Option "Button2" "3"
EndSection
```

However modifying the N-trig snippet should have no effect on your TX2500.

---

### Post by fearless.75 on 2010-10-06
Thanks for your help guys, everything works perfectly on the TX2-1224ca and also the TX2525nr.

Do you have any idea for the following issues :
- how to make the fingerprint work
- how to make recognized the other buttons of the laptop (like screen rotation)
- how to make the light of the mute button go to orange when mute on (like on the windows OS)

Your helps is highly appreciated !

---

### Post by Ayuthia on 2010-10-06
> **fearless.75 said:**
> Thanks for your help guys, everything works perfectly on the TX2-1224ca and also the TX2525nr.

Do you have any idea for the following issues :
- how to make the fingerprint work
- how to make recognized the other buttons of the laptop (like screen rotation)
- how to make the light of the mute button go to orange when mute on (like on the windows OS)

Your helps is highly appreciated !

If your fingerprint device is (via lsusb):
```

08ff:1600 AuthenTec, Inc. AES1600

```
you should be able to use fprint-demo and libfprint.  I will say that it does not work as well as it does in Windows though mainly because it is reading just one fingerprint scan so each time you swipe your finger, there is a good chance that the portion of the fingerprint does not match up enough.  

As for the missing buttons, as far as I know, they have not been discovered as of yet.  There is a Q button that has been used for some to do the rotate and there is an "m" like button on others that is currently mapped for the media button.  You can find out what keys work by using the Terminal and running xev.

Finally for the orange light, as far as I know, that has not been found yet either.

---

