---
title: "Synaptics Multi-finger"
date: 2009-09-26
forum: Hardware
---

### Post by Ayuthia on 2009-09-26
In order to help people determine whether their mouse touchpad is able to us multi-finger tap or scrolling, I have created a [community help page]("https://help.ubuntu.com/community/SynapticsCapabilitesListing/") to list out the models and capabilities.

In order to configure the touchpad in Jaunty and higher, I tend to copy the file from /usr/share/hal/fdi/policy/ to /etc/hal/fdi/policy/:
```
sudo cp /usr/share/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi /etc/hal/fdi/policy/10osvendor
```
Then you can edit the file:
```
sudo gksu gedit /etc/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi
```
I move it over to /etc/hal/fdi/policy because any system updates to Synaptics will update /usr/share/hal/fdi/policy but it should not touch /etc/hal/fdi/policy.  Most likely, the 10osvendor folder will not be there unless you have any any other changes.  If you need to create the folder:
```
sudo mkdir /etc/hal/fdi/policy/10osvendor
```

An example of what one might look like:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```
The example above will provide the two-finger vertical scroll option.

For more information about what options are available, please read:
```
man synaptics
```
The man page (also /etc/X11/xorg.conf) will display options like:
```
Option "TouchpadOff" "integer"
```
To add that to the .fdi file, convert the line to:
```
<merge key="input.x11_options.TouchpadOff" type="integer">0</merge>
```
and this will enable the touchpad.

As you can see in the community link above, there are not too many entries at this time.  Please help contribute to it by registering to the community help documentation and edit the file to add your information in there.

---

### Post by gwydionwaters on 2009-09-26
mine is currently in /usr/share/hal/fdi/policy/20thirdparty
should i move it to 10osvendors?
it looks like this
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
    <!-- Arbitrary options can be passed to the driver using 
         the input.x11_options property since xorg-server-1.5. -->
    <!-- EXAMPLE:
    <merge key="input.x11_options.LeftEdge" type="string">120</merge>
    -->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by Ayuthia on 2009-09-26
> **gwydionwaters said:**
> mine is currently in /usr/share/hal/fdi/policy/20thirdparty
should i move it to 10osvendors?
it looks like this
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
    <!-- Arbitrary options can be passed to the driver using 
         the input.x11_options property since xorg-server-1.5. -->
    <!-- EXAMPLE:
    <merge key="input.x11_options.LeftEdge" type="string">120</merge>
    -->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

It is ok to have it there, but just be cautious that it might get wiped out when there is an update to the Synaptics driver.  The /etc/hal/... version should not be affected by the update.

---

### Post by gwydionwaters on 2009-09-28
strangely enough there are no folders inside /etc/hal/policy just preferences.hdi
i am going to add some files, restart and see what that does :)

---

### Post by Ayuthia on 2009-09-28
> **gwydionwaters said:**
> strangely enough there are no folders inside /etc/hal/policy just preferences.hdi
i am going to add some files, restart and see what that does :)

Sorry about that.  I should have mentioned that.  It does start off without any folders so you do need to create any missing ones.  The system will look in /usr/share/hal/fdi/policy first, then it looks in /etc/hal/fdi/policy, and finally it goes to /etc/X11/xorg.conf.

---

### Post by phorgan1 on 2009-10-16
I'm having problems with no edge scrolling since upgrading to koala.  In my /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi I have the following uncommented.
```

        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">true</merge>

```

Yet when using synclient -l I'm told that for instance:

```

VertEdgeScroll          = 0
VertTwoFingerScroll     = 0

```
After using synclient to turn them on, vertical edge scrolling works, but not the two finger scrolling. But of course that's only temporary and they are off next time I boot.  Sytem/Preferences/Mouse/Touchpad/EnableVerticalScrolling is selected.

Help!

---

### Post by Ayuthia on 2009-10-16
> **phorgan1 said:**
> I'm having problems with no edge scrolling since upgrading to koala.  In my /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi I have the following uncommented.
```

        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">true</merge>

```

Yet when using synclient -l I'm told that for instance:

```

VertEdgeScroll          = 0
VertTwoFingerScroll     = 0

```
After using synclient to turn them on, vertical edge scrolling works, but not the two finger scrolling. But of course that's only temporary and they are off next time I boot.  Sytem/Preferences/Mouse/Touchpad/EnableVerticalScrolling is selected.

Help!

From what you are describing, it sounds like the system is not taking the information from your .fdi file.  There are two ways to check this.  The first way is to look at /var/log/Xorg.0.log.  This file tells you what the system is using for your input devices like your keyboard, mouse, and monitor.  Somewhere in the file you will see some entries for the synaptics module.  It will look something like this:
```
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib64/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.5, module version = 1.2.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.2.0
(**) Option "Device" "/dev/input/event3"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "1700"
(**) Option "RightEdge" "5300"
(**) Option "TopEdge" "1700"
(**) Option "BottomEdge" "4200"
(**) Option "VertScrollDelta" "100"
(**) Option "VertEdgeScroll" "true"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) Option "SendCoreEvents" "true"
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found

```If you see the Option "VertEdgeScroll" "true" show up without any error messages, the system knew to use the vertical edge scrolling.  It might then be possible that you need to define where to place the edge.  In my example above, you will see that it has the TopEdge, BottomEdge, LeftEdge, and RightEdge defined.  That was how I was able to get my scrolling in place for my touchpad.

If you don't see the VertEdgeScroll information there, then that means that it did not like something from your .fdi file or else there is something defined in /etc/hal/fdi/policy for it or something defined in /etc/X11/xorg.conf.

Another place to look is in lshal.  You can do this from the Terminal:
```
lshal|less
```To exit out of that command, just press the letter q.  You can search for synaptic by typing the following when you are in lshal|less:
```
/synaptic
```and press enter.  You should find an entry like:
```
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.BottomEdge = '4200'  (string)
  input.x11_options.Emulate3Buttons = 'true'  (string)
  input.x11_options.LeftEdge = '1700'  (string)
  input.x11_options.RightEdge = '5300'  (string)
  input.x11_options.SHMConfig = 'true'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TapButton1 = '1'  (string)
  input.x11_options.TapButton2 = '2'  (string)
  input.x11_options.TapButton3 = '3'  (string)
  input.x11_options.TopEdge = '1700'  (string)
  input.x11_options.VertEdgeScroll = 'true'  (string)
  input.x11_options.VertScrollDelta = '100'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input3/event3'  (string)

```This is what gets built from the .fdi file information.  If you don't have the VertEdgeScroll here, then the system did not like something in your .fdi file.

Hopefully this information is helpful to you.  If you are encountering problems with the .fdi file, please post your .fdi entry and we can take a look at it.

From what you are describing, it sounds like xorg is not recognizing something from the .fdi file because it did not turn on the scrolling for you until you used synclient.

---

### Post by Tiede on 2009-10-29
Hello, just as the original poster, I am having problems with my synaptics configuration as well. It appears that some settings are not being set until I use synclient.

here is the relevant section of my preferences.fdi file:
```

<!--
   Here be Angle/Two-Finger scrolling. ---> 
<device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">65</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="int">0</merge>
    </match>
  </device>
```
I have also tried changing VertTwoFingerScroll's value to "true" to no avail...

---

### Post by Ayuthia on 2009-10-29
> **Tiede said:**
> Hello, just as the original poster, I am having problems with my synaptics configuration as well. It appears that some settings are not being set until I use synclient.

here is the relevant section of my preferences.fdi file:
```

<!--
   Here be Angle/Two-Finger scrolling. ---> 
<device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">65</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="int">0</merge>
    </match>
  </device>
```
I have also tried changing VertTwoFingerScroll's value to "true" to no avail...

Can you post the results of /var/log/Xorg.0.log and attach the results of lshal?  It will help us see what is happening.

---

### Post by Tiede on 2009-10-29
I have attached both :)
Disclaimer: This used to work in Jaunty just three days ago...
I just updated to Karmic and noticed the error after that.

EDIT:The complete log files are in the gziped file...

---

### Post by Ayuthia on 2009-10-29
```
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input8/event8'  (string)

```
This is a portion of the lshal file.  It is showing that the .fdi file is not being used.  I noticed in your post that you called it "preferences.fdi".  What is the actual name and location of the file?  Usually the name is 11-x11-synaptics.fdi and is located in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi or /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi.  I think that the system needs to have a number at the beginning of the filename so if you just have "preferences.fdi" it might be ignored.

---

### Post by Tiede on 2009-10-29
Thanks for the quick reply.

Hmm... That's a new requirement, then. I have used that naming perfectly fine in Jaunty...
I will  rename it as you suggested and let you know if anything changed...

---

