---
title: "Thinkpad x201 tablet.  Touchscreen not found"
date: 2014-08-08
forum: Hardware
---

### Post by mgoodwin6 on 2014-08-08
As the title states, I have a Lenovo Thinkpad X201 Tablet PC with a touch screen, and the touch screen does not work.  I am running 14.04LTS and the system is telling me the device is not found.  What would be the reason for this?  Improper, malfunctioning or non-existent driver?  Touch screen not functioning?  Any help would be appreciated.

When I run xinput list-props "Serial Wacom Tablet touch" 
I get this
unable to find device Serial Wacom Tablet touch

When I run xsetwacom --get "Serial Wacom Tablet touch" touch on
I get
Cannot find device 'Serial Wacom Tablet touch'.

When I run inputattach --daemon --w8001 /dev/ttyS0
I get
inputattach: can't set device type

When I run xinput list
I get
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons  

When I run lsinput
I get
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
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS


/dev/input/event6
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xa
   version : 0
   name    : "TPPS/2 IBM TrackPoint"
   phys    : "synaptics-pt/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_REL


/dev/input/event7
   bustype : BUS_HOST
   vendor  : 0x17aa
   product : 0x5054
   version : 16641
   name    : "ThinkPad Extra Buttons"
   phys    : "thinkpad_acpi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_SW


/dev/input/event8
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel MID HDMI/DP,pcm=3"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW


/dev/input/event9
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel MID Headphone"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW


/dev/input/event10
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel MID Dock Headphone"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW


/dev/input/event11
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel MID Dock Mic"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW


/dev/input/event12
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA Intel MID Mic"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW


/dev/input/event13
   bustype : BUS_USB
   vendor  : 0x17ef
   product : 0x4816
   version : 9029
   name    : "Integrated Camera"
   phys    : "usb-0000:00:1a.0-1.6/button"
   bits ev : EV_SYN EV_KEY

And dmsg shows me these
[ 1105.883766] input: Wacom Serial Touchscreen as /devices/pnp0/00:09/tty/ttyS4/serio3/input/input15
[   14.787132] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode


Again any help figuring this out would be appreciated.

---

