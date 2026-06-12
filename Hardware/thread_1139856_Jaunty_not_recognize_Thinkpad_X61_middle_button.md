---
title: "Jaunty not recognize Thinkpad X61 middle button"
date: 2009-04-27
forum: Hardware
---

### Post by Dermis on 2009-04-27
Be gentle with me, im just a newbie here :)

I've just make a fresh ubuntu jaunty install to my thinkpad x61.

My middle button scrolling did not work out of the box.

I've create 

/etc/hal/fdi/policy/mouse-wheel.fdi 

with

<?xml version="1.0" encoding="UTF-8"?> 
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>


but it didn't work for me with jaunty :( (work with intrepid before)

can anyone guide me with this problem?

---

### Post by Barry Carroll on 2009-04-27
Did you restart HAL or the system after you made those changes?

```
/etc/init.d/hal restart
```

You should also check on the info.product bit that matches your hardware to the hal configuration file as that might have changed.  You can do an lshal command and have a look for your trackpoint in there.  It might have a different name now.

If it does then your xml file will have to be changed to something like:
 
```
<match key="info.product" string="The new value from lshal">
```

---

### Post by Dermis on 2009-04-27
yup, i've already restart HAL + also restart my laptop.

part of my lshal:

> 
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  access_control.file = '/dev/input/event8'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'TPPS/2 IBM TrackPoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'TPPS/2 IBM TrackPoint'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input8/event8'  (string)



i've also edited my xorg.conf but nothing happened :(

---

### Post by jon13 on 2009-04-27
I can confirm having same problems with my X31, scrolling does work, but only when cursor is placed over scrollbar similar to mousebutton 1. it does paste clipboard when i click middlebutton in an editor, which i would rater it didnt. I have also confirmed that my info.product is correct. ??? Other than this i think jaunty is great on my thinkpad.

---

### Post by Barry Carroll on 2009-04-27
You have a few options different to the example on thinkwiki - have you tried their configuration

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)

```
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
</match>

```

---

### Post by jon13 on 2009-04-27
Holy  smokes it did actually work, but only after restarting the system, just restarting hald wasnt enough. midlle button still pastes though. 
Thx

---

### Post by Dermis on 2009-04-27
OMG..what a careless..it works..a lot of karma's for u Barry :D

---

### Post by Barry Carroll on 2009-04-27
Great!, credit to thinkwiki though as it is a great site.  I hope to get something similar working with my ultranav usb keyboard.

---

### Post by tinkerpad on 2009-05-10
Dear all,
I have a Thinkpad R40 and can't get that thing to scroll...

My trackpoint device seems to be not exactly the same, it calls itself "SynPS/2 Synaptics TouchPad".

On Ubuntu 8.10 I used to edit the xorg.conf file with the two parameters EmulateWheel and EmulateWheelButton, it worked.

Now on 9.04 I try to add them by a .fdi file like:
```

<?xml version="1.0" encoding="UTF-8"?> 

<match key="info.product" string="SynPS/2 Synaptics TouchPad">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
</match>

```

lshal reports:
```

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.EmulateWheel = 'true'  (string)
  input.x11_options.EmulateWheelButton = '2'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input8/event8'  (string)

```

But still I cant get that thing to scroll!
I also tried the above suggestion with XAxisMapping, YAxisMapping and all that stuff, still no success...

Thanks for any suggestions!

---

### Post by tisungho on 2009-05-11
Hi,

It doesn't work for my thinkpad X61 either, even though I copied exactly the same text from thinkwiki, restarted hal, and restarted the system.
Please help!!!

---

### Post by tisungho on 2009-05-11
Hi,

I know how to fix it ;) 
The solution is from [THIS]("http://duncanelliot.com/blog/?p=22")
I changed **Y**AxisMapping to **Z**AxisMapping
So, the xml looks like this:

<match key=&#8221;info.product&#8221; string=&#8221;TPPS/2 IBM TrackPoint&#8221;>
<merge key=&#8221;input.x11_options.EmulateWheel&#8221; type=&#8221;string&#8221;>true</merge>
<merge key=&#8221;input.x11_options.EmulateWheelButton&#8221; type=&#8221;string&#8221;>2</merge>
<merge key=&#8221;input.x11_options.**Z**AxisMapping&#8221; type=&#8221;string&#8221;>4 5</merge>
<merge key=&#8221;input.x11_options.XAxisMapping&#8221; type=&#8221;string&#8221;>6 7</merge>
<merge key=&#8221;input.x11_options.Emulate3Buttons&#8221; type=&#8221;string&#8221;>true</merge>
<merge key=&#8221;input.x11_options.EmulateWheelTimeout&#8221; type=&#8221;string&#8221;>200</merge>
</match>

---

### Post by Leszek Tarkowski on 2009-05-23
Try this:

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Y Axis" 8 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation X Axis" 8 6 7
```

Notice Evdev before property name. Works on X61t under 9.04

---

### Post by shaferkamp on 2009-08-12
Thanks Barry, that worked just excellent on my X61 :)


> **Barry Carroll said:**
> You have a few options different to the example on thinkwiki - have you tried their configuration

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)

```
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
</match>

```

---

### Post by fuxter on 2009-09-10
> **Leszek Tarkowski said:**
> Try this:

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Y Axis" 8 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation X Axis" 8 6 7
```Notice Evdev before property name. Works on X61t under 9.04

this magically worked after all other attempts failed, and was rebooting all the times.
i'm on r61. now i guess i have to put these lines to some startup script.

thanks, Leszek

---

### Post by Duncan J Murray on 2009-09-25
Hurrah!  Another very satisfied customer...

 :)

---

### Post by helgesdk on 2009-10-27
Is there any way to configure XAxisMapping, YAxisMapping and ZAxisMapping on-the-fly??
(i.e. without creating a file in /etc/hal/fdi/policy/, having to restart both hal and X)

I use these commands in a startup script:
```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Axes" 8 6 7 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Timeout" 16 200
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Middle Button Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Middle Button Timeout" 16 50
```
The only thing not working is horizontal scrolling. For that I need XAxisMapping.

*edit*
Oh... I can actually rmmod/modprobe the psmouse module instead of restarting X.
Still, it would be much nicer to just use a command like xinput.

---

### Post by Palumbo on 2009-12-29
> **Barry Carroll said:**
> You have a few options different to the example on thinkwiki - have you tried their configuration

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)

```
<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
</match>

```

Many thanks for bringing this to my attention, Barry. This works perfect for my ThinkPad T43! 

-Palumbo

---

### Post by jackubun on 2010-01-14
> **tisungho said:**
> Hi,

I know how to fix it ;) 
The solution is from [THIS]("http://duncanelliot.com/blog/?p=22")
I changed **Y**AxisMapping to **Z**AxisMapping
So, the xml looks like this:

<match key=&#8221;info.product&#8221; string=&#8221;TPPS/2 IBM TrackPoint&#8221;>
<merge key=&#8221;input.x11_options.EmulateWheel&#8221; type=&#8221;string&#8221;>true</merge>
<merge key=&#8221;input.x11_options.EmulateWheelButton&#8221; type=&#8221;string&#8221;>2</merge>
<merge key=&#8221;input.x11_options.**Z**AxisMapping&#8221; type=&#8221;string&#8221;>4 5</merge>
<merge key=&#8221;input.x11_options.XAxisMapping&#8221; type=&#8221;string&#8221;>6 7</merge>
<merge key=&#8221;input.x11_options.Emulate3Buttons&#8221; type=&#8221;string&#8221;>true</merge>
<merge key=&#8221;input.x11_options.EmulateWheelTimeout&#8221; type=&#8221;string&#8221;>200</merge>
</match>

This works on my computer. 
The reason why i could not launch previously I guess is installing [COLOR=Black]gpointing-device-settings[/COLOR][FONT=Verdana][COLOR=Black] following the instruction on [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint).
After I removed it, the scrolling works.

The paragraph on the page is:
[/COLOR][/FONT]> **Configuration using DevKit **

 Most recent distributions like Ubuntu 9.10 switch from HAL (being deprecated) to DevKit. Hence, the HAL configurations explained underneath, fail to work. 
The easiest way to configure your touchpad and trackpoint with DevKit is by using the [GPointingDeviceSettings]("http://live.gnome.org/GPointingDeviceSettings") panel that fully supports the hardware. You can easily download the panel by installing  gpointing-device-settings. On Ubuntu open a terminal and execute the command $  sudo apt-get install gpointing-device-settings 
Launch the UI through the $  gpointing-device-settings command, but you can also add a menu entry to your System / Preferences menu for easier access to the UI panel.

---

### Post by baxna on 2010-06-30
Just wanted to add that the commands on this page worked on my Thinkpad X61, using Lucid 10.04, and without restarting! Nice.

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)

---

### Post by tonnisw on 2010-10-25
Thanks for this help. Just wanted to add the following for 10.04 users (on a ThinkPad x61):

The link referenced in the previous posts ([http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)) made reference to "GPointing Device Settings" for GNOME. I installed it using Applications > Ubuntu Software Center.
Search for "GPointing". Once it's installed you can find it under System > Preferences > Pointing Devices. Click "Use wheel emulation", set the "button" drop-down to 2. Enable vertical and horizontal scroll. Works perfectly!

---

