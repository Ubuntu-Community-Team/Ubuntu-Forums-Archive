---
title: "Synaptics touchpad stopped working without apparent reason"
date: 2009-06-26
forum: Hardware
---

### Post by Einsamkeit on 2009-06-26
Yesterday, the Synaptics touchpad on my Acer AspireOne simply stopped working without notice. One moment it was working fine, seconds later, totally unresponsive, may it be the pad or the left/right click buttons. It's been unfunctional ever since, even after a few reboots.

I've searched for an answer all morning, either the problems the others had wasn't the same as I did or the solutions failed.

Now, from xinput I know that the device is detected:
> "PS/2 Generic Mouse"    id=7    [XExtensionPointer]
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
        Resolution is 1And since literally nothing changed between the time that it worked and the moment after, I'm kinda lost. 
At first, from a layman's perspective, I thought that having Axis Min&Max values could cause the problem, simply out of the fact that that only terminal-ish setting experience I have comes from my TI graph.calc. and in there, similar Min&Max spits out errors like it's Mardi Gras, but apparently that's normal (the values from xinput) so I guess the problem eludes me.

Anyone has a clue? Any input is greatly welcomed, I'm working alot with my netbook and have the touchpad out of the game is a major problem..

Oh, also, I'm using an up-to-date 9.04 UNR install, nothing tweaked out of the ordinary, if that can be of any help.

---

### Post by Einsamkeit on 2009-06-27
Desperate bump. :(

---

### Post by Ayuthia on 2009-06-27
I am not for sure if this will help confirm anything or not, but have you tried xidump?  
```
xidump --list
```will list out the input devices that X sees and
```
xidum -v name-of-device
```will bring up a screen that will show some feedback when you use that device.  So if it is your mousepad, it should give something like this:
```

InputDevice: SynPS/2 Synaptics TouchPad    Valuators: Relative
             x-axis    y-axis
     data:
      min:  +01472    +01408
      max:  +05472    +04448
      res:  +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:

```If things are working, it will provide some numbers in the data line when you use the touchpad.  The Buttons will respond if you left click or right click.

If nothing happens, have you checked Xorg.0.log to see if it is being used with the synaptics driver?  You might also check dmesg.

Some other things that I am guessing that you have checked--Do you have an on/off button for the touchpad?  Have you checked in the BIOS just in case it somehow flipped it off?  If you are dual-booting, have you checked with the other OS to see if it is running?  You can also try it out with a liveCD if you have one handy.

---

### Post by Einsamkeit on 2009-06-27
> **Ayuthia said:**
> I am not for sure if this will help confirm anything or not, but have you tried xidump?  
```
xidump --list
```will list out the input devices that X sees and
```
xidum -v name-of-device
```will bring up a screen that will show some feedback when you use that device.  So if it is your mousepad, it should give something like this:
```

InputDevice: SynPS/2 Synaptics TouchPad    Valuators: Relative
             x-axis    y-axis
     data:
      min:  +01472    +01408
      max:  +05472    +04448
      res:  +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:

```If things are working, it will provide some numbers in the data line when you use the touchpad.  The Buttons will respond if you left click or right click.

If nothing happens, have you checked Xorg.0.log to see if it is being used with the synaptics driver?  You might also check dmesg.

Some other things that I am guessing that you have checked--Do you have an on/off button for the touchpad?  Have you checked in the BIOS just in case it somehow flipped it off?  If you are dual-booting, have you checked with the other OS to see if it is running?  You can also try it out with a liveCD if you have one handy.

I didn't have xidump, but I installed it.
Here's the output of xidump --list:
> marc-andre@TheSofaOfReasonableComfort:~$ xidump --list
Virtual core pointer           disabled
Virtual core keyboard          keyboard
AT Translated Set 2 keyboard   extension
Video Bus                      extension
Macintosh mouse button emulation extension
PS/2 Generic Mouse             extension
Primax Electronics Dynex Wireless Optical Mouse extension
Upon typing "xidump -v PS/2 Generic Mouse" I get an error, unknown argument "Generic", I'm guessing I have the syntax wrong writing the device name.

The Primax mouse is the USB mini-mouse I'm using as a replacement for the touchpad, I've tried the touchpad without it and seen no changes, so having it on is not part of the problem.

As for the questions:
- I don't have any button for the touchpad, except a "FN-F7" shortcut to enable/disable the touchpad, but I've tried it already.
- My BIOS doesn't have anything mentionning the touchpad.
- I'm not Dual-Booting on my laptop, I've tried it with Ubuntu, Kubuntu & Xubuntu, no changes.

Could the touchpad being detected as a Generic Mouse device be the problem? It seems to have been that way before, at the time it was working, but perhaps it's a lead to something else.

Thanks alot for your answer! Clues shedding light on the problem.

EDIT: Could the Virtual Core Pointer being disabled be the problem?? If so, any idea on how to enable it?

---

### Post by Ayuthia on 2009-06-27
> **Einsamkeit said:**
> I didn't have xidump, but I installed it.
Here's the output of xidump --list:
Upon typing "xidump -v PS/2 Generic Mouse" I get an error, unknown argument "Generic", I'm guessing I have the syntax wrong writing the device name.

The Primax mouse is the USB mini-mouse I'm using as a replacement for the touchpad, I've tried the touchpad without it and seen no changes, so having it on is not part of the problem.

As for the questions:
- I don't have any button for the touchpad, except a "FN-F7" shortcut to enable/disable the touchpad, but I've tried it already.
- My BIOS doesn't have anything mentionning the touchpad.
- I'm not Dual-Booting on my laptop, I've tried it with Ubuntu, Kubuntu & Xubuntu, no changes.

Could the touchpad being detected as a Generic Mouse device be the problem? It seems to have been that way before, at the time it was working, but perhaps it's a lead to something else.

Thanks alot for your answer! Clues shedding light on the problem.

EDIT: Could the Virtual Core Pointer being disabled be the problem?? If so, any idea on how to enable it?

My Virtual Core Pointer is currently disabled also so it is not the problem.  You can try to see if you can access the Generic Mouse by doing the following:
```
xidump -v PS/2\ Generic\ Mouse\ extension
```This will let the system know that the spaces belong to the name instead of being an extra command.

Did you say that you checked /var/log/Xorg.0.log?  It should tell you if it tried to install the synaptics driver for it.

---

### Post by Einsamkeit on 2009-06-27
> **Ayuthia said:**
> My Virtual Core Pointer is currently disabled also so it is not the problem.  You can try to see if you can access the Generic Mouse by doing the following:
```
xidump -v PS/2\ Generic\ Mouse\ extension
```This will let the system know that the spaces belong to the name instead of being an extra command.

Did you say that you checked /var/log/Xorg.0.log?  It should tell you if it tried to install the synaptics driver for it.

The xidump output:
> InputDevice: PS/2 Generic Mouse
Valuators: Relative   ID: Unreported  Serial Number: Unreported

             x-axis    y-axis
     data:
      min:  -00001    -00001
      max:  -00001    -00001
      res:  +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:
As for Xorg.0.log, it has no mention at all of Synaptics, it mentions the PS/2 Generic Mouse a lot tho.

EDIT: Also, no changes when buttons are pressed / touchpad touched.

---

### Post by Ayuthia on 2009-06-27
I am not for sure if I have this command correct or not, but can you try the following:
```
hal-device $(hal-find-by-property --key info.product --string 'PS/2 Generic Mouse')
```
It will produce some information about your mouse and how HAL sees it.

---

### Post by Einsamkeit on 2009-06-27
> **Ayuthia said:**
> I am not for sure if I have this command correct or not, but can you try the following:
```
hal-device $(hal-find-by-property --key info.product --string 'PS/2 Generic Mouse')
```It will produce some information about your mouse and how HAL sees it.

Output: 
> marc-andre@TheSofaOfReasonableComfort:~$ hal-device $(hal-find-by-property --key info.product --string 'PS/2 Generic Mouse')
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port_logicaldev_input'
  access_control.file = '/dev/input/event9'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = { 'hal-acl-tool --add-device' } (string list)
  info.callouts.remove = { 'hal-acl-tool --remove-device' } (string list)
  input.device = '/dev/input/event9'  (string)
  input.product = 'PS/2 Generic Mouse'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio2/input/input9/event9'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'PS/2 Generic Mouse'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port_logicaldev_input'  (string)
  input.x11_driver = 'evdev'  (string)
  info.category = 'input'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse', 'access_control' } (string list)

I guess that if I try to install the Synaptics drivers, the touchpad could be recognized as Synaptics instead of Generic Mouse?
Running a search to install those as I speak.

EDIT: The drivers seem to be installed already.

---

### Post by Ayuthia on 2009-06-27
You might want to check and see if the following are installed:
synaptic
xserver-xorg-input-synaptics

Those are the two that are currently installed on my laptop.

If it is, it might just be a matter of updating the .fdi entry for your mouse.

---

### Post by Einsamkeit on 2009-06-27
> **Ayuthia said:**
> You might want to check and see if the following are installed:
synaptic
xserver-xorg-input-synaptics

Those are the two that are currently installed on my laptop.

If it is, it might just be a matter of updating the .fdi entry for your mouse.

They are indeed installed.
.fdi entry?

---

### Post by Ayuthia on 2009-06-27
You might also create a file called /etc/hal/fdi/policy/20thirdparty/11-mouse.fdi:
```
sudo mkdir /etc/hal/fdi/policy/20thirdparty
gksu gedit /etc/hal/fdi/policy/20thirdparty/11-mouse.fdi
```
and have it contain the following information:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="PS/2 Generic Mouse">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

```
This is based off of /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi but modified to have it search for this mouse name.

I did not test this out, but it should work (at least change the x11-driver entry to synaptics).  You will have to reboot or try the following:
```
sudo /etc/init.d/hal restart
```Log out and then log back in.

What the .fdi file is going to do is when the system finds this mouse, it is going to load the synaptics driver instead of evdev.

---

### Post by Einsamkeit on 2009-06-28
> **Ayuthia said:**
> You might also create a file called /etc/hal/fdi/policy/20thirdparty/11-mouse.fdi:
```
sudo mkdir /etc/hal/fdi/policy/20thirdparty
gksu gedit /etc/hal/fdi/policy/20thirdparty/11-mouse.fdi
```and have it contain the following information:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="PS/2 Generic Mouse">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

```This is based off of /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi but modified to have it search for this mouse name.

I did not test this out, but it should work (at least change the x11-driver entry to synaptics).  You will have to reboot or try the following:
```
sudo /etc/init.d/hal restart
```Log out and then log back in.

What the .fdi file is going to do is when the system finds this mouse, it is going to load the synaptics driver instead of evdev.

I've made the changes & rebooted, but the touchpad is still dead. :(

I had to install gedit, since I'm now under Xubuntu (was under standard Ubuntu when the problem began, then switched to Xubuntu to see if it would help anything, then decided to stay under Xub.) and didn't bother to find Xubuntu's alternative.

I'm beginning to consider taking it back to the store, since I have a plan that covers faulty hardware they might be able to fix it if it's a hardware failure. Altho an hardware failure, under no special stress, no special conditions at all, seems rather uncommon.

EDIT: "xidump" still detects the device as a PS/2 Generic Mouse too.

---

### Post by Ayuthia on 2009-06-28
It sounds like it might be a hardware issue.  I would think that if synaptics failed, the evdev driver would have worked, but you would have lost some of the touchpad functionality.  In this scenario, it looks like it does not recognize it as a touchpad at all.  The hal info does not show input.touchpad in the info.capabilities section.

You might look through:
```
lshal|less
``` and see if you can find any other hardware that has the capabilities of input.touchpad.  Just press q to get out of the command.

---

### Post by Einsamkeit on 2009-06-28
> **Ayuthia said:**
> It sounds like it might be a hardware issue.  I would think that if synaptics failed, the evdev driver would have worked, but you would have lost some of the touchpad functionality.  In this scenario, it looks like it does not recognize it as a touchpad at all.  The hal info does not show input.touchpad in the info.capabilities section.

You might look through:
```
lshal|less
``` and see if you can find any other hardware that has the capabilities of input.touchpad.  Just press q to get out of the command.

I went thru the list, it listed 102 devices but none had info.capabilities input.touchpad.

EDIT: Today I've taken the thing to the shop, free delivery to Acer & back, should have it in 1-3 weeks. Thanks a lot for your help tho, even if it didn't work, I learned some things and could even argue better with the Geek Squad representative who was checking my problem out. :)

---

