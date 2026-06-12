---
title: "Fujitsu siemens T4210 Taplet PC: Pen not working"
date: 2009-11-10
forum: Hardware
---

### Post by dheym on 2009-11-10
Hello.

Just installed fresh copy of ubuntu 9.10 on my Fujitsu siemens T4210 Taplet PC. At first the taplet-pen **did work** perfectly, but not this time at this reboot. Havent changed anything, the only thing i have done is installed wine. I have googled and did my best to find information, but i find it confusing and i'm not sure what to do.

So, what to do?

---

### Post by dheym on 2009-11-11
Still not working. Is the solution to follow parts of theguide at this site: [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/) ?

Don't want to mess anything up.

---

### Post by dheym on 2009-11-13
No one? (Sorry for bumping)

---

### Post by dheym on 2009-11-25
Last bump :(

---

### Post by Favux on 2009-11-25
Hi dheym,

That has happened to others with serial Wacom digitizers.  Is that what you have?  There are a couple of bug reports.  It apparently only affects 64-bit Karmic and 32-bit Karmic works fine.  Are you using 64-bit?

---

### Post by dheym on 2009-11-26
Favux: How do i tell? I *think* it's serial. 
How do i know if i have 32-bit or 64-bit Karmic?

---

### Post by Favux on 2009-11-26
Hi dheym,

Your Fujitsu T4219 probably has a serial Wacom digitizer that is identified in the .fdi (or lshal) with "FUJ02e5".  So the digitizer won't show up in "lsusb" but should in "lspci".

To find out if it is 32-bit or 64-bit:
```
uname -m
```

For your tablet you could skim over these threads:

[http://ubuntuforums.org/showthread.php?t=1136848](http://ubuntuforums.org/showthread.php?t=1136848)

[http://ubuntuforums.org/showthread.php?t=1075239](http://ubuntuforums.org/showthread.php?t=1075239)

---

### Post by dheym on 2009-11-26
Favux:
uname -m gives me:
i686
> 
Your Fujitsu T4219 probably has a serial Wacom digitizer that is identified in the .fdi (or lshal) with "FUJ02e5". So the digitizer won't show up in "lsusb" but should in "lspci".

I wrote lshal in terminal but the text didn't have FUJ02e5, lsusb or lspci in it.

Thanks for the threads but i don't want do do anything wrong, i'm new to ubuntu. I have tried to make it work a couple of times but failed.

---

### Post by Favux on 2009-11-26
Hi dheym,

OK, so you have a 32-bit install.

In a terminal enter (copy and paste) the following.
```
lsusb
```
```
lspci
```
```
xinput --list
```
```
 more /proc/bus/input/devices
```
And see if anything talks about the digitizer, Fujitsu or FUJ02e5.

To get a searchable lshal:
```
lshal>dheym_lshal.txt
```
Open in Text Editor (gedit) and use in Find FUJ02e5.

---

### Post by dheym on 2009-11-26
Favux: Ok, when ```
xinput --list
``` i get ```
"PnP Device (FUJ02e5)"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
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
"PnP Device (FUJ02e5) eraser"    id=3    [XExtensionKeyboard]
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

```And in the LSHAL i can find: ```
udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
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
  linux.sysfs_path = '/sys/devices/pnp0/00:04/tty/ttyS0'  (string)
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
```

And the pen randomely started working again.. but i havent changed anything.. it will probaly go away later.

---

### Post by dheym on 2009-12-25
Favux?

---

### Post by Favux on 2009-12-25
Hi dheym,

Oops!  I'm sorry I forgot you.  :(  I must have thought you were another Fujitsu thread.

OK, make sure you have all the latest updates through Update Manager.  Some are reporting the latest udpdates fixed the problem.  Then install one of the two .fdi's at the bottom of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Instructions are in Section 2 b).

Then you should be able to use wacomcpl (Section 3)).  Good luck!

---

### Post by dheym on 2009-12-28
Favux: I followed the steps and installed the Favux_new-generic_rc2_10-linuxwacom.fdi But now only the eraser works on the pen. When i do 
"xsetwacom list"

I get: 

"eraser           eraser"


The eraser also shows up in the wacomcpl-box. What went wrong you think? I have a backup of the original .fdi.

---

### Post by Favux on 2009-12-28
Hi dheym,

That's not the .fdi, that's the stylus bug.  The eraser means the .fdi is working.

OK, some say restarting X fixes it for them.  Directions in [post #654]("http://ubuntuforums.org/showpost.php?p=8424078&postcount=654").

You might want to look at [raccoonone's thread]("http://ubuntuforums.org/showthread.php?t=1358524").  He got it working.  Check out if it is actually hiding in a corner like he says.  Then his .xinitrc could be helpful.

Also you could look at some of the bug reports and maybe post on them:

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181)

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997)

---

### Post by dheym on 2009-12-28
Ok, first I tested the other favux-.fdi. Then i restarted X. Now xsetwacom list gives stylus and eraser. :)

Thank you for all your help btw, much appreciated!

---

### Post by Favux on 2009-12-28
Hi dheym,

That's great!  :)  You are welcome.

---

### Post by Jaguar13 on 2010-02-04
Thank you all, for helpfull information, I also get my T4210 work on Karmic 9.10.

Jut to help other T4210 users save time:

1. ```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```2. Download > **dheym said:**
> <...>other favux-.fdi. <...> - [Favux_serial-tablet&tablet-pc_test2_10-wacom.fdi.txt]("http://ubuntuforums.org/attachment.php?attachmentid=140255&d=1261034609") from Favux [HOWTO]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

3. Follow Section 2 b, from Favux [HOWTO]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012").

4. Thank Favux for working pen on your T4210 ;).

---

