---
title: "Genius G-Pen F610 Pen Buttons Not Working"
date: 2010-03-16
forum: Hardware
---

### Post by CuriousCurmudge on 2010-03-16
I am having problems getting the pen buttons to work with a Genius G-Pen F610 in Ubuntu 9.10 64-bit. I had no problems getting it to recognize input, but have had no luck getting it to register clicks. I have installed wacom-tools. Below is what I hope to be relevant information to solve this problem.

Running "xinput list" showed that tablet is being recognized as a keyboard device, which seems like it could be the problem.
```

xinput list

"Virtual core pointer"    id=0    [XPointer]
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
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"WALTOP International Corp. Slim Tablet"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 13
    Num_axes is 20
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 10000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 10000
    Axis 3 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 4 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 5 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 6 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 7 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 8 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 9 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 10 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 11 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 12 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 13 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 14 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 15 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 16 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 17 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 18 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 19 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
"HID 05f3:0007"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"HID 05f3:0007"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=7    [XExtensionPointer]
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
"MosArt Optical Mouse"    id=8    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 7
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
</blockquote>

```Running "xinput test 2" does recognize motion, but not button clicks.
```

xinput test 2

motion a[0]=10788 a[1]=5194 
motion a[0]=10777 a[1]=5159 
motion a[0]=10730 a[1]=5088 
motion a[0]=10673 a[1]=5017 
motion a[0]=10628 a[1]=4960 
motion a[0]=10595 a[1]=4907 
motion a[0]=10570 a[1]=4846 
motion a[0]=10546 a[1]=4787 
motion a[0]=10521 a[1]=4756 

```Getting the button map and the query state shows more things that look weird because of it being recognized as a keyboard.
```

xinput get-button-map 2 

1 2 3 4 5 6 7 8 9 10 11 12 13 

xinput query-state 2

3 classes :
KeyClass
    key[0]=up
    key[1]=up
    key[2]=up
    key[3]=up
    ...
    key[245]=up
    key[246]=up
    key[247]=up
ButtonClass
    button[1]=up
    button[2]=up
    ...
    button[12]=up
    button[13]=up
ValuatorClass Mode=Absolute Proximity=In
    valuator[0]=9356
    valuator[1]=4409
    valuator[2]=0
    ...
    valuator[18]=0
    valuator[19]=0

``````

lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 172f:0034                  <--Tablet???
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 062a:0003 Creative Labs 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05f3:0007 PI Engineering, Inc. Kinesis Advantage PRO MPC/USB Keyboard
Bus 001 Device 003: ID 05f3:0081 PI Engineering, Inc. Kinesis Integrated Hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Below is some more information.

```

xorg.conf

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "hp f1503"
    HorizSync       30.0 - 63.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1024+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

``````

lshal

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  info.product = 'WALTOP International Corp. Slim Tablet'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.options = 'lv3:ralt_switch'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input3/event3'  (string)

``````

less /var/log/Xorg.0.log | grep -i waltop

(II) config/hal: Adding input device WALTOP International Corp. Slim Tablet
(**) WALTOP International Corp. Slim Tablet: always reports core events
(**) WALTOP International Corp. Slim Tablet: Device: "/dev/input/event3"
(II) WALTOP International Corp. Slim Tablet: Found 9 mouse buttons
(II) WALTOP International Corp. Slim Tablet: Found x and y relative axes
(II) WALTOP International Corp. Slim Tablet: Found scroll wheel(s)
(II) WALTOP International Corp. Slim Tablet: Found x and y absolute axes
(II) WALTOP International Corp. Slim Tablet: Found absolute touchpad
(II) WALTOP International Corp. Slim Tablet: Found keys
(II) WALTOP International Corp. Slim Tablet: Configuring as touchpad
(II) WALTOP International Corp. Slim Tablet: Configuring as keyboard
(**) WALTOP International Corp. Slim Tablet: YAxisMapping: buttons 4 and 5
(**) WALTOP International Corp. Slim Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "WALTOP International Corp. Slim Tablet" (type: KEYBOARD)
(WW) WALTOP International Corp. Slim Tablet: touchpads and touchscreens ignore relative axes.
(**) WALTOP International Corp. Slim Tablet: (accel) keeping acceleration scheme 1
(**) WALTOP International Corp. Slim Tablet: (accel) filter chain progression: 2.00
(**) WALTOP International Corp. Slim Tablet: (accel) filter stage 0: 20.00 ms
(**) WALTOP International Corp. Slim Tablet: (accel) set acceleration profile 0
(II) WALTOP International Corp. Slim Tablet: initialized for absolute axes.
(WW) WALTOP International Corp. Slim Tablet: unable to handle keycode 331

``````

xsetwacom list
 ### nothing ###

```For those brave enough to have made it this far I congratulate you. I just spent about four hours trying to get this to work so any suggestions are appreciated.

---

### Post by Fir3chi3f on 2010-03-17
I'm not sure if this applies to 9.10 but have you installed xserver-xorg-input-wacom?


[http://art.ubuntuforums.org/showthread.php?t=1261407](http://art.ubuntuforums.org/showthread.php?t=1261407)

---

### Post by CuriousCurmudge on 2010-03-17
Yes, I have installed xserver-xorg-input-wacom.

---

### Post by CuriousCurmudge on 2010-03-17
I also tried installing                 xserver-xorg-input-wizardpen ([https://launchpad.net/~doctormo/+archive/xorg-wizardpen]("https://launchpad.net/%7Edoctormo/+archive/xorg-wizardpen")), but didn't have any luck with that. The information I can find is very confusing as to whether this will work with the G-Pen F610.

Here is the content of my 99-x11-wizardpen.fdi. I was able to calibrate using "wizardpen-calibrate". It still seems to me the most likely problem is that "xinput list" says my tablet is of type keyboard.
```

<?xml version=”1.0&#8243; encoding=”ISO-8859-1&#8243; ?>
<deviceinfo version=”0.2&#8243;>
    <device>
        <!– This MUST match with the name of your tablet –>
        <match key=”info.product” contains=”WALTOP International Corp. Slim Tablet”>
        <merge key=”input.x11_driver” type=”string”>wizardpen</merge>
        <merge key=”input.x11_options.SendCoreEvents” type=”string”>true</merge>
        <merge key=”input.x11_options.TopX” type=”string”>218</merge>
        <merge key=”input.x11_options.TopY” type=”string”>0</merge>
        <merge key=”input.x11_options.BottomX” type=”string”>20000</merge>
        <merge key=”input.x11_options.BottomY” type=”string”>12395</merge>
        <merge key=”input.x11_options.MaxX” type=”string”>20000</merge>
        <merge key=”input.x11_options.MaxY” type=”string”>12395</merge>
        <merge key=”info.product” type=”string”>stylus</merge>
    </match>
    </device>
</deviceinfo>

```

---

### Post by CuriousCurmudge on 2010-03-19
What additional information can I give to help with this problem? I have looked through the forums here, but the following discussions/tutorials didn't solve my problem.

[http://ubuntuforums.org/showthread.php?t=1108207](http://ubuntuforums.org/showthread.php?t=1108207)
[http://ubuntuforums.org/showthread.php?t=806824](http://ubuntuforums.org/showthread.php?t=806824)
[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)
[http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en](http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en)

I would prefer not to, but I might just reinstall to start from a clean slate.

---

### Post by tudor117 on 2010-03-21
Hi, I have the same problem as you. I still didn't fix the buttons. However, does your pressure work in karmic? Mine didn't and I had to fix it. Here's what I did so far [http://ubuntuforums.org/showthread.php?t=1261407]("http://ubuntuforums.org/showthread.php?t=1261407")
Hope you can figure it out because it's been killing me to have both buttons do the same thing.

---

### Post by CuriousCurmudge on 2010-03-22
> **tudor117 said:**
> Hi, I have the same problem as you. I still didn't fix the buttons. However, does your pressure work in karmic? Mine didn't and I had to fix it. Here's what I did so far [http://ubuntuforums.org/showthread.php?t=1261407](http://ubuntuforums.org/showthread.php?t=1261407)
Hope you can figure it out because it's been killing me to have both buttons do the same thing.
 
Thanks for the link. I looked through that thread initially, but with some more experience it seems more helpful now. Right now all I can do is move the cursor with the stylus. I can't click by pressing the stylus on the tablet or with either button.

The big difference I see is that xinput list for you lists four items for your tablet: eraser, cursor, pad, and just the tablet name. These are all listed as XExtensionPointers. Mine gives only the tablet and it is of type XExtensionKeyboard. Did you get your results just by installing wacom-tools and plugging the tablet in?

---

### Post by tudor117 on 2010-03-22
Sorry for being so vague. The link I gave you was from when I was using Jaunty. It seemed to work a lot better then. First off which Ubuntu are you using?
Second, definitely install all the wacom related stuff. It might not fix the problem, but its a step.
Then, change the wizardpen fdi so that it doesn't include your tablet and add your tablet to the wacom fdi. [_Here's_]("http://ubuntuforums.org/showpost.php?p=8350200&postcount=114") what my fdi looks like; also says where the fdi is located.
If you're using karmic, chances are that once you plug in the tablet, xorg will crash. That's ok, there's a small change we need to do to the wacom source.
You can grab the source from [Linux Wacom]("http://linuxwacom.sourceforge.net/") however its a newer version than the one ubuntu has. If you want the same version as ubuntu I have the source [_**HERE**_]("http://cid-22da660e7f9be118.skydrive.live.com/self.aspx/Tablet/linuxwacom-0.8.4-3.tar.bz2"). The code is already changed and should work once you built it. Don't forget to configure it because it was configured for my computer and I didn't remove the config. Configure it with:
```
./configure --prefix=/usr
```

If you use the new code, the wcmUSB file that should be changed is [_here_]("http://ubuntuforums.org/showpost.php?p=8244156&postcount=92") in the compressed file.

The command *wacomcpl* should allow you to configure your tablet. Good luck.

---

### Post by CuriousCurmudge on 2010-03-23
tudor, you are my personal hero right now. I now am in the same place you are I think. I can click with the tip, but both side buttons do the same thing. I just had to fix my wacom fdi and remove everything from the wizardpen fdi. I installed your patched linux wacom driver and it worked. I had gotten confused between various tutorials doing things differently. Thanks.

---

### Post by tudor117 on 2010-03-23
No problem.
Now if we only found a way to fix the button thing.

---

