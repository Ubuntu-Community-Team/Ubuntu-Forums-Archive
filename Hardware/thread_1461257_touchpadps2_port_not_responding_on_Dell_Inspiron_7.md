---
title: "touchpad/ps2 port not responding on Dell Inspiron 7500"
date: 2010-04-24
forum: Hardware
---

### Post by jasloper on 2010-04-24
I've had this issue since loading Karmic on the laptop.  The touchpad will work a few times, then won't for several boots.  I've tried several "fixes", but no change.

When I try to launch the synaptics touchpad utility, I get an error "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I set the following in xorg.conf:

Option "SHMConfig" "true"               (default was "on")    -  no effect.

So, the GSynaptics is not working, which may be the root issue here....   any ideas would be welcome....

One thing I have not tried is reloading (i.e. starting from scratch).  

Also, this is a fresh install, not an upgrade from previous Ubuntu version......

---

### Post by pi/roman on 2010-04-24
If gsynaptics is causing that much of a problem I would just remove it.

xorg.conf is deprecated, you should use hal to configure the touchpad. My guide is here:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

---

### Post by jasloper on 2010-04-25
OK - following your guide, I get the following with the synclient command:

john@john-laptop:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

I have updated the apts.  After this, I tried re-installing the synaptics drivers.  This produced:

$ sudo apt-get install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  libgpds0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, it appears the drivers are installed, but the system is not seeing the touchpad.

Today, the touchpad was working, and I tried another "fix"  changing the "on" to "True" for shmconfig.fdi.  After reboot, the touchpad was not working again....

Any ideas?

Thanks.

---

### Post by pi/roman on 2010-04-25
Please post the output of the following command:
```
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
```and also your xorg.conf
```
cat /etc/X11/xorg.conf
```

---

### Post by jasloper on 2010-04-26
first command line yielded:

john@john-laptop:~$ sudo find /usr/shar/hal /etc/hal -name *synaptics.fdi -print0 | xargs -0 -t cat
[sudo] password for john: 
find: `/usr/shar/hal': No such file or directory
cat /etc/hal/fdi/policy/99-x11-synaptics.fdi 
<html><head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">
</head><body><deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
    <!-- Enable/Disable SHM -->
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>
    <!-- Enable Tap Clicking -->
    <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
    <!-- Tap Click Sensitivity -->
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>
    <!-- Vertical Edge Scrolling -->
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
    <!-- Vertical 2 finger scrolling -->
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
    <!-- Horizontal 2 finger scrolling -->
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
    <!-- Circular Scrolling -->
    <merge key="input.x11_options.CircularScrolling" type="string">false</merge>
    </match>
  </device>
</deviceinfo>

---

### Post by jasloper on 2010-04-26
here is the Xorg.config:
john@john-laptop:~$ cat /etc/X11/xorg.conf
Section "InputDevice"

Identifier "Synaptics Touchpad"

Driver "synaptics"

Option "SendCoreEvents" "true"

Option "Device" "/dev/psaux"

Option "Protocol" "auto-dev"

Option "HorizScrollDelta" "0"

Option "SHMConfig" "true"

EndSection
john@john-laptop:~$ 

I greatly appreciate your looking into this!!!

---

### Post by pi/roman on 2010-04-27
This should get your touchpad working normally.

First delete the entire input device section for the synaptics touchpad from xorg.conf.

Open the hal configuration in gedit:
```
sudo gedit /etc/hal/fdi/policy/99-x11-synaptics.fdi 
```To make it simpler just select it all and delete it then paste this in:
[HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<merge key="input.x11_driver" type="string">synaptics</merge>
<!-- Enable/Disable SHM -->
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<!-- Enable Tap Clicking -->
<merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">2</merge>
<merge key="input.x11_options.TapButton3" type="string">3</merge>
<!-- Tap Click Sensitivity -->
<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>
<!-- Vertical Edge Scrolling -->
<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
<!-- Vertical 2 finger scrolling -->
<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
<!-- Horizontal 2 finger scrolling -->
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
<!-- Circular Scrolling -->
<merge key="input.x11_options.CircularScrolling" type="string">false</merge>
</match>
</device>
</deviceinfo>[/HTML]Then run the following commands and the touchpad should be working normally:
```
sudo modprobe -r -v psmouse
sudo modprobe -v psmouse
```

---

### Post by tgalati4 on 2010-04-27
Boot the live CD of Jaunty or older and see if the touchpad works correctly.  Since the 7500 is an older machine, it's possible that the touchpad is dying or the ribbon cable needs to be reseated.  You want to be sure the hardware is OK vs a software problem.

---

### Post by jasloper on 2010-04-28
OK - I may be looking at a hardware issue here, then.... swapped out the file as directed, ran the commands, and rebooted...... not working.

I don't have a CD of Jaunty right now, but may have to download the image to try that out...

It's not a huge issue if the touchpad doesn't work, but it is handy when I just want to transfer a file or check something quickly.... I got the laptop for free, so I can't complain too much - 9.10 works great otherwise!

---

### Post by pi/roman on 2010-04-28
Please rerun this command being sure to put an "e" on the end of share and post the output of it:
```
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
```

---

### Post by jasloper on 2010-04-30
sorry - didn't get to this yesterday.....

john@john-laptop:~$ sudo find /usr/share/hal etc/hal -name *synaptics.fdi -print0 | xargs -0 -t cat
[sudo] password for john: 
find: `etc/hal': No such file or directory
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 
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
    <merge key="input.x11_options.SHMConfig" type="string">On</merge>
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
john@john-laptop:~$

---

### Post by jasloper on 2010-04-30
ok - I noticed I missed a /.......

john@john-laptop:~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/99-x11-synaptics.fdi 
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
    <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>

---

### Post by jasloper on 2010-04-30
sheesh - didn't get everything.....

john@john-laptop:~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/99-x11-synaptics.fdi 
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
    <merge key="input.x11_options.SHMConfig" type="string">On</merge>
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
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<merge key="input.x11_driver" type="string">synaptics</merge>
<!-- Enable/Disable SHM -->
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<!-- Enable Tap Clicking -->
<merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">2</merge>
<merge key="input.x11_options.TapButton3" type="string">3</merge>
<!-- Tap Click Sensitivity -->
<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>
<!-- Vertical Edge Scrolling -->
<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
<!-- Vertical 2 finger scrolling -->
<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
<!-- Horizontal 2 finger scrolling -->
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
<!-- Circular Scrolling -->
<merge key="input.x11_options.CircularScrolling" type="string">false</merge>
</match>
</device>
</deviceinfo>
john@john-laptop:~$

---

### Post by pi/roman on 2010-04-30
That would be good if the info.product and info.capabilities both work but you should normally only need one of them. See if you can get the lshal of the touchpad with this command:
```
lshal -s | grep AUX_port_ | xargs lshal -u
```

---

### Post by jasloper on 2010-05-02
this is what I got:

john@john-laptop:~$ lshal -s | grep AUX_port_ | xargs lshal -u
lshal: option requires an argument -- 'u'
lshal version 0.5.13

usage : lshal [options]

Options:
    -m, --monitor        Monitor device list
    -s, --short          short output (print only nonstatic part of udi)
    -l, --long           Long output
    -t, --tree           Tree view
    -u, --show <udi>     Show only the specified device

    -h, --help           Show this information and exit
    -V, --version        Print version number

Without any given options lshal will start with option --long.
Shows all devices and their properties. If the --monitor option is given
then the device list and all devices are monitored for changes.

---

### Post by pi/roman on 2010-05-03
You can just dump lshal to a text file on your desktop then and compress it and post it here and I will have a look at it.

```
lshal > ~/Desktop/lshalout.txt
```

---

### Post by jasloper on 2010-05-05
Am I missing something?  When I run the above command, I get "no such file or directory".  I created a blank .txt file on the desktop.  Same thing......

---

### Post by pi/roman on 2010-05-05
[SIZE=5]Try 
```
locate Desktop | grep home
```The path to your desktop should be listed first.

Then use the lshal and output it to a text file on your desktop.

lshal > "/pathtodesktop/"lshalout.txt[/SIZE]

---

### Post by jasloper on 2010-05-09
sorry - I thought I had posted this already (guess I forgot to hit the "submit" button ).....

It also appears there are too many image tags in the output.....  I'll split it in  half....

Dumping 84 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  org.freedesktop.Hal.version = '0.5.13'  (string)
  org.freedesktop.Hal.version.major = 0  (0x0)  (int)
  org.freedesktop.Hal.version.micro = 13  (0xd)  (int)
  org.freedesktop.Hal.version.minor = 5  (0x5)  (int)
  power_management.acpi.linux.version = '20090521'  (string)
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
  system.board.product = '440BX Desktop Reference Platform'  (string)
  system.board.serial = 'None'  (string)
  system.board.vendor = 'Compal Electronics, Inc.'  (string)
  system.board.version = 'None'  (string)
  system.chassis.manufacturer = 'Dell Computer Corporation'  (string)
  system.chassis.type = 'Other'  (string)
  system.firmware.release_date = '11/08/2000'  (string)
  system.firmware.vendor = 'Phoenix Technologies LTD'  (string)
  system.firmware.version = 'A14'  (string)
  system.formfactor = 'laptop'  (string)
  system.hardware.primary_video.product = 19533  (0x4c4d)  (int)
  system.hardware.primary_video.vendor = 4098  (0x1002)  (int)
  system.hardware.product = 'Inspiron 7500'  (string)
  system.hardware.serial = '123456789'  (string)
  system.hardware.uuid = ''  (string)
  system.hardware.vendor = 'Dell Computer Corporation'  (string)
  system.hardware.version = 'Revision B0'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.31-21-generic'  (string)
  system.kernel.version.major = 2  (0x2)  (int)
  system.kernel.version.micro = 31  (0x1f)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'sleep'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Sleep Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Sleep Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Power Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  button.has_state = true  (bool)
  button.state.value = false  (bool)
  button.type = 'lid'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.switch', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Lid Switch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Lid Switch'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_FAN0'
  fan.enabled = false  (bool)
  info.capabilities = {'fan'} (string list)
  info.category = 'fan'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fan'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_FAN0'  (string)
  linux.acpi_path = '/proc/acpi/fan/FAN0'  (string)
  linux.acpi_type = 2  (0x2)  (int)
  linux.hotplug_type = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_FAN1'
  fan.enabled = false  (bool)
  info.capabilities = {'fan'} (string list)
  info.category = 'fan'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Fan'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_FAN1'  (string)
  linux.acpi_path = '/proc/acpi/fan/FAN1'  (string)
  linux.acpi_type = 2  (0x2)  (int)
  linux.hotplug_type = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Pentium III (Coppermine)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 0  (0x0)  (int)

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

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  battery.charge_level.current = 59616  (0xe8e0)  (int)
  battery.charge_level.design = 64800  (0xfd20)  (int)
  battery.charge_level.last_full = 64800  (0xfd20)  (int)
  battery.charge_level.percentage = 92  (0x5c)  (int)
  battery.charge_level.rate = 0  (0x0)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'I 7500'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = true  (bool)
  battery.remaining_time = 8280  (0x2058)  (int)
  battery.reporting.current = 4140  (0x102c)  (int)
  battery.reporting.design = 4500  (0x1194)  (int)
  battery.reporting.last_full = 4500  (0x1194)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.serial = '3658Q'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'DELL'  (string)
  battery.voltage.current = 16000  (0x3e80)  (int)
  battery.voltage.design = 14400  (0x3840)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'I 7500'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'
  ac_adapter.present = false  (bool)
  info.capabilities = {'ac_adapter'} (string list)
  info.category = 'ac_adapter'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic AC Adapter Device'  (string)
  info.subsystem = 'power_supply'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'power_supply'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC'  (string)

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

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

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

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ECP printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'ECP printer port'  (string)
  pnp.id = 'PNP0401'  (string)

udi = '/org/freedesktop/Hal/devices/ppdev_parport0'
  info.capabilities = {'ppdev'} (string list)
  info.category = 'ppdev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0401'  (string)
  info.product = 'Parallel Port Device'  (string)
  info.subsystem = 'ppdev'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ppdev_parport0'  (string)
  linux.device_file = '/dev/parport0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'ppdev'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03/ppdev/parport0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'PC standard floppy disk controller'  (string)
  pnp.id = 'PNP0700'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PCI Bus'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.description = 'PCI Bus'  (string)
  pnp.id = 'PNP0a03'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

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
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

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
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0'
  info.linux.driver = 'floppy'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (floppy.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/floppy.0'  (string)
  platform.id = 'floppy.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'
  block.device = '/dev/fd0'  (string)
  block.is_volume = false  (bool)
  block.major = 2  (0x2)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  info.product = 'PC Floppy Drive'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy'  (string)
  info.vendor = ''  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/platform/floppy.0/block/fd0'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'platform'  (string)
  storage.drive_type = 'floppy'  (string)
  storage.hotpluggable = false  (bool)
  storage.media_check_enabled = false  (bool)
  storage.model = ''  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.requires_eject = false  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'PC Floppy Drive'  (string)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'uid='} (string list)

udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/eisa.0'  (string)
  platform.id = 'eisa.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_dock_0'
  info.docked = false  (bool)
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

udi = '/org/freedesktop/Hal/devices/platform_dcdbas'
  info.linux.driver = 'dcdbas'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (dcdbas)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_dcdbas'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/dcdbas'  (string)
  platform.id = 'dcdbas'  (string)

udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'  (string)
  platform.id = 'Fixed MDIO bus.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978'
  info.linux.driver = 'ES1968 (ESS Maestro)'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ES1978 Maestro 2E'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978'  (string)
  info.vendor = 'ESS Technology'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'  (string)
  pci.product = 'ES1978 Maestro 2E'  (string)
  pci.product_id = 6520  (0x1978)  (int)
  pci.subsys_product_id = 158  (0x9e)  (int)
  pci.subsys_vendor = 'Dell'  (string)
  pci.subsys_vendor_id = 4136  (0x1028)  (int)
  pci.vendor = 'ESS Technology'  (string)
  pci.vendor_id = 4701  (0x125d)  (int)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978'  (string)
  info.product = 'ESS ES1978 (Maestro 2E) Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'ESS ES1978 (Maestro 2E)'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_7'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/pcmC0D0p'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_6'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/pcmC0D0c'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_5'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/mixer'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_4'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/midiC0D0'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_3'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/midi'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_2'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/dsp'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_1'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/dmmidi'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/controlC0'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0_sound_unknown'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/sound/card0/audio'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_125d_1978_sound_card_0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7113'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82371AB/EB/MB PIIX4 ACPI'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7113'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.3'  (string)
  pci.product = '82371AB/EB/MB PIIX4 ACPI'  (string)
  pci.product_id = 28947  (0x7113)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7112'
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82371AB/EB/MB PIIX4 USB'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7112'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2'  (string)
  pci.product = '82371AB/EB/MB PIIX4 USB'  (string)
  pci.product_id = 28946  (0x7112)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7112'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:07.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

---

### Post by jasloper on 2010-05-09
and the second part .....

udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2'  (string)
  info.product = 'Mouse'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial'  (string)
  info.vendor = 'Dell Computer Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 272  (0x110)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Mouse'  (string)
  usb_device.product_id = 12800  (0x3200)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Dell Computer Corp.'  (string)
  usb_device.vendor_id = 16700  (0x413c)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 272  (0x110)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 12800  (0x3200)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Dell Computer Corp.'  (string)
  usb.vendor_id = 16700  (0x413c)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0'  (string)
  info.product = 'Dell Dell USB Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_413c_3200_noserial_if0'  (string)
  input.product = 'Dell Dell USB Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_07_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0'  (string)
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
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:07.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111'
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82371AB/EB/MB PIIX4 IDE'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 128  (0x80)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1'  (string)
  pci.product = '82371AB/EB/MB PIIX4 IDE'  (string)
  pci.product_id = 28945  (0x7111)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host1/target1:0:0/1:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 1  (0x1)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'CD-ROM XM-1902B'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'TOSHIBA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_CD_ROM_XM_1902B'
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CD_ROM_XM_1902B'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'CD-ROM XM-1902B'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_CD_ROM_XM_1902B'  (string)
  info.vendor = 'TOSHIBA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host1/target1:0:0/1:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = false  (bool)
  storage.cdrom.cdrw = false  (bool)
  storage.cdrom.dvd = false  (bool)
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
  storage.cdrom.write_speed = 0  (0x0)  (int)
  storage.cdrom.write_speeds = {} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = '1A15'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'CD-ROM XM-1902B'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'TOSHIBA'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host1/target1:0:0/1:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'FUJITSU MHG2102A'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0'  (string)
  info.product = 'FUJITSU MHG2102A'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = 'B015'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'FUJITSU MHG2102A'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 10056130560  (0x257646000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'FUJITSU_MHG2102AT_01084901'  (string)
  storage.size = 10056130560  (0x257646000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
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
  volume.partition.media_size = 10056130560  (0x257646000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 9574225920  (0x23aab1800)  (uint64)
  volume.partition.type = '0x05'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_f3de6cd8_92ce_4ed3_a227_32d0d26e0267'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_f3de6cd8_92ce_4ed3_a227_32d0d26e0267'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
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
  volume.num_blocks = 931707  (0xe377b)  (uint64)
  volume.partition.media_size = 10056130560  (0x257646000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 9574258176  (0x23aab9600)  (uint64)
  volume.size = 477033984  (0x1c6ef600)  (uint64)
  volume.uuid = 'f3de6cd8-92ce-4ed3-a227-32d0d26e0267'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_46f56d14_eb18_4899_90b9_e3bbf730e37f'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MHG2102AT_01084901'  (string)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_46f56d14_eb18_4899_90b9_e3bbf730e37f'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
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
  volume.num_blocks = 18699597  (0x11d554d)  (uint64)
  volume.partition.media_size = 10056130560  (0x257646000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.size = 9574193664  (0x23aaa9a00)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '46f56d14-eb18-4899-90b9-e3bbf730e37f'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7111_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.1/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7110'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82371AB/EB/MB PIIX4 ISA'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7110'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0'  (string)
  pci.product = '82371AB/EB/MB PIIX4 ISA'  (string)
  pci.product_id = 28944  (0x7110)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_104c_ac1c_0'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PCI1225'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_104c_ac1c_0'  (string)
  info.vendor = 'Texas Instruments'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1'  (string)
  pci.product = 'PCI1225'  (string)
  pci.product_id = 44060  (0xac1c)  (int)
  pci.subsys_product_id = 158  (0x9e)  (int)
  pci.subsys_vendor = 'Dell'  (string)
  pci.subsys_vendor_id = 4136  (0x1028)  (int)
  pci.vendor = 'Texas Instruments'  (string)
  pci.vendor_id = 4172  (0x104c)  (int)

udi = '/org/freedesktop/Hal/devices/pci_104c_ac1c'
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PCI1225'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_104c_ac1c'  (string)
  info.vendor = 'Texas Instruments'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'  (string)
  pci.product = 'PCI1225'  (string)
  pci.product_id = 44060  (0xac1c)  (int)
  pci.subsys_product_id = 158  (0x9e)  (int)
  pci.subsys_vendor = 'Dell'  (string)
  pci.subsys_vendor_id = 4136  (0x1028)  (int)
  pci.vendor = 'Texas Instruments'  (string)
  pci.vendor_id = 4172  (0x104c)  (int)

udi = '/org/freedesktop/Hal/devices/pci_168c_13'
  info.linux.driver = 'ath5k'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_104c_ac1c'  (string)
  info.product = 'Atheros AR5001X+ Wireless Network Adapter'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)
  info.vendor = 'Atheros Communications Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0'  (string)
  pci.product = 'Atheros AR5001X+ Wireless Network Adapter'  (string)
  pci.product_id = 19  (0x13)  (int)
  pci.subsys_product_id = 23808  (0x5d00)  (int)
  pci.subsys_vendor = 'Netgear'  (string)
  pci.subsys_vendor_id = 4997  (0x1385)  (int)
  pci.vendor = 'Atheros Communications Inc.'  (string)
  pci.vendor_id = 5772  (0x168c)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_1f_33_31_68_22_0'
  info.capabilities = {'net', 'net.80211control'} (string list)
  info.category = 'net.80211control'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_33_31_68_22_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wmaster0'  (string)
  net.address = '00:1f:33:31:68:22'  (string)
  net.arp_proto_hw_id = 801  (0x321)  (int)
  net.interface = 'wmaster0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_1f_33_31_68_22'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_33_31_68_22'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/wlan0'  (string)
  net.80211.mac_address = 134002862114  (0x1f33316822)  (uint64)
  net.address = '00:1f:33:31:68:22'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)

udi = '/org/freedesktop/Hal/devices/pci_168c_13_rfkill_phy0_wlan'
  info.addons.singleton = {'hald-addon-rfkill-killswitch'} (string list)
  info.capabilities = {'killswitch'} (string list)
  info.category = 'killswitch'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.KillSwitch'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_13'  (string)
  info.product = 'phy0 wlan Killswitch'  (string)
  info.subsystem = 'rfkill'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_13_rfkill_phy0_wlan'  (string)
  info.vendor = 'Atheros Communications Inc.'  (string)
  killswitch.access_method = 'rfkill'  (string)
  killswitch.name = 'phy0'  (string)
  killswitch.state = 1  (0x1)  (int)
  killswitch.type = 'wlan'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'rfkill'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/ieee80211/phy0/rfkill0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_7191'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '440BX/ZX/DX - 82443BX/ZX/DX AGP bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7191'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.product = '440BX/ZX/DX - 82443BX/ZX/DX AGP bridge'  (string)
  pci.product_id = 29073  (0x7191)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4c4d'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7191'  (string)
  info.product = 'Rage Mobility P/M AGP 2x'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4c4d'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.product = 'Rage Mobility P/M AGP 2x'  (string)
  pci.product_id = 19533  (0x4c4d)  (int)
  pci.subsys_product_id = 158  (0x9e)  (int)
  pci.subsys_vendor = 'Dell'  (string)
  pci.subsys_vendor_id = 4136  (0x1028)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_7190'
  info.linux.driver = 'agpgart-intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '440BX/ZX/DX - 82443BX/ZX/DX Host bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_7190'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = '440BX/ZX/DX - 82443BX/ZX/DX Host bridge'  (string)
  pci.product_id = 29072  (0x7190)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_7190'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 84 device(s) from the Global Device List.
------------------------------------------------

---

### Post by pi/roman on 2010-05-10
That's not good.

Your touchpad is not being recognized properly. I'm guessing it's an Alps touchpad as this is a typical problem for them. Do a search for "Alps touchpad recognize" in the forums here and you will see.

This looks to be what is supposed to be your touchpad:

> udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'
info.linux.driver = 'i8042 aux' (string)
info.parent = '/org/freedesktop/Hal/devices/computer' (string)
info.product = 'PS/2 Port for PS/2-style Mice' (string)
info.subsystem = 'pnp' (string)
info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13' (string)
linux.hotplug_type = 2 (0x2) (int)
linux.subsystem = 'pnp' (string)
linux.sysfs_path = '/sys/devices/pnp0/00:0b' (string)
pnp.description = 'PS/2 Port for PS/2-style Mice' (string)
pnp.id = 'PNP0f13' (string)You could also do a search for "PNP0f13" and you may come up with information specific to your problem.

---

### Post by jasloper on 2010-05-11
That would explain why the synaptics "fixes" didn't work... I'll check on that.  Thanks for the help....  would upgrading to 10.04 help with this?

---

### Post by pi/roman on 2010-05-11
If your touchpad were recognized correctly the synaptics driver should be able to operate it, at least from what I've heard.  I don't have one of these touchpads.  An alternate distribution may be able to work properly but I don't really know.  That would be something to look for in the forums.

---

### Post by jasloper on 2010-05-19
OK - I'm hoping I'm not being too hasty about this, but upgrading to 10.04 appears to have resolved the touchpad issue.   I have booted the laptop 5 times and the touchpad is working!!!:P

Be prepared for several hours for the upgrade, though.....

---

### Post by jasloper on 2010-05-24
Just an update, in the event anyone is following the this string...... no problems with the touchpad since the upgrade!!!   It has worked on every subsequent boot!!!   :guitar:

---

