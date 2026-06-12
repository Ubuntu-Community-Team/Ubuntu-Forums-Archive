---
title: "T4010 Touchscreen does not work"
date: 2010-08-31
forum: Hardware
---

### Post by jozze on 2010-08-31
Hello,

i just changed my OS from Windows Tablet to Ubuntu 9.10. After installing Ubuntu my touchscreen worked just fine, but after a reboot it stoped working. I googled this problem, but every help is just for Ubuntu 9.04... but Ubuntu 9.10 doesnt have a xorg.conf anymore... what do i have to do now?
Please help me.

Thanks a lot!
(PS: Sorry for my bad english... but i'm german :))

---

### Post by rekado on 2010-08-31
You say it worked before rebooting. I assume you didn't play with the settings after completing the install. Please boot the live CD and check if it works. If it does, then check out the xorg.conf and copy it to your installation.

You can still use a minimal xorg.conf in 9.10.

---

### Post by jozze on 2010-08-31
Thanks for the response.
I did'nt change any settings. I'll boot the live CD, when I'm home again. So the live CD has a xorg.conf or do i have to generate it or something like that?
What should I do, if it does'nt work there too?

---

### Post by rekado on 2010-08-31
The live CD is a complete system, including all configuration files. If the touchscreen does work when the live system is running, you should investigate the /etc directory. I'm not sure if 9.10 still uses HAL. If so, check out the HAL fdi files (/etc/hal/fdi/); there might just be one that instructs the system how to configure the touchscreen. Alternatively, there might be an xorg.conf or instead individual configuration segments in /etc/X11/xorg.conf.d/.
If none of these exist or none of them seem to have anything to do with your machine's touchscreen, investigate if there are udev rules in /etc/udev/rules.d/.

If your touchscreen doesn't work after booting from the live CD, then you've got no master configuration to model your installed system's configs after. In that case follow those instructions you said you found for 9.04; they might work.

(Maybe you could even start the other way around. If you want to learn more about your system, though, I encourage you to check out the three main sources for device configuration as described above.)

---

### Post by jozze on 2010-08-31
/etc/hal/fdi/ has no informations about my touchscreen... a directory /etc/X11/xorg.conf.d/ does not exist and there are no udefs defined to prevent the touchscreen from working...
the system doesn't contain a xorg.conf and the tutorial for ubuntu 9.04 depends on that. i heard, that if I would create a xorg.conf it would be recognized... but i just know what to change in the xorg.conf... but not the rest of the file... do i just need to create a file with these specific changes?

---

### Post by Favux on 2010-08-31
Hi jozze,

The Fujitsu Stylistic 4010 has a wacom serial digitizer.  I think you have a stylus/pen with an eraser and two side switches on the stylus.  It does not have touch, ie using a finger.  Is that correct?

In Karmic (9.10) you configure through HAL and the 10-linuxwacom.fdi file.  You can use the xorg.conf but it is not needed.

First check in Synaptic Package Manager that both xserver-xorg-input-wacom & wacom-tools are installed.  Wacom-tools will have the .fdi.  If not install them and reboot.  If installed tell Synaptic to reinstall them and then reboot.

---

### Post by jozze on 2010-08-31
Hi Favux,

I have a pen with two side switches... i can't see an indicator for an eraser... You can't use a finger to touch to control the screen.
I installed wacom-tools and reinstalled xserver-xorg-input-wacom and rebooted the system... but it still doesn't work.
Where can i find the .fdi from wacom-tools? Whereis just shows me the path of a .gz file.

Thanks

---

### Post by Favux on 2010-08-31
Hi jozze,

Actually the native linuxwacom.fdi doen't work with wacomcpl (wacom control panel).  Which is the configuration/calibration gui.  So try one of my modified .fdi's attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Instructions are in Section 3 b).

---

### Post by jozze on 2010-08-31
Hi Favux,

I follower all your instructions under 3b) but the list in wacomcpl is still empty... i did a backup of my original 10-linuxwacom.fdi and replaced the content with the content of the file you attached. after a reboot and entering the command "xinput --list" it doesn't show pen, eraser, stylus, or touch...
I realy don't know what to do... :(

---

### Post by Favux on 2010-08-31
First let's check Xorg.0.log in /var/log.  Compress it with Create Archive and then attach it to your next post with Manage Attachments.

Also let's look at the output of lshal, in a terminal:
```
lshal>jozze_lshal.txt
```

---

### Post by jozze on 2010-08-31
I attached both files - Thank you so much for your help!

[ATTACH]168091[/ATTACH]

[ATTACH]168092[/ATTACH]

---

### Post by Favux on 2010-08-31
Hi Jozze,

You're welcome.

The Xorg.0.log shows there is a problem with ISD4.
```
II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) stylus: always reports core events
(**) stylus device is /dev/ttyS0
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device stylus cursor
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/ttyS0
(**) stylus cursor is in relative mode
(**) stylus cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "stylus cursor"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device eraser
(**) eraser: always reports core events
(**) eraser device is /dev/ttyS0
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom ISDV4 control data (0) error in * query
(EE) Couldn't init device "eraser"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
```
Let's try changing the .fdi.  Go to the serial section and change:
```
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
```
to
```
	<merge key="input.x11_options.ForceDevice" type="string">SERIAL</merge>
```
and reboot.  If that doesn't work try removing the line altogether.

---

### Post by jozze on 2010-08-31
both don't work... first i changed the value and rebooted, but it didn't work and after deleting the line and rebooting it didn't work too. :(

---

### Post by Favux on 2010-08-31
OK, change it back to the original.

That doesn't leave us with a lot of choices.  What we can do is hope there is an error in the linuxwacom code which is preventing it from correctly reading the ISD4 protocol from your serial digitizer.  And hope the error was fixed in a later linuxwacom.

Or we could mess with xorg.conf and see if somehow we could get it working that way.  Or we could mess with the serial settings and see if flow control changes or whatever would get it reading it correctly.  I think both these options aren't so good.

My vote is you try updating linuxwacom and hope.  Follow Section 1 in the HOW TO and install linuxwacom 0.8.8-8.

---

### Post by jozze on 2010-08-31
ok, i tried Section 1 in the HOW TO and it recognizes something... i think its just not calibrated correctly... but i dont know how to calibrate it... wacomcpl still don't show a thing...

(i can move my curser over the whole screen, whenn ich just use the top left corner of my screen :/ )

---

### Post by jozze on 2010-08-31
ok... now its 1:15 am... i've got to go to work in a few hours --> sleep. Thanks again. I'll continue after work... maybe i just take my tablet-pc with me ;)

---

### Post by Favux on 2010-08-31
Great!  Progress.

Let's look at the output of:
```
xinput --list
```

Guten Abend.

---

### Post by jozze on 2010-09-01
Good Morning.
Woho! Perfect!
```
"PnP Device (FUJ02e5)" id=2 [XExtension Keyboard]
Type is Wacom Stylus.
...
```
It has been recognized but the resolution values are way to high.
```
Num_keys is 248
Min_keycode is 8
Max_keycode is 255
Num_buttons is 32
Num_axes is 6
Mode is Absolute
Motion_buffer is 256
Axis 0 :
Min_value is 0
Max_value is 0
Resolution is 2540
...
```

---

### Post by Favux on 2010-09-01
I've seen:
```
Resolution is 2540

```
before, just recently.  I think there may be a glitch in the wacom code.

Seeing:
```
"PnP Device (FUJ02e5)" id=2 [XExtension Keyboard]

```
usually indicates the wacom driver has the digitizer (the [XExtension Keyboard] part).  And it looks like the "Device name" for your stylus is:

stylus = "PnP Device (FUJ02e5)"

Does:
```
xsetwacom list
```
now show something?

---

### Post by jozze on 2010-09-01
No, it doesn't... wacomcpl still shows nothing...

---

### Post by jozze on 2010-09-01
... and xsetwacom list neigther btw. ;)

---

### Post by Favux on 2010-09-01
Hi Jozze,

Wacomcpl is the gui front end for xsetwacom.  So checking 'xsetwacom list' should be a quick way of checking whether wacomcpl will work.

Could you show me the complete output of?:
```
xinput --list
```

The modified .fdi I pointed you to should be giving "stylus" for the stylus instead of "PnP Device (FUJ02e5)".  But the wacomcpl in 0.8.8-8 shouldn't care either way.  It's been rewritten to handle the longer, more descriptive "Device names".

---

### Post by jozze on 2010-09-01
I attached the output from "xinput --list"
[ATTACH]168178[/ATTACH]

---

### Post by Favux on 2010-09-01
OK, that shows:

stylus = "PnP Device (FUJ02e5)"

eraser = "PnP Device (FUJ02e5) eraser"

Which looks correct.

But when you enter wacomcpl into a terminal the gui pops up but it is blank?  You should see those "Device names" in the 0.8.8-8 linuxwacom wacomcpl.  I don't understand why you aren't.  Unless you missed a dependency wacomcpl requires when you compiled linuxwacom 0.8.8-8.  But then I don't think the gui would pop up.

The stylus is working, correct?

It's clear you have the default 10-linuxwacom.fdi at /usr/share/hal/fdi/policy/20thirdparty/.  You should only have one wacom.fdi and it should be located there.  Also you should not have any wacom entries in xorg.conf.

Edit:  Actually, thinking about it, if you copied the 0.8.8-8 wacom.ko into place correctly then the name for the stylus should probably be:

"PnP Device (FUJ02e5) stylus"

So that's probably the problem.  You missed the copy (cp) command.

---

### Post by jozze on 2010-09-01
my stylus pen is working, because it's working, when i boot the live cd.
I don't have a xorg.conf.
I did copy the wacom file :
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 
```
The first cp command did not work, because the file in this directory didn't exist.

---

### Post by Favux on 2010-09-01
Let us look at your Xorg.0.log again after a fresh boot and see if that tells us what is going on.

---

### Post by jozze on 2010-09-01
here is the Xorg.0.log after a fresh reboot:
[ATTACH]168180[/ATTACH]

---

### Post by Favux on 2010-09-01
Well your new Xorg.0.log looks ok:
```
(II) config/hal: Adding input device PnP Device (FUJ02e5)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.8-8 $
(**) Option "Device" "/dev/ttyS0"
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5)" (type: Wacom Stylus)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) usbDetect: can not ioctl version
(WW) Wacom ISDV4 control data (0) error in * query
(==) Wacom using pressure threshold of 27 for button 1
(==) Wacom General ISDV4 tablet speed=9600 (38400) maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled
(II) config/hal: Adding input device PnP Device (FUJ02e5) eraser
(**) Option "Device" "/dev/ttyS0"
(**) PnP Device (FUJ02e5) eraser: always reports core events
(**) PnP Device (FUJ02e5) eraser device is /dev/ttyS0
(**) PnP Device (FUJ02e5) eraser is in absolute mode
(**) PnP Device (FUJ02e5) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (FUJ02e5) eraser: threshold = 27
(**) Option "BaudRate" "9600"
(**) PnP Device (FUJ02e5) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (FUJ02e5) eraser" (type: Wacom Eraser)
```
And it says it is linuxwacom 0.8.8-8.  We're still seeing a:
```
WW) Wacom ISDV4 control data (0) error in * query
```
error.  And again, I don't believe the resolution it is giving:
```
(==) Wacom General ISDV4 tablet speed=9600 (38400) maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled
```
Like I said earlier I've seen this before so I think there is a new bug in the code.

But why isn't wacomcpl working?  Let's look at the contents of your 10-linuxwacom.fdi.  Please post it.

---

### Post by jozze on 2010-09-01
here is the 10-linuxwacom.fdi
[ATTACH]168183[/ATTACH]

---

### Post by Favux on 2010-09-01
That looks like the latest wacom.fdi included in 0.8.8-8.  Let's try substituting one of my modified .fdi's attached to the linuxwacom HOW TO for it and see if it makes any difference.  Remember to reboot and remember to back it up first.  Also make sure there's only one wacom.fdi called 10-linuxwacom.fdi.

---

### Post by jozze on 2010-09-01
YEAH! This time my stylus works. wacomcpl shows pen and eraser!!!
Thank you sooooo much!
I hope it will work after a reboot... lets try...

---

### Post by jozze on 2010-09-01
NOOOOOOOOO! Again the same problem... How is this posible?

---

### Post by jozze on 2010-09-01
at least wacomcpl still shows stylus and eraser. but i can't calibrate it... it shows two squares that i'm trying to hit, but nothing happens...

---

### Post by Favux on 2010-09-01
Very strange!!!

It seems something may have gone wrong with the 0.8.8-8 compile.  The only thing I can think of is to try it again being very careful.  Let me know if there are any errors.

---

### Post by jozze on 2010-09-02
every time i do it nothing changes at all... is there a way do copy the configurations from my live cd? there it works just fine. can i somehow use these configurations?

---

### Post by jozze on 2010-09-02
This is, what xinput --list shows with my live cd:

```
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

```
Can i somehow transfer these configurations?

---

### Post by Favux on 2010-09-02
Hi jozze,

It looks like the default linuxwacom.fdi was reinstalled when you compiled.  Have you tried putting the modified linuxwacom.fdi back in?

---

### Post by jozze on 2010-09-02
No, this 10-linuxwacom.fdi was the one from my live cd where everything works just fine. My stylus works nearly all the time i start with a live cd. So maybe its not about the fdi?

---

### Post by Favux on 2010-09-02
> My stylus works nearly all the time i start with a live cd. So maybe its not about the fdi? 
You could be right.  Unfortunately I don't know what's wrong.  Seems like it should be working.

---

### Post by jozze on 2010-09-02
would it be a good idea to compare the live cd /etc and my /etc to see if there are any diffenrences? i just have to figure out how to copy the live cd /etc to ... maybe my home directory to boot my system and compare them...

---

### Post by Favux on 2010-09-02
You could try that or you could ask for help on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

---

### Post by rekado on 2010-09-02
I have to admit that I lost the overview. You've copied things here and there which attributes to a lot of confusion.

Let's start all over again, shall we?

These are the known facts:
1. the touch screen works perfectly in the live system
2. the touch screen doesn't work at all in the installed vanilla system
3. the touchscreen is served by the wacom kernel module

Possible explanations for 2:
a) the installed wacom kernel module version differs from the module version used in the live CD
b) the configuration of the touch screen (through HAL's fdi files or xorg.conf) differs

Let's verify these assumptions.

Boot the live system. Become root.
```
su -
```

Make a list of all fdi files:
```
find / -name "*.fdi" > fdi_files_on_live_system
```

Mount your local hard disk in a temporary directory.
```

mkdir local_disk_1
mount /dev/sdX1 local_disk_1

```

Then search for all fdi files on your hard disk:
```
sudo find local_disk_1 -name "*.fdi" > fdi_files_on_installed_system
```

Manually inspect the names. Are there more files on your hard disk than on the live system? Are there files with the names "linuxwacom.fdi" and "wacom.fdi" or maybe "touchscreen.fdi" (or similar)? There should only be one.

Next, compare the files "wacom.fdi" or "linuxwacom.fdi" to see if there are any differences in the configuration:

```
diff /path/to/live/wacom.fdi local_disk_1/path/to/local/wacom.fdi
```

If the files are the same: great. If they are not: backup your local file and copy over the file from the live system.

```

cp local_disk_1/path/to/local/wacom.fdi{,.original}
cp /path/to/live/wacom/fdi local_disk_1/path/to/local/

```

Do the same for xorg.conf. If there is one: go get it after backing up your local file.

While you're at it, copy the wacom kernel module from the live system to your hard disk, in case the configurations are all the same.

```

find /lib/modules -name "*wacom*"
cp /whatever/the/path/is/wacom.ko local_disk_1/some/place/for/later

```

Reboot your installed system.

Now you should be able to tell us more about the differences between the two systems. Comparing all of /etc would be overkill, as we know (or suspect) that the only factor here is misconfiguration (or possibly a different driver version).

If the configuration changes didn't fix your problems, replace the kernel module, remove it and reload it. Do not forget to restart HAL and X (or just reboot).
If this doesn't change anything, our assumptions are wrong.

---

### Post by Favux on 2010-09-02
Hi rekado,

Very nice.  Concise, clear, and logical.  Thank you.


Frankly I've been wondering for a while if there is a problem with Upstart or some of the upstream udev rules.

There have been considerable changes and fixes to the serial ISD4 part of xf86-input-wacom from the default 0.10.5 in Lucid to the recent 0.10.8 + of the git repo.  Along with many other additions and fixes for example:  pressure & xsetwacom.

---

### Post by jozze on 2010-09-03
hey rekado,

i'll try it out, when i get home again.

thanks! :D

---

### Post by jozze on 2010-09-03
it didn't work... i think i might have a solution... when i type in xinput --list i can compare the values. so i found out, that the axis calibration values are different. as far as i know you can edit these values... but i don't know how to edit for example the value "Max_value" of "Axis 0" from "PnPDevice (FUJ02e5)". i have to change it and some other values from 0 to 24576.

---

### Post by Favux on 2010-09-03
Hi jozze,

When the stylus works, with the live CD, have you verified it is the Wacom drivers that have the tablet?  Look in Xorg.0.log in /var/log.  Select All > copy & paste into gedit > search 'wacom'.

---

### Post by jozze on 2010-09-03
This is from the og file:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.8-8 $
(**) Option "Device" "/dev/ttyS0"
(**) PnP Device (FUJ02e5): always reports core events
(**) PnP Device (FUJ02e5) device is /dev/ttyS0
(**) PnP Device (FUJ02e5) is in absolute mode
(**) PnP Device (FUJ02e5): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
...
```
It looks correct...

would it be a good solution to edit the configuration of the resoulution with xinput?

---

### Post by Favux on 2010-09-03
Would need to see more to be sure.  That's on a live CD session right?  Because it's claiming the driver is:
```
(II) Wacom driver level: 47-0.8.8-8 $

```
whereas the default Lucid wacom.ko driver is 0.8.4-4 I believe.  But since that's usb it shouldn't make a difference.

One difference with the live CD is the default 10-linuxwacom.fdi on the CD would have:
```
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
```
But the need for that line was supposedly eliminated when the ISD4 reorganize and fix branch was merged with the master at about xf86-input-wacom version 0.10.7.

---

### Post by jozze on 2010-09-03
> **Favux said:**
> That's on a live CD session right?  Because it's claiming the driver is:
```
(II) Wacom driver level: 47-0.8.8-8 $

```
whereas the default Lucid wacom.ko driver is 0.8.4-4 I believe.  
No, this is from my installed system. shall i post the whole log file?

---

### Post by Favux on 2010-09-03
Please.

---

### Post by jozze on 2010-09-03
the log file: [ATTACH]168417[/ATTACH]

---

### Post by Favux on 2010-09-03
Yours is the Lifebook not the Stylistic?  Does it have multi-touch?  Or how new is it?

---

### Post by jozze on 2010-09-03
It's a Lifebook T4010 ... maybe 4 years old, it doesn't have multitouch... got it on ebay.

---

### Post by Favux on 2010-09-03
The Xorg.0.log again looks pretty good but we still see:
```
(WW) usbDetect: can not ioctl version
(WW) Wacom ISDV4 control data (0) error in * query
```
We could try manually adjusting the coordinates using xsetwacom commmands.

OK, this is a long shot.  But within the last day two commits were made to xf86-input-wacom.  One mainly to support jjulia's Fujitsu T4410's multi-touch, the FUJ02e7 while yours is the FUJ02e5.  But I noticed a line that seemed to add more general Fujitsu support.  Also the other commit to wcmISD4.c involved some reworking of tablet ID matching in preparation of more to come.

So why don't you try cloning the git again?  A fresh copy of xf86-input-wacom and recompile?

Edit:  Oops!  What I am talking about.  You're in Karmic not Lucid.  Those fixes may make into the next linuxwacom release, or may not.

---

### Post by rekado on 2010-09-03
> **jozze said:**
> it didn't work... i think i might have a solution... when i type in xinput --list i can compare the values. so i found out, that the axis calibration values are different. as far as i know you can edit these values... but i don't know how to edit for example the value "Max_value" of "Axis 0" from "PnPDevice (FUJ02e5)". i have to change it and some other values from 0 to 24576.

What do you mean when you say "it didn't work"? The steps I outlined only help you to understand if our assumptions are correct.
Do the configuration files of the two systems differ? Are there different driver versions?

The output of xinput is not really helpful as it just states the obvious---the touchscreen doesn't work in your installed system, but it does in the live system. xinput only shows what your Xserver knows about the input devices. This info is usually dependent on the configuration of the devices themselves.

Please provide more info, so we can advise the next step to you.

---

### Post by jozze on 2010-09-04
This are the differences between my installed system and my live system:
[ATTACH]168450[/ATTACH]
[ATTACH]168451[/ATTACH]
[ATTACH]168452[/ATTACH]

---

### Post by rekado on 2010-09-04
> **jozze said:**
> This are the differences between my installed system and my live system
*snip*


Well, the very fact that you've got something to attach shows that the files are different -- and they probably should not be. I've only checked the last attachment, the differences in 10-linuxwacom.fdi.
Knowing that it works in the live system, but not in the installed system, your target should be to minimize the discrepancies in the configurations. So, go ahead, backup your current configuration file on the installed system and replace it with the one from the live system as I said earlier. Your installed system would then be less different from the live system (the state you want to achieve). Reboot and then check if it works.

If it doesn't, there are more possible differences (in order of likelihood):
- the wacom driver module version
- udev rules
- an odd boot-script that screws with the configuration

If you are sure that you haven't changed anything, but after a reboot suddenly things don't work as before, do make sure that your configuration files are unchanged. Your attachment here shows that whatever you have done when following my steps has been reverted (as there are differences between the files). Make sure that you don't accidentally overwrite configs that are known to work (might happen when recompiling or reinstalling packages).

---

### Post by jozze on 2010-09-04
> **rekado said:**
> Your attachment here shows that whatever you have done when following my steps has been reverted (as there are differences between the files).
No, thats just because i saved these files before i did the things you wrote. my new 10-linuxwacom.fdi is now exactly the same - and it still is, but it doesn't work.
How can i get the wacom driver version or what do i have to do next?
Thanks.

---

### Post by rekado on 2010-09-04
Okay, good.
You can check the driver version by searching for "wacom" in the kernel log:

```
dmesg | grep -i wacom
```

Explanation: the output of dmesg is piped to the filter program grep which will block all lines that do not contain "wacom" (case-insensitive with the -i switch). On my system the output is this:
```
wacom: v.1.52:USB Wacom tablet driver
```

Do the same on both systems to see if the versions differ. While you're at it, copy the kernel module from the live system (again, mount your local disk first etc.). You can find the exact location of the kernel module like this:

```
find /lib/modules -name "*wacom*.ko"
```

Copy it in case you cannot install the desired driver version through proper means, i.e. through the package manager. I'm sorry for not being able to give more detailed instructions; I'm using Arch Linux and installation of specific versions is not much of a problem here through the Ports-like Arch Build System. You might be able to specify the exact version when compiling the module yoursef, though.

---

### Post by jozze on 2010-09-05
today i restarted my system after using my livecd all the time and my system suddenly worked. i did all the backup and logging things you discribed. now i have a folder with all the configurations and log where my system is working.
after a rebboot id stoped working again, but now i'll check out all the configurations and logs to see where the differences are. i'll attach all the files, when i'm ready.

btw. my wacom driver version is v.1.51.

---

### Post by jozze on 2010-09-05
I found the difference in the two Xorg.0.log-files.

-(==) Wacom General ISDV4 tablet speed=9600 (38400) maxX=24576 maxY=18432 maxZ=255 resX=2540 resY=2540  tilt=disabled
+(==) Wacom General ISDV4 tablet speed=9600 (38400) maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled

where can i change these settings?

i attached the whole diff-file: [ATTACH]168565[/ATTACH]

---

### Post by jozze on 2010-09-05
I think i've got it... i tried to restart the x-server after i changed the settings with "xinput set-int-prop" and it worked!!!
i just restarted the system and it didn't work again, but when i restarted the x-server it worked again!
is there a way to fix it without restarting the x-server all the time? for now i just have to restart the x-server every time i log in an log in again.

---

### Post by rekado on 2010-09-05
> **jozze said:**
> I think i've got it... i tried to restart the x-server after i changed the settings with "xinput set-int-prop" and it worked!!!
i just restarted the system and it didn't work again, but when i restarted the x-server it worked again!
is there a way to fix it without restarting the x-server all the time? for now i just have to restart the x-server every time i log in an log in again.

Do you do anything before restarting X? Do you issue "xinput set-int-prop" before restarting X every time?

In any case: check the Xorg.0.log right after booting and right after restarting X. What is different? The logs can tell you.

EDIT: sorry haven't seen your earlier post with the logs.

---

### Post by jozze on 2010-09-05
i dont have to set any values anymore. i just have to restart the x-server. i put a shortkey to that on ctrl+alt+backspace, so it gets faster.

---

### Post by rekado on 2010-09-05
> **jozze said:**
> btw. my wacom driver version is v.1.51.

Which system? Remember, you only check for the driver version to see if it differs between the two systems. If it is the same version, we may pretty much ignore the driver.

---

### Post by jozze on 2010-09-05
> **rekado said:**
> Which system? Remember, you only check for the driver version to see if it differs between the two systems. If it is the same version, we may pretty much ignore the driver.
both systems.

---

### Post by rekado on 2010-09-05
(On a side note: please attach the full logs in the future, not the diffed output; having both files we can use our own tools to diff/view them.)

Please compare one more time the kernel module on the live system with the one you've got installed. Just diff the two and see if it says that they are different. If they are, backup your current module and replace it with the one from the live system.

I'd just like to be sure that those things are the same and this weird behaviour is nothing to do with different versions or configurations. We then know that we have to look somewhere else.

It is very interesting that the maximum values are set to zero and after restarting X are set properly, but I cannot say what would cause behaviour like that. A blind guess would be that after starting X for the first time some secondary configuration is run (like through HAL or udev) which becomes active after you restart X.

Another idea: unload the module when you are in X and then load it again.
```

sudo modprobe -r wacom
sudo modprobe wacom

```

Check dmesg for output.

---

### Post by omskates on 2010-09-06
jozze,  I read through the thread and you reported installing 9.10 and rebooting but I don't see where you reported attempting to update the system after install.  Had you done a ```
sudo apt-get udpate && apt-get upgrade
``` followed by a reboot?

---

### Post by jozze on 2010-09-06
Hi omskates,

no, i did not. Does this update my Ubuntu to 10.x or something like that? I don't want to do that.

thx

---

### Post by omskates on 2010-09-06
No, only update manager will upgrade to the next release.

apt-get upgrade upgrades what you have on the system already but doesn't introduce new packages unless absolutely necessary.

apt-get dist-upgrade upgrades everything on your system and resolves any new dependancies as well, thus introducing more new stuff to your system.

You will remain in your currently installed release.
 
**Try this first as is more conservative but both are safe:**```
apt-get update && apt-get upgrade
``` Then Reboot.  Its good to do anyway after an install and general maintenance time to time.

---

### Post by jozze on 2010-09-06
ok, i'll check it out, when i get home. thx

---

### Post by jozze on 2010-09-06
The 10-linuxwacom.fdi file is the same as in my livesystem.
> **rekado said:**
> 
Another idea: unload the module when you are in X and then load it again.
```

sudo modprobe -r wacom
sudo modprobe wacom

```

Check dmesg for output.
That didn't work.
dmesg shows
> [   297.036267] usbcore: deregistering interface driver wacom
[   312.137175] usbcore: registering new interface driver wacom
[   312.137181] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver
restarting hal didn't work too... just restarting X worked.

@omskates: My brother told me, that i should not update my system. Otherwise i would mess up all the configurations we did befor.

---

### Post by rekado on 2010-09-06
Well, then. That's too bad. I've got no idea, why restarting X should work, but nothing else will quite do it.

I'd say, do the full update and investigate more. One question, though: why is it you want to avoid upgrading to the latest version of Ubuntu? In my earlier experiments with Ubuntu I found that new version always showed a lot of progress, so I never actually regretted upgrading (well, maybe once when that nasty regression was introduced...).

---

### Post by omskates on 2010-09-06
Support for 9.10 lasts until April 2011 if you prefer you can stay with that version as long as it serves you well.

You may want to save your new config files to USB flash drive. 

 Here was my experience, I don't see why things would be different now as I have continued to update my system.  Last year I made an install of 9.10 to a Fujitsu LifeBook T4010 Wacom enabled laptop.  Shortly after some changes upstream  were beneficial after an update/upgrade as I had excellent wacom support with the wacom tools installed.  The fjbtndrv package enabled all my screen hot keys, rotation etc.  Have not had any problems since. 

Perhaps save your config files to USB, do a re-installation, install wacom tools and fjbtndrv package then do an update/upgrade.  Reboot and check, if the issue is persisting then continue with the excellent troubleshooting in this thread.  (Note I was using the 'Linux Mint - Helena' version of Ubuntu 9.10 but I don't see why that would have made a difference with wacom support in this case.)

---

### Post by jozze on 2010-09-07
ok, i did an update/upgrade but it didn't change anything. there were just 2 files to be upgraded an they were part of wine... so it's still the same... but doesn't bother me that much anymore, cause i know how to fix it temporarily. it's a bit annoying, but it works.
(hit [ctrl]+[alt]+[backspace] and login again)

---

### Post by omskates on 2010-09-07
OK, that's not too bad then.  Does your screen rotation & buttons work?  Had you seen this from another thread?:> **amador.duran said:**
> Hi verb0ss,

I had the same problem, in Ubuntu 9.04 and now in Xubuntu 9.10. After reading a lot, I decided to modify the 10-linuxwacom.fdi for serial tablets provided by Favux at the end of this [post]("http://ubuntuforums.org/showthread.php?t=1038949") ([Favux_serial-tablet&tablet-pc_test2_10-wacom.fdi.txt]("http://ubuntuforums.org/attachment.php?attachmentid=140255&d=1261034609")).

I simply add the following line:

    <append key="wacom.types" type="strlist">stylus</append>

before:

    <append key="wacom.types" type="strlist">eraser</append>
    <append key="wacom.types" type="strlist">cursor</append>

Now, the stylus works without restarting X and the "xsetwacom list" command returns "stylus   stylus" only, even after restarting X (it used to show both stylus and eraser after restarting X).

Hope it helps. Happy new year.

---

### Post by jozze on 2010-09-07
No, screen rotation & buttons dont work. And after i inserted this line nothing worked at all... i changed it back and now its working like it did befor... but i still have to restart X every reboot.

---

### Post by omskates on 2010-09-07
> **jozze said:**
> No, screen rotation & buttons dont work. And after i inserted this line nothing worked at all... i changed it back and now its working like it did befor... but i still have to restart X every reboot.

fjbtndrv package should handle rotation and buttons, rotate when screen is flipped to tablet mode etc.  ```
sudo add-apt-repository ppa:khnz
``` ```
sudo apt-get update
``` ```
sudo apt-get -y install fjbtndrv
```

REBOOT

---

### Post by jozze on 2010-09-11
Well, installing the driver did the trick... buttons and pen are now working perfectly. Thanks a lot!

---

