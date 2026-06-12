---
title: "multitouch on thinkpad x201?"
date: 2010-10-16
forum: Hardware
---

### Post by luisito on 2010-10-16
I have a Thinkpad x201. I thought that after Maverick 10.10 we would have multitouch support out of the box or quasi. I have just updated from 10.04 to 10.10 and everything works exactly the same. More precisely, the stylus, touchscreen and touchpad work, but without multitouch.

I installed utouch. I did some tests with gesturetest and I get nothing.

This is what I get when I run lsinput
```

/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event3
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43860
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_HOST
   vendor  : 0x17aa
   product : 0x5054
   version : 16641
   name    : "ThinkPad Extra Buttons"
   phys    : "thinkpad_acpi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_SW

/dev/input/event5
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x4816
   version : 9029
   name    : "Integrated Camera"
   phys    : "usb-0000:00:1a.0-1.6/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event6
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event7
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xa
   version : 0
   name    : "TPPS/2 IBM TrackPoint"
   phys    : "synaptics-pt/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_REL

```

This is what I get from xinput list
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```

And this is what I get from xinput list-props "Serial Wacom Tablet touch"
```

Device 'Serial Wacom Tablet touch':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (243):	0
	Device Accel Constant Deceleration (244):	1.000000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	10.000000
	Wacom Tablet Area (293):	0, 0, 2631, 1652
	Wacom Rotation (294):	0
	Wacom Serial IDs (296):	227, 0, 3, 0
	Wacom TwinView Resolution (297):	0, 0, 0, 0
	Wacom Display Options (298):	-1, 0, 1
	Wacom Screen Area (299):	0, 0, 1280, 800
	Wacom Proximity Threshold (300):	0
	Wacom Capacity (301):	-1
	Wacom Pressure Threshold (302):	27
	Wacom Sample and Suppress (303):	2, 4
	Wacom Enable Touch (304):	1
	Wacom Hover Click (305):	0
	Wacom Enable Touch Gesture (306):	1
	Wacom Touch Gesture Parameters (307):	50, 20, 250
	Wacom Tool Type (308):	"TOUCH" (310)
	Wacom Button Actions (309):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

Any idea if multitouch gestures on the screen can be activated or not?

---

### Post by Favux on 2010-10-16
Hi luisito,

I think the multitouch code is available in Maverick but not really active, except in an experimental way.  I believe it will be active in Natty.

If your X200t supports 2 finger touch (2FG) you can get 2 finger touch/gestures through the wacom driver xf86-input-wacom.  You may need to turn it on with a line in the 50-wacom.conf or using an xsetwacom command.

But remember, your wacom digitizer if it supports multitouch, only supports two fingers.

---

### Post by luisito on 2010-10-23
I don't think there is anything I did. I don't know if it was some update or what. But multi-touch is working on my Thinkpad X201 with Ubuntu 10.10 now.

---

### Post by irwand on 2010-10-23
I've been trying to get multi-touch working on x201. I've aptitude upgrade today, but mtdev-tools nor "gesturetest 0 0 0xffffffff" give me anything.

How do you test the multi-touch on x201? Nothing in lsinput mention anything about wacom touch. I'm confused.

---

### Post by Favux on 2010-10-23
Hi irwand,

It depends on what release of Ubuntu you are in.  The default xf86-input-wacom in Lucid, 0.10.5, doesn't support gestures.  You need to install a newer one.  The 0.10.8 in Maverick does.
```
xsetwacom set "Device name" Touch "on"
xsetwacom set "Device name" Gesture "on"
```
Where "Device name" is from 'xinput --list'.  Something like "Wacom serial tablet touch".

---

### Post by irwand on 2010-10-23
Thanks Favux,

I verified that both are on. I'm running 10.10 Maverick.
```
$ xsetwacom --get "Serial Wacom Tablet touch" touch
on
$ xsetwacom --get "Serial Wacom Tablet touch" gesture
on
```

What application supports multitouch right now to try it out?
Thanks man!

---

### Post by luisito on 2010-10-23
Gestures might be enabled already. You can try the zoom and scroll on the web browser, but the right click is the easiest to perform.

Put one finger on the screen first and the second later without releasing the first finger. The right click should be performed (usually giving you a popup menu) where your first finger is.

---

### Post by irwand on 2010-11-01
To my surprise when I used 2 fingers to zoom in/out in Firefox, it somewhat works.. albeit kinda klunky, since it has a long delay before Firefox does it. Oh well. I guess it works. :) Thanks guys!

---

### Post by noah++ on 2010-12-19
Same Ubuntu, same Thinkpad model,
```
**noahplusplus@x201:~$** xsetwa*** --get "Serial Wa*** Tablet touch" gesture
on
**noahplusplus@x201:~$** xsetwa*** --get "Serial Wa*** Tablet touch" touch
on
```but no multitouch function I can perceive. Touching the screen in Firefox just highlights some text near my finger, which refuses to be unhighlighted except by another touch (i.e. not by mouse). Can't scroll, can't zoom. Any idea what I'm missing?

(And, apropos of nothing, is every instance of c-o-m appearing as "***" for everyone else in this forum right now, too?)

---

### Post by Favux on 2010-12-19
Hi noah++,

Yep, everyone is seeing c o m replaced with ***.

I just added a new xsetwacom script to the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") on post #2 for X200t/X201t's.  I don't think the commands you are using are quite right.  You might want to check it out.

Hopefully I'll have some new stuff to add to the HOW TO in a few days if I get a chance to do some testing.

---

### Post by irwand on 2010-12-20
On Firefox, I use firefox grab and drag extension so I can scroll with my finger. It's kinda klunky and manual, not as automatic as it is on Windows. I also find on Linux the battery life on that laptop is pretty poor.. :( So I end up more using Windows.

---

### Post by noah++ on 2010-12-24
Thanks in part to your document, **Favux**, I realized that my multitouch interface was working as expected. Now I have been practicing the Linux variation on the multitouch gestures all week, but I still can't get reliable results. I think I just need to make a gesture of crossed fingers in hopes that multitouch development will progress quickly to the intuitive "just works" state it has on Windows now.

---

### Post by Favux on 2010-12-24
Hi noah++,

Sorry gestures aren't working as well as you'd like right now.  They come and go as more code is added to the X server driver.  So improvement might be a few commits away.  The MT code for the kernel has been accepted by linux-input so we should see it in the 2.6.37 kernel.

[SIZE="4"][COLOR="Blue"]Attention XT200t & XT201t tablet pc Users[/COLOR][/SIZE]

We have python tray applet that gives automatic rotation for HP and Dell tablet pc's.  I read the other day that Lenovo started including a wmi interface beginning with the X200t.  If so then we may be able to add your Thinkpads to Magick Rotation.

I need to know if you have an oem-wmi kernel module on your systems.  Probably called something like lenovo_wmi (ibm_wmi?).  So please look through lsmod and see if you see anything like that.  Enter:
```
lsmod
```
in a terminal.  If you do it is possible your swivel hinge switch is sending a signal through the wmi to Lenovo Hotkeys and we can intercept it.

If you do have the module a few simple tests will tell us if we can get it working through Magick.  Magick also offers other features like toggling touch on and off and letting you execute shell commands before and after you rotate.  To increase panel size when rotated to make the panels more touch friendly, or to show and hide CellWriter for example.

---

### Post by noah++ on 2010-12-25
No such driver in **lsmod **for my X201 tablet. Should I try to build it and use it?

---

### Post by irwand on 2010-12-26
AFAIK, the swivel hinge switch on x201t sends acpi signal. More specifically:

event=ibm/hotkey HKEY 00000080 00005009 -- when switching to tablet mode

event=ibm/hotkey HKEY 00000080 0000500a -- when switching to laptop mode

Does that help any? I currently control auto rotation using acpi-events. It works ok, but would definitely be interested in better ways to do it.

---

### Post by Favux on 2010-12-26
Hi noah++ and irwand,

Thank you for responding.

Right, I knew the X60t & X61t's were using thinkpad_acpi.c in Linux/drivers/platform/x86/ (or Linux/drivers/misc/ in older kernels).  A quick scan through it only showed the X60t & X61t mentioned.  Given what I read I was hoping maybe a lenovo-wmi had been added for the X200t and X201t.

But looking at the 2.6.36.2 kernel doesn't show any sign of it.  Oh well.  So it looks like that project was dropped or never ported to linux.  Unless by some chance noah++ you're saying you have source for it available?

So it appears the X200's are using the same code in the thinkpad_acpi.c:
```
	/* User-interface events */
	TP_HKEY_EV_LID_CLOSE		= 0x5001, /* laptop lid closed */
	TP_HKEY_EV_LID_OPEN		= 0x5002, /* laptop lid opened */
	TP_HKEY_EV_TABLET_TABLET	= 0x5009, /* tablet swivel up */
	TP_HKEY_EV_TABLET_NOTEBOOK	= 0x500a, /* tablet swivel down */
	TP_HKEY_EV_PEN_INSERTED		= 0x500b, /* tablet pen inserted */
	TP_HKEY_EV_PEN_REMOVED		= 0x500c, /* tablet pen removed */
	TP_HKEY_EV_BRGHT_CHANGED	= 0x5010, /* backlight control event */
```
```
static void tpacpi_input_send_tabletsw(void)
{
	int state;

	if (tp_features.hotkey_tablet &&
	    !hotkey_get_tablet_mode(&state)) {
		mutex_lock(&tpacpi_inputdev_send_mutex);

		input_report_switch(tpacpi_inputdev,
				    SW_TABLET_MODE, !!state);
		input_sync(tpacpi_inputdev);

		mutex_unlock(&tpacpi_inputdev_send_mutex);
	}
}
```
We're getting close to bringing out Magick 1.3.  It adds two new HP models, and Dell tablet pc's.  So the Thinkpads won't make it in, since it looks like we need at least a new acpi module.  And we were thinking of adding a calibration feature next.

But we'll get to them soon with luck.  And hopefully I can anticipate some testers?

---

### Post by noah++ on 2010-12-26
> **Favux said:**
> But looking at the 2.6.36.2 kernel doesn't show any sign of it.  Oh well.  So it looks like that project was dropped or never ported to linux.  Unless by some chance noah++ you're saying you have source for it available?
:) Nope. I was thinking the module was available in Ubuntu's kernel sources but just not built by default.
> But we'll get to them soon with luck.  And hopefully I can anticipate some testers?
I am often pretty busy with school outside of these term breaks, but you are welcome to private message me and I will try to participate. I will stay subscribed to this thread, too.

---

### Post by irwand on 2010-12-27
> **Favux said:**
> But we'll get to them soon with luck.  And hopefully I can anticipate some testers?

Let us know what you need.. I don't know much about all the things you just said.. :)

---

### Post by linuxd00 on 2010-12-31
X201 tablet owner here.

i can test whatever you want me to :D

---

### Post by supr0 on 2011-01-14
Hi Favux, another X201 user here, I'll be happy to test whatever you need. I really appreciate you helping out.

---

### Post by Favux on 2011-01-16
Hi everyone,

Can someone tell me if you have a directory called "/sys/devices/platform/thinkpad_acpi"?  And in it is there a file called "hotkey_tablet_mode"?  If so could you tell me what the value is when in laptop and what it changes to in tablet?

---

### Post by supr0 on 2011-01-16
> **Favux said:**
> Hi everyone,

Can someone tell me if you have a directory called "/sys/devices/platform/thinkpad_acpi"?  And in it is there a file called "hotkey_tablet_mode"?  If so could you tell me what the value is when in laptop and what it changes to in tablet?

Hi Favux,

Yes there is a file called  "hotkey_tablet_mode" in  "/sys/devices/platform/thinkpad_acpi"

This file contains 0 in normal mode and 1 when the X201 is in tablet mode.

Hope this helps and let me know if you need any other diagnostics!

supr0

---

### Post by Favux on 2011-01-16
Thanks supr0,

Just doodling for now, trying to figure out where things are.

---

### Post by linuxd00 on 2011-01-17
i also can confirm the existence and behavior of that file

```


:/sys/devices/platform/thinkpad_acpi$ ls -la

total 0
drwxr-xr-x  7 root root    0 2011-01-17 13:09 .
drwxr-xr-x 14 root root    0 2011-01-17 14:09 ..
-rw-r--r--  1 root root 4096 2011-01-17 13:38 bluetooth_enable
--w-------  1 root root 4096 2011-01-17 13:38 cmos_command
lrwxrwxrwx  1 root root    0 2011-01-17 13:09 driver -> ../../../bus/platform/drivers/thinkpad_acpi
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_all_mask
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_bios_enabled
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_bios_mask
-rw-r--r--  1 root root 4096 2011-01-17 13:38 hotkey_enable
-rw-r--r--  1 root root 4096 2011-01-17 13:38 hotkey_mask
-rw-r--r--  1 root root 4096 2011-01-17 13:38 hotkey_poll_freq
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_radio_sw
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_recommended_mask
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_report_mode
-rw-r--r--  1 root root 4096 2011-01-17 13:38 hotkey_source_mask
-r--r--r--  1 root root 4096 2011-01-17 13:38 hotkey_tablet_mode
drwxr-xr-x  3 root root    0 2011-01-17 13:09 input
drwxr-xr-x  6 root root    0 2011-01-17 13:09 leds
-r--r--r--  1 root root 4096 2011-01-17 13:38 modalias
drwxr-xr-x  2 root root    0 2011-01-17 13:38 power
drwxr-xr-x  3 root root    0 2011-01-17 13:09 rfkill
drwxr-xr-x  3 root root    0 2011-01-17 13:09 sound
lrwxrwxrwx  1 root root    0 2011-01-17 13:09 subsystem -> ../../../bus/platform
-rw-r--r--  1 root root 4096 2011-01-17 13:09 uevent
-r--r--r--  1 root root 4096 2011-01-17 13:38 wakeup_hotunplug_complete
-r--r--r--  1 root root 4096 2011-01-17 13:38 wakeup_reason

```

---

### Post by linuxd00 on 2011-01-17
also the hotkey_tablet_mode file only turns to 1 when the pc is in tablet mode (when the display is flatened AND rotated) only flatening the display or only rotating it keeps the value at 0.

this is interesting since it seems that there are two separate sensors for rotating and flattening

---

### Post by Favux on 2011-01-17
Hi supr0, linuxd00 & everyone,

Not sure where or what the physical switch for tablet is.  In the swivel hinge, closure clapse, magnets?

Could someone show me the output of the following:
```
ls -l /dev/input/by-id

ls -l /dev/input/by-path
```
The following may require install of input-utils:
```
sudo apt-get install input-utils
```
We're looking for the output of:
```
sudo lsinput
```
to verify something posted earlier.

---

### Post by supr0 on 2011-01-17
> **Favux said:**
> Hi supr0, linuxd00 & everyone,

Not sure where or what the physical switch for tablet is.  In the swivel hinge, closure clapse, magnets?

Could someone show me the output of the following:
```
ls -l /dev/input/by-id

ls -l /dev/input/by-path
```
The following may require install of input-utils:
```
sudo apt-get install input-utils
```
We're looking for the output of:
```
sudo lsinput
```
to verify something posted earlier.

Hi Favux,

Here's the output for the commands you requested:


```

$ ls -l /dev/input/by-id
total 0
lrwxrwxrwx 1 root root 10 2011-01-17 21:24 usb-17ef_Lenovo_Ultraslim_Wireless_Keyboard___Mouse-event-kbd -> ../event10
lrwxrwxrwx 1 root root 10 2011-01-17 21:24 usb-17ef_Lenovo_Ultraslim_Wireless_Keyboard___Mouse-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 usb-17ef_Lenovo_Ultraslim_Wireless_Keyboard___Mouse-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2011-01-17 18:49 usb-Chicony_Electronics_Co.__Ltd._Integrated_Camera-event-if00 -> ../event4

```

```

$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 10 2011-01-17 21:24 pci-0000:00:1a.0-usb-0:1.5.1:1.0-event-kbd -> ../event10
lrwxrwxrwx 1 root root 10 2011-01-17 21:24 pci-0000:00:1a.0-usb-0:1.5.1:1.1-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 pci-0000:00:1a.0-usb-0:1.5.1:1.1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2011-01-17 18:49 pci-0000:00:1a.0-usb-0:1.6:1.0-event -> ../event4
lrwxrwxrwx 1 root root  9 2011-01-17 18:49 platform-i8042-serio-0-event-kbd -> ../event3
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-1-event-mouse -> ../event6
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-1-mouse -> ../mouse0
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-4-event-mouse -> ../event8
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-4-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-5-event-mouse -> ../event9
lrwxrwxrwx 1 root root  9 2011-01-17 21:24 platform-i8042-serio-5-mouse -> ../mouse2
lrwxrwxrwx 1 root root  9 2011-01-17 18:49 platform-thinkpad_acpi-event -> ../event5


```

```

$ sudo lsinput
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event3
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43860
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x4816
   version : 9029
   name    : "Integrated Camera"
   phys    : "usb-0000:00:1a.0-1.6/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x17aa
   product : 0x5054
   version : 16641
   name    : "ThinkPad Extra Buttons"
   phys    : "thinkpad_acpi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_SW

/dev/input/event6
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event7
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xa
   version : 0
   name    : "TPPS/2 IBM TrackPoint"
   phys    : "synaptics-pt/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event9
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xa
   version : 0
   name    : "TPPS/2 IBM TrackPoint"
   phys    : "synaptics-pt/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x600d
   version : 273
   name    : "Lenovo Ultraslim Wireless Keyboa"
   phys    : "usb-0000:00:1a.0-1.5.1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event11
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x600d
   version : 273
   name    : "Lenovo Ultraslim Wireless Keyboa"
   phys    : "usb-0000:00:1a.0-1.5.1/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC

```

---

### Post by Favux on 2011-01-17
Hi supr0,

Thanks.  Looking good.  One more:
```
ls -l /dev/input/
```

---

### Post by supr0 on 2011-01-17
> **Favux said:**
> Hi supr0,

Thanks.  Looking good.  One more:
```
ls -l /dev/input/
```

Cheers Favux,

I should mention I'm using a usb wireless mouse in case it is confusing why there are 3 mice below. I'm also using an UltraBase (a kind of dock for the thinkpad).

I can remove these before I do tests if its helpful.

Here's the output for 'ls -l /dev/input/'

```

$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root    120 2011-01-17 21:56 by-id
drwxr-xr-x 2 root root    240 2011-01-17 21:56 by-path
crw-r----- 1 root root 13, 64 2011-01-17 21:56 event0
crw-r----- 1 root root 13, 65 2011-01-17 21:56 event1
crw-r----- 1 root root 13, 74 2011-01-17 21:56 event10
crw-r----- 1 root root 13, 66 2011-01-17 21:56 event2
crw-r----- 1 root root 13, 67 2011-01-17 21:56 event3
crw-r----- 1 root root 13, 68 2011-01-17 21:56 event4
crw-r----- 1 root root 13, 69 2011-01-17 21:56 event5
crw-r----- 1 root root 13, 70 2011-01-17 21:56 event6
crw-r----- 1 root root 13, 71 2011-01-17 21:56 event7
crw-r----- 1 root root 13, 72 2011-01-17 21:56 event8
crw-r----- 1 root root 13, 73 2011-01-17 21:56 event9
crw-r----- 1 root root 13, 63 2011-01-17 21:56 mice
crw-r----- 1 root root 13, 32 2011-01-17 21:56 mouse0
crw-r----- 1 root root 13, 33 2011-01-17 21:56 mouse1
crw-r----- 1 root root 13, 34 2011-01-17 21:56 mouse2

```

---

### Post by supr0 on 2011-01-17
> **Favux said:**
> Hi supr0,

Thanks.  Looking good.  One more:
```
ls -l /dev/input/
```

Cheers Favux,

I should mention I'm using a usb wireless mouse in case it is confusing why there are 3 mice below. I'm also using an UltraBase (a kind of dock for the thinkpad).

I can remove these before I do tests if its helpful.

Here's the output for 'ls -l /dev/input/'

```

$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root    120 2011-01-17 21:56 by-id
drwxr-xr-x 2 root root    240 2011-01-17 21:56 by-path
crw-r----- 1 root root 13, 64 2011-01-17 21:56 event0
crw-r----- 1 root root 13, 65 2011-01-17 21:56 event1
crw-r----- 1 root root 13, 74 2011-01-17 21:56 event10
crw-r----- 1 root root 13, 66 2011-01-17 21:56 event2
crw-r----- 1 root root 13, 67 2011-01-17 21:56 event3
crw-r----- 1 root root 13, 68 2011-01-17 21:56 event4
crw-r----- 1 root root 13, 69 2011-01-17 21:56 event5
crw-r----- 1 root root 13, 70 2011-01-17 21:56 event6
crw-r----- 1 root root 13, 71 2011-01-17 21:56 event7
crw-r----- 1 root root 13, 72 2011-01-17 21:56 event8
crw-r----- 1 root root 13, 73 2011-01-17 21:56 event9
crw-r----- 1 root root 13, 63 2011-01-17 21:56 mice
crw-r----- 1 root root 13, 32 2011-01-17 21:56 mouse0
crw-r----- 1 root root 13, 33 2011-01-17 21:56 mouse1
crw-r----- 1 root root 13, 34 2011-01-17 21:56 mouse2

```

---

### Post by Favux on 2011-01-17
Let's see if we can work with everything in place.

I think we know where the hinge switch signals are coming from now.

What we want to do next is see if we can construct a symlink/device node that we can read.  And then read it.

So download the attached file and place it in /etc/udev/rules.d calling it '62-magick.rules'.  I don't think this will break anything but just in case be prepared to remove the file from the command line and having a live CD handy wouldn't be a bad idea.  Reboot.  You should now see the symlink in:
```
ls -l /dev/input/
```
It will be called 'lenovo-acpi'.  Go ahead and post the output.

If you see it let's read it and see what the values are.  First use evtest:
```
sudo evtest /dev/input/lenovo-acpi
```
Rotate your screen to tablet and then back to laptop and post the results.  Then do the same thing with:
```
sudo xxd /dev/input/lenovo-acpi
```
Three lines should appear after you rotate to tablet and three more when you go back to laptop.  Post all 6.

---

### Post by linuxd00 on 2011-01-19
i'd test that... but im really afraid of messing my system... 

woud you explain what it does and how might i repair my system if it breaks?

---

### Post by Favux on 2011-01-19
Hi linuxd00,

Sorry, I should have explained more.  Basically adding symlinks is no big deal and people do it all the time for convenience. 

The "/etc/udev/rules.d" directory is where they want you to put custom rules.  If you use the system location "/lib/udev/rules.d/" your custom rule can be overwritten by updates.  The directory should already be there with files in it.

Then you just open the downloaded file in gedit.  Then create a new empty file in xorg.conf.d with:
```
gksudo gedit /etc/udev/rules.conf.d/62-magick.rules
```
and copy & paste the entire contents of the gedit file into the empty root gedit file and Save.  Then reboot.

If this breaks X or something, and it shouldn't, just remove the offending file when you get to the command line during boot with:
```
sudo rm /etc/udev/rules.d/62-magick.rules
```

Hopefully this is a more complete and understandable explanation.

---

### Post by forti on 2011-01-19
Hi, 
there are some more x201 tablet testers.
I got the following output:
```
$ ls -l /dev/input/
drwxr-xr-x 2 root root    120 2011-01-19 20:43 by-id
drwxr-xr-x 2 root root    240 2011-01-19 20:43 by-path
crw-r----- 1 root root 13, 64 2011-01-19 19:29 event0
crw-r----- 1 root root 13, 65 2011-01-19 19:29 event1
crw-r----- 1 root root 13, 74 2011-01-19 19:29 event10
crw-r----- 1 root root 13, 66 2011-01-19 19:29 event2
crw-r----- 1 root root 13, 67 2011-01-19 19:29 event3
crw-r----- 1 root root 13, 68 2011-01-19 19:29 event4
crw-r----- 1 root root 13, 69 2011-01-19 19:29 event5
crw-r----- 1 root root 13, 70 2011-01-19 19:29 event6
crw-r----- 1 root root 13, 71 2011-01-19 20:43 event7
crw-r----- 1 root root 13, 72 2011-01-19 19:29 event8
crw-r--r-- 1 root root 13, 73 2011-01-19 19:29 event9
lrwxrwxrwx 1 root root      6 2011-01-19 19:29 lenovo-acpi -> event9
crw-r----- 1 root root 13, 63 2011-01-19 19:29 mice
crw-r----- 1 root root 13, 32 2011-01-19 19:29 mouse0
crw-r----- 1 root root 13, 33 2011-01-19 19:29 mouse1
crw-r----- 1 root root 13, 34 2011-01-19 19:29 mouse2
``````
$ sudo evtest /dev/input/lenovo-acpi 
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Coffee)
    Event code 192 (F22)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (?)
    Event code 228 (?)
    Event code 236 (?)
    Event code 238 (?)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (?)
    Event code 471 (?)
    Event code 475 (?)
    Event code 476 (?)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (?)
    Event code 1 (?)
    Event code 3 (?)
Testing ... (interrupt to exit)
Event: time 1295467698.172883, type 5 (?), code 1 (?), value 1
Event: time 1295467698.172887, -------------- Report Sync ------------
Event: time 1295467705.190841, type 5 (?), code 1 (?), value 0
Event: time 1295467705.190844, -------------- Report Sync ------------
``````
sudo xxd /dev/input/lenovo-acpi
0000000: 0345 374d 0000 0000 f9a0 0e00 0000 0000  .E7M............
0000010: 0500 0100 0100 0000 0345 374d 0000 0000  .........E7M....
0000020: fca0 0e00 0000 0000 0000 0000 0000 0000  ................
0000030: 0b45 374d 0000 0000 a3d3 0d00 0000 0000  .E7M............
0000040: 0500 0100 0000 0000 0b45 374d 0000 0000  .........E7M....
0000050: a6d3 0d00 0000 0000 0000 0000 0000 0000  ................
```

Thanks for your work on this stuff!

---

### Post by forti on 2011-01-19
Hi, 
there are some more x201 tablet testers.
I got the following output:
```
$ ls -l /dev/input/
drwxr-xr-x 2 root root    120 2011-01-19 20:43 by-id
drwxr-xr-x 2 root root    240 2011-01-19 20:43 by-path
crw-r----- 1 root root 13, 64 2011-01-19 19:29 event0
crw-r----- 1 root root 13, 65 2011-01-19 19:29 event1
crw-r----- 1 root root 13, 74 2011-01-19 19:29 event10
crw-r----- 1 root root 13, 66 2011-01-19 19:29 event2
crw-r----- 1 root root 13, 67 2011-01-19 19:29 event3
crw-r----- 1 root root 13, 68 2011-01-19 19:29 event4
crw-r----- 1 root root 13, 69 2011-01-19 19:29 event5
crw-r----- 1 root root 13, 70 2011-01-19 19:29 event6
crw-r----- 1 root root 13, 71 2011-01-19 20:43 event7
crw-r----- 1 root root 13, 72 2011-01-19 19:29 event8
crw-r--r-- 1 root root 13, 73 2011-01-19 19:29 event9
lrwxrwxrwx 1 root root      6 2011-01-19 19:29 lenovo-acpi -> event9
crw-r----- 1 root root 13, 63 2011-01-19 19:29 mice
crw-r----- 1 root root 13, 32 2011-01-19 19:29 mouse0
crw-r----- 1 root root 13, 33 2011-01-19 19:29 mouse1
crw-r----- 1 root root 13, 34 2011-01-19 19:29 mouse2
``````
$ sudo evtest /dev/input/lenovo-acpi 
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Coffee)
    Event code 192 (F22)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (?)
    Event code 228 (?)
    Event code 236 (?)
    Event code 238 (?)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (?)
    Event code 471 (?)
    Event code 475 (?)
    Event code 476 (?)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (?)
    Event code 1 (?)
    Event code 3 (?)
Testing ... (interrupt to exit)
Event: time 1295467698.172883, type 5 (?), code 1 (?), value 1
Event: time 1295467698.172887, -------------- Report Sync ------------
Event: time 1295467705.190841, type 5 (?), code 1 (?), value 0
Event: time 1295467705.190844, -------------- Report Sync ------------
``````
sudo xxd /dev/input/lenovo-acpi
0000000: 0345 374d 0000 0000 f9a0 0e00 0000 0000  .E7M............
0000010: 0500 0100 0100 0000 0345 374d 0000 0000  .........E7M....
0000020: fca0 0e00 0000 0000 0000 0000 0000 0000  ................
0000030: 0b45 374d 0000 0000 a3d3 0d00 0000 0000  .E7M............
0000040: 0500 0100 0000 0000 0b45 374d 0000 0000  .........E7M....
0000050: a6d3 0d00 0000 0000 0000 0000 0000 0000  ................
```Thanks for your work on this stuff!

---

### Post by forti on 2011-01-19
Hi, 
there are some more x201 tablet testers.
I got the following output:
```
$ ls -l /dev/input/
drwxr-xr-x 2 root root    120 2011-01-19 20:43 by-id
drwxr-xr-x 2 root root    240 2011-01-19 20:43 by-path
crw-r----- 1 root root 13, 64 2011-01-19 19:29 event0
crw-r----- 1 root root 13, 65 2011-01-19 19:29 event1
crw-r----- 1 root root 13, 74 2011-01-19 19:29 event10
crw-r----- 1 root root 13, 66 2011-01-19 19:29 event2
crw-r----- 1 root root 13, 67 2011-01-19 19:29 event3
crw-r----- 1 root root 13, 68 2011-01-19 19:29 event4
crw-r----- 1 root root 13, 69 2011-01-19 19:29 event5
crw-r----- 1 root root 13, 70 2011-01-19 19:29 event6
crw-r----- 1 root root 13, 71 2011-01-19 20:43 event7
crw-r----- 1 root root 13, 72 2011-01-19 19:29 event8
crw-r--r-- 1 root root 13, 73 2011-01-19 19:29 event9
lrwxrwxrwx 1 root root      6 2011-01-19 19:29 lenovo-acpi -> event9
crw-r----- 1 root root 13, 63 2011-01-19 19:29 mice
crw-r----- 1 root root 13, 32 2011-01-19 19:29 mouse0
crw-r----- 1 root root 13, 33 2011-01-19 19:29 mouse1
crw-r----- 1 root root 13, 34 2011-01-19 19:29 mouse2
``````
$ sudo evtest /dev/input/lenovo-acpi 
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Coffee)
    Event code 192 (F22)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (?)
    Event code 228 (?)
    Event code 236 (?)
    Event code 238 (?)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (?)
    Event code 471 (?)
    Event code 475 (?)
    Event code 476 (?)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (?)
    Event code 1 (?)
    Event code 3 (?)
Testing ... (interrupt to exit)
Event: time 1295467698.172883, type 5 (?), code 1 (?), value 1
Event: time 1295467698.172887, -------------- Report Sync ------------
Event: time 1295467705.190841, type 5 (?), code 1 (?), value 0
Event: time 1295467705.190844, -------------- Report Sync ------------
``````
sudo xxd /dev/input/lenovo-acpi
0000000: 0345 374d 0000 0000 f9a0 0e00 0000 0000  .E7M............
0000010: 0500 0100 0100 0000 0345 374d 0000 0000  .........E7M....
0000020: fca0 0e00 0000 0000 0000 0000 0000 0000  ................
0000030: 0b45 374d 0000 0000 a3d3 0d00 0000 0000  .E7M............
0000040: 0500 0100 0000 0000 0b45 374d 0000 0000  .........E7M....
0000050: a6d3 0d00 0000 0000 0000 0000 0000 0000  ................
```Thanks for your work on this stuff!

---

### Post by supr0 on 2011-01-19
Hey Favux,

Here's the results for those commands:

```

$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root     60 2011-01-19 20:27 by-id
drwxr-xr-x 2 root root    180 2011-01-19 20:27 by-path
crw-r----- 1 root root 13, 64 2011-01-19 20:27 event0
crw-r----- 1 root root 13, 65 2011-01-19 20:27 event1
crw-r----- 1 root root 13, 66 2011-01-19 20:27 event2
crw-r----- 1 root root 13, 67 2011-01-19 20:27 event3
crw-r----- 1 root root 13, 68 2011-01-19 20:27 event4
crw-r--r-- 1 root root 13, 69 2011-01-19 20:27 event5
crw-r----- 1 root root 13, 70 2011-01-19 20:27 event6
crw-r----- 1 root root 13, 71 2011-01-19 20:27 event7
crw-r----- 1 root root 13, 72 2011-01-19 20:27 event8
lrwxrwxrwx 1 root root      6 2011-01-19 20:27 lenovo-acpi -> event5
crw-r----- 1 root root 13, 63 2011-01-19 20:27 mice
crw-r----- 1 root root 13, 32 2011-01-19 20:27 mouse0
crw-r----- 1 root root 13, 33 2011-01-19 20:27 mouse1

```

```

$ sudo evtest /dev/input/lenovo-acpi
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Coffee)
    Event code 192 (F22)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (?)
    Event code 228 (?)
    Event code 236 (?)
    Event code 238 (?)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (?)
    Event code 471 (?)
    Event code 475 (?)
    Event code 476 (?)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (?)
    Event code 1 (?)
    Event code 3 (?)
Testing ... (interrupt to exit)
Event: time 1295469147.284853, type 5 (?), code 1 (?), value 1
Event: time 1295469147.284857, -------------- Report Sync ------------
Event: time 1295469171.323958, type 5 (?), code 1 (?), value 0
Event: time 1295469171.323962, -------------- Report Sync ------------
^C

```

```

$ sudo xxd /dev/input/lenovo-acpi
0000000: db4a 374d 0000 0000 e9d8 0600 0000 0000  .J7M............
0000010: 0500 0100 0100 0000 db4a 374d 0000 0000  .........J7M....
0000020: edd8 0600 0000 0000 0000 0000 0000 0000  ................
0000030: de4a 374d 0000 0000 aa40 0e00 0000 0000  .J7M.....@......
0000040: 0500 0100 0000 0000 de4a 374d 0000 0000  .........J7M....
0000050: ad40 0e00 0000 0000 0000 0000 0000 0000  .@..............
^C

```

---

### Post by supr0 on 2011-01-19
Hey Favux,

Here's the results for those commands:

```

$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root     60 2011-01-19 20:27 by-id
drwxr-xr-x 2 root root    180 2011-01-19 20:27 by-path
crw-r----- 1 root root 13, 64 2011-01-19 20:27 event0
crw-r----- 1 root root 13, 65 2011-01-19 20:27 event1
crw-r----- 1 root root 13, 66 2011-01-19 20:27 event2
crw-r----- 1 root root 13, 67 2011-01-19 20:27 event3
crw-r----- 1 root root 13, 68 2011-01-19 20:27 event4
crw-r--r-- 1 root root 13, 69 2011-01-19 20:27 event5
crw-r----- 1 root root 13, 70 2011-01-19 20:27 event6
crw-r----- 1 root root 13, 71 2011-01-19 20:27 event7
crw-r----- 1 root root 13, 72 2011-01-19 20:27 event8
lrwxrwxrwx 1 root root      6 2011-01-19 20:27 lenovo-acpi -> event5
crw-r----- 1 root root 13, 63 2011-01-19 20:27 mice
crw-r----- 1 root root 13, 32 2011-01-19 20:27 mouse0
crw-r----- 1 root root 13, 33 2011-01-19 20:27 mouse1

```

```

$ sudo evtest /dev/input/lenovo-acpi
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Coffee)
    Event code 192 (F22)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (?)
    Event code 228 (?)
    Event code 236 (?)
    Event code 238 (?)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (?)
    Event code 471 (?)
    Event code 475 (?)
    Event code 476 (?)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (?)
    Event code 1 (?)
    Event code 3 (?)
Testing ... (interrupt to exit)
Event: time 1295469147.284853, type 5 (?), code 1 (?), value 1
Event: time 1295469147.284857, -------------- Report Sync ------------
Event: time 1295469171.323958, type 5 (?), code 1 (?), value 0
Event: time 1295469171.323962, -------------- Report Sync ------------
^C

```

```

$ sudo xxd /dev/input/lenovo-acpi
0000000: db4a 374d 0000 0000 e9d8 0600 0000 0000  .J7M............
0000010: 0500 0100 0100 0000 db4a 374d 0000 0000  .........J7M....
0000020: edd8 0600 0000 0000 0000 0000 0000 0000  ................
0000030: de4a 374d 0000 0000 aa40 0e00 0000 0000  .J7M.....@......
0000040: 0500 0100 0000 0000 de4a 374d 0000 0000  .........J7M....
0000050: ad40 0e00 0000 0000 0000 0000 0000 0000  .@..............
^C

```

---

### Post by Favux on 2011-01-19
Awesome forti and supr0 and everyone,,

Don't worry about the double post.  The server gave me a quintuple post the other day.  A new record!  The server has been acting funny for a few days.  You just have to sit and wait when you see the "waiting" stuff and not try to resend.

I think we have enough to work with.  I'd appreciate some more confirmation.  It would also be nice to have other ThinkPad tablet results.

Give me a little time to add X200t code to Magick.  I'll use our latest testing code in the Unstable branch, v. 1.3.  Hopefully the problem with the server won't stop me from posting.

---

### Post by Favux on 2011-01-19
Hi everyone,

It looks like I didn't follow my own advice and ended up with a double post.  But I did wait for the Server Error.  Looks like it still goes through after that with about a 10 minute lag time.  Huh.

And again I'd love results from other ThinkPad models.

This is the code from our unstable branch.  The upcoming version 1.3.

Magick Rotation is at:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Download the attached file and extract it.  Go into the magick-rotation folder and double click on the magick-rotation file and let the Installer go to work.  You shouldn't have to reboot to test it if you already installed the 62-magick.rules file.

Right click on the Magick Rotation tray icon if it appears and chose Quit.  Open a terminal and navigate into the magick-rotation folder.  Then run this command:
```
./magick-rotation
```
The tray icon should appear.  Go ahead and rotate the screen to tablet and back.  Right click on the tray icon and chose Quit.  Let me know if the screen orientation changed.  You should have output in the terminal.  Go ahead and post it.

Edit:  Fixed hingevalue_toggle issue in config.py.

---

### Post by forti on 2011-01-19
sorry about the triple post, i got some 502 Proxy Error when posting, refreshed the thread and the post wasnt there, so i tried it again.

> **Favux said:**
> 
Download the attached file and extract it.  Go into the magick-rotation folder and double click on the magick-rotation file and let the Installer go to work.  You shouldn't have to reboot to test it if you already installed the 62-magick.rules file.

Right click on the Magick Rotation tray icon if it appears and chose Quit.  Open a terminal and navigate into the magick-rotation folder.  Then run this command:
```
./magick-rotation
```The tray icon should appear.  Go ahead and rotate the screen to tablet and back.  Right click on the tray icon and chose Quit.  Let me know if the screen orientation changed.  You should have output in the terminal.  Go ahead and post it.
I unpacked it but running magick-rotation didnt do anything, running it in the console gave me the following error
```
./magick-rotation
Traceback (most recent call last):
  File "./magick-rotation", line 236, in <module>
    magick = engine()
  File "./magick-rotation", line 94, in __init__
    self.win = magick_gui()
  File "/home/forti/magick-rotation/gui_gtk.py", line 277, in __init__
    self.load_data()
  File "/home/forti/magick-rotation/gui_gtk.py", line 286, in load_data
    data = cfg.load_data()
  File "/home/forti/magick-rotation/config.py", line 21, in load_data
    return self.load_old_data()
  File "/home/forti/magick-rotation/config.py", line 53, in load_old_data
    bool(hingevalue_toggle), version]
NameError: global name 'hingevalue_toggle' is not defined
```So i added it in the definition of the default values (config.py line 36) 
```
hingevalue_toggle = False
```then running it again in the terminal gave the green arrow in the tray and rotating the tablet worked fine! The screen was rotated as expected and cellwriter was opened. I will do some more testing tomorrow.

output in the terminal is as follows:
```
type 7657  code 4d37  value 0
type 25bb  code 8  value 0
type 5  code 1  value 1
tablet
type 7657  code 4d37  value 0
type 25bf  code 8  value 0
type 0  code 0  value 0
type 765c  code 4d37  value 0
type 2beb  code b  value 0
type 5  code 1  value 0
laptop
type 765c  code 4d37  value 0
type 2bef  code b  value 0
type 0  code 0  value 0
```

---

### Post by Favux on 2011-01-19
Outstanding forti!!!  Nice work.  Output looks good.

We have rotation on the ThinkPad X201t!  Cool!

OK, to avoid what forti ran into I'll fix and repost Magick if needed.

Love some more confirmation.

Thank you very much testers.

---

### Post by supr0 on 2011-01-19
Hi Favux,

I also added the line hingevalue_toggle = False to config.py and everything works a charm! Thanks.

My output from magic-rotation is:

```

type 83e9  code 4d37  value 0
type a70c  code 6  value 0
type 5  code 1  value 1
tablet
type 83e9  code 4d37  value 0
type a713  code 6  value 0
type 0  code 0  value 0
cellwriter: Failed to open user's profile '/home/aja/.cellwriter/profile' for reading: No such file or directory
type 8409  code 4d37  value 0
type 9ffe  code 2  value 0
type 5  code 1  value 0
laptop
type 8409  code 4d37  value 0
type a004  code 2  value 0
type 0  code 0  value 0

```

Thanks a million!

---

### Post by Favux on 2011-01-19
Great supr0!

Thank you very much for the confirmation.

OK, I'll fix the hingevalue_toggle issue and repost the magick-rotation tar in post #37.  Misled myself when I added that because I didn't start with a clean system.


Edit:  Updated the Magick Rotation site:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)
The unstable branch with the testing version 1.3 now supports ThinkPads.  You can download it as a Bazaar branch - see the FAQs.

---

### Post by linuxd00 on 2011-01-20
just downloaded the 1.3 bazaar version and ran it.

It doesnt work on my X201:

Things i expected to work different but might be only my expectation:

basically nothing works apart from turning "touch" on and off. It will turn off touch and pen though... i was kind of expecting only to turn off "finger touch".
i also had already cellwriter runing in the taskbar...  but afer going into tablet mode it didnt bring it up.

things that obviously shouldt work that way:



when going into tablet mode it doesnt rotate at all and as soon as its active(as soon as you run the program) it will use 35% of my core i7 2,13Ghz (2 cores with hyperthreading).

2 Cores run constantly at 60% and the other two at around 13~20, gnome monitor reports a rough overall total of 35 for the magick rotation process. monitor shows that its only magick that is using the cpu.

---

### Post by Favux on 2011-01-20
Hi linuxd00,

Oops!  That shouldn't be happening.

Could you try the version on post #37 and see if that works?  Hopefully I didn't break anything in the updates and that will help tell me if I did so I can fix it.

---

### Post by Favux on 2011-01-20
A quick look at the diffs on the changed files isn't showing me anything wrong.

---

### Post by supr0 on 2011-01-21
> **linuxd00 said:**
> just downloaded the 1.3 bazaar version and ran it.

It doesnt work on my X201:

Things i expected to work different but might be only my expectation:

basically nothing works apart from turning "touch" on and off. It will turn off touch and pen though... i was kind of expecting only to turn off "finger touch".
i also had already cellwriter runing in the taskbar...  but afer going into tablet mode it didnt bring it up.

things that obviously shouldt work that way:



when going into tablet mode it doesnt rotate at all and as soon as its active(as soon as you run the program) it will use 35% of my core i7 2,13Ghz (2 cores with hyperthreading).

2 Cores run constantly at 60% and the other two at around 13~20, gnome monitor reports a rough overall total of 35 for the magick rotation process. monitor shows that its only magick that is using the cpu.

First I just want to say another big thanks to Favux, I don't know what inspired you to help us out but I'm very grateful.

>>linuxd: I know this sounds very obvious but did you restart after install? And give the attachment in this thread a go, that's the one I used and it works perfectly after a reboot.

The toggle for turning off touch should definitely be to toggle multitouch on and off. It's hard to write on the screen with the pen while multitouch is on as if you touch the screen with your hand it will mark it.

---

### Post by forti on 2011-01-21
I used the post-version (from two days ago) which worked fine and there was no noticeable cpu usage. With the bazaar version I also have two of my four cores constantly at about 50% ... (but rotation also works fine).

And i agree that just switching multitouch on/off would be better. I think there is no reason to switch the pen off.

---

### Post by Favux on 2011-01-21
Hi supr0 & forti,

Thank you for the feedback.
> The toggle for turning off touch should definitely be to toggle multitouch on and off. It's hard to write on the screen with the pen while multitouch is on as if you touch the screen with your hand it will mark it. 
> And i agree that just switching multitouch on/off would be better. I think there is no reason to switch the pen off. 
That's exactly what it does for usb tablet pc's, turn off touch while leaving the stylus working.  Apparently we've discovered a problem with serial tablet pc's like the X200t.  The signals for the stylus and touch are multi-plexed on the same input (usu. ttyS0) and apparently turning off touch is also knocking out your stylus.  Which shouldn't happen since we're using a xsetwacom command and all that should already be handled.  So the question becomes can we handle the serial case?  Or is this part of the CPU issue?
> With the bazaar version I also have two of my four cores constantly at about 50% ... (but rotation also works fine).
CPU usage should not even show in TOP except when actually rotating or using some other Magick function.  So I (or we?) definitely broke something.  forti can you test the current package in post #37.  Same CPU usage problem or is it OK?  Please save the last post #37 download in case I need it to find out what I did wrong because I modified it into the current one.

---

### Post by Favux on 2011-01-21
Alright, running the current post #37 version or the bazaar unstable version shows no CPU usage in TOP for me.  When rotated it briefly hits 2 to 3% usage and then disappears from TOP again.  So it seems to be a ThinkPad issue, which helps narrow it down.  Are you doing anything else when this happens, like toggling off touch?

Could someone who has this issue run Magick from a console/terminal with:
```
./magick-rotation
```
Rotate the tablet and post any output that appears in the console before and after Quitting Magick.

---

### Post by forti on 2011-01-21
> **Favux said:**
> CPU usage should not even show in TOP except when actually rotating or using some other Magick function.  So I (or we?) definitely broke something.  forti can you test the current package in post #37.  Same CPU usage problem or is it OK?  Please save the last post #37 download in case I need it to find out what I did wrong because I modified it into the current one.
The version from post #37 (freshly downloaded) shows no cpu usage, except for the spikes during rotation and also works fine.

The high CPU begins instantly after starting it, and there is no output on the console except when rotating:
```
~/magick-rotation-bzr$ ./magick-rotation 
type da35  code 4d39  value 0
type 7c2  code 8  value 0
type 5  code 1  value 1
type da35  code 4d39  value 0
type 7c7  code 8  value 0
type 0  code 0  value 0
type da3a  code 4d39  value 0
type 1bed  code e  value 0
type 5  code 1  value 0
type da3a  code 4d39  value 0
type 1bf1  code e  value 0
type 0  code 0  value 0
~/magick-rotation-bzr$ 
```I didnt do anything except starting, rotating and stopping it. Touch is enabled. I also removed the config file (.magick-rotation.xml) before starting to reset everything to the default values which didnt change the cpu usage.

---

### Post by Favux on 2011-01-21
Thanks forti,

Let me be sure I understand you.  The new one in post #37 is fine, no CPU issue?  It is the one you downloaded from the Magick site the v. 1.3 in the unstable branch?  That's the one with the high CPU usage issue, correct?  And that's the one you are showing me has what looks like a normal output in the terminal?

Once we get this figured out we can test some xsetwacom commands and figure out why toggling touch isn't working for you.

---

### Post by forti on 2011-01-21
> **Favux said:**
> Let me be sure I understand you.  The new one in post #37 is fine, no CPU issue?  It is the one you downloaded from the Magick site the v. 1.3 in the unstable branch?  That's the one with the high CPU usage issue, correct?  And that's the one you are showing me has what looks like a normal output in the terminal?
The new one from post #37 is fine, no high cpu usage.

The output is from v1.3 which I downloaded via bazaar, and that is the one showing high CPU usage.

---

### Post by Favux on 2011-01-21
Thank you once again!

That should let me figure out the problem.


Now let's figure out the touch issue.  The command Magick is using to turn off touch is:
```
xsetwacom set "Serial Wacom Tablet touch" Touch "off"
```
You can just run it in a terminal and it will turn off touch.  Could you check that please?  Note you should run 'xinput list' for your device name and use that, although they should be the same.

Using the xf86-input-wacom X driver the basic commands for multi-touch are:
```
xsetwacom set "Serial Wacom Tablet touch" Touch "on"
xsetwacom set "Serial Wacom Tablet touch" Gesture "on"
```
Touch and gesture should be on by default if your tablet is properly recognized.  Then to turn them off:
```
xsetwacom set "Serial Wacom Tablet touch" Touch "off"
xsetwacom set "Serial Wacom Tablet touch" Gesture "off"
```
as you'd expect.

---

### Post by forti on 2011-01-21
I have the following devices:
```
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=17    [slave  pointer  (2)]
``````
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS    
Serial Wacom Tablet touch TOUCH
```First: The mentioned commands to turn off Touch work fine and just switch of the Fingers and Gestures. The Stylus keeps working.

But:
When Touch is disabled using the icon and nothing (Stylus, Eraser, Fingers) works, then xsetwacom says that those features are still enabled for all devices:
```
xsetwacom get "Serial Wacom Tablet touch" Gesture && xsetwacom get "Serial Wacom Tablet touch" Touch && xsetwacom get "Serial Wacom Tablet stylus" Touch && xsetwacom get "Serial Wacom Tablet eraser" Touch
on
on
on
on
```Enabling debug in line 6 of xrotate.py i noticed that it doesnt use those xsetwacom commands but uses xinput:
```
$ ./magick-rotation 
xinput set-prop 17 "Device Enabled" 1
xinput set-prop 17 "Device Enabled" 0
xinput set-prop 17 "Device Enabled" 1
```I did some more digging in the code and it seems like this Tablet isnt recogniced as "linuxwacom" device but instead as "wacom" where xinput is used, since its name does not start with "Wacom" ( xrotate.py:98 )

After changing this line to "Serial Wacom" the debug output is xsetwacom instead of xinput but touch doesnt work at all anymore, but the stylus does!
After some more testing i noticed that xsetwacom is very sensitive to capitalization:
```
$ xsetwacom set "Serial Wacom Tablet touch" Touch On
$ xsetwacom get "Serial Wacom Tablet touch" Touch
off
```After changing lines 178 and 180 to "on" and "off" i now have working rotation and only touch is disabled by clicking the icon (The stylus keeps working!).
:grin:

---

### Post by Favux on 2011-01-21
Thank you again forti!  Looks like you've done all the work!  And really nice work too.

So two issues.  We were just using usb device names which start with Wacom whereas the serial ones start with "Serial Wacom".  And with the constant evolution of xf86-input-wacom we've run into a capitalization issue for "on" and "off"!

Let me process it further and talk it over with jayhawk and get a fix for it.

The thing we have to keep in mind is that the xf86-input-wacom 0.10.x series was intended for code optimization and function changes.  The 0.11 is what was intended for general user testing followed by 1.0.  But because the agreement between Xorg and the LWP was that Xorg would take over the X driver for Xorg 1.7 the distros were forced to start using 0.10.x.  And 0.10.5 (Lucid) was really an alpha release as is the whole series.

Frequently when they reorganize another code block something gets busted.  But they usually fix it pretty quickly.  The xsetwacom commands were rewritten for xf86-input-wacom and are different from linuxwacom's xsetwacom commands.

---

### Post by Favux on 2011-01-21
Could someone substitute this xrotate.py for the one in the magick rotation folder from the tar in post #37 and let me know if it works.  Turns touch off while leaving the stylus on in other words.  Thanks.

---

### Post by Favux on 2011-01-23
Hi,

It seems likely that what was causing the high CPU usage issue was a "hang" of some sort.  We're wondering if it was a xsetwacom error caused by the case sensitive issue discovered by forti.  So I've pushed the fix for that and the touch toggle switch into unstable.  If you like you could test unstable again and see if the high CPU usage issue is addressed now.

---

### Post by forti on 2011-01-23
some good and some bad news:

There is still high cpu usage with bzr version, but the problem was a missing checkmagick64 file which was never compiled since the installer doesnt run automatically. The reason is that there is no "firstrun" file in the bazaar repository and i didnt notice that checkmagick64 was missing.
After compiling checkmagick64 by hand the cpu issue is gone.

But it still doesnt recognize the Serial Wacom tablet. (i.e. uses xinput instead of xsetwacom)
Somehow the elif construct doesnt work as i would expect, even if i switch those strings.

This version does not work (uses xinput):
```
            for prop_data in prop_info:
                if prop_data.startswith("Serial Wacom"):
                    return 1
                # added for serial wacom tablet pc's
                elif prop_data.startswith("Wacom"):
                    return 1
        return 0
```When commenting out the elif part it does work (uses xsetwacom):
```
            for prop_data in prop_info:
                if prop_data.startswith("Serial Wacom"):
                    return 1
                # added for serial wacom tablet pc's
                #elif prop_data.startswith("Wacom"):
                #    return 1
        return 0
```

---

### Post by Favux on 2011-01-23
Hi forti,

By gum, you are correct.  How did I miss that?  No firstrun.  Hate that stupid file.  Always forgetting it after a test of the branch.  Shoot.

Thanks for pinning down a problem with the elif.  Back to the drawing board.

---

### Post by Favux on 2011-01-23
Hmmm.  It works either way for me.
```
            for prop_data in prop_info:
                if prop_data.startswith("Wacom"):
                    return 1
                # added for serial wacom tablet pc's
                elif prop_data.startswith("Serial Wacom"):
                    return 1
```
or
```
            for prop_data in prop_info:
                if prop_data.startswith("Serial Wacom"):
                    return 1
                # added for serial wacom tablet pc's
                elif prop_data.startswith("Wacom"):
                    return 1
```
What am I missing?  Let's see, the 0th iter...

Edit:  Does changing "Serial Wacom" to "Serial" make any difference?

---

### Post by forti on 2011-01-23
Sorry, i think i misunderstood some of the code ....

There are those two different kind of devices:
The linuxwacom class which uses xsetwacom for the touch-change,
and the wacom class which uses xinput for the touch-change.

If I am correct now, we do _not_ want a match in this is_wacom method because this would make it of class wacom. If we return 0 here the toggle_touch method (line 550)  runs through the linuxwacom part which uses xsetwacom and thus works.

But lots of the properties of this device start with Wacom (and not Serial Wacom Tablet which is only the device name) so as soon as the '[FONT=monospace]if prop_data.startswith("Wacom"):[/FONT]' part is in there we get a wacom device instead of linuxwacom, so i suppose we need some other changes in the devicelookup.

---

### Post by Favux on 2011-01-23
Right, right.  Jayhawk added that for backward compatablility with Karmic which is what I run my usb tablet pc in.  We need to add some comments in there, don't we?  So what we probably need is the list-props in Lucid or Maverick of a serial tablet pc and see where things are breaking down.
```
xinput list-props "Serial Wacom Tablet touch"
```

---

### Post by supr0 on 2011-01-23
> **Favux said:**
> Right, right.  Jayhawk added that for backward compatablility with Karmic which is what I run my usb tablet pc in.  We need to add some comments in there, don't we?  So what we probably need is the list-props in Lucid or Maverick of a serial tablet pc and see where things are breaking down.
```
xinput list-props "Serial Wacom Tablet touch"
```

Hey Favux,

Sorry not been involved lately, last thing I did was install the magicrotate you posted here so I'm not sure if you're looking for me to have done something else after that before I run this?

Anyways here's the result for xinput list-props "Serial Wacom Tablet touch":

```

Device 'Serial Wacom Tablet touch':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (246):	0
	Device Accel Constant Deceleration (247):	1.000000
	Device Accel Adaptive Deceleration (248):	1.000000
	Device Accel Velocity Scaling (249):	10.000000
	Wacom Tablet Area (296):	0, 0, 2631, 1652
	Wacom Rotation (297):	0
	Wacom Serial IDs (299):	227, 0, 3, 0
	Wacom TwinView Resolution (300):	0, 0, 0, 0
	Wacom Display Options (301):	-1, 0, 1
	Wacom Screen Area (302):	0, 0, 1280, 800
	Wacom Proximity Threshold (303):	0
	Wacom Capacity (304):	-1
	Wacom Pressure Threshold (305):	27
	Wacom Sample and Suppress (306):	2, 4
	Wacom Enable Touch (307):	1
	Wacom Hover Click (308):	0
	Wacom Enable Touch Gesture (309):	1
	Wacom Touch Gesture Parameters (310):	50, 20, 250
	Wacom Tool Type (311):	"TOUCH" (313)
	Wacom Button Actions (312):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

---

### Post by Favux on 2011-01-23
Hi supr0,

No you're good.  That's what I needed.  Now I've got to sit down and see if I can work out what's going on.

Meanwhile we can just use the change from "Wacom" to "Serial Wacom" and comment out the elif if you have it.

---

### Post by Favux on 2011-01-24
Hi again,

OK, back with two ways to go.  We'll start with the simple one.  But first it would be good if someone could post the debug output of xrotate.py when things are working and when they aren't working so we can get a better look at what's happening.  To turn debug on go to line #6 in xrotate.py and change debug from 0 to 1.  Then run Magick from a terminal './magick-rotation' and post the output.  It'll be kind of long so you may want to compress it and attach it to your post.

To give you an idea for me toggling touch shows:
```
xsetwacom set "Wacom_ISDv4_93_Finger" Touch on

xsetwacom set "Wacom_ISDv4_93_Finger" Touch off

xsetwacom set "Wacom_ISDv4_93_Finger" Touch on
```
And then rotating shows a lot of stuff but the key lines, after a lot of evdev stuff, look like:
```
wacom count:  0
direction: right
name: Wacom_ISDv4_93_Pen direction: right
xsetwacom set "Wacom_ISDv4_93_Pen" rotate cw

name: Wacom_ISDv4_93_Pen_eraser direction: right
xsetwacom set "Wacom_ISDv4_93_Pen_eraser" rotate cw

name: Wacom_ISDv4_93_Finger direction: right
xsetwacom set "Wacom_ISDv4_93_Finger" rotate cw
```
But I'd like to see the entire output for both cases.

Alright the simple change is to go from, at about line #98:
```
            for prop_data in prop_info:
                if prop_data.startswith("Wacom"):
                    return 1
                # added for serial wacom tablet pc's
                elif prop_data.startswith("Serial Wacom"):
                    return 1
```
to
```
            for prop_data in prop_info:
                if "Wacom" in prop_data:
                    return 1
```
Which again also works for me.

---

### Post by forti on 2011-01-24
Hi,

In all cases i first switched touch off and on and then rotated the display to tablet mode and back to laptop mode, both exactly once.

With both your versions it does not work correctly (i.e. rotate works but clicking also switches off the pen) and the debug output is attached, files "bzr-magick" and "bzr-magick-modifed". 
It also seems to rotate all three devices twice (16,17,18 are exactly the wacom devices). This has no effect on the resulting screen orientation, since the rotation is absolute.
```
rotating wacom device Serial Wacom Tablet stylus
skipping next rotation check
xsetwacom set 18 rotate cw
rotating wacom device Serial Wacom Tablet eraser
skipping next rotation check
xsetwacom set 16 rotate cw
rotating wacom device Serial Wacom Tablet touch
skipping next rotation check
xsetwacom set 17 rotate cw
name: Serial Wacom Tablet stylus direction: right
xsetwacom set "Serial Wacom Tablet stylus" rotate cw
name: Serial Wacom Tablet eraser direction: right
xsetwacom set "Serial Wacom Tablet eraser" rotate cw
name: Serial Wacom Tablet touch direction: right
xsetwacom set "Serial Wacom Tablet touch" rotate cw
```I tested a third version with the following code block which works fine (only the finger is disabled, rotation works and it does not set the rotation twice) and the output is in file "bzr-magick-return0": (I know that this version is not useful in general)
```
            for prop_data in prop_info:
                return 0;
                #if prop_data.startswith("Wacom"):
                #    return 1
                # added for serial wacom tablet pc's
                #elif prop_data.startswith("Serial Wacom"):
                #    return 1
```PS: Why does the toggle_touch method in class wacom use xinput to disable the device instead of using xsetwacom ? Or alternatively, what exactly is the difference between the class linuxwacom and wacom ?

---

### Post by Favux on 2011-01-25
Hi forti and everyone,

Those debug outputs helped a lot.  While it's probably a bit of overkill I'm hoping the attached xrotate.py will work for everybody.
> PS: Why does the toggle_touch method in class wacom use xinput to disable the device instead of using xsetwacom ? Or alternatively, what exactly is the difference between the class linuxwacom and wacom ? 
Well we'll have to ask jayhawk to be for sure but I believe class wacom was the original version using xinput.  That sort of standardized the code for evdev and wacom devices.  But as I mentioned the class wacom didn't work for Karmic due to the difference in xinput output.  So jayhawk was forced to add the class linuxwacom, which by happy coincidence also apparently works for serial tablet pc's.

At least that's the way I think I remember it.

---

### Post by forti on 2011-01-25
Sorry, but it does not work. 

In the list of xinput properties supr0 posted, none actually starts with "Serial Wacom" but there are a lot which start with "Wacom" so it will never reach the elif part.
I think it is impossible to use those property names to decide whether it is a "Serial Wacom" device as in the x201 or a normal Wacom device.

My proposal would be instead to check the device name:
```
    def is_wacom(self, id_val):
        idx = self.get_id_num(id_val)
        if (self.devices[idx][0].find("Serial Wacom") != -1):
            return 0
        for prop in self.devices[idx][2]:
            prop_info = prop.split("\t")
            for prop_data in prop_info:
                if prop_data.startswith("Wacom"):
                    return 1
        return 0
```

---

### Post by Favux on 2011-01-25
Edit:  Nevermind

---

### Post by Ayuthia on 2011-01-25
> **forti said:**
> Sorry, but it does not work. 

In the list of xinput properties supr0 posted, none actually starts with "Serial Wacom" but there are a lot which start with "Wacom" so it will never reach the elif part.
I think it is impossible to use those property names to decide whether it is a "Serial Wacom" device as in the x201 or a normal Wacom device.

My proposal would be instead to check the device name:
```
    def is_wacom(self, id_val):
        idx = self.get_id_num(id_val)
        if (self.devices[idx][0].find("Serial Wacom") != -1):
            return 0
        for prop in self.devices[idx][2]:
            prop_info = prop.split("\t")
            for prop_data in prop_info:
                if prop_data.startswith("Wacom"):
                    return 1
        return 0
```

Sorry for joining in so late.  I was looking at the code and the checks that are being made here are not necessary.  The is_wacom function is just a check to see if the current driver is 'wacom'.  We are trying to figure out what command we are supposed to use for the device based on the driver that it is using.

One of the problems that I do see is that from this [source version]("http://bazaar.launchpad.net/~magick-admin-team/magick-rotation/unstable/view/head:/xrotate.py") (the unstable from bzr), line 489 was left there by accident.  I meant to remove it before pushing it out there and it looks like it is still there.  That is why it is making the duplicate call.

---

### Post by Ayuthia on 2011-01-25
> **forti said:**
> PS: Why does the toggle_touch method in class wacom use xinput to disable the device instead of using xsetwacom ? Or alternatively, what exactly is the difference between the class linuxwacom and wacom ?

The reason why the xinput version was used was mainly for GIMP.  I was told that GIMP will still see the device if it is still active.  So I figured that if we just turn of the touch from xinput, it will prevent it from being seen.  From the previous results it looked like it only turned off the touch.

Have you confirmed that xinput will turn off the stylus, eraser, and touch if you turn off touch only using the Terminal?  I just want to confirm that before making the changes to switch it over to xsetwacom.  Thanks.

---

### Post by forti on 2011-01-25
I have the following devices 
```
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=16    [slave  pointer  (2)]
```and calling:
```
xinput set-prop 16 "Device Enabled" 0
```switches off touch, stylus **and** eraser. And there are some other people in this thread reporting that magick-rotation did switch off everything instead of only touch.
(I noticed the strange side-effect that the last touch i made while everything was disabled is executed after enabling the device again)

Edit: There is another xinput property which does work:
```
xinput set-prop 16 "Wacom Enable Touch" 0
```
This one only switches touch off, but stylus and eraser keep working.

---

### Post by Ayuthia on 2011-01-25
> **forti said:**
> I have the following devices 
```
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=16    [slave  pointer  (2)]
```and calling:
```
xinput set-prop 16 "Device Enabled" 0
```switches off touch, stylus **and** eraser. And there are some other people in this thread reporting that magick-rotation did switch off everything instead of only touch.
(I noticed the strange side-effect that the last touch i made while everything was disabled is executed after enabling the device again)

Thanks for checking into that for me.  We will make the update so that it will call xsetwacom instead of using xinput.

---

### Post by supr0 on 2011-01-25
> **Ayuthia said:**
> Thanks for checking into that for me.  We will make the update so that it will call xsetwacom instead of using xinput.

Hi Ayuthia,

I may be stating the obvious (excuse me if I am) but this works for me:

```

xsetwacom --set "Serial Wacom Tablet touch" TOUCH 0

```

---

### Post by Favux on 2011-01-25
Hi supr0, forti, and everyone,

Thanks supr0.


Try, try again.  Ok this xrotate.py sets the touch toggle on xsetwacom as per Ayuthia/jayhawk.  I do not see any issues in Gimp or Xournal.  In other words if I toggle off touch it is off in Gimp etc.

It should also fix the double rotation issue in the xrotate.py debug output.

Could I get some testing of it please?  Just substitute it in for the xrotate.py in the post #37 magick-rotation 1.3.

---

### Post by supr0 on 2011-01-25
> **Favux said:**
> Hi supr0, forti, and everyone,

Thanks supr0.


Try, try again.  Ok this xrotate.py sets the touch toggle on xsetwacom as per Ayuthia/jayhawk.  I do not see any issues in Gimp or Xournal.  In other words if I toggle off touch it is off in Gimp etc.

It should also fix the double rotation issue in the xrotate.py debug output.

Could I get some testing of it please?  Just substitute it in for the xrotate.py in the post #37 magick-rotation 1.3.

Hey Favux, this works for turning off multitouch however it also turns off the 'click' for both the mouse and the wacom pen, i.e. I can move the cursor using either the mouse or the pen but can click with either.

We're getting there!

---

### Post by forti on 2011-01-25
Hi,

It works fine here, turns of touch but the pen and also my mouse keep working, and i can still click with them.

---

### Post by Favux on 2011-01-25
Hi forti and supr0,

I'm seeing what forti is seeing.  No problem with click.  Any issues in Gimp or whatever?

supr0 could you try rebooting and checking it out again and see if the clicks work?  Are you able to draw in Gimp etc. with pressure and everything?

---

### Post by forti on 2011-01-25
Everything (including pressure sensitivity) works fine in gimp and xournal. And switching off touch did what it should do.

Only thing i noticed is that, with pressure enabled but when using the finger, gimp and xournal always draw with the lowest pressure possible. (Very thin lines in xournal even though the biggest line is selected.) But thats a different issue and not very important for me.

---

### Post by Favux on 2011-01-25
Good.  I see the thin line in Xournal but not in Gimp although I didn't really look into it.  Who draws in Gimp with their finger?  But you're right, an unrelated issue.  Other serial tablet pc's report spurious lines in Xournal unless touch is off, so it's good we can do that now.

---

### Post by supr0 on 2011-01-25
> **Favux said:**
> Good.  I see the thin line in Xournal but not in Gimp although I didn't really look into it.  Who draws in Gimp with their finger?  But you're right, an unrelated issue.  Other serial tablet pc's report spurious lines in Xournal unless touch is off, so it's good we can do that now.

Sorry Favux, I restarted and everything is fine. I get the same thin line with Xournal but not with GIMP when drawing with finger, but you're right - who is going to draw with their finger lol.

---

### Post by Favux on 2011-01-25
Great!  So I think we finally have it!

Anybody disagree or want to chime in?

---

### Post by linuxd00 on 2011-01-29
Sorry to  be so late.. my notebook was in repair :\


anyways i can happily confirm that it works as a charm (i was the one whinning that it didnt work last week:)).

CPU overload is gone and touch is disabled correctly without affecting pen.

Just as an unrelated side note:ubuntu seems to be so smart that it automatically temporarily disables touch when the pen in detected.. so i never had issues with the pen being in my way when writing..

but this comes just great when i need to show something on screen or even clean the screen from little smudges :)

THANKS FOR THIS GREAT PIECE OF SOFTWARE!!!!

---

### Post by linuxd00 on 2011-01-29
asa quick question: when will the version be officially updated?

---

### Post by Favux on 2011-01-29
Hi linuxd00,

Glad you got your tablet fixed and happy Magick now works for you.  :)

I think we finished up everything yesterday so it should be any time for version 1.3.  Whenever jayhawk finds the time to finish his review and push it.

---

### Post by Favux on 2011-01-29
Hi everyone,

Magick Rotation v. 1.3 with ThinkPad support has been released:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Once again a big thank you to all of our testers.  We couldn't have done it without you.

---

### Post by linuxd00 on 2011-02-08
hey favux,
thanks for the great app!

i have a question:

i installed the testing version. how do i remove to install the official one? is deleting the "unstable" folder enough? it says it install some "rules" somewhere..

---

### Post by Favux on 2011-02-08
Hi linuxd00,

I just copy the new magick-rotation folder over the old one in my /home/username directory.  Most of the files stay in it.  There are a few files that go elsewhere.  The Magick-README.txt has a little section telling you where.

If you installed the bazaar version of unstable you can just leave it there if you want to test along with v. 1.4.  When we get around to uploading new files you can update/synch your unstable by entering:
    bzr pull
in the unstable folder.

In other words you can switch between which version you are running by double clicking on the magick-rotation file in the folder of the version you want to run.

---

### Post by linuxd00 on 2011-02-28
Lenovo X201t:

the wacom drivers were just updated... and they broke stylus rotation as we knew it :\

it seems the stylus still rotates somehow.. but not in the expected way.

neither magick rotation nor [my custom scripts]("http://ubuntuforums.org/showthread.php?t=1656632") work anymore.

haalp!

---

### Post by sofiamarcella on 2011-02-28
Hello guy....  where I can find for newibie:guitar:    [IMG]http://freeimagestocks.com/content/5/love.gif[/IMG]

---

### Post by Favux on 2011-02-28
Hi linuxd00,

What release of Ubuntu had a Wacom driver update?  Natty?

The only thing that happened with xsetwacom is some of the parameter names changed.  The *get* or *set* commands will tell you the old and new names.  Also this table:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

With rotation they just stopped using the Capitalized NONE, CCW etc. for none, ccw, etc.  But Magick already used the non-capitalized ones.

So I don't see how the Wacom driver would have broke rotation.  Are you able to describe what's happening to the stylus a little more?


Hi sofiamarcella,

If you're asking about Magick Rotation it is at:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by linuxd00 on 2011-03-01
im using Ubuntu 10.10 Maverick Meerkat. I updated just yesterday (but for the first time in like 2 months).

i think rotation is defintely buggy at least:

first of all the rotation is broken in my scripts as well in the unstable version of magick rotaion i downloaded right before 1.3 came out.

when you rotate cw and ccw the screen rotates but the stylus does not anymore.

upside and normal work fine.

using my scripts i have noticed that after rotating to position "left" with
```
xrandr -o left

```

you can use the command 

```
xsetwacom set "Serial Wacom Tablet eraser"  Rotate  cw 
```

to fix it (yes cw as in clockwise(and CW or cw works the same)). but it cant be used in a cript as it wont be recognized. it seems it has to be used at least a second after.

ccw or CCW does not seem to work. it just resets to normal

half and normal work just ok.

---

### Post by Favux on 2011-03-01
> I updated just yesterday (but for the first time in like 2 months).
Hmmm.  Does the Thinkpad X201t use an Intel motherboard video chip?  It seems to me I remember a new Intel video driver coming through a week or two ago.  Hopefully the install got corrupted a little, and that's the problem.  And not the Intel driver itself.  Try going into Software Center or Synaptic Package Manager and reinstalling it and rebooting.

---

### Post by linuxd00 on 2011-03-02
nope.. just reinstalled intel and wacom drivers.. stays same as stated.

any other x201 owner can confirm or unconfirm this?

---

### Post by Favux on 2011-03-02
Hi linuxd00,

Looks like Timo Aaltonen may have found the problem and just submitted a patch to fix it.  Turns out the same commit I told you about to change them to lower case had a typo, ccw was accidentally cww.  Should be committed quickly and hopefully will fix the issue.

---

### Post by Favux on 2011-03-04
OK, patch comitted.  Does cloning the latest xf86-input-wacom git repository fix the issue?

---

### Post by linuxd00 on 2011-03-06
ok i tried to install it from git and also built and installe it
using this

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

i am not sure if it installed correctly.. after logging out and in the rotation still does not work correctly..


when checking if the git driver loaded i get this.. but dont really know what it means.. i mean i dont know what driver version i should expect.. so i dont know if the new driver is loaded.

> [  2662.041] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2662.041] (II) Module wacom: vendor="X.Org Foundation"
[  2662.041] 	compiled for 1.9.0, module version = 0.10.99
[  2662.041] 	Module class: X.Org XInput Driver
[  2662.041] 	ABI class: X.Org XInput driver, version 11.0


since im entering terrain i am not sure about im thinking about leaving this at that. do you can make something out of this?

it seems i am not the only one..
 this guy in my other thread also seems to have problems:

[http://ubuntuforums.org/showpost.php?p=10512088&postcount=11](http://ubuntuforums.org/showpost.php?p=10512088&postcount=11)

since i use my own scripts for full rotation i dont see the same error lines he gets

---

### Post by pfein on 2011-03-07
Just getting set up on a new Thinkpad X200 tablet. Things worked fine with packages out of the Ubuntu maverick repos... when I upgraded to PPAs, I started having rotation problems (backwards orientation on wacom in left/right modes). Hard to identify the exact source, as I added a few PPAs at the same time (including utouch-team - moral: one. thing. at. a. time). Problem began when I upgraded to ppa:doctormo/wacom-plus xf86-input-wacom 1:0.10.11-0ubuntu8. Adding ppa:irie/wacom xf86-input-wacom 1:0.10.99+git20110303-0irie1 didn't help either. Note that the orientation problem occurred with thjaeger's wacomrotate as well, so I suspect a sign got flipped somewhere upstream in xf86-input-wacom.

Anyway, currently working around the problem using this patch to magick-rotate:

```

--- xrotate.py	2011-03-07 09:08:50.551671999 -0800
+++ xrotate.py.orig	2011-03-07 09:01:36.221672002 -0800
@@ -108,7 +108,7 @@
 
         self.wacom_table = ["none", "cw", "ccw", "half"]
         self.wac_to_randr = {"none":"normal", "ccw":"left", "half":"inverted", "cw":"right"}
-        self.randr_to_wac = {"normal":"none", "left":"cw", "inverted":"half", "right":"ccw"}
+        self.randr_to_wac = {"normal":"none", "left":"ccw", "inverted":"half", "right":"cw"}
         self.rotate_order = ["normal", "left", "inverted", "right"]

```

For the non-technical, in xrotate.py line 111, swap ccw & cw in randr_to_wac.

HTH.

---

### Post by pcolamar on 2011-06-14
Hi,
  I just installed "magick.." but when I  rotates the screen becomes black in the half part (see screenshot).
I guess the problem is not in magick.. because I have tried to use xrandr alone and it is just the same.
Has anybody got the same problem ?

Thanks
_________
Lenovo x201t 
Ubuntu natty 11.04
2:2.14.0-4ubuntu7.1 (xserver-xorg-video-intel)

---

### Post by Favux on 2011-10-04
Hi everyone,

Back again with a request regarding Magick.

If you are using Magick Rotation with a ThinkPad could you please post the output of the following in a terminal?
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/lenovo-acpi)
```
And also the output of:
```
sudo lsinput
```
This would be very helpful for some contemplated changes to Magick.

Thank you.

---

### Post by forti on 2011-10-04
> **Favux said:**
> If you are using Magick Rotation with a ThinkPad could you please post the output of the following in a terminal?
```
$ udevadm info -a -p $(udevadm info -q path -n /dev/input/lenovo-acpi)
 
 Udevadm info starts with the device specified by the devpath and then
 walks up the chain of parent devices. It prints for every device
 found, all possible attributes in the udev rules key format.
 A rule to match, can be composed by the attributes of the device
 and the attributes from one single parent device.
 
   looking at device '/devices/platform/thinkpad_acpi/input/input7/event7':
     KERNEL=="event7"
     SUBSYSTEM=="input"
     DRIVER==""
 
   looking at parent device '/devices/platform/thinkpad_acpi/input/input7':
     KERNELS=="input7"
     SUBSYSTEMS=="input"
     DRIVERS==""
     ATTRS{name}=="ThinkPad Extra Buttons"
     ATTRS{phys}=="thinkpad_acpi/input0"
     ATTRS{uniq}==""
     ATTRS{properties}=="0"
 
   looking at parent device '/devices/platform/thinkpad_acpi':
     KERNELS=="thinkpad_acpi"
     SUBSYSTEMS=="platform"
     DRIVERS=="thinkpad_acpi"
     ATTRS{hotkey_enable}=="1"
     ATTRS{hotkey_bios_enabled}=="0"
     ATTRS{hotkey_bios_mask}=="0x0000080c"
     ATTRS{hotkey_report_mode}=="1"
     ATTRS{wakeup_reason}=="0"
     ATTRS{wakeup_hotunplug_complete}=="0"
     ATTRS{hotkey_mask}=="0x078dffff"
     ATTRS{hotkey_all_mask}=="0x07ffffff"
     ATTRS{hotkey_recommended_mask}=="0x078dffff"
     ATTRS{hotkey_source_mask}=="0x00000000"
     ATTRS{hotkey_poll_freq}=="10"
     ATTRS{hotkey_radio_sw}=="0"
     ATTRS{hotkey_tablet_mode}=="0"
     ATTRS{bluetooth_enable}=="0"
     ATTRS{wwan_enable}=="0"
 
   looking at parent device '/devices/platform':
     KERNELS=="platform"
     SUBSYSTEMS==""
     DRIVERS==""
``` ```
$ sudo lsinput
 /dev/input/event0
    bustype : BUS_HOST
    vendor  : 0x0
    product : 0x5
    version : 0
    name    : "Lid Switch"
    phys    : "PNP0C0D/button/input0"
    bits ev : EV_SYN EV_SW
 
 /dev/input/event1
    bustype : BUS_HOST
    vendor  : 0x0
    product : 0x3
    version : 0
    name    : "Sleep Button"
    phys    : "PNP0C0E/button/input0"
    bits ev : EV_SYN EV_KEY
 
 /dev/input/event2
    bustype : BUS_HOST
    vendor  : 0x0
    product : 0x1
    version : 0
    name    : "Power Button"
    phys    : "LNXPWRBN/button/input0"
    bits ev : EV_SYN EV_KEY
 
 /dev/input/event3
    bustype : BUS_I8042
    vendor  : 0x1
    product : 0x1
    version : 43860
    name    : "AT Translated Set 2 keyboard"
    phys    : "isa0060/serio0/input0"
    bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP
 
 /dev/input/event4
    bustype : BUS_HOST
    vendor  : 0x0
    product : 0x6
    version : 0
    name    : "Video Bus"
    phys    : "LNXVIDEO/video/input0"
    bits ev : EV_SYN EV_KEY
 
 /dev/input/event5
    bustype : BUS_USB
    vendor  : 0x46d
    product : 0xc526
    version : 273
    name    : "Logitech USB Receiver"
    phys    : "usb-0000:00:1a.0-1.1/input0"
    uniq    : ""
    bits ev : EV_SYN EV_KEY EV_REL EV_MSC
 
 /dev/input/event6
    bustype : BUS_USB
    vendor  : 0x46d
    product : 0xc526
    version : 273
    name    : "Logitech USB Receiver"
    phys    : "usb-0000:00:1a.0-1.1/input1"
    uniq    : ""
    bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC
 
 /dev/input/event7
    bustype : BUS_HOST
    vendor  : 0x17aa
    product : 0x5054
    version : 16641
    name    : "ThinkPad Extra Buttons"
    phys    : "thinkpad_acpi/input0"
    bits ev : EV_SYN EV_KEY EV_MSC EV_SW
 
 
```

---

### Post by Favux on 2011-10-04
Thank you very much forti.  Good to hear from you again.  :)

---

### Post by pcolamar on 2011-10-05
On my X201T I get something slightly different than Forti:


palmer@palmer-X201t:~$ udevadm info -a -p $(udevadm info -q path -n /dev/input/lenovo-acpi)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/platform/thinkpad_acpi/input/input5/event5':
    KERNEL=="event5"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/platform/thinkpad_acpi/input/input5':
    KERNELS=="input5"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="ThinkPad Extra Buttons"
    ATTRS{phys}=="thinkpad_acpi/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/platform/thinkpad_acpi':
    KERNELS=="thinkpad_acpi"
    SUBSYSTEMS=="platform"
    DRIVERS=="thinkpad_acpi"
    ATTRS{hotkey_enable}=="1"
    ATTRS{hotkey_bios_enabled}=="0"
    ATTRS{hotkey_bios_mask}=="0x0000080c"
    ATTRS{hotkey_report_mode}=="1"
    ATTRS{wakeup_reason}=="0"
    ATTRS{wakeup_hotunplug_complete}=="0"
    ATTRS{hotkey_mask}=="0x078dffff"
    ATTRS{hotkey_all_mask}=="0x07ffffff"
    ATTRS{hotkey_recommended_mask}=="0x078dffff"
    ATTRS{hotkey_source_mask}=="0x00000000"
    ATTRS{hotkey_poll_freq}=="10"
    ATTRS{hotkey_radio_sw}=="1"
    ATTRS{hotkey_tablet_mode}=="0"
    ATTRS{bluetooth_enable}=="0"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""
----------------------


palmer@palmer-X201t:~$ sudo lsinput
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x3
   version : 0
   name    : "Sleep Button"
   phys    : "PNP0C0E/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event3
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43860
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x17aa
   product : 0x5054
   version : 16641
   name    : "ThinkPad Extra Buttons"
   phys    : "thinkpad_acpi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_SW

/dev/input/event6
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x4816
   version : 9029
   name    : "Integrated Camera"
   phys    : "usb-0000:00:1a.0-1.6/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event7
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xa
   version : 0
   name    : "TPPS/2 IBM TrackPoint"
   phys    : "synaptics-pt/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_REL
--------------------------------------------

---

### Post by Favux on 2011-10-05
Hi pcolamar,

Thank you.

So far looking good.  No major surprises with your or forti's attributes walk.  I'm becoming reasonably confident my changes will work for the Thinkpads too.

---

### Post by Favux on 2011-10-10
**[SIZE="4"]Magick Rotation 1.5[/SIZE] has been released**:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

