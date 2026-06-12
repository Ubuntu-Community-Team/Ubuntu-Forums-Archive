---
title: "Touch Calibration Siso Tablo"
date: 2009-09-12
forum: Hardware
---

### Post by bkanuka on 2009-09-12
I got a Siso Tablo as a gift the other day. It attaches to the top of a laptop screen and turns it into a touch screen (tracks pen like a wiimote).

It basically works out of the box, except it isn't calibrated.

I read some threads on the Wacom tablet and some other touch screen issues. They suggest puting something in xorg.conf with "Xmax=" and "Ymax=" values, which makes sense to me, but the sections always include "driver=" and I have no idea what driver this is using. How do I find out?

Ubuntu recognizes this as a mouse, I think, and may not know what to do with Xmax and Ymax for a mouse anyway.

Also I find it strange that I would put anything in xorg.conf when it is so empty in Jaunty.  It is not the xorg I tweaked when I was on Slackware 11 years ago.

Please and Thank you!

---

### Post by Favux on 2009-09-12
Hi bkanuka,

Tough problem.  It would help if you had a driver or could re-purpose one.  To figure out which mouse(?) .fdi is configuring it you need to do a "lshal>lshal.txt" and find the section(s) dealing with Siso Tablo.  Figure out the id from them, or what match line is picking it up.

Maybe you could then re-purpose the .fdi or write one for it.  Something along the lines in here:  [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)  An example (ignoring the driver) would be the Aiptek.fdi in post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5](http://ubuntuforums.org/showthread.php?t=1191826&highlight=medion&page=5)  And for what it's worth the Xlib manual:  [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)

Lot's of work.  You might want to see if the evtouch driver (in Synaptics) picks it up.

---

### Post by bkanuka on 2009-09-13
Thank you Favux, there is some very good information in your post.

However, I cannot for the life of me get my .fdi file to have any effect. Here are the relevant parts of command outputs:

lshal
```
udi = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0'  (string)
  info.product = 'HID 1b28:4617'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event14'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0'  (string)
  input.product = 'HID 1b28:4617'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event14'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input24/event14'  (string)

```

xinput list
```
"HID 1b28:4617"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 6500
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 6500
		Resolution is 10000

```

xinput list-props "HID 1b28:4617"
```
Device 'HID 1b28:4617':
	Device Enabled (109):		1
	Evdev Axis Inversion (241):		0, 0
	Evdev Reopen Attempts (242):		10
	Evdev Axis Calibration (243):		
	Evdev Axes Swap (244):		0
	Evdev Middle Button Emulation (245):		2
	Evdev Middle Button Timeout (246):		50
	Evdev Wheel Emulation (247):		0
	Evdev Wheel Emulation Axes (248):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (249):		10
	Evdev Wheel Emulation Timeout (250):		200
	Evdev Wheel Emulation Button (251):		4
	Evdev Drag Lock Buttons (252):		0

```

10-siso.fdi
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
	<match key="info.capabilities" contains="input.tablet">

      
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">130</merge>
        <merge key="input.x11_options.miny" type="string">197</merge>
        <merge key="input.x11_options.maxx" type="string">3945</merge>
        <merge key="input.x11_options.maxy" type="string">3894</merge>

      </match>
    </match>
  </device>
</deviceinfo>

</deviceinfo>
```

10-siso.fdi is located at /usr/share/hal/fdi/policy/20thirdparty/10-siso.fdi  and  /etc/hal/fdi/policy/10-siso.fdi

It never has any effect and I have tried many variants.  Any ideas?

---

### Post by Favux on 2009-09-13
Hi bkanuka,

I guess I would try something like:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="HID 1b28:4617">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">130</merge>
        <merge key="input.x11_options.miny" type="string">197</merge>
        <merge key="input.x11_options.maxx" type="string">3945</merge>
        <merge key="input.x11_options.maxy" type="string">3894</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
I think I'd try it in the "/etc/hal/fdi/policy/" location.  This one would execute last.  And the one that executes last "controls".  You probably don't want two .fdi's, unless there's some specific reason.  You could end up with "interference".

A link to the HAL 5.11 spec.:  [http://people.freedesktop.org/~dkukawka/hal-spec-0.5.11/hal-spec.html](http://people.freedesktop.org/~dkukawka/hal-spec-0.5.11/hal-spec.html)

If that works, then the question is does evtouch handle "stylus" so you could add a line like:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
```
below the evtouch line?

---

### Post by bkanuka on 2009-09-13
Hey, that worked!

I don't know exactly where I went wrong, but the .fdi in your post worked. None of the input.x11_options worked as expected but getting the device to use the evtouch driver was the important thing because then I could then use a graphical callibrate tool.

Unfortunatley, the device itself is a peice of crap. Its sensor is a clip at the top of the screen, and if you can imagine, any small movement in the sensor totally messes up calibration. Also it works by highly sensitive ultrasonic sensors (the pen emitts these barely audible clicks), so forget using it when you play music loudly.  And overall, it's just not good enough to make me want to use it.

So thank you very much for your help. I totally got the software side of things working and learned a lot, but the hardware side of things is going back in the box.

---

### Post by Favux on 2009-09-13
Hi bkanuka,

Well outstanding the .fdi worked anyway!  You're welcome.

Sorry about the rest, the demo video I saw looked awfully good.

No way to reproducibly and firmly clip the sensor on the laptop screen?

I gather it uses a doppler effect b/w the U/S and IR.

Any chance you can add a few more details about what you did and what input.x11_options didn't work (driver related?)?  Maybe a lshal with the working .fdi and Xorg.log.  It would help out other Siso Tablo users.  Makes me wonder if a different driver and maybe sampling rate would function better.

---

### Post by LastHylian on 2010-04-30
Hi guys. I'm in the same situation. Got a Siso Tablo, the only problem is I'm not a tech savy as you two. Could you possibly dumb this down a little for me? directions like, download this, then do this would be sufficient enough. I GREATLY appreciate it!

---

### Post by Favux on 2010-04-30
Hi LastHylian,

I can try, but as you read bkanuka didn't give details on some of the things he did.

Need some more information.  What release/version of Ubuntu are you using?

---

### Post by LastHylian on 2010-04-30
Oh you are AWESOME for responding so quickly! I'm running Ubuntu 9.10 x64 with a NVIDIA Ge force 210. This may get quirky as I have a dual monitor setup. My xorg.conf is below. Now, you may notice some unnecessary entries from ATI in there. that is from my previous video card. I've yet to prune it =P

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder58)  Fri Mar 12 02:13:46 PST 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Mar 12 02:12:40 PST 2010

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "off"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "aticonfig-Monitor[0]-0"
    Option         "VendorName" "ATI Proprietary Driver"
    Option         "ModelName" "Generic Autodetecting Monitor"
    Option         "DPMS" "true"
EndSection

Section "Monitor"
    Identifier     "0-CRT1"
    Option         "VendorName" "ATI Proprietary Driver"
    Option         "ModelName" "Generic Autodetecting Monitor"
    Option         "DPMS" "true"
    Option         "PreferredMode" "1680x1050"
    Option         "TargetRefresh" "60"
    Option         "Position" "0 0"
    Option         "Rotate" "normal"
    Option         "Disable" "false"
EndSection

Section "Monitor"
    Identifier     "0-CRT2"
    Option         "VendorName" "ATI Proprietary Driver"
    Option         "ModelName" "Generic Autodetecting Monitor"
    Option         "DPMS" "true"
    Option         "PreferredMode" "1440x900"
    Option         "TargetRefresh" "60"
    Option         "Position" "1680 0"
    Option         "Rotate" "normal"
    Option         "Disable" "false"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w2207"
    HorizSync       24.0 - 83.0
    VertRefresh     48.0 - 76.0
EndSection

Section "Device"
    Identifier     "aticonfig-Device[0]-0"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection

Section "Screen"
    Identifier     "aticonfig-Screen[0]-0"
    Device         "aticonfig-Device[0]-0"
    Monitor        "aticonfig-Monitor[0]-0"
    DefaultDepth    24
    Option         "Monitor-CRT1" "0-CRT1"
    Option         "Monitor-CRT2" "0-CRT2"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Once again, thanks man!

---

### Post by Favux on 2010-04-30
Hi LastHylian,

Alright, you are in Karmic.  Remember this will only work with Jaunty or Karmic because they use HAL/.fdi.  Lucid drops HAL and uses xorg.conf and xorg.conf.d .conf files.  So going to Lucid will break the tablet.

It actually is pretty straight forward.  You want to create a new .fdi file located at "/etc/hal/fdi/policy/".  We'll go with bkanuka's name and call it 10-siso.fdi.  So enter (copy and paste) in a terminal:
```
gksudo gedit /etc/hal/fdi/policy/10-siso.fdi
```
The gksudo is the graphical version of sudo that makes you root/super user and which you use with graphical programs like gedit is the gnome graphical Text Editor.  Copy the entire contents of the .fdi file I posted in post #4.  That's the box that starts with "<?xml version="1.0" encoding="UTF-8"?>".  Then Save and Close gedit and reboot.

We don't need to work with your xorg.conf for this.  Although you are right, and it could use a good clean up.

---

### Post by LastHylian on 2010-04-30
Wow! Thanks man! This is pretty close to perfect. Don't know if it is due to my dual monitors or not,  but the cursor accelerates a little faster than the pen. For example, the cursor will meet the pen at the left, right, and top edges of the screen, but when i have the pen near the middle of the monitor, the cursor is all the way at the bottom edge of the screen. I tried this with one monitor disabled too and the effect is the same. is there a portion of the file where we can specify the desktop resolution to set boundaries or, if the flying spaghetti monster blesses us, is there a program to do it for us?

As always, thanks!

---

### Post by Favux on 2010-05-01
Well bkanuka said:
> getting the device to use the evtouch driver was the important thing because then I could then use a graphical callibrate tool.
So we need to find the tool he used.  Try searching Synaptic Package Manager with calibrate, calibration, touch, etc.  You can also Google.

If we fail to find the tool we can probably configure evdev manually.  The [evdev man]("http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html") tells us how.

---

### Post by flynx on 2010-05-01
I have the same Siso Tablo pen (WOOT!) on an Acer AspireOne with GMA500 graphics running Karmic Koala.

The pen was plug-and-play with the evdev driver, but it is not calibrated.

I found a graphical calibration tool, but it wasn't compatible with my poulsbo graphics.  Don't know if it would have worked anyway.

I have had some success with calibrating using xinput.

use 

```
xinput list
```

 to find the pen.  Probably called "HID 1b28:4617"

use 

```
xinput list-props "HID 1b28:4617"
```

 which outputs

```
Device 'HID 1b28:4617':
	Device Enabled (117):	1
	Evdev Reopen Attempts (252):	10
	Evdev Axis Inversion (253):	0, 0
	Evdev Axis Calibration (254):	
	Evdev Axes Swap (255):	0
	Evdev Middle Button Emulation (256):	2
	Evdev Middle Button Timeout (257):	50
	Evdev Wheel Emulation (258):	0
	Evdev Wheel Emulation Axes (259):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (260):	10
	Evdev Wheel Emulation Timeout (261):	200
	Evdev Wheel Emulation Button (262):	4
	Evdev Drag Lock Buttons (263):	0

```

the fourth line is calibration, but its empty.  
set the calibration by entering

 ```
xinput set-int-prop "HID 1b28:4617" 254 32 0 5000 0 4000
```

Now repeat the list-props command and see the new data for the calibration line.

```
Device 'HID 1b28:4617':
	Device Enabled (117):	1
	Evdev Reopen Attempts (252):	10
	Evdev Axis Inversion (253):	0, 0
	Evdev Axis Calibration (254):	0, 5000, 0, 4000
	Evdev Axes Swap (255):	0
	Evdev Middle Button Emulation (256):	2
	Evdev Middle Button Timeout (257):	50
	Evdev Wheel Emulation (258):	0
	Evdev Wheel Emulation Axes (259):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (260):	10
	Evdev Wheel Emulation Timeout (261):	200
	Evdev Wheel Emulation Button (262):	4
	Evdev Drag Lock Buttons (263):	0
```

The changes happen instantaneously, so you can immediately try the pen.

So now i'm just using trial-and-error to get decent calibration.

---

### Post by Favux on 2010-05-01
Hi flynx,

Welcome to Ubuntu forums!

Wow!  Thanks!  And once you establish the calibration you could add it to the siso.fidi using the 'Option "Calibration" "min-x max-x min-y max-y"' in the evdev manual I linked above.

---

### Post by flynx on 2010-05-01
> **Favux said:**
> Hi flynx,

Welcome to Ubuntu forums!

Wow!  Thanks!  And once you establish the calibration you could add it to the siso.fidi using the 'Option "Calibration" "min-x max-x min-y max-y"' in the evdev manual I linked above.

Hey Favux, thanks for the warm welcome!

I am not using a siso.fdi file.  I tried using yours in /etc/hal/fdi/policy but none of the changes I ever made had any effect with the evdev driver, and the evtouch driver didn't work for me at all.  I also have nothing in xorg.conf.

But you are right, the xinput calibration commands do not persist through a reboot.  So I just made a one-line bash script and added it to my 'startup applications' in preferences.

~/Scripts/calpen.sh

which contains

xinput set-int-prop "HID 1b28:4617" 254 32 900 5550 250 4475

So I guess the next questions are:

(1) what happens to my bash script if I reboot without the pen connected

and (2) is there a way to read the raw data coming from the pen to use that as cal data instead of trial-and-error like I did.  (although trial-and-error wasn't really that hard)

---

### Post by flynx on 2010-05-01
A note about using the device...

The sensor tracks a point on the pen just above the tip, not the tip itself.

Because of this, you get the best accuracy by keeping the pen perpendicular to the screen.

If you tilt the pen at an angle relative to the screen, the cursor will be offset by a few pixels in the direction of the tilt.  While you didn't move the tip of the pen, you did move the sensor.

Also, right-clicking doesn't work out-of-box.  Working on that now.

---

### Post by Favux on 2010-05-01
Looking good!

> (1) what happens to my bash script if I reboot without the pen connected
Hopefully nothing.

> (2) is there a way to read the raw data coming from the pen to use that as cal data instead of trial-and-error like I did.
Probably.  You should be able to use:
```
xidump stylus
```
where stylus stands for whatever device name your pen is being called.  Trace the edge of the screen, ie corners should give coordinates.

You might want to install input-utils and see what 'sudo lsinput' shows you.

You can pull the raw data stream from the kernel if you know the path to it, ie "/dev/?".  You can then use xxd (hidrawX hexdump) with or without switches.  Eg.:
```
sudo xxd -g1 /dev/hidraw0
```
or
```
xxd /dev/ttyS0
```
etc.

---

### Post by flynx on 2010-05-01
I was hoping right-clicking would just be a button mapping problem, but it looks more complicated than that.

There are three buttons on the pen but evdev recognizes all three buttons as button 1.

---

### Post by Favux on 2010-05-01
Hi flynx,

Thinking about it I believe the evtouch driver had a calibration tool or routine.  I can't remember where I saw instructions for it.  Here's a little dated "manual" for it:  [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)

The [evdev manual]("http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html") discusses button mapping.

---

### Post by flynx on 2010-05-01
> **Favux said:**
> The [evdev manual]("http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html") discusses button mapping.

Thanks for the evdev manual.

A button mapping of "3 0 0 0 0" makes all three buttons on the pen act as right-click.  That makes me think that evdev is only seeing a single hardware button.


> **Favux said:**
> You should be able to use:
```
xidump stylus
```

xidump also only saw one button activated by all three physical buttons.  buttons worked with xidump but coordinates did not.

> 

You can pull the raw data stream from the kernel if you know the path to it, ie "/dev/?".  You can then use xxd (hidrawX hexdump) with or without switches.  Eg.:
```
sudo xxd -g1 /dev/hidraw0
```
or
```
xxd /dev/ttyS0
```
etc.

I was able to pull the raw data, now i'm trying to make sense of the hex.

Thanks for the help :)

---

### Post by Favux on 2010-05-01
You're welcome.

If you get a chance a mini write up or HOW TO on how you're setting the siso up in Karmic with evdev would I'm sure be greatly appreciated.

---

### Post by flynx on 2010-05-01
> **Favux said:**
> You're welcome.

If you get a chance a mini write up or HOW TO on how you're setting the siso up in Karmic with evdev would I'm sure be greatly appreciated.

I will admit to having no idea what an fdi is.  As far as I know, I am not using one, unless it was automatically configured for me.

When I plugged it in it just worked, but wasn't calibrated.  So far I've posted all the steps I took to achieve calibration.

Whenever I tried to use /ect/hal/fdi/policy/10-siso.fdi, it just made the pen quit working completely.

---

### Post by LastHylian on 2010-05-01
Hey guys. Tryin flynx's method here and this is what I got. 

xinput list puts out

```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HP HP Wireless Keyboard Kit"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"HP HP Wireless Keyboard Kit"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"EVTouch TouchScreen"	id=7	[XExtensionPointer]
	Type is TOUCHSCREEN
	Num_buttons is 5
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 3120
		Resolution is 1024
	Axis 1 :
		Min_value is 0
		Max_value is 1050
		Resolution is 1024

```

Pretty sure the last entry "EVTouch TouchScreen " is the device :)

So, after I do 

```
xinput list-props EVTouch\ TouchScreen
```
all I get is ...

```
Device 'EVTouch TouchScreen':
	Device Enabled (93):	1

```

Do I need to manually set all of the parameters that flynx is showing?! The resolutions shown in xinput list for Axis 1 is almost correct. My primary monitor is 1680 x 1050, so the horizontal is correct, just not the vertical. Axis 0's resolution of 3120 would be the extended display onto my secondary monitor.

---

### Post by flynx on 2010-05-01
> **LastHylian said:**
> 
Do I need to manually set all of the parameters that flynx is showing?! The resolutions shown in xinput list for Axis 1 is almost correct. My primary monitor is 1680 x 1050, so the horizontal is correct, just not the vertical. Axis 0's resolution of 3120 would be the extended display onto my secondary monitor.

Favux mentioned checking lshal

```

lshal>lshal.txt

```

Then open lshal.txt.  See if you are using the "evdev" driver, around line 10 of that file.  I'm just guessing but maybe you are using a different driver?

bkanuka said he had luck with the evtouch driver but I did not.  I am using evdev, which was the default when I plugged it in.

---

### Post by flynx on 2010-05-01
I guess I should post some words about my trial-and-error method too in case people are confused.

When using this command:

xinput set-int-prop "HID 1b28:4617" 254 32 0 5000 0 4000

the last four numbers in the command are xmin, xmax, ymin, ymax
which essentially correspond to the left, right, top, and bottom edges of the screen in that order.

So just change the xmin number (in this case, the first zero), then check the accuracy of finding the left edge of the screen (there will be a vertical offset).  Increase or decrease the xmin number and repeat until accurate.  Then move on to xmax... and repeat.

---

### Post by flynx on 2010-05-01
> **Favux said:**
> 
The [evdev manual]("http://www.x.org/releases/X11R7.5/doc/man/man4/evdev.4.html") discusses button mapping.

I am trying to get calibration to work without using a script.  I tried putting this in my xorg.conf: 

```
Section "InputDevice"
  Identifier "HID 1b28:4617"
  Driver "evdev"
  Option "Device" "/dev/input/event5"
  Option "Calibration" "900 5550 250 4475"
EndSection
```

But it had no effect.  ideas?

---

### Post by Favux on 2010-05-01
Hi,

> Whenever I tried to use /ect/hal/fdi/policy/10-siso.fdi, it just made the pen quit working completely. 
Sounds like you didn't install evtouch through Synaptic Package Manager or whatever.

You are running on a .fdi.  The evdev .fdi is set up so that evdev picks up any input device nothing else has grabbed.  I forget where it is, somewhere in /usr/share/hal/fdi/policy/.  That's where you want to add the options.

In your xorg.conf attempts are you adding a "ServerLayout" with a line for evdev sending core events?  I need to see your current working xorg.conf to help you.

Remember we are talking two drivers.  Evtouch or evdev.  I think evtouch supports the stylus better, but hey.

You want to use "EVTouch TouchScreen" with the quotes or the id #, so I think it would be:
```
xinput list-props "EVTouch TouchScreen"
```

---

### Post by LastHylian on 2010-05-01
Results of lshal

```
udi = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0'  (string)
  info.product = 'HID 1b28:4617'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_1b28_4617_noserial_if0'  (string)
  input.product = 'HID 1b28:4617'  (string)
  input.x11_driver = 'evtouch'  (string)
  input.x11_options.maxx = '3945'  (string)
  input.x11_options.maxy = '3894'  (string)
  input.x11_options.minx = '130'  (string)
  input.x11_options.miny = '197'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input5/event5'  (string)

```

I noticed the boundaries of Min x Min y Max x and Max y are WAAAY off. So I tried 

```
sudo xinput set-int-prop "EVTouch TouchScreen" 254 32 0 1680 0 1050

```

Logged out, came back, nothing. Disabled secondary monitor, nothing. Did a lshal again and the boundaries did not change. Am i even trying to edit the right thing?

We are getting SOOO close!

---

### Post by flynx on 2010-05-01
Favux:  You were correct.  I did not even have evtouch installed and was using evdev driver.  

LastHylian:  My calibration method only works with the evdev driver.  Once I installed evtouch, I got the exact same result you did.  BUT I was able to transfer my evdev calibration to evtouch using the fdi file Favux recommended:

 /etc/hal/fdi/policy/10-siso.fdi which contains the cal numbers from my earlier method:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="HID 1b28:4617">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.minx" type="string">900</merge>
        <merge key="input.x11_options.miny" type="string">250</merge>
        <merge key="input.x11_options.maxx" type="string">5550</merge>
        <merge key="input.x11_options.maxy" type="string">4475</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

So I can have a calibrated pen with either driver.  Supposedly evtouch supports a graphical calibration tool but my graphics card choked on it.  The only other advantage I see for using evtouch driver is it has support for interpreting a long-click as a right-click.  

However: this requires configuring xorg.conf.  I don't know enough to edit it correctly.  Every time I try, I get low-graphics mode.

These links talks about long-touch and evtouch: 
[http://www.conan.de/touchscreen/libtouch.html](http://www.conan.de/touchscreen/libtouch.html)
[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)

Favux: If I post my xorg.conf here, can you help configure it?

xorg.conf:
```
Section "Device"
        Identifier      "GMA500"
        Driver 		"psb"
	Option		"AccelMethod" "EXA"
        Option 		"DownScale" "false"
        Option 		"ExaNoComposite" "false"
        #Option 	"ExaMem" "131072"
	#Option		"ExaScratch" "4"
	#Option		"ExaCached" "false"
        Option 		"IgnoreACPI" "true"
        Option 		"LidTimer" "false"
        Option 		"NoAccel" "false"
        Option		"NoFitting" "false"
        Option 		"NoPanel" "false"
        Option 		"MigrationHeuristic" "greedy"
        Option 		"ShadowFB" "false"
        Option 		"SWcursor" "false"
        Option 		"Vsync" "false"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
	Option		"RENDER" "Enable"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

Its pretty sparse.  Basically, I need a ServerLayout section that doesn't crash X.

---

### Post by flynx on 2010-05-01
LastHylian:  Since you are already using EVTouch, try opening a console and running ```
calibrate_touchscreen
```.  It may be part of the evtouch package.  This is the calibration tool that I can't use because of my closed-source graphics card.

Also: the tablet calibration numbers have nothing to do with screen resolution.  

Example:  my screen is 1366x768 and my tablet cal is 900 5550 250 4475.

---

### Post by Favux on 2010-05-01
Hi flynx,

I've never seen video sections quite like that.  Was that auto-configured by Xorg or did you do that manually?  I do remember something about the GMA500 being a problem.  Is that an early motherboard integrated video chipset that Intel licensed from someone for it's motherboards?

---

### Post by LastHylian on 2010-05-01
> **flynx said:**
> LastHylian:  Since you are already using EVTouch, try opening a console and running ```
calibrate_touchscreen
```.  It may be part of the evtouch package.  This is the calibration tool that I can't use because of my closed-source graphics card.

Also: the tablet calibration numbers have nothing to do with screen resolution.  

Example:  my screen is 1366x768 and my tablet cal is 900 5550 250 4475.

Ooohhh! That is damn close! That calibration program definitely made changes, but it is kinda weird during the process. First, you have to run the stylus around all the edges of your screen. This is fine. The second step involves tapping some X's, but the X's are not quite in the corners like they should be. I have a widescreen resolution and I have a gap between the right-side X's and the edge of my screen whereas the other X's are at the edges.

The second issue comes with tapping the RED X's. On some of them, i can't tell if the X is red or not. Sometimes I can see one of the X's will have a couple red pixels, but it won't be completely red like some of the others.

Any other way to calibrate or perhaps fix this method?

---

### Post by flynx on 2010-05-01
> **Favux said:**
> Hi flynx,

I've never seen video sections quite like that.  Was that auto-configured by Xorg or did you do that manually?  I do remember something about the GMA500 being a problem.  Is that an early motherboard integrated video chipset that Intel licensed from someone for it's motherboards?

Aparantly it is an Imagination Technologies Series 5 SGX integrated graphics card that Intel licensed for low-power-draw Atom-based machines.  Maybe that's why Intel can't release the source, b/c its from Imagination.

It was a major pain getting the graphics working when I installed Ubuntu on this machine since there isn't really a driver for it.  I had to manually enter that in xorg.conf, mostly just copied from other forums I read.

Even with crummy graphics, this little machine with its dual-core 1.3ghz atom, 2 gigs of ram, 250gig HD, 1366x768 screen, webcam, cardreader, wireless and bluetooth for only $280 is still the most computer for the dollar I've ever gotten :-D

---

### Post by LastHylian on 2010-05-01
Yeah. i love my HP Mini 1000. Got it from a friend for $200 and put Mac OS X 10.5.7 on it with Ubuntu NBR =^_^=

---

### Post by flynx on 2010-05-01
> **LastHylian said:**
> 

Any other way to calibrate or perhaps fix this method?

Even if the red X's aren't in the corner, tap in the corner anyway.  If that still doesn't work, all I can tell you is uninstall evtouch using synaptics package manager or ```
sudo apt-get remove evtouch
```

Then reboot and use my method described earlier with xinput.  Write down the calibration numbers you get.

Then reinstall evtouch. sudo apt-get install evtouch.  Reboot.

Then create the file /etc/hal/fdi/policy/10-siso.fdi I posted earlier but enter your own calibration numbers.  Reboot.  Should work then.

---

### Post by Favux on 2010-05-01
> Aparantly it is an Imagination Technologies Series 5 SGX integrated graphics card that Intel licensed for low-power-draw Atom-based machines. Maybe that's why Intel can't release the source, b/c its from Imagination.

It was a major pain getting the graphics working when I installed Ubuntu on this machine since there isn't really a driver for it. I had to manually enter that in xorg.conf, mostly just copied from other forums I read.
OK, given that we probably don't want 'Identifier	"X.org Configured"' in "ServerLayout".  Instead we'll try the old:
```
	Identifier	"Default Layout"
	Screen		"Default Screen"
```
I'm not real sure about "Default Screen" because you don't have a default screen section.

I commented out some options to "simplify" things.  Actually I doubt the "DeviceName" option is needed at all.

Remember to back up your current working xorg.conf and be prepared to restore it from the command line.

---

### Post by flynx on 2010-05-02
> **Favux said:**
> 
I commented out some options to "simplify" things.  Actually I doubt the "DeviceName" option is needed at all.

Remember to back up your current working xorg.conf and be prepared to restore it from the command line.

TOTAL SUCCESS!!!!  But dang that took a lot of work.

Thanks for all the help Favux!

I was never able to map the buttons on the pen itself, but I successfully mapped long-taps to right-click. Now I have a calibrated pen with right-click-ability.

It's past mid-night and I have a flight in the morning to catch so I should have plently of time sitting in the airport tomorrow to write a full how-to.  Until then, here is a summary of what I did.

1) plug up pen.  let it start with evdev driver.
2) calibrate pen with xinput as described earlier.
3) install evtouch driver
4) add /etc/hal/fdi/policy/10-siso.fdi as posted earlier with calibration numbers found with xinput.
5) modify xorg.conf for right-click on long-tap. 

the successful xorg.conf is the only thing not yet posted.  here it is:

xorg.conf:
```
Section "InputDevice"
    Identifier "Siso Tablo"
    Driver "evtouch"
    Option "Device" "/dev/input/event5"
    Option "SendCoreEvents" "On"
    Option "ReportingMode" "Raw"
    Option "MinX" "900"
    Option "MinY" "250"
    Option "MaxX" "5550"
    Option "MaxY" "4475"
    Option "longtouched_action" "down"
    Option "longtouched_button" "3"
EndSection


Section "Device"
        Identifier      "GMA500"
        Driver 		"psb"
	Option		"AccelMethod" "EXA"
        Option 		"DownScale" "false"
        Option 		"ExaNoComposite" "false"
        #Option 	"ExaMem" "131072"
	#Option		"ExaScratch" "4"
	#Option		"ExaCached" "false"
        Option 		"IgnoreACPI" "true"
        Option 		"LidTimer" "false"
        Option 		"NoAccel" "false"
        Option		"NoFitting" "false"
        Option 		"NoPanel" "false"
        Option 		"MigrationHeuristic" "greedy"
        Option 		"ShadowFB" "false"
        Option 		"SWcursor" "false"
        Option 		"Vsync" "false"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
	Option		"RENDER" "Enable"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Screen"
Identifier "screen1"
Device "GMA500"
Monitor "monitor1"
DefaultColorDepth 24
     Subsection "Display"
	Depth 24
	Modes "1366x768" "800x600"
     EndSubsection
     Subsection "Display"
	Depth 32
	Modes "1366x768" "800x600"
     EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen1"
	InputDevice	"Siso Tablo" "CorePointer"
EndSection


```

The documentation for long-taps is jacked up.  The name of the option is documented as "longtouch_action" but its actually "longtouched_action".  Also, the number 3 has to be in quotes.

:guitar:

---

### Post by flynx on 2010-05-02
Two more things

If your like me, the first time you looked at the ball-point ink tips, the first thing you thought was "by the time I need refills, this company won't exist."

I was hoping drafting leads would fit perfectly in this thing.  They don't, but its pretty dang close.  Break off a piece of a drafting lead of the same length and you can use it in this pen - making it a digital pencil.

Also, for those who get it working, here is a neat website with lots of tablet linux apps like gesture recognition and handwriting recognition:

[http://tuxmobil.org/tablet_unix.html](http://tuxmobil.org/tablet_unix.html)  (scroll to bottom)

---

### Post by Favux on 2010-05-02
Hi flynx,

Absolutely awesome!  Nice work.  :)

Thanks for posting a description of the steps.  What I find interesting is you're using both a .fdi and xorg.conf and it's working.  I forgot to mention it usually works better if you use one or the other.  But maybe not with the Siso.  You could try renaming the siso.fdi to siso.bak or something and see how it works.

---

### Post by flynx on 2010-05-02
> **Favux said:**
> Hi flynx,

Absolutely awesome!  Nice work.  :)

Thanks for posting a description of the steps.  What I find interesting is you're using both a .fdi and xorg.conf and it's working.  I forgot to mention it usually works better if you use one or the other.  But maybe not with the Siso.  You could try renaming the siso.fdi to siso.bak or something and see how it works.

Yes, your right.  Now that all the cal numbers are in xorg.conf, the siso.fdi is not required.

Always nice to have someone smarter than you look over your shoulder :)

I also commented out the last two lines of the device section for the tablo.  Turns out, you don't need long-taps mapped to right-click because tap-tap-hold is default mapped to right-click.

---

### Post by LastHylian on 2010-05-02
Since you are able to use xorg, does this mean it could possibly work in 10.4 now? You said earlier Lynx does away with the HAL, right?

---

### Post by flynx on 2010-05-02
> **LastHylian said:**
> Since you are able to use xorg, does this mean it could possibly work in 10.4 now? You said earlier Lynx does away with the HAL, right?

Sounds like it would work to me.  All you need is evtouch and xorg.conf.

Unfortunately this isn't perfect yet.  If I reboot my computer with the pen unplugged, my touchpad comes up in absolute mode, instead of relative like it should be.  Maybe evtouch is grabbing my touchpad.  At any rate, it makes the touchpad unusable.  Work-around is boot with the pen connected, then unplug it.

---

### Post by Favux on 2010-05-02
Hi LastHylian,

That's right.  The .fdi files have been replaced by .conf files in xorg.conf.d.  But you can still use xorg.conf like always.

Edit:  Oops, forgot half the post!
> If I reboot my computer with the pen unplugged, my touchpad comes up in absolute mode, instead of relative like it should be. Maybe evtouch is grabbing my touchpad. At any rate, it makes the touchpad unusable. Work-around is boot with the pen connected, then unplug it.
Not sure I completely follow that.  But I do have a question whether hot plugging is enabled through xorg.conf now.  Or since .fdi files were introduced to get us hot plugging are the .conf files the equivalent and the only way in Lucid to get hot plugging?  If so then we've got to figure out how to configure the siso through a .conf file.  Maybe there's someway to get coordinates working.  So we may need to look at your udevadm info.:
```
udevadm info --export-db > $HOME/udev.txt
```

---

### Post by flynx on 2010-05-07
> **Favux said:**
>   But I do have a question whether hot plugging is enabled through xorg.conf now.  Or since .fdi files were introduced to get us hot plugging are the .conf files the equivalent and the only way in Lucid to get hot plugging?  If so then we've got to figure out how to configure the siso through a .conf file.  Maybe there's someway to get coordinates working.  So we may need to look at your udevadm info.:
```
udevadm info --export-db > $HOME/udev.txt
```

Relative vs absolute - hard to explain over text. A touchpad has similar output coordinates as a touchscreen, but they are used differently.  A touchscreen maps each specific touch coordinate to a point on the screen.  The only way to click that button is to touch that coordinate.

When you tap a touchpad, it clicks where ever the mouse cursor happens to be, rather than a specific point on the screen.

A touchpad in absolute mode would only click the bottom-left start button if you tapped in the very bottom-left corner of the touchpad.  Additionally, the mouse cursor jumps to a corner whenever I lift my finger from the touchpad because the touchpad is outputting data continuously unlike a touchscreen.

Anyway - no - hotplugging with xorg.conf does not work.  I have to reboot to swap USB devices.

You asked for udev.txt - see attached. This was run with the siso connected and operational.

I think I can configure the siso to use either xorg.conf or fdi successfully.  I just didn't see an advantage to one over the other, so I used xorg since i'm more familiar with it.  When I get some time I'll try going back to the fdi and see if I can get hotplugging to work.

---

### Post by Favux on 2010-05-07
Hi flynx,

Thank you for the udevadm info.!  Since you are in Karmic this doesn't apply to you, but I think it will apply to Lucid.  Here's a first pass at a 90-Siso-tablo.conf for /usr/lib/X11/xorg.conf.d/ in Lucid:
```
Section "InputClass"
#    Identifier "???"
    MatchProduct "1b28"
    MatchDevicePath "/dev/input/event*"
    Driver "evtouch"
    Option "MinX" "900"
    Option "MinY" "250"
    Option "MaxX" "5550"
    Option "MaxY" "4475"
EndSection
```
I'm not sure what to put in identifier.  Say "Siso-Tablo Class"?

By the way is flynx from the Flynx series?

---

### Post by flynx on 2010-05-13
Got really bored reviewing manuals at work today, so I came back to this project.

First a reminder of where I left off.  I was using xorg.conf because I couldn't get the fdi to work.  xorg worked, but did not support hot swapping of USB.  So the pen had to be connected during boot or bad things happened.

Today I got the fdi to work.  I still have to determine my calibration numbers using evdev, but you can use the same numbers with evtouch.  I cleared out xorg.conf and use only the fdi.

The key was using the raw reporting mode.  None of the calibration numbers did anything until I added that line to fdi.

Here is the 10-siso.fdi in /etc/hal/fdi/policy:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.tablet">
      <match key="info.product" contains="1b28">
        <merge key="input.x11_driver" type="string">evtouch</merge>
	<merge key="input.x11_options.reportingmode" type="string">raw</merge>
        <merge key="input.x11_options.minx" type="string">900</merge>
        <merge key="input.x11_options.miny" type="string">250</merge>
        <merge key="input.x11_options.maxx" type="string">5550</merge>
        <merge key="input.x11_options.maxy" type="string">4475</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

Now I can hot-swap all day long, and the pen doesn't need to be connected at boot.  Both touchpad and pen are working and calibrated.


And no... Flynx did not come from the television series.  I used to fly blimps over sporting events, mostly for a team called the Lynx.  Flying-Lynx collapsed over the years to Flynx.

---

### Post by flynx on 2010-05-14
the following lines added to the fdi control click behavior.  with these settings, a single tap is a left-click, tap-and-hold is left-click-hold to enable dragging, and tap-tap-hold is mapped to right-click

```
	<merge key="input.x11_options.maybetapped_action" type="string"> click </merge>
	<merge key="input.x11_options.maybetapped_button" type="string"> 1 </merge>
	<merge key="input.x11_options.longtouched_action" type="string"> down </merge>
	<merge key="input.x11_options.longtouched_button" type="string"> 1 </merge>
	<merge key="input.x11_options.oneandahalftap_action" type="string"> click </merge>
	<merge key="input.x11_options.oneandahalftap_button" type="string"> 3 </merge>	
```

if you decide to mount the sensor on the left or right side of the screen, you can add a line like this:

```
<merge key="input.x11_options.rotate" type="string">CW</merge>
```

CW for clockwise or use CCW for counter-clockwise.  

that's about it for me, i've got this thing working exactly like i want it to, so i probably won't be monitoring this thread anymore.  but i learned a lot.  if everything in this thread doesn't get you there, PM me.

---

### Post by flynx on 2011-05-05
I got some PMs for help so I put together this list of steps to detail what I did to get my pen working in Karmic:


Step 1)  Plug up the pen.  It should start working.  It won't be calibrated.

Step 2)  We need to find our calibration numbers.  Open a terminal and type ```
xinput list
```.  You should find a touch device in the list.  If your not sure which one it is, un-plug the pen and run "xinput list" again.  Whichever one is missing was the pen.  My pen was the device called "HID 1b28:4617"


Step 3)  Run  
 ```
xinput list-props "HID 1b28:4617" 
```    Replace the part in quotes with whatever your pen was called from step 2.  Line 4 or 5 should say calibration and will probably be empty.

Step 4)  Run this command to enter some calibration numbers:  ```
xinput set-int-prop "HID 1b28:4617" 254 32 0 5000 0 4000
```          The last four numbers in that command are the left, right, top, and bottom calibration numbers.

Step 5)  Re-run the command from step 3 to verify the 4th or 5th line about calibration now has numbers in it.

Step 6)  Place the pen on the left-edge of the screen and slowly drag it to the right.  The cursor should probably lag behind the pen.  (It will be above or below the pen, we don't care about that now)  Re-run the command from step 4 to increase the xmin like this:  ```
xinput set-int-prop "HID 1b28:4617" 254 32 100 5000 0 4000
```  Repeat this step until the cursor follows the left-right motion of the pen at the left side of the screen accurately.  If the mouse cursor is to the left of the pen, increase the number.  If the cursor is to the right of the pen, decrease the number.

Step 7)  Repeat step 6 at the right, top, and bottom edges of the screen while only changing one number at a time.  Do this until the pen is calibrated to your satisfaction.

Step 8:  Install the evtouch driver.  (can't find package name right now.  run sudo apt-get install <package name>)

Step 9)  Make a new file in /etc/hal/fdi/policy called 10-siso.fdi.  That file should contain:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.tablet">
      <match key="info.product" contains="1b28">
        <merge key="input.x11_driver" type="string">evtouch</merge>
    <merge key="input.x11_options.reportingmode" type="string">raw</merge>
        <merge key="input.x11_options.minx" type="string">900</merge>
        <merge key="input.x11_options.miny" type="string">250</merge>
        <merge key="input.x11_options.maxx" type="string">5550</merge>
        <merge key="input.x11_options.maxy" type="string">4475</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

The last long lines in that file configure the calibration numbers (in this case, 900, 250, 5550, and 4475).  You should replace those numbers with the calibration numbers you found earlier.

Step 10 (optional):  there are a few options to control click behavior in the FDI file.  If you want, you can add these lines to the file from step 9:

```
<merge key="input.x11_options.maybetapped_action" type="string"> click </merge>
    <merge key="input.x11_options.maybetapped_button" type="string"> 1 </merge>
    <merge key="input.x11_options.longtouched_action" type="string"> down </merge>
    <merge key="input.x11_options.longtouched_button" type="string"> 1 </merge>
    <merge key="input.x11_options.oneandahalftap_action" type="string"> click </merge>
    <merge key="input.x11_options.oneandahalftap_button" type="string"> 3 </merge>
```a single tap is a left-click, tap-and-hold is left-click-hold to enable dragging, and tap-tap-hold is mapped to right-click

Step 11 (optional):  If you mount the sensor on the left or right side of the screen instead of the top, add this line to the FDI file from step 9:

```
<merge key="input.x11_options.rotate" type="string">CW</merge>
```CW for clockwise or use CCW for counter-clockwise. 


Thats it.  This worked for me in Karmic 32-bit.  I am now running Natty 64-bit.  I haven't installed this device in Natty yet.  Maybe out of curiosity I will try this same process there and see how it works.  

I was never able to make the side-buttons on the pen do anything but left-click.

---

### Post by flynx on 2011-06-11
Update!  I tried setting up my Siso Tablo in Natty.  One important thing to note is that in step 6, the number 254 is the number that identifies the calibration property.  This number may be different (and what's worse, it might change) but using xinput to list the properties will give you the number in parenthesis.

I was able to get the pen calibrated in Natty, but I don't know enough about Natty to have the calibration automatically apply at boot.  So I have a script again to set the calibration after attaching the pen on usb.  If anyone knows how to configure the calibration to be correct after reboot, let me know!

---

