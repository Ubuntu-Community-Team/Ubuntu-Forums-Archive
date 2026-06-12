---
title: "Tablet PC eraser and Screen rotation on Jaunty"
date: 2009-04-25
forum: Hardware
---

### Post by joehardflec on 2009-04-25
Hello,
I have a Fujitsu Siemens T4220 tablet PC, which I had configured as per the guide at [https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220) under Hardy and Intrepid.

Upon upgrading to Jaunty, the tablet eraser no longer works in Xournal or the GIMP. It just acts as the normal pen rather than working as a separate tool.

Also, the screen rotation script from that page no longer rotates the pen input, it just rotates the screen.

I suspect this is due to the changes the Jaunty update made to xorg.conf;
all of the previous lines I added have been commented out. However, when I tried removing the commenting, X would not start correctly, hanging on a black screen with a corrupted circle timer cursor in the center.


How can I get back to the previous tablet functionality I had under Intrepid?

Thanks
Joel

---

### Post by aussiedwarf on 2009-04-25
I have a similar situation. I'm using a Fujitsu t4010 tablet(so slightly different). I installed Jaunty from scratch on a partition I left spare. I tried the stylus working by installing wacom tools, set serial and adding the right lines to xorg.conf. This crashed the computer on restart in the same manner as you described above. Black screen, corrupted circle timer in the center and some weird green fuzzy lines all around.

I'm currently mucking around with it to see what is causing this.

here is my xorg.conf from jaunty when it works.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Section "Module"
	Load		"wacom"
EndSection
```

here is my xorg from intrepid which works (90% of the time anyway), but causes jaunty to crash

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Section "Module"
	Load		"wacom"
EndSection

# These lines should go after the detected mouse and touchpad
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
	Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
	Option		"button2"	"3"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
	Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
	Option		"Button1"	"2"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"cursor"		"SendCoreEvents"
	InputDevice	"stylus"		"SendCoreEvents"
	InputDevice	"eraser"		"SendCoreEvents"
EndSection
```

I haven't tried screen rotation or buttons yet.

---

### Post by SINternet on 2009-04-25
Same issue here as original Post. I have a Panasonic Toughbook CF-19. I think its great that Ubuntu start using HAL but my guess is this is a work in progress. As it stands now we have no way of calibrating the Pen or adjusting the buttons. I would recommend a Utility not unlike the Windows Intel Display utility that handles screen rotation, add in a Cal of Stylus, and Stylus Button options. My guess in Screen Rotation is restarting the Mouse when in portait would be a workaround and yes is an additional step. Everything else works.

SIN

---

### Post by Favux on 2009-04-25
Hi aussiedwarf and everyone,

We, I mean rec, found the problem out a while ago.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)  There are two scripts by rec there.  The first shows the problem and the second fixes it.  He posted it to Timo Aaltonen's launchpad feedback site here:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340) (near the bottom).  If you go here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And look at Jaunty users near the top it explains the problem.  The link takes you to gali98's HOW TO on post 104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Since it looks like all of you have serial tablets I doubt you need to do the part about compiling the 0.8.3-2 wacom.ko kernel driver.  You could probably just implement the script if you want to experiment.  It should get xsetwacom working again and thus wacomcpl

It's possible Timo already patched xorg-xserver to fix things, at least if that's what the changelog here means:  [https://launchpad.net/~tjaalton/+archive/ppa](https://launchpad.net/~tjaalton/+archive/ppa)  Of course no telling when and if this update will come through.

I hope this is helpful.

Oh to add eraser and button2 3 (eraser in Xournal) to the .fdi do:
```
	  <merge key="input.x11_driver" type="string">wacom</merge>
	  <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
        <merge key="input.x11_options.Button2" type="string">3</merge>
```
Except they are all suppose to be lined up.

---

### Post by joehardflec on 2009-04-28
> **Favux said:**
> 
I hope this is helpful.


Indeed, thanks. Although that's a hell of a lot of reading to go through.

I think what it boils down to is:
use xinput to find the true names of your stylus, then
xsetwacom set "PnP Device (yourdevicename)" rotate cw

That works for me, at least. Now I've got to figure out how to script it properly to rotate both together in progressive steps of 90deg, like the old script.

> **Favux said:**
> 
Oh to add eraser and button2 3 (eraser in Xournal) to the .fdi do:
```
	  <merge key="input.x11_driver" type="string">wacom</merge>
	  <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
        <merge key="input.x11_options.Button2" type="string">3</merge>
```
Except they are all suppose to be lined up.

So, where do I put this?
Is it into /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi ?
And if so, where in that file should it go?

---

### Post by Favux on 2009-04-28
Hi joehardflec,

You are right, sorry about the info dump.  I just didn't want to point you to rec's script without some background.

That's why rec's script is so convienent.  You don't have to go around renaming things.  Then when they fix things and wacom stops working all you should need to do is remove rec's script.

Since you have a Fujitsu Siemens T4220 tablet PC, I'm assuming it is a serial Wacom tablet pc, correct?  If you don't want to put in a custom .fdi then it would go in this part of Timo's 10-wacom.fdi:
```
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
```
Just remember to change to the appropriate names.

---

### Post by victorhooi on 2009-04-30
heya,

I'm using a Fujitsu T4215 (similar model) on the release version of Kubuntu 9.04.

The stylus didn't work at first - I could have sworn it did work for a little bit, just randomly before, until my system seemed to lock-up (Kubuntu seems strangely buggy on me, no idea why...although it always has seemed a bit funny...*sigh*).

Should the stylus at least work right out of the box, or is there something I can check? (I was using the 9.04 alpha before, followed those steps in post 104, seemed to work for a while, then broke...).

My xorg.conf is empty, except for a section enabling UXA (yeah, buggy, I know).

Checking my Xorg.0.log, I have:

```
(II) intel(0): Setting screen physical size to 270 x 203
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) (PnP Device (FUJ02e5)) is not a pad
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser (PnP Device (FUJ02e5) eraser) is not a pad
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device Fujitsu FUJ02B1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event6"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02B1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02B1: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02B1: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard

```

Does that seem like it should work?

Cheers,
Victor

---

### Post by Favux on 2009-04-30
Hi victorhooi,

Do you know if the Fujitsu T4215 and similar models use a Wacom digitizer?  I know some need the f-pit driver.  In the subsection of the 10-wacom.fdi is this line:
```
 <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">

```
It ends with "FUJ02e5" which is apparently how HAL identifies your tablet.  It is failing twice with:
```
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

```
So the Wacom module fails and then evdev apparently goes on to grab your keyboard as Fujitsu FUJ02B1.

So it may be a problem with linuxwacom or maybe with the .fdi.  Maybe if we simplify the .fdi?  What does your tablet have?  No touch?  A stylus.  Does it have an eraser?  Does it have buttons?  How many?

---

### Post by victorhooi on 2009-04-30
heya,

Favux: Thanks for the awesomely quick reply.

Yeah, I'm pretty sure it's a Wacom digitiser.

The tablet is a Fujitsu T4215, it doesn't have touch, only an active digitiser, it has an eraser button on the back, and two button near the front (used as right-click and an eraser under Windows).

Any commands you want me to paste the output from?

Cheers,
Victor

---

### Post by Favux on 2009-04-30
Hi victorhooi,

Why don't we start off with going into Synaptics and telling it to reinstall the 0.8.2-2 linuxwacom.  The xserver-xorg-input-wacom and wacom tools.  See if that does anything.

---

### Post by aussiedwarf on 2009-05-02
Hi,right, been a while since I tried doing this. I havent got any stylus input (though i did briefly when i was using the xorg just no erasor).

I seem to be getting a similar problem to victorhooi. My Xorg.0.log is a little different though but still contains "usbDetect: can not ioctl version".

This seems strange as my tablet like victorhooi is serialand it says "usbDetect".

```

(II) intel(0): Setting screen physical size to 270 x 203
(II) config/hal: Adding input device fsc tablet switch
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) fsc tablet switch: always reports core events
(**) fsc tablet switch: Device: "/dev/input/event6"
(WW) fsc tablet switch: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "fsc tablet switch"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) (PnP Device (FUJ02e5)) is not a pad 
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) WACOM: PressCurve 50,0,100,50
(**) Option "KeepShape" "on"
(**) PnP Device (FUJ02e5): keeps shape
(**) Option "Threshold" "1"
(**) PnP Device (FUJ02e5): threshold = 1
(**) Option "TPCButton" "on"
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser (PnP Device (FUJ02e5) eraser) is not a pad 
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) WACOM: PressCurve 50,0,100,50
(**) Option "KeepShape" "on"
(**) PnP Device (FUJ02e5) eraser: keeps shape
(**) Option "Threshold" "1"
(**) PnP Device (FUJ02e5) eraser: threshold = 1
(**) Option "TPCButton" "on"
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom General ISDV4 tablet speed=9600 (19200) maxX=-256 maxY=24576 maxZ=36 resX=2540 resY=2540  tilt=enabled
(==) Wacom device "PnP Device (FUJ02e5) eraser" top X=0 top Y=0 bottom X=-256 bottom Y=-192 resol X=2540 resol Y=2540
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
xf86WcmSerialValidate: bad magic at 2 v=c0 l=9
(II) config/hal: Adding input device fsc tablet buttons
(**) fsc tablet buttons: always reports core events
(**) fsc tablet buttons: Device: "/dev/input/event5"
(II) fsc tablet buttons: Found keys
(II) fsc tablet buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "fsc tablet buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) fsc tablet buttons: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) fsc tablet buttons: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) fsc tablet buttons: xkb_layout: "us"
(II) config/hal: Adding input device Fujitsu FUJ02B1
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event7"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02B1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02B1: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02B1: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus

```

Wheni used rec's script i got this message afer using sudo update-rc.d wacomtohal defaults 27
```

update-rc.d: warning: /etc/init.d/wacomtohal missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

```

I tried a complete wipe of xserver-xorg-input-wacom and wacom tools but no success.

On another note i have installed fjbtndrv and have automatic rotation and working buttons :D

---

### Post by Favux on 2009-05-02
Hi aussiedwarf,

Another problem.  From man update-rc.d:
> If defaults is used then update-rc.d will make links to start the  ser&#8208;
       vice  in runlevels 2345 and to stop the service in runlevels 016 unless
       an  LSB-style  header  is  present  in  the  init.d  script   and   the
       /etc/update-rc.d-lsbparse file exist.  If such header exist, the levels
       listed in the Default-Start and Default-Stop fields in that header  are
       used  instead.
Why LSB is entering the picture I don't know.  You can also use:
```
sudo update-rc.d wacom-names start 27 2 3 4 5 .
```
Rec also had a serial tablet, a Thinkpad X61t.

I don't know why you are getting the usb etc. error.  I guess you could:
```
lshal>lshal.txt
```
and use gedit to search for sections containing "FUJ02e5" or "FUJ" and see if the identifier is actually the correct one for your tablet.  Or maybe install gnome-device-manager, which is the gui frontend for HAL.  Be sure to check properties in view.

Do you remember what the line you used in serial.conf in the long, long, ago looked like?  Maybe compare that to the log output and see if there's a difference.  Maybe in baudrate or something.

But since the error always starts with "usbDetect: can not ioctl version" I tend to doubt that's the problem.  As you see in gali98's HOW TO we had to swap the wacom.ko with the 0.8.3-2 wacom.ko to get usb working for us.  The kernel driver wacom.ko is for usb.  Why that would matter to you, and how it could possible affect you is beyond me.  But then why does a serial Wacom digitizer identify itself with FUJ instead of WAC.  Did Fujitsu mess with the digitizer somehow?

Frankly I suspect some sort of problem with the patched linuxwacom.  Another bug report:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643)

And at the risk of heresy.  If you don't care about hotplugging it looks like you can compile linuxwacom 0.3.8-2 and use xorg.conf as before and pretend none of this is happening.

---

### Post by Favux on 2009-05-02
Hi everyone,

I should complete what I was saying to victorhooi.  Let's try simplifying the .fdi to just stuff you have in case your digitizer is barfing on some of the extra stuff, ie touch.  So take the serial subsection:
```
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
```
to
```
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
      </match>
    </match>
```

---

### Post by aussiedwarf on 2009-05-03
Thanks Favux.

I don't mind heresy so I had a go at installing the linux wacom 0.8.3-3 using your instructions. No sucsess so far. It appears that it installs. When I modinfo -d wacom I get
"USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver"

After setting up the xorg, no response from the stylus.

back in intrepid all I ever did with set serial was install it.

Maybe its also worth trying from a clean install.For all I know, fjbtndrv could be interfering.

---

### Post by Favux on 2009-05-03
Hi aussiedwarf,

Which line are you using in xorg.conf for the stylus?  Are you using the ttyS0 line or "/dev/input/wacom" line?  If the latter your wacom symlinks may not be in place.  Check to see if you have &#8220;50-xserver-xorg-input-wacom.rules&#8221; in &#8220;/etc/udev/rules.d/&#8221;.  If not use Appendix 3 on the compiling HOW TO to put it in.

---

### Post by aussiedwarf on 2009-05-03
Im using ttys0 in my xorg. I will have a go at using "/dev/input/wacom" when i get some free time and a stable internet connection.

---

### Post by victorhooi on 2009-05-04
heya,

I had a go reinstalling xserver-xorg-wacom-input and wacom-tools, and did a reinstall.

Still no luck.

However, I noticed that if I suspended the laptop (in my case, closing the lid does that), when I resumed, the Wacom stylus would work. Very weird. A restart after that seemed to break it.

I've attached my Xorg.0.log as well as the syslog and dmesg from after that unsuspend, where it worked. I think you might be right about the ioctl version error being a red herring, because that line is still there, while it worked.

I just tried doing it again, but the laptop seemed to hang at a black screen while attempting to resume (black screen for a long time, no disk access light, caps lock didn't work).

There's all sorts of weirdness like that sometimes on this laptop/Kubuntu...*sigh*....sometimes when I attempt to restart/resume, it stays on, and goes to a black screen, and the cd-rom access light blinks a steady pattern, and nothing else happens, no disc access. Not really sure how I could file a bug-report in that case, since I don't know how to grab log files or anything else that could be useful in that state.

Anyway, back to this problem, I just did a update/dist-upgrade, and it pulled in a new udev package. The stylus **is** working now, I'll do a few restarts/suspends, and see if it stays.

Cheers,
Victor

---

### Post by victorhooi on 2009-05-07
heya,

I was incorrect, it still doesn't work on startup.

When I shut the lid, it goes into suspend. However, if I wait for a period of time, when I resume, instead of going to the unlock screen, it brings me to the main login screen, and it appears as if the laptop has restarted during suspend (e.g. Konquerer closed uncleanly, files not saved etc.)

This in itself is another weird (I assume) bug...as far as I can see, there isn't a setting to restart the computer when it's in suspend after a specific time.

However, when it hasn't restarted, the stylus doesn't work. When it has restarted (which is itself bad, and annoying), it works.

All very weird. Are there any log files or diagnostics I could provide that would help clear thsi up?

Cheers,
Victor

---

### Post by Favux on 2009-05-08
Hi victorhooi,

Ha, I hoped it was working.  Darn.  I'll look at your outputs.

To summarize you have a Fujitsu T4215 with a serial Wacom digitizer that is identified in the .fdi with "FUJ02e5".  It has a stylus, 2 stylus buttons, and an eraser.  You are using the Jaunty default 0.8.2-2 linuxwacom packages.  Have you made any wacom modifications?

What is the video chipset in your laptop?  In KDE I'm not sure what the equivalent of asking are you using Compiz is.  It is Kwin, correct?  Is it compositing, or advanced compositing?  Whatever it is are you using it?

One thing, to be sure I have the story.  The stylus doesn't work when you first start up.  It works after the restart being caused by suspend.  So it doesn't work with restarting X or just restarting?

Why don't we also look at lshal so we can find your tablet section(s).  In a terminal:
```
lshal>lshal.txt
```
and then attach lshal.txt to your next post.

---

### Post by aussiedwarf on 2009-05-11
Right, well I decided to start out all new since I found some free time. I reinstalled jaunty and tried going through hal. That didnt work so I compiled linuxwacom 0.8.3-4. I restarted and I had Success! All seemed to work. I had stylus, eraser and right click. The only fault is i briefly had a fuzzy screen with a corrupted pointer just before logging in.

I then tried installing fjbtndrv from [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa). I restarted and it seemed to crach X. I got a fuzzy screen with a corrupted pointer. I then went into the the live cd. This is where I got a huge shock as the stylus worked, from the live cd! Albeit with no right click or eraser. Why would it work there but not from a fresh install?

fjbtndrv does not work properly with rotate either. The screen when in portrait form is all squashed together. I just tried completely removing fjbtndrv and restarting but it still seems to kill ubuntu.

Now, I go into the live cd and guess what, the stylus is Not picked up. ???????

---

### Post by Favux on 2009-05-11
Hi aussiedwarf,

What's your video chipset?  Jaunty has trouble with Intel and some ATI's.

---

### Post by aussiedwarf on 2009-05-11
Wow, Favux, that was fast. I was not expecting a reply so quickly. Totally awesome.

My video set is intel 82852/855GM integrated (according to lspci | grep VGA)

Getting into jaunty and looking in synaptic I can see that wacom-tools and xserver-xorg-input-wacom version 0.8.2.2 have been reinstalled. I am guessing that fjbtndrv did this.

also last couple of time i have been in the live cd when the pen did not work, the shutting down screen is corrupted. Each line has been segmented and pushed over as if its trying to place the picture on a wider or thinner screen.

---

### Post by Favux on 2009-05-11
Hi aussiedwarf,

OK I know that was a lot of stuff on Intel motherboard chipsets in the Jaunty forum.  And I'm sure a lot more since.  So you could research that.  There is also a wiki on how to revert with some more info:  [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

And Ubuntu's aware of the problem so they set up a Xorg video driver ppa to speed up availability of fixes:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Can you see a way to get the fjbtndrv functionality without installing it?

---

### Post by black_shadow on 2009-05-11
Hi 

Have a look here for what I had to do to get full stylus and screen rotation to work.

Mike

---

### Post by aussiedwarf on 2009-05-11
its strange as before i reinstalled jaunty rotation worked 100%. Without fjbtndrv I know rotation can be done though I'm not sure if it will be automatic. I dont know of any way to get the buttons to work though without it. I think I will have to stick to Intrepid till things are fixed as that seems to work all fine (well, apart from a few snagging errors). Shame as I was really enjoying the fast start ups.

Thanks for the help

---

### Post by victorhooi on 2009-05-12
heya,

I've attached the output from lshal.

According to lspci | grep VGA, my graphics card is

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Compositing is turned on, from what I gather. Hope that helps.

Cheers,
Victor

---

### Post by Favux on 2009-05-13
Hi victorhooi,

The Xorg.O.log shows that linuxwacom is now working, but your stylus is called "PnP Device (FUJ02e5)" and your eraser "PnP Device (FUJ02e5) eraser".  So adding rec's script should allow you to run wacomcpl and calibrate and also get rotation working.  Or you could rename everything.  You should see the above HAL names if you type  "xinput --list" in a terminal.

I culled out the Wacom sections from lshal and made a first pass at a serial wacom.fdi.  You'll know it's working when "xsetwacom list" returns stylus and eraser.  I left touch out of it to simplify things.  If you want to try it copy your current 10-wacom.fdi somewhere safe and rename it (say .bak instead of .fdi).  Then replace it with the attached 10-wacom.fdi.  After making sure to change its name to 10-wacom.fdi of course.

Cyberfish wrote a script to keep our .xinitrc settings (the file wacomcpl makes) after a suspend.

For now I would turn off all video effects until you have things working.  I noticed upstream of the 10-wacom.fdi there is a Fujitsu.fdi that has "video tweaks" for various models, including the T4200 if I remember correctly.  So maybe that is something else to look at.  Beside any Intel driver issues I mean.

---

### Post by victorhooi on 2009-05-20
heya,

Favux: I tried replacing my 10-wacom.fdi file with the file you attached (backing up the original, of course), but no luck. No response to stylus or eraser on reboot, and also, my keyboard appears to not work (trackpad still works).

I was going to try to login, and get some log output I could give you, but unfortunately, didn't know a way to login without a keyboard (mouse, yes, no keyboard, no...lol).

Any other suggestions? *looks hopeful*

Cheers,
Victor

---

### Post by Favux on 2009-05-20
Hi victorhooi,

Thank you very much for trying it.  Well back to the drawing board on the .fdi.  I don't understand why it took out your keyboard.  I guess we could try xorg.conf or rec's script or renaming things.  Do you care about hotplugging?

Hi aussiedwarf,

rarara77 says he got the fjbtndrv drivers working on post #16 here:  [http://ubuntuforums.org/showthread.php?p=7318554#post7318554](http://ubuntuforums.org/showthread.php?p=7318554#post7318554)

---

### Post by victorhooi on 2009-05-30
heya,

Favux: Do you mean hotplugging in Xorg in general, or just for the tablet stuff? Hotplugging would be nice, but I am willing to forgo it, if that's what it'll take to get the tablet pen working.

I thought the renaming was to get it to work with wacomcpl/utilities? Or does that affect whether X detects it as well?

Which approach would you recommend I try next? (Xorg.cof/renaming/rec's script - speaking of which, I've seen references to this, and multiples versions of this - is this the best version? [http://ubuntuforums.org/showpost.php?p=7068115&postcount=93](http://ubuntuforums.org/showpost.php?p=7068115&postcount=93))

Cheers,
Victor

---

### Post by Favux on 2009-05-30
Hi victorhooi,

I'm going to assume you have the 0.8.2-2 linuxwacom packages that came with Jaunty and have reinstalled the "default" Jaunty wacom.fdi.

If you go to xorg.conf you lose hotplugging.  The old hot plug commands might still work:  ctrl-alt-F1 and then Ctrl-alt-F7.

Renaming would be simpler and preserve hotplugging.  Let's see what you see with:
```
xinput --list
```
I'm assuming:
```
xsetwacom list
```
is blank.

---

### Post by victorhooi on 2009-05-31
heya,

"wacom-tools" is at version 0.8.3.2-1ubuntu1. "xserver-xorg-input-wacom" is also at 0.8.3.2-1ubuntu1.

My "10-linuxwacom.fdi" file:
```
victorhooi@ubuntu:/usr/share/hal/fdi/policy/20thirdparty$ cat 10-linuxwacom.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>                                     
<!-- this is probably a bit imprecise -->                                       
<deviceinfo version="0.2">                                                      
  <device>                                                                      
    <match key="info.category" contains="input">                                
      <match key="info.product" contains_outof="Wacom;WALTOP">                  
        <merge key="input.x11_driver" type="string">wacom</merge>               
        <merge key="input.x11_options.Type" type="string">stylus</merge>        
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append> 
        <append key="wacom.types" type="strlist">eraser</append>                
        <append key="wacom.types" type="strlist">cursor</append>                
        <append key="wacom.types" type="strlist">pad</append>                   
      </match>                                                                  
    </match>                                                                    
    <match key="info.capabilities" contains="serial">                           
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```

Output from xinput --list:
```
victorhooi@ubuntu:/media$ xinput --list
"Virtual core pointer"  id=0    [XPointer]
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
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248                    
        Min_keycode is 8                   
        Max_keycode is 255                 
"Fujitsu FUJ02E3"       id=2    [XExtensionKeyboard]
        Type is KEYBOARD                            
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
"PnP Device (FUJ02e5) eraser"   id=3    [XExtensionKeyboard]
        Type is Wacom Eraser                                
        Num_keys is 248                                     
        Min_keycode is 8                                    
        Max_keycode is 255                                  
        Num_buttons is 32                                   
        Num_axes is 6                                       
        Mode is Absolute                                    
        Motion_buffer is 256                                
        Axis 0 :                                            
                Min_value is 0                              
                Max_value is 24576                          
                Resolution is 2540                          
        Axis 1 :                                            
                Min_value is 0                              
                Max_value is 18432                          
                Resolution is 2540                          
        Axis 2 :                                            
                Min_value is 0                              
                Max_value is 255                            
                Resolution is 1                             
        Axis 3 :                                            
                Min_value is -64                            
                Max_value is 63                             
                Resolution is 1                             
        Axis 4 :                                            
                Min_value is -64                            
                Max_value is 63                             
                Resolution is 1                             
        Axis 5 :                                            
                Min_value is 0                              
                Max_value is 1023                           
                Resolution is 1                             
"AT Translated Set 2 keyboard"  id=4    [XExtensionKeyboard]
        Type is KEYBOARD                                    
        Num_keys is 248                                     
        Min_keycode is 8                                    
        Max_keycode is 255
"Fujitsu FUJ02B1"       id=5    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=6    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=7    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 32
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
"SynPS/2 Synaptics TouchPad"    id=8    [XExtensionPointer]
        Type is TOUCHPAD
        Num_buttons is 12
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 1472
                Max_value is 5472
                Resolution is 1
        Axis 1 :
                Min_value is 1408
                Max_value is 4448
                Resolution is 1

```
xsetwacom list is indeed blank.

Cheers,
Victor

---

### Post by Favux on 2009-05-31
Hi victorhooi,

That is very weird and interesting.

Since it is seeing:

eraser = "PnP Device (FUJ02e5) eraser"

then it should be showing your stylus as:

stylus = "PnP Device (FUJ02e5)"

But I don't see it.  If it did then you could go to Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)  And probably follow 3 or 3a and things would work.  Then follow Section 3 towards the bottom to get "wacomcpl" set up.

The .fdi you show isn't the default Jaunty wacom.fdi because it doesn't have the USB subsection above Waltop.  I wouldn't have thought that makes a difference.  Did you edit the output you show?

---

### Post by victorhooi on 2009-05-31
heya,

Favux: I'm pretty sure it's the default 10-linuxwacom.fdi file.

I just moved the file to backup, then did a reinstall of xserver-xorg-input-wacom, which provides that file, and did a diff, same contents. And I pasted it verbatim into my original post, just checked.

However, I'm actually running on 9.10 now, would that make a difference to that file? Should I try either 3 (rename) or 3a (rec's script) on that page? Or is there a custom fdi for Fujitsu tablets? (T4210/T4215/T4220?)

Cheers,
Victor

---

### Post by Favux on 2009-05-31
Hi victorhooi,

Thank you very much for checking that!  It is a new "default" 10-wacom.fdi.  Probably Kharmic's.  I wonder if they back ported it to Jaunty?  Or plan to.  They merged wacom and waltop and made another change for usb tablets!  I wonder if it parses things correctly now?  And Synaptics says it is using linuxwacom 0.8.3-2-1?  That makes sense because 0.8.3.2 is the first version of linuxwacom to support Xserver 1.6.  By the way it is development branch, which is up to 0.8.3-5.  The last production branch was 0.8.2-2.

I don't see a change for serial tablets though.  So yes you'd use either 3 or 3a.  I wonder where stylus is though.

As far as I know no one's posted a custom .fdi for Fujitsu tablets (T4210/T4215/T4220)?  But there are laptop brand name specific .fdi's upstream of the wacom.fdi where you can add quirks and stuff.  I don't remember where exactly, somewhere in "/usr/share/hal/fdi/".  And for info. on adding quirks see:  [http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

---

### Post by victorhooi on 2009-05-31
heya,

Favux: Well, this is rather embarrassing...lol. I've just realised that before, when I was using your .fdi file, I actually used the lshal output file, and not the fdi file. I did actually open the files, and I noticed the completely different format (and that it wasn't even XML), but I must have been like...oh...must be an alternate form or something....haha...sorry.

Anyhow, have just used it, and when I logged in, the pen didn't seem to work, but then I flipped my pen around, and used the eraser, and low and behold, that end of the pen now works =), and the eraser button acts as a mouse-click (not eraser). The tip of the pen still doesn't work, nor do the two buttons near that end, but this is a start, and maybe it'll give you a clue on my situation.

[IMG]https://www.nottes.com/shop/shop_images/fpcpn23_300.jpg[/IMG]

Also, I'm using Sun VirtualBox atm, and I've noticed that using the eraser end, I can get the cursor to move in Windows (Windows 7, to be exact). However, I suspect its simply treating it as a mouse input - I don't have any tablet features. Do you have any idea of how to pass through the stylus as a tablet device to VirtualBox?

Cheers,
Victor

---

### Post by Favux on 2009-05-31
Hi victorhooi,

Wow!  So my serial .fdi kind of works.  It doesn't take out the keyboard like you said in post #28?  Cool.  Maybe there is hope for it.  Since the eraser has the append, what would happen if we just also append the stylus?  You shouldn't have to do that but...

I'm getting myself confused.  The eraser works in your Kharmic alpha using the .fdi?  But not the buttons or tip?  And you noticed that Win 7 in VirtualBox also reacts to the eraser?  Or are you saying you're also running Kharmic in VirtualBox?  And since only eraser works in both Kharmic and Win 7 in VirtualBox you're wondering if it is a VirtualBox problem?

Sorry I keep meaning to get around to playing with virtualizing but haven't yet.  So I don't know diddly about VirtualBox.

---

### Post by victorhooi on 2009-05-31
heya,

**1. Tablet under Kubuntu**

Yeah, it is a all bit confusing. I just restarted with the stock .fdi (from the package), and the eraser also works. So it works with both. But your .fdi doesn't blow away the keyboard (but if you're silly like me, and try to use lshal output as a .fdi, it does...haha).

It's just that I never thought to turn my pen over and see whether the eraser end worked (I just assumed the two would work together, or not at all).

I just did a diff between the files to make sure I wasn't getting confused between the different versions.

So for some weird reason - with either your .fdi or with the stock .fdi, the eraser end will work, and the eraser button will function as mouse-clicks, but the pen end doesn't work, nor do the two buttons at that end.

This is with Kubuntu Karmic Koala installed directly onto the laptop.

**2. Windows 7 in VirtualBox, under Kubuntu**

Windows 7 is running inside a VirtualBox virtual machine under Kubuntu - the eraser also functions inside the VM, but apparently just as a mouse, no pressure sensitivity or tablet features (or I need to do something to enable tablet functionality). That may be more a question for the VirtualBox forums - how to get VirtualBox to pass through the tablet device to the virtualised OS, unless someobdy here happen to know something about this issue as well?

Cheers,
Victor

---

### Post by Favux on 2009-05-31
Hi victorhooi,

OK I got you.  I'm not sure I've seen that before.  Except something like that in some of my experiments in Intrepid with wacom.rules and symlinks.  Stylus should be showing up in xinput like I said in #33.  It should work but not eraser.  Once you get the name thing straightened out you should have everything working, using wacomcpl and rotation etc.  So I don't know what's going on.

You don't have anything wacom related in xorg.conf do you?

I know the tablet pc .fdi has a special setup for one serial tablet pc.  I can't remember which brand.  Does yours need one maybe?  A different baud rate or ttyS?  Do you know what your old setserial line looked like?

---

### Post by victorhooi on 2009-06-01
heya,

Nope, my xorg.conf has only one small section, to turn on UXA (buggy, I know, but KDE4 was pretty much unusable without it...).

```
victorhooi@ubuntu:~/.kde/share/apps$ cat /etc/X11/xorg.conf
Section "Device"
        Identifier    "Configured Video Device"
        Option "AccelMethod" "uxa"
EndSection
```

I'm not sure about any special settings for my tablet, I've never ever actually tried to get the tablet working under Linux before on this one.

I do know a while back, I did try the approach in section 1 listed here, with compiling the kernel.

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

I've done apt-get --reinstall a few times since then, and also upgraded to 9.10 (from 9.04), so I'm assuming none of that would have any effect still? And it's weird that the eraser end/button work, but not the pen end.

Cheers,
Victor

---

### Post by Favux on 2009-06-01
Hi victorhooi,

It is weird, and like I said I don't understand it.  The 10-tablePCs.fdi is located at "/usr/share/hal/fdi/policy/10osvendor/".  Maybe we should look at it.  There are a couple sections.  For example what's the "FPI20004" about?  At least it shows some serial tablets need a baud_rate different from the standard.  You could see if it applies to you by doing:
```
lshal | grep "FPI2004"
```
And so on.  Anyway it may be worth a glance.

Theoretically it shouldn't matter.  I do know some folks swear on doing a "clean" reinstall when changing to a different version.  They feel it eliminates the risk of unwanted, lingering side-effects.  Others say an upgrade is no problem.  So I don't know.

---

### Post by victorhooi on 2009-06-01
heya,

Output from my 10-tabletPCs.fdi:

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input.tablet.tabletPC">
      <!-- There is a report that we should use ttyS2 instead of ttyS0 -->
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="HP Compaq tc4200">
	<merge key="input.device.set" type="string">/dev/ttyS2</merge>
      </match>

      <!-- to get the device up we need to set the baud_rate correct -->
      <match key="pnp.id" contains="FPI2004">
	<merge key="input.device.set" type="string">/dev/ttyS0</merge>
	<merge key="pnp.serial.baud_base" type="int">38400</merge>
      </match>
    </match>

    <!-- add addon if need special ttySx settings -->
    <match key="input.device.set" exists="true">
      <append key="info.callouts.add" type="strlist">hal-system-setserial</append>	
    </match>

    <!-- handle USB tablets -->
    <match key="usb_device.vendor_id" int="0x56a">
      <!-- WACOM Tablets -->
      <match key="usb_device.product_id" int_outof="0x90;0x93;0x9a">
	<!-- TabletPCs with USB Wacom Tablets -->
        <match key="/org/freedesktop/Hal/devices/computer:system.formfactor" compare_ne="laptop">
	  <!-- set the correct formfactor if not already laptop -->
	  <merge key="/org/freedesktop/Hal/devices/computer:system.formfactor" type="string">laptop</merge>
	</match>
	<!-- set the correct subtype -->
	<merge key="/org/freedesktop/Hal/devices/computer:system.formfactor.subtype" type="string">tabletpc</merge>
      </match>
    </match>

  </device>

</deviceinfo>
```

I did a grep for various terms in lshal against 10-tabletPCs.fdi, didn't seem to get any hits.

Output from lshal

```

Dumping 125 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-acl-tool --remove-all', 'hal-storage-cleanup-all-mountpoints'} (string list)
  info.callouts.session_active = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_add = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_inactive = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_remove = {'hal-acl-tool --reconfigure'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20090320'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)
  system.board.product = 'FJNB1B9'  (string)
  system.board.serial = ''  (string)
  system.board.vendor = 'FUJITSU'  (string)
  system.board.version = ''  (string)
  system.chassis.manufacturer = 'DE6C00G607643000'  (string)
  system.chassis.type = 'Notebook'  (string)
  system.firmware.release_date = '06/02/2008'  (string)
  system.firmware.vendor = 'FUJITSU // Phoenix Technologies Ltd.'  (string)
  system.firmware.version = 'Version 1.18'  (string)
  system.formfactor = 'laptop'  (string)
  system.formfactor.subtype = 'tabletpc'  (string)
  system.hardware.primary_video.product = 10146  (0x27a2)  (int)
  system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
  system.hardware.product = 'T4215'  (string)
  system.hardware.serial = 'R7302314'  (string)
  system.hardware.uuid = '3391E550-AF8C-11DB-8B14-001742279D60'  (string)
  system.hardware.vendor = 'FUJITSU'  (string)
  system.hardware.version = ''  (string)
  system.kernel.machine = 'x86_64'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.30-6-generic'  (string)
  system.kernel.version.major = 2  (0x2)  (int)
  system.kernel.version.micro = 30  (0x1e)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/net_f2_ad_23_43_44_21'
  info.capabilities = {'net', 'net.bridge'} (string list)
  info.category = 'net.bridge'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Bridge Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_f2_ad_23_43_44_21'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/pan0'  (string)
  net.address = 'f2:ad:23:43:44:21'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.bridge.mac_address = 266825434874913  (0xf2ad23434421)  (uint64)
  net.interface = 'pan0'  (string)
  net.linux.ifindex = 6  (0x6)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'
  button.has_state = true  (bool)
  button.state.value = false  (bool)
  button.type = 'lid'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.switch', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Lid Switch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Lid Switch'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fujitsu FUJ02B1'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = 'Fujitsu FUJ02B1'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/FUJ02B1:00/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Video Bus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event8'  (string)
  input.product = 'Video Bus'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fujitsu FUJ02E3'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = 'Fujitsu FUJ02E3'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  access_control.file = '/dev/snd/timer'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  access_control.file = '/dev/sequencer2'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  access_control.file = '/dev/sequencer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  access_control.file = '/dev/snd/seq'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'
  access_control.file = '/dev/input/event3'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'  (string)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU1'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_76_62_6e_65_74'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_76_62_6e_65_74'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/vboxnet0'  (string)
  net.80203.mac_address = 508457543028  (0x76626e6574)  (uint64)
  net.address = '00:76:62:6e:65:74'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'vboxnet0'  (string)
  net.linux.ifindex = 5  (0x5)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = {'net', 'net.loopback'} (string list)
  info.category = 'net.loopback'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'  (string)
  net.address = '00:00:00:00:00:00'  (string)
  net.arp_proto_hw_id = 772  (0x304)  (int)
  net.interface = 'lo'  (string)
  net.linux.ifindex = 1  (0x1)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.addons = {'hald-addon-generic-backlight'} (string list)
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.brightness_in_hardware = false  (bool)
  laptop_panel.num_levels = 8  (0x8)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB1'
  battery.charge_level.current = 43718  (0xaac6)  (int)
  battery.charge_level.design = 56160  (0xdb60)  (int)
  battery.charge_level.last_full = 43718  (0xaac6)  (int)
  battery.charge_level.percentage = 100  (0x64)  (int)
  battery.charge_level.rate = 0  (0x0)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'CP293420'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.reporting.current = 4050  (0xfd2)  (int)
  battery.reporting.design = 5200  (0x1450)  (int)
  battery.reporting.last_full = 4048  (0xfd0)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.serial = '1'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'Fujitsu'  (string)
  battery.voltage.current = 12522  (0x30ea)  (int)
  battery.voltage.design = 10800  (0x2a30)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'CP293420'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/CMB1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'
  ac_adapter.present = true  (bool)
  info.capabilities = {'ac_adapter'} (string list)
  info.category = 'ac_adapter'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic AC Adapter Device'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_SMCf010'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (SMCf010)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_SMCf010'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.id = 'SMCf010'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.id = 'PNP0103'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PS/2 Port for PS/2-style Mice'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'PS/2 Port for PS/2-style Mice'  (string)
  pnp.id = 'PNP0f13'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.linux.driver = 'rtc_cmos'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.id = 'FUJ02e5'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x220'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device', 'hal-setup-wacom'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  info.product = 'PnP Device (FUJ02e5) eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02bf'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02bf)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02bf'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.id = 'FUJ02bf'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_IFX0102'
  info.linux.driver = 'tpm_inf_pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (IFX0102)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_IFX0102'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.id = 'IFX0102'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.id = 'PNP0a08'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'
  info.linux.driver = 'vboxdrv'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (vboxdrv.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/vboxdrv.0'  (string)
  platform.id = 'vboxdrv.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_3'
  access_control.file = '/dev/ttyS3'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_3'  (string)
  linux.device_file = '/dev/ttyS3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250/tty/ttyS3'  (string)
  serial.device = '/dev/ttyS3'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.port = 3  (0x3)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (regulatory.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/regulatory.0'  (string)
  platform.id = 'regulatory.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'
  info.linux.driver = 'iTCO_wdt'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (iTCO_wdt)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/iTCO_wdt'  (string)
  platform.id = 'iTCO_wdt'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX3 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4'  (string)
  serio.description = 'i8042 AUX3 port'  (string)
  serio.id = 'serio4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.SHMConfig = 'True'  (string)
  input.x11_options.VertEdgeScroll = 'true'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX2 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio3'  (string)
  serio.description = 'i8042 AUX2 port'  (string)
  serio.id = 'serio3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX1 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio2'  (string)
  serio.description = 'i8042 AUX1 port'  (string)
  serio.id = 'serio2'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX0 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX0 port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_fujitsu_laptop'
  info.linux.driver = 'fujitsu-laptop'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (fujitsu-laptop)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_fujitsu_laptop'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/fujitsu-laptop'  (string)
  platform.id = 'fujitsu-laptop'  (string)

udi = '/org/freedesktop/Hal/devices/platform_dock_0'
  info.docked = true  (bool)
  info.interfaces = {'org.freedesktop.Hal.Device.DockStation'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (dock.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_dock_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/dock.0'  (string)
  org.freedesktop.Hal.Device.DockStation.method_argnames = {''} (string list)
  org.freedesktop.Hal.Device.DockStation.method_execpaths = {'hal-dockstation-undock'} (string list)
  org.freedesktop.Hal.Device.DockStation.method_names = {'Undock'} (string list)
  org.freedesktop.Hal.Device.DockStation.method_signatures = {''} (string list)
  platform.id = 'dock.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'  (string)
  platform.id = 'Fixed MDIO bus.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27da'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27da'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.product = '82801G (ICH7 Family) SMBus Controller'  (string)
  pci.product_id = 10202  (0x27da)  (int)
  pci.subsys_product_id = 5000  (0x1388)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5'
  info.linux.driver = 'ahci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801GBM/GHM (ICH7 Family) SATA AHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 6  (0x6)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.product = '82801GBM/GHM (ICH7 Family) SATA AHCI Controller'  (string)
  pci.product_id = 10181  (0x27c5)  (int)
  pci.subsys_product_id = 4999  (0x1387)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_2'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3'  (string)
  scsi_host.host = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_1'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'WDC WD3200BEVT-2'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  info.product = 'WDC WD3200BEVT-2'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '11.0'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'WDC WD3200BEVT-2'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 320072933376  (0x4a85d56000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'SATA_WDC_WD3200BEVT-_WD-WXH808426103'  (string)
  storage.size = 320072933376  (0x4a85d56000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = 'partitiontable'  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (uint64)
  volume.partition.flags = {} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 80541941760  (0x12c0ac8000)  (uint64)
  volume.partition.type = '0x0f'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_96012680_a45e_4fa8_a1f9_17f09408b345'
  block.device = '/dev/sda6'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 6  (0x6)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_96012680_a45e_4fa8_a1f9_17f09408b345'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 3903732  (0x3b90f4)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 6  (0x6)  (int)
  volume.partition.start = 107389287936  (0x1900e67e00)  (uint64)
  volume.size = 1998710784  (0x7721e800)  (uint64)
  volume.uuid = '96012680-a45e-4fa8-a1f9-17f09408b345'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_e6b4f8b9_2fbc_4a42_a39c_704b4854abd6'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_e6b4f8b9_2fbc_4a42_a39c_704b4854abd6'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec'} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 52436097  (0x3201c81)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 80541974016  (0x12c0acfe00)  (uint64)
  volume.size = 26847281664  (0x640390200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'e6b4f8b9-2fbc-4a42-a39c-704b4854abd6'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_8A5E8F125E8EF5EB'
  block.device = '/dev/sda4'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 4  (0x4)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_8A5E8F125E8EF5EB'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/win7'  (string)
  volume.num_blocks = 52436097  (0x3201c81)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 4  (0x4)  (int)
  volume.partition.start = 53694660096  (0xc80737e00)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 26847281664  (0x640390200)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '8A5E8F125E8EF5EB'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_B4CCF2DACCF29638'
  block.device = '/dev/sda3'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 3  (0x3)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'New Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_B4CCF2DACCF29638'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'New Volume'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/x_drive'  (string)
  volume.num_blocks = 411488910  (0x1886d28e)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 3  (0x3)  (int)
  volume.partition.start = 109387998720  (0x1978086600)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 210682321920  (0x310da51c00)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'B4CCF2DACCF29638'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_A0B02B11B02AEE0A'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_A0B02B11B02AEE0A'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/winxp'  (string)
  volume.num_blocks = 104872257  (0x6403941)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 53694595584  (0xc80728200)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'A0B02B11B02AEE0A'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df'
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.product = '82801G (ICH7 Family) IDE Controller'  (string)
  pci.product_id = 10207  (0x27df)  (int)
  pci.subsys_product_id = 4997  (0x1385)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 4  (0x4)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'UJDA770 DVD/CDRW'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'MATSHITA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'
  access_control.file = '/dev/sr0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  info.product = 'UJDA770 DVD/CDRW'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'  (string)
  info.vendor = 'MATSHITA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrdl = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.write_speeds = {'4234', '2822', '1411', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = '1.00'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'UJDA770 DVD/CDRW'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'MATSHITA'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'
  access_control.file = '/dev/sg1'  (string)
  access_control.type = 'cdrom'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'scsi_generic', 'access_control'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27b9'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801GBM (ICH7-M) LPC Interface Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27b9'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.product = '82801GBM (ICH7-M) LPC Interface Bridge'  (string)
  pci.product_id = 10169  (0x27b9)  (int)
  pci.subsys_product_id = 4996  (0x1384)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2448'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801 Mobile PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.product = '82801 Mobile PCI Bridge'  (string)
  pci.product_id = 9288  (0x2448)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7130'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'Integrated MS/xD Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7130'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.3'  (string)
  pci.product = 'Integrated MS/xD Controller'  (string)
  pci.product_id = 28976  (0x7130)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7120'
  info.linux.driver = 'sdhci-pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'Integrated MMC/SD Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2'  (string)
  pci.device_class = 8  (0x8)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2'  (string)
  pci.product = 'Integrated MMC/SD Controller'  (string)
  pci.product_id = 28960  (0x7120)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7120_mmc_host'
  info.capabilities = {'mmc_host'} (string list)
  info.category = 'mmc_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.subsystem = 'mmc_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7120_mmc_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'mmc_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2/mmc_host/mmc0'  (string)
  mmc_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/leds_mmc0'
  info.capabilities = {'leds'} (string list)
  info.category = 'leds'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_mmc0'  (string)
  leds.device_name = 'mmc0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2/leds/mmc0::'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1217_7134_0'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7134_0'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1'  (string)
  pci.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  pci.product_id = 28980  (0x7134)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7134_0'  (string)
  info.product = 'SmartCardBus Reader'  (string)
  info.subsystem = 'pcmcia'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.vendor = 'O2Micro'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pcmcia'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1/1.0'  (string)
  pcmcia.card_id = 1  (0x1)  (int)
  pcmcia.manf_id = 65535  (0xffff)  (int)
  pcmcia.prod_id1 = 'O2Micro'  (string)
  pcmcia.prod_id2 = 'SmartCardBus Reader'  (string)
  pcmcia.prod_id3 = 'V1.0'  (string)
  pcmcia.product = 'O2Micro'  (string)
  pcmcia.socket_number = 1  (0x1)  (int)
  pcmcia.vendor = 'O2Micro'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1217_7134'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7134'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.0'  (string)
  pci.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  pci.product_id = 28980  (0x7134)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB2 EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.product = '82801G (ICH7 Family) USB2 EHCI Controller'  (string)
  pci.product_id = 10188  (0x27cc)  (int)
  pci.subsys_product_id = 5002  (0x138a)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cc'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 8  (0x8)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:1d.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 8  (0x8)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:1d.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #4'  (string)
  pci.product_id = 10187  (0x27cb)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cb'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.3'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.3'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #3'  (string)
  pci.product_id = 10186  (0x27ca)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27ca'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'AES2501 Fingerprint Sensor'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'  (string)
  info.vendor = 'AuthenTec, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 255  (0xff)  (int)
  usb_device.device_protocol = 255  (0xff)  (int)
  usb_device.device_revision_bcd = 1569  (0x621)  (int)
  usb_device.device_subclass = 255  (0xff)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'AES2501 Fingerprint Sensor'  (string)
  usb_device.product_id = 9600  (0x2580)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'AuthenTec, Inc.'  (string)
  usb_device.vendor_id = 2303  (0x8ff)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 255  (0xff)  (int)
  usb.device_protocol = 255  (0xff)  (int)
  usb.device_revision_bcd = 1569  (0x621)  (int)
  usb.device_subclass = 255  (0xff)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 9600  (0x2580)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'AuthenTec, Inc.'  (string)
  usb.vendor_id = 2303  (0x8ff)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #2'  (string)
  pci.product_id = 10185  (0x27c9)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c9'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #1'  (string)
  pci.product_id = 10184  (0x27c8)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c8'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  pci.product_id = 10196  (0x27d4)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.linux.driver = 'ath5k'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.vendor = 'Atheros Communications Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0'  (string)
  pci.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  pci.product_id = 28  (0x1c)  (int)
  pci.subsys_product_id = 5020  (0x139c)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Atheros Communications Inc.'  (string)
  pci.vendor_id = 5772  (0x168c)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35_0'
  info.capabilities = {'net', 'net.80211control'} (string list)
  info.category = 'net.80211control'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wmaster0'  (string)
  net.address = '00:16:e3:a0:83:35'  (string)
  net.arp_proto_hw_id = 801  (0x321)  (int)
  net.interface = 'wmaster0'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlan0'  (string)
  net.80211.mac_address = 98308227893  (0x16e3a08335)  (uint64)
  net.address = '00:16:e3:a0:83:35'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  pci.product_id = 10194  (0x27d2)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  pci.product_id = 10192  (0x27d0)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_11ab_4363'
  info.linux.driver = 'sky2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.product = '88E8055 PCI-E Gigabit Ethernet Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  info.vendor = 'Marvell Technology Group Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.product = '88E8055 PCI-E Gigabit Ethernet Controller'  (string)
  pci.product_id = 17251  (0x4363)  (int)
  pci.subsys_product_id = 5018  (0x139a)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Marvell Technology Group Ltd.'  (string)
  pci.vendor_id = 4523  (0x11ab)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_17_42_27_9d_60'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_17_42_27_9d_60'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0'  (string)
  net.80203.mac_address = 99894140256  (0x1742279d60)  (uint64)
  net.address = '00:17:42:27:9d:60'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  pci.product_id = 10200  (0x27d8)  (int)
  pci.subsys_product_id = 5044  (0x13b4)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.product = 'HDA Intel Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA Intel'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'
  access_control.file = '/dev/snd/pcmC0D0p'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'STAC92xx Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'
  access_control.file = '/dev/snd/pcmC0D0c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'STAC92xx Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'
  access_control.file = '/dev/dsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'
  access_control.file = '/dev/mixer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'
  access_control.file = '/dev/snd/controlC0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'
  access_control.file = '/dev/audio'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.product = 'HDA Digital PCBeep'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  input.product = 'HDA Digital PCBeep'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/input/input10/event10'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10150  (0x27a6)  (int)
  pci.subsys_product_id = 4992  (0x1380)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10146  (0x27a2)  (int)
  pci.subsys_product_id = 4992  (0x1380)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm__null__card0'
  access_control.file = '/dev/dri/card0'  (string)
  access_control.type = 'video'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'drm', 'access_control'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm__null__card0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.device_file = '/dev/dri/card0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a0'
  info.linux.driver = 'agpgart-intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub'  (string)
  pci.product_id = 10144  (0x27a0)  (int)
  pci.subsys_product_id = 4984  (0x1378)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27a0'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 125 device(s) from the Global Device List.
------------------------------------------------

```

Cheers,
Victor

---

### Post by Favux on 2009-06-01
Hi victorhooi,

Well according to these two sites:  [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D)  and  [http://ubuntuforums.org/showthread.php?t=110050&highlight=fujitsu+tablet](http://ubuntuforums.org/showthread.php?t=110050&highlight=fujitsu+tablet)  It looks like your setserial line would be:
```
/dev/ttyS0 port 0x220 irq 4 autoconfig
```
Which looks like a plain vanilla Wacom serial tablet pc setserial line.  Nothing unusual.  So...

I don't see a discussion of baud_rate stuff.  Probably irrelevant.

---

### Post by victorhooi on 2009-06-03
heya,

Well, that's fine and dandy...now the eraser end doesn't work either. I've done a few apt-get upgrades (including one which upgraded the kernel, I believe - currently at 2.6.30-7), and somewhere along the line, the eraser end doesn't work now, either

I've tried with both the stock .fdi and your .fdi, no response from either end of the pen under both.

I've included the latest output from everything, in case that helps (I didn't want to cull out stuff, in case I culled out something that was important, without knowing).

My Xorg.0.log (it does mention Fujitsu, Wacom and the erase, but I didn't see anything on why it doesn't work):
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.6.1.901 (1.6.2 RC 1)
Release Date: 2009-5-8
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.30-7-generic #8-Ubuntu SMP Mon May 25 13:52:54 UTC 2009 x86_64
Build Date: 23 May 2009  09:46:34PM
xorg-server 2:1.6.1.901-2ubuntu1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  3 14:20:40 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0300000/524288, 0xe0000000/268435456, 0xf0400000/262144, I/O @ 0x00001800/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.7.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, IGD_GM, IGD_G, 965G, G35,
	965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF0300000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(**) intel(0): Using UXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA has no monitor section
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVOB: device VID/DID: 02:43.00, clock range 25.0MHz - 200.0MHz
(II) intel(0): SDVOB: 1 input channel
(II) intel(0): SDVOB: TMDS0 output reported
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): Current clock rate multiplier: 1
(II) intel(0): Resizable framebuffer: available (1 4)
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1248  768 771 777 868 (52.1 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TMDS-1
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TMDS-1 disconnected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000400
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000202 to 0x80000242
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS LBLC_EVENT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000000 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710087
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x6b405140
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 810752 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 3243004 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Current clock rate multiplier: 1
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x005fffff: compressed frame buffer (6144 kB, 0x00000000cf800000 physical
)
(II) intel(0): 0x00600000-0x00600fff: compressed ll buffer (4 kB, 0x00000000cfe00000 physical
)
(II) intel(0): 0x00601000-0x0060afff: HW cursors (40 kB, 0x00000000cfe01000 physical
)
(II) intel(0): 0x0060b000-0x0060bfff: overlay registers (4 kB, 0x00000000cfe0b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x0f9f3fff: DRI memory manager (248020 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007bf000:            start of memory manager
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0f9f4000:            end of memory manager
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS-1 is connected to pipe none
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Fujitsu FUJ02B1
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event5"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Fujitsu FUJ02E3
(**) Fujitsu FUJ02E3: always reports core events
(**) Fujitsu FUJ02E3: Device: "/dev/input/event6"
(II) Fujitsu FUJ02E3: Found keys
(II) Fujitsu FUJ02E3: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02E3" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.3-2 $
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5)"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5) eraser"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.0
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(**) Option "SHMConfig" "True"
(**) Option "VertEdgeScroll" "true"
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1248  768 771 777 868 (52.1 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TMDS-1
(II) intel(0): EDID for output TV
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1248  768 771 777 868 (52.1 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output TMDS-1
(II) intel(0): EDID for output TV
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x005fffff: compressed frame buffer (6144 kB, 0x00000000cf800000 physical
)
(II) intel(0): 0x00600000-0x00600fff: compressed ll buffer (4 kB, 0x00000000cfe00000 physical
)
(II) intel(0): 0x00601000-0x0060afff: HW cursors (40 kB, 0x00000000cfe01000 physical
)
(II) intel(0): 0x0060b000-0x0060bfff: overlay registers (4 kB, 0x00000000cfe0b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x0f9f3fff: DRI memory manager (248020 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007bf000:            start of memory manager
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0f9f4000:            end of memory manager
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS-1 is connected to pipe none
(II) intel(0):   Output TV is connected to pipe none
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Fujitsu FUJ02B1: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Fujitsu FUJ02E3: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

```

Output from lshal:
```
:
Dumping 130 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20090320'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)
  system.board.product = 'FJNB1B9'  (string)
  system.board.serial = ''  (string)
  system.board.vendor = 'FUJITSU'  (string)
  system.board.version = ''  (string)
  system.chassis.manufacturer = 'DE6C00G607643000'  (string)
  system.chassis.type = 'Notebook'  (string)
  system.firmware.release_date = '06/02/2008'  (string)
  system.firmware.vendor = 'FUJITSU // Phoenix Technologies Ltd.'  (string)
  system.firmware.version = 'Version 1.18'  (string)
  system.formfactor = 'laptop'  (string)
  system.formfactor.subtype = 'tabletpc'  (string)
  system.hardware.primary_video.product = 10146  (0x27a2)  (int)
  system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
  system.hardware.product = 'T4215'  (string)
  system.hardware.serial = 'R7302314'  (string)
  system.hardware.uuid = '3391E550-AF8C-11DB-8B14-001742279D60'  (string)
  system.hardware.vendor = 'FUJITSU'  (string)
  system.hardware.version = ''  (string)
  system.kernel.machine = 'x86_64'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.30-7-generic'  (string)
  system.kernel.version.major = 2  (0x2)  (int)
  system.kernel.version.micro = 30  (0x1e)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/net_9a_7d_ca_0d_48_fc'
  info.capabilities = {'net', 'net.bridge'} (string list)
  info.category = 'net.bridge'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Bridge Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_9a_7d_ca_0d_48_fc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/pan0'  (string)
  net.address = '9a:7d:ca:0d:48:fc'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.bridge.mac_address = 169865051457788  (0x9a7dca0d48fc)  (uint64)
  net.interface = 'pan0'  (string)
  net.linux.ifindex = 6  (0x6)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'
  button.has_state = true  (bool)
  button.state.value = false  (bool)
  button.type = 'lid'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.switch', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Lid Switch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Lid Switch'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fujitsu FUJ02B1'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = 'Fujitsu FUJ02B1'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/FUJ02B1:00/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Video Bus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event8'  (string)
  input.product = 'Video Bus'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fujitsu FUJ02E3'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = 'Fujitsu FUJ02E3'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU1'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_76_62_6e_65_74'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_76_62_6e_65_74'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/vboxnet0'  (string)
  net.80203.mac_address = 508457543028  (0x76626e6574)  (uint64)
  net.address = '00:76:62:6e:65:74'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'vboxnet0'  (string)
  net.linux.ifindex = 5  (0x5)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = {'net', 'net.loopback'} (string list)
  info.category = 'net.loopback'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'  (string)
  net.address = '00:00:00:00:00:00'  (string)
  net.arp_proto_hw_id = 772  (0x304)  (int)
  net.interface = 'lo'  (string)
  net.linux.ifindex = 1  (0x1)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'  (string)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.addons = {'hald-addon-generic-backlight'} (string list)
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.brightness_in_hardware = false  (bool)
  laptop_panel.num_levels = 8  (0x8)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB1'
  battery.charge_level.current = 41148  (0xa0bc)  (int)
  battery.charge_level.design = 56160  (0xdb60)  (int)
  battery.charge_level.last_full = 43718  (0xaac6)  (int)
  battery.charge_level.percentage = 94  (0x5e)  (int)
  battery.charge_level.rate = 0  (0x0)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'CP293420'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.reporting.current = 3810  (0xee2)  (int)
  battery.reporting.design = 5200  (0x1450)  (int)
  battery.reporting.last_full = 4048  (0xfd0)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.serial = '1'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'Fujitsu'  (string)
  battery.voltage.current = 12290  (0x3002)  (int)
  battery.voltage.design = 10800  (0x2a30)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'CP293420'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/CMB1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'
  ac_adapter.present = true  (bool)
  info.capabilities = {'ac_adapter'} (string list)
  info.category = 'ac_adapter'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic AC Adapter Device'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_SMCf010'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (SMCf010)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_SMCf010'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.id = 'SMCf010'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.id = 'PNP0103'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PS/2 Port for PS/2-style Mice'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'PS/2 Port for PS/2-style Mice'  (string)
  pnp.id = 'PNP0f13'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.linux.driver = 'rtc_cmos'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.id = 'FUJ02e5'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x220'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = 'stylus'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  info.product = 'PnP Device (FUJ02e5) eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
  serial.originating_device = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02bf'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02bf)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02bf'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.id = 'FUJ02bf'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_IFX0102'
  info.linux.driver = 'tpm_inf_pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (IFX0102)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_IFX0102'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.id = 'IFX0102'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.id = 'PNP0a08'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'
  info.linux.driver = 'vboxdrv'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (vboxdrv.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/vboxdrv.0'  (string)
  platform.id = 'vboxdrv.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_3'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_3'  (string)
  linux.device_file = '/dev/ttyS3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250/tty/ttyS3'  (string)
  serial.device = '/dev/ttyS3'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.port = 3  (0x3)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (regulatory.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/regulatory.0'  (string)
  platform.id = 'regulatory.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'
  info.linux.driver = 'iTCO_wdt'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (iTCO_wdt)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/iTCO_wdt'  (string)
  platform.id = 'iTCO_wdt'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX3 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4'  (string)
  serio.description = 'i8042 AUX3 port'  (string)
  serio.id = 'serio4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.SHMConfig = 'True'  (string)
  input.x11_options.VertEdgeScroll = 'true'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX2 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio3'  (string)
  serio.description = 'i8042 AUX2 port'  (string)
  serio.id = 'serio3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX1 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio2'  (string)
  serio.description = 'i8042 AUX1 port'  (string)
  serio.id = 'serio2'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX0 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX0 port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_fujitsu_laptop'
  info.linux.driver = 'fujitsu-laptop'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (fujitsu-laptop)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_fujitsu_laptop'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/fujitsu-laptop'  (string)
  platform.id = 'fujitsu-laptop'  (string)

udi = '/org/freedesktop/Hal/devices/platform_dock_0'
  info.docked = true  (bool)
  info.interfaces = {'org.freedesktop.Hal.Device.DockStation'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (dock.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_dock_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/dock.0'  (string)
  org.freedesktop.Hal.Device.DockStation.method_argnames = {''} (string list)
  org.freedesktop.Hal.Device.DockStation.method_execpaths = {'hal-dockstation-undock'} (string list)
  org.freedesktop.Hal.Device.DockStation.method_names = {'Undock'} (string list)
  org.freedesktop.Hal.Device.DockStation.method_signatures = {''} (string list)
  platform.id = 'dock.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'  (string)
  platform.id = 'Fixed MDIO bus.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27da'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27da'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.product = '82801G (ICH7 Family) SMBus Controller'  (string)
  pci.product_id = 10202  (0x27da)  (int)
  pci.subsys_product_id = 5000  (0x1388)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5'
  info.linux.driver = 'ahci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801GBM/GHM (ICH7 Family) SATA AHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 6  (0x6)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.product = '82801GBM/GHM (ICH7 Family) SATA AHCI Controller'  (string)
  pci.product_id = 10181  (0x27c5)  (int)
  pci.subsys_product_id = 4999  (0x1387)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_2'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3'  (string)
  scsi_host.host = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_1'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'WDC WD3200BEVT-2'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  info.product = 'WDC WD3200BEVT-2'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '11.0'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'WDC WD3200BEVT-2'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 320072933376  (0x4a85d56000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'SATA_WDC_WD3200BEVT-_WD-WXH808426103'  (string)
  storage.size = 320072933376  (0x4a85d56000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_96012680_a45e_4fa8_a1f9_17f09408b345'
  block.device = '/dev/sda6'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 6  (0x6)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_96012680_a45e_4fa8_a1f9_17f09408b345'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 3903732  (0x3b90f4)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 6  (0x6)  (int)
  volume.partition.start = 107389287936  (0x1900e67e00)  (uint64)
  volume.size = 1998710784  (0x7721e800)  (uint64)
  volume.uuid = '96012680-a45e-4fa8-a1f9-17f09408b345'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_e6b4f8b9_2fbc_4a42_a39c_704b4854abd6'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_e6b4f8b9_2fbc_4a42_a39c_704b4854abd6'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec'} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 52436097  (0x3201c81)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 80541974016  (0x12c0acfe00)  (uint64)
  volume.size = 26847281664  (0x640390200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'e6b4f8b9-2fbc-4a42-a39c-704b4854abd6'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_8A5E8F125E8EF5EB'
  block.device = '/dev/sda4'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 4  (0x4)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_8A5E8F125E8EF5EB'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/win7'  (string)
  volume.num_blocks = 52436097  (0x3201c81)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 4  (0x4)  (int)
  volume.partition.start = 53694660096  (0xc80737e00)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 26847281664  (0x640390200)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '8A5E8F125E8EF5EB'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_B4CCF2DACCF29638'
  block.device = '/dev/sda3'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 3  (0x3)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'New Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_B4CCF2DACCF29638'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'New Volume'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/x_drive'  (string)
  volume.num_blocks = 411488910  (0x1886d28e)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 3  (0x3)  (int)
  volume.partition.start = 109387998720  (0x1978086600)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 210682321920  (0x310da51c00)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'B4CCF2DACCF29638'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = 'partitiontable'  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (uint64)
  volume.partition.flags = {} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 80541941760  (0x12c0ac8000)  (uint64)
  volume.partition.type = '0x0f'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_A0B02B11B02AEE0A'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200BEVT__WD_WXH808426103'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_A0B02B11B02AEE0A'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = '/media/winxp'  (string)
  volume.num_blocks = 104872257  (0x6403941)  (uint64)
  volume.partition.media_size = 320072933376  (0x4a85d56000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 53694595584  (0xc80728200)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'A0B02B11B02AEE0A'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c5_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df'
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.product = '82801G (ICH7 Family) IDE Controller'  (string)
  pci.product_id = 10207  (0x27df)  (int)
  pci.subsys_product_id = 4997  (0x1385)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 4  (0x4)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'UJDA770 DVD/CDRW'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'MATSHITA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  info.product = 'UJDA770 DVD/CDRW'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_UJDA770_DVD_CDRW'  (string)
  info.vendor = 'MATSHITA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrdl = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.write_speeds = {'4234', '2822', '1411', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = '1.00'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'UJDA770 DVD/CDRW'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'MATSHITA'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host4/target4:0:0/4:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27b9'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801GBM (ICH7-M) LPC Interface Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27b9'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.product = '82801GBM (ICH7-M) LPC Interface Bridge'  (string)
  pci.product_id = 10169  (0x27b9)  (int)
  pci.subsys_product_id = 4996  (0x1384)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2448'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801 Mobile PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.product = '82801 Mobile PCI Bridge'  (string)
  pci.product_id = 9288  (0x2448)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7130'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'Integrated MS/xD Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7130'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.3'  (string)
  pci.product = 'Integrated MS/xD Controller'  (string)
  pci.product_id = 28976  (0x7130)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7120'
  info.linux.driver = 'sdhci-pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'Integrated MMC/SD Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2'  (string)
  pci.device_class = 8  (0x8)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2'  (string)
  pci.product = 'Integrated MMC/SD Controller'  (string)
  pci.product_id = 28960  (0x7120)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1217_7120_mmc_host'
  info.capabilities = {'mmc_host'} (string list)
  info.category = 'mmc_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.subsystem = 'mmc_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7120_mmc_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'mmc_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2/mmc_host/mmc0'  (string)
  mmc_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/leds_mmc0'
  info.capabilities = {'leds'} (string list)
  info.category = 'leds'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7120'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_mmc0'  (string)
  leds.device_name = 'mmc0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.2/leds/mmc0::'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1217_7134_0'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7134_0'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1'  (string)
  pci.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  pci.product_id = 28980  (0x7134)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'
  info.parent = '/org/freedesktop/Hal/devices/pci_1217_7134_0'  (string)
  info.product = 'SmartCardBus Reader'  (string)
  info.subsystem = 'pcmcia'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.vendor = 'O2Micro'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pcmcia'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.1/1.0'  (string)
  pcmcia.card_id = 1  (0x1)  (int)
  pcmcia.manf_id = 65535  (0xffff)  (int)
  pcmcia.prod_id1 = 'O2Micro'  (string)
  pcmcia.prod_id2 = 'SmartCardBus Reader'  (string)
  pcmcia.prod_id3 = 'V1.0'  (string)
  pcmcia.product = 'O2Micro'  (string)
  pcmcia.socket_number = 1  (0x1)  (int)
  pcmcia.vendor = 'O2Micro'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1217_7134'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1217_7134'  (string)
  info.vendor = 'O2 Micro, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:08:03.0'  (string)
  pci.product = 'OZ711MP1/MS1 MemoryCardBus Controller'  (string)
  pci.product_id = 28980  (0x7134)  (int)
  pci.subsys_product_id = 4894  (0x131e)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'O2 Micro, Inc.'  (string)
  pci.vendor_id = 4631  (0x1217)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB2 EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.product = '82801G (ICH7 Family) USB2 EHCI Controller'  (string)
  pci.product_id = 10188  (0x27cc)  (int)
  pci.subsys_product_id = 5002  (0x138a)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cc'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 8  (0x8)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:1d.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 8  (0x8)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:1d.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #4'  (string)
  pci.product_id = 10187  (0x27cb)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cb'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.3'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.3'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #3'  (string)
  pci.product_id = 10186  (0x27ca)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27ca'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'AES2501 Fingerprint Sensor'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'  (string)
  info.vendor = 'AuthenTec, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/004/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 255  (0xff)  (int)
  usb_device.device_protocol = 255  (0xff)  (int)
  usb_device.device_revision_bcd = 1569  (0x621)  (int)
  usb_device.device_subclass = 255  (0xff)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'AES2501 Fingerprint Sensor'  (string)
  usb_device.product_id = 9600  (0x2580)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'AuthenTec, Inc.'  (string)
  usb_device.vendor_id = 2303  (0x8ff)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ff_2580_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 255  (0xff)  (int)
  usb.device_protocol = 255  (0xff)  (int)
  usb.device_revision_bcd = 1569  (0x621)  (int)
  usb.device_subclass = 255  (0xff)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 9600  (0x2580)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'AuthenTec, Inc.'  (string)
  usb.vendor_id = 2303  (0x8ff)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'Bluetooth Driver (V2.0+EDR)'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial'  (string)
  info.vendor = 'Taiyo Yuden'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 224  (0xe0)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 6421  (0x1915)  (int)
  usb_device.device_subclass = 1  (0x1)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 3  (0x3)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Bluetooth Driver (V2.0+EDR)'  (string)
  usb_device.product_id = 15  (0xf)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Taiyo Yuden'  (string)
  usb_device.vendor_id = 3108  (0xc24)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if2'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial'  (string)
  info.product = 'USB Application Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.2'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 224  (0xe0)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 6421  (0x1915)  (int)
  usb.device_subclass = 1  (0x1)  (int)
  usb.interface.class = 254  (0xfe)  (int)
  usb.interface.number = 2  (0x2)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.2'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Application Specific Interface'  (string)
  usb.product_id = 15  (0xf)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Taiyo Yuden'  (string)
  usb.vendor_id = 3108  (0xc24)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if1'
  info.linux.driver = 'btusb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial'  (string)
  info.product = 'USB Wireless Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 224  (0xe0)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 6421  (0x1915)  (int)
  usb.device_subclass = 1  (0x1)  (int)
  usb.interface.class = 224  (0xe0)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Wireless Interface'  (string)
  usb.product_id = 15  (0xf)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Taiyo Yuden'  (string)
  usb.vendor_id = 3108  (0xc24)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0'
  info.linux.driver = 'btusb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial'  (string)
  info.product = 'USB Wireless Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 224  (0xe0)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 6421  (0x1915)  (int)
  usb.device_subclass = 1  (0x1)  (int)
  usb.interface.class = 224  (0xe0)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 3  (0x3)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Wireless Interface'  (string)
  usb.product_id = 15  (0xf)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Taiyo Yuden'  (string)
  usb.vendor_id = 3108  (0xc24)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0_bluetooth_hci_0'
  bluetooth_hci.address = 0  (0x0)  (uint64)
  bluetooth_hci.originating_device = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0'  (string)
  info.capabilities = {'bluetooth_hci'} (string list)
  info.category = 'bluetooth_hci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0'  (string)
  info.product = 'Bluetooth Host Controller Interface'  (string)
  info.subsystem = 'bluetooth'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c24_f_noserial_if0_bluetooth_hci_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'bluetooth'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/bluetooth/hci0'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #2'  (string)
  pci.product_id = 10185  (0x27c9)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c9'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) USB UHCI Controller #1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.product = '82801G (ICH7 Family) USB UHCI Controller #1'  (string)
  pci.product_id = 10184  (0x27c8)  (int)
  pci.subsys_product_id = 5001  (0x1389)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c8'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  pci.product_id = 10196  (0x27d4)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.linux.driver = 'ath5k'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.vendor = 'Atheros Communications Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0'  (string)
  pci.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  pci.product_id = 28  (0x1c)  (int)
  pci.subsys_product_id = 5020  (0x139c)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Atheros Communications Inc.'  (string)
  pci.vendor_id = 5772  (0x168c)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35_0'
  info.capabilities = {'net', 'net.80211control'} (string list)
  info.category = 'net.80211control'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wmaster0'  (string)
  net.address = '00:16:e3:a0:83:35'  (string)
  net.arp_proto_hw_id = 801  (0x321)  (int)
  net.interface = 'wmaster0'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_e3_a0_83_35'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/net/wlan0'  (string)
  net.80211.mac_address = 98308227893  (0x16e3a08335)  (uint64)
  net.address = '00:16:e3:a0:83:35'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  pci.product_id = 10194  (0x27d2)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  pci.product_id = 10192  (0x27d0)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_11ab_4363'
  info.linux.driver = 'sky2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.product = '88E8055 PCI-E Gigabit Ethernet Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  info.vendor = 'Marvell Technology Group Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.product = '88E8055 PCI-E Gigabit Ethernet Controller'  (string)
  pci.product_id = 17251  (0x4363)  (int)
  pci.subsys_product_id = 5018  (0x139a)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Marvell Technology Group Ltd.'  (string)
  pci.vendor_id = 4523  (0x11ab)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_17_42_27_9d_60'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_17_42_27_9d_60'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0'  (string)
  net.80203.mac_address = 99894140256  (0x1742279d60)  (uint64)
  net.address = '00:17:42:27:9d:60'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_11ab_4363'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  pci.product_id = 10200  (0x27d8)  (int)
  pci.subsys_product_id = 5044  (0x13b4)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.product = 'HDA Intel Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA Intel'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'STAC92xx Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'STAC92xx Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'STAC92xx Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'STAC92xx Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.product = 'HDA Digital PCBeep'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  input.product = 'HDA Digital PCBeep'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/input/input10/event10'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10150  (0x27a6)  (int)
  pci.subsys_product_id = 4992  (0x1380)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10146  (0x27a2)  (int)
  pci.subsys_product_id = 4992  (0x1380)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm__null__card0'
  info.capabilities = {'drm'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm__null__card0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.device_file = '/dev/dri/card0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a0'
  info.linux.driver = 'agpgart-intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub'  (string)
  pci.product_id = 10144  (0x27a0)  (int)
  pci.subsys_product_id = 4984  (0x1378)  (int)
  pci.subsys_vendor = 'Fujitsu Limited.'  (string)
  pci.subsys_vendor_id = 4303  (0x10cf)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27a0'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 130 device(s) from the Global Device List.
------------------------------------------------

```
My xinput --list:
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
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Fujitsu FUJ02B1"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Fujitsu FUJ02E3"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 32
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
"SynPS/2 Synaptics TouchPad"	id=7	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

```
The command, xsetwacom list returns blank (nothing).

My 10-linuwacom.fdi (original, provided by package), should be the same as before:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom;WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
	  <!-- Serial tablets with touch capabilities -->
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
	  <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```

Is there some voodoo dance I can do to make this work? *looks hopeful*

Cheers,
Victor

---

### Post by victorhooi on 2009-06-03
heya,

Well, ok...*sigh*...did another apt-get upgrade, and it updated xserver-xorg-video-intel, and now the eraser works. Hmm, I think part of my problem, and what might be making things difficult might be the fact I'm on Karmic Koala (cool name, btw)...so my apologies for that.

So I'm back to the state before - pen side doesn't work, eraser does work. I'm willing to try pretty much anything at this stage.

Cheers,
Victor

---

### Post by Favux on 2009-06-03
Hi victorhooi,

At first blush all that looks relevant is:
```
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.3-2 $
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5)"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5) eraser"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

```
And doesn't this part look familiar?:
```
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "PnP Device (FUJ02e5)"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
```
So either there is quirk your tablet needs in an upstream .fdi in both Jaunty and Kharmic, or there is a bug in linuxwacom in the version in Jaunty persisting to the version in Kharmic.

Either way it looks like it's time to open a launchpad bug report.  The default Kharmic .fdi should be giving you something in Xinput.  HAL is trying to load and chokes on the same old thing.  Right now my guess is it's a configuration quirk that is lacking.  What it is I have no idea.

---

### Post by Favux on 2009-06-03
And the lshal seems to show the right setserial settings:
```
udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.id = 'FUJ02e5'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x220'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = 'stylus'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0'  (string)
  info.product = 'PnP Device (FUJ02e5) eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
  serial.originating_device = 'eraser'  (string)

```
And it seems to see stylus and eraser.

---

### Post by victorhooi on 2009-06-03
heya,

Favux: Thanks so much for your help so far. I've made a post on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181)

Let me know if you can think of anything for me to try.

Cheers,
Victor

---

### Post by gigahz on 2009-08-03
> **joehardflec said:**
> 
I think what it boils down to is:
use xinput to find the true names of your stylus, then
xsetwacom set "PnP Device (yourdevicename)" rotate cw


That is definately what it boils down to on my Acer TravelMate C200 with jaunty. I didn't notice the right-click was gone...

Thanks to this post and xinput list I could figure out:

xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" button3 2

which gives me pen-click+tap = right click. [menu]. Now, before I could hover-click the pen and it would give me a right click. Wonder what happened to that...

---

### Post by Favux on 2009-08-03
Hi gigahz.

The hover click option is in wacomcpl.  In the Tool Buttons tab you change Side Switch Mode.

---

### Post by gigahz on 2009-08-03
> **Favux said:**
> The hover click option is in wacomcpl.
Well, I don't get anything in the list when I run wacomcpl. It says "Select device" but there are no items in the list. 

Please note, I didn't try to use wacomcpl before either. I didn't even know it was installed. Just happy the right-click thing works now. And after a quick guess, 


xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" TPCButton off

worked as a one-liner :) I stuck it into .xinitrc after the other line :D

thanks anyway for your quick response.

---

### Post by Favux on 2009-08-03
Hi gigahz,

Good.  Wacomcpl won't work unless:
```
xsetwacom list
```
returns linuxwacom names like stylus, eraser, etc.  You'd have to edit the .xinitrc it generates and change the names like you've been doing.  That file contains the xsetwacom commands to calibrate and configure things.  But you're saying you don't have an old .xinitrc.

---

### Post by lospo on 2009-11-05
excuse me, i'm not an expert, but i need a hand too :)
can you help with this tablet?

[http://ubuntuforums.org/showthread.php?t=1315438](http://ubuntuforums.org/showthread.php?t=1315438)

It's not a WACOM but a WALTOP and it is worked before the Karmic Koala distro upgrade.

---

