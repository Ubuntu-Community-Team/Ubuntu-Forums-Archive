---
title: "Thinkpad x61t tablet PC pen stopped working after Update"
date: 2012-04-01
forum: Hardware
---

### Post by Kinst on 2012-04-01
Hi, so here's the story and the point at which I am stumped on what to do next. I have an older thinkpad tablet PC which runs windows and Ubuntu. When I updated Ubuntu 11.10 via synaptic my pen stopped working! It still works on windows, so the hardware should be OK. I then (stupidly) updated again to Ubuntu 12.04 Beta thinking that would help, but it didn't change a thing. 

```
mshaw@Pierre:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons
```

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```

```
sudo dmesg | grep tty
[    0.000000] console [tty0] enabled
```

So the problem is that the pen isn't being recognized anymore! I attached my Xorg.0.log if that helps figure out what's wrong...

---

### Post by Favux on 2012-04-01
Hi Kinst,

To summarize Precise Beta 2 with Thinkpad X61t (serial Wacom digitizer).  And:
```
sudo dmesg | grep ttyS
```
shows nothing.  The 50-wacom.conf at /usr/share/X11/xorg.conf.d looks OK.

The Xorg.0.log does not show the digitizer at all nor anything setting up on a serial port.  Another weird thing is it seems to be claiming a 2.6.38 kernel with X Server 1.11.3 which doesn't make sense.  What is the output of?
```
uname -r
```
I think we're back to wondering about a udev rule conflict.  Let's look again at /lib/udev/rules.d/40-inputattach.rules.  What are the contents?  By any chance did you reinstall xf86-input-wacom (the xserver-xorg-input-wacom package)?

Do you have an inputattach command in rc.local?

---

### Post by Kinst on 2012-04-01
Okay so I was trying an older kernel to see if that did anything, but my actual kernel is: 

```
uname -r
3.2.0-21-generic-pae
```

I tried reinstalling the xserver-xorg-input-wacom package a while ago. 

40-inputattach is currently: 
```
# Attach Wacom W8001 devices
# SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
```

/etc/rc.local includes:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

---

### Post by Kinst on 2012-04-01
Wait, the weirdest thing happened. I tried booting with the pnpacpi=off command removed and on the right kernel and now I get this:

```
mshaw@Pierre:~$ sudo dmesg | grep ttyS
[    0.860907] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a NS16550A
```

I attached the new Xorg.0.log for this session. Is that good?

---

### Post by Favux on 2012-04-01
Ah, we have the wrong udev rule commented out.  Should keep both commented out I suppose.  Also comment out the rule with WACf00c since that is the one matching your PnP ID:
```
# Attach Wacom W8001 devices
# SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
```
Then restart.

Edit:  Ah again.  Yes that's progress.  Now there is a ttyS4 port it is trying to set the Wacom up on although it fails with a time out.

---

### Post by Kinst on 2012-04-01
OK, so I tried commenting out the other line and restarting but it still shows the same thing in /var/log/Xorg.0.log. Here's the part with "wacom":

```
[    44.566] (**) Option "xkb_rules" "evdev"
[    44.566] (**) Option "xkb_model" "pc105"
[    44.566] (**) Option "xkb_layout" "ca"
[    44.567] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    44.567] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    44.567] (II) LoadModule: "wacom"
[    44.567] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    44.567] (II) Module wacom: vendor="X.Org Foundation"
[    44.567] 	compiled for 1.11.3, module version = 0.14.0
[    44.568] 	Module class: X.Org XInput Driver
[    44.568] 	ABI class: X.Org XInput driver, version 16.0
[    44.568] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    44.568] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    44.568] (**) Serial Wacom Tablet: always reports core events
[    44.568] (**) Option "Device" "/dev/ttyS4"
[    44.568] (**) Option "StopBits" "1"
[    44.568] (**) Option "DataBits" "8"
[    44.568] (**) Option "Parity" "None"
[    44.568] (**) Option "Vmin" "1"
[    44.568] (**) Option "Vtime" "10"
[    44.568] (**) Option "FlowControl" "Xoff"
[    44.568] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    44.568] (II) Serial Wacom Tablet: other types will be automatically added.
[    47.822] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    47.822] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    51.075] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    51.076] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    51.076] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    51.076] (II) UnloadModule: "wacom"
[    51.076] (II) Unloading wacom
```

---

### Post by Favux on 2012-04-01
The Xorg.0.log says you have xf86-input-wacom-0.14.0.  Let's check that:
```
xsetwacom -V
```
And just to be thorough do a little attributes walk:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)
```

Can I ask why you had the pnpacpi=off command on your kernel boot line?

---

### Post by Kinst on 2012-04-01
I can't remember why :-(

```
mshaw@Pierre:~$ xsetwacom -V
0.14.0
mshaw@Pierre:~$ udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:0a/tty/ttyS4':
    KERNEL=="ttyS4"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0a':
    KERNELS=="00:0a"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="WACf004"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Favux on 2012-04-01
This is probably some code thing, not a set up thing, I'm thinking.  It seems like the time out thing has been happening more and more recently.

Although 0.14.0 is very recent and there have been only a few commits since it was released I'd like you to clone the git repository.  One of the commits has to do with the:
```
       fclose(file);
```
line in wcmISDV4.c at about line 989, which was pretty much the same line that was tripping up one of the legacy serial tablets.  He felt it was because of the goto:
```
out:
	udev_device_unref(device);
	udev_unref(udev);
	fclose(file);
```
so he added some if's.  The patch does something a little different but it does change the line to:
```
+       if (file)
+               fclose(file);
```
Let's see if we get lucky.

See part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Kinst on 2012-04-01
Okay, I think I did that correctly, but it hasn't made a difference. :frown:

It was a good idea though. Maybe I should try using an older version of xf86-input-wacom?

---

### Post by Favux on 2012-04-01
Darn.
> Maybe I should try using an older version of xf86-input-wacom? 
Sort of do a bisection?  That might work.  The older tars are here:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

But first may want to look at the Xorg.0.log with debug turned on and see if it gives us some more information.  In either *man wacom* or man *xsetwacom* you'll see the debug commands.  Probably want to do it in the 50-wacom.conf since the problem is at initialization.  So below the driver line in the snippet:
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
        Option "Debug level" "12"
        Option "CommonDBG" "12"
EndSection
```
That's the correct snippet unless you're seeing "Serial Wacom Tablet" in *xinput list*.

After that three options it seems to me.  My preferred is post on [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") for help.  Or try the xf86-input-wacom bisection.  If you found a working version that would give us an idea where things went wrong.  There haven't been a lot of changes to wcmISDV4.c in a while, but it could be something else.  And the third one would be to try wacom_w8001.ko and inputattach and see if that makes a difference.

---

### Post by Kinst on 2012-04-02
Okay! I'm going to take a few days off trying things and then I'll let you know as soon when I get back to testing it. Thank you so much for helping me this far! I'm sure it's fixable once I get some time to try. ;)

---

### Post by Kinst on 2012-04-02
Okay, I don't know if this helps me, but I tried booting off a usb using old ubuntu versions to see what works out of the box and here's what I found:

11.10: Doesn't work
11.04: Doesn't work
10.04: Doesn't work
9:10: Works!!

Come to think of it, 9:10 was the last version I installed from scratch, since then I've only been upgrading! If you know what that means I should try on my system without reinstalling let me know... right now reinstalling is tempting, after all my stuff is in the cloud anyways.

---

### Post by Favux on 2012-04-02
That's interesting.  Karmic (9.10) was the last version with linuxwacom.  Linuxwacom had the kernel driver package with the X driver.  Starting in Lucid they forked the X driver to xf86-input-wacom and the kernel driver went to be a regular kernel driver being submitted to linux-input.

Another thing to check is the udev rules for serial tablets.  They're located at /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules.  Most of the stuff is usb rules most of them in a big table.  The serial ones are near the top and look something like:
```
# Catch the serial tablets and tell X that's what they are
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="WACf*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="FUJ*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

```
At least in Oneiric they were still using the old rules.  A while ago a udev rule expert dropped by the LWP and explained why the old serial rules were bad, really bad.  So there are new rules, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)  We tried changing those once or twice with no noticeable effect so far.

---

### Post by Kinst on 2012-04-04
Hey Favux, I don't know what was wrong before, but as it turns out, a fresh installation of 11.10 works perfectly with my pen & all my other hardware!

So instead of worrying about what was wrong with my setup, I just backed all my stuff up and reinstalled. 

Thank you for all of your guidance though! You were a big help :KS.

---

### Post by Favux on 2012-04-04
Great!  :)

I think that has happened a couple of times before too.  So now you have to wonder what goes wrong with the install to mess up serial input?  How can we tell that's the problem?

Now that it is working you might be interested in Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

