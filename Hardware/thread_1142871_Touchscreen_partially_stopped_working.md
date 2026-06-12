---
title: "Touchscreen partially stopped working"
date: 2009-04-29
forum: Hardware
---

### Post by corwinspyre on 2009-04-29
Hi all!

Months ago I used this post [http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447) to get the touchscreen working on my HP tx2500z laptop, but recently touch (but not the stylus--they're separate things) stopped working.

It appears Linux can't see it at all.  There should be two events, one for the stylus and one for touch, but only event8 is there: 
```

  $ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 2009-04-29 05:30 pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event8
lrwxrwxrwx 1 root root  9 2009-04-29 05:30 pci-0000:00:14.5-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2009-04-29 05:30 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2009-04-29 05:30 platform-i8042-serio-1-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2009-04-29 05:30 platform-i8042-serio-1-mouse -> ../mouse3

```

But touch had been input9, as you can see from my xorg.conf and where it loads Wacom (which is a result of xorg.conf)
```

  $ dmesg | grep Wacom
[   10.711065] input: Wacom ISDv4 93 as /class/input/input8
[   10.771935] input: Wacom ISDv4 93 as /class/input/input9
[   10.820540] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```

```

Section "InputDevice"
  Identifier  "stylus"
  Driver      "wacom"
  Option      "Type" "stylus"
  Option      "USB" "on"
  Option      "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
  Option      "Button2" "3" # make side-switch a right button
  Option      "TopX" "225"
  Option      "TopY" "225"
  Option      "BottomX" "26300"
  Option      "BottomY" "16375"
EndSection

Section "InputDevice"
  Identifier  "touch"
  Driver      "wacom"
  Option      "Type" "touch"
  Option      "USB" "on"
  Option      "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
  Option      "TopX" "200"
  Option      "TopY" "225"
  Option      "BottomX" "4000"
  Option      "BottomY" "3875"
EndSection

```

It happened after I changed the resolution via the ATI Catalyst Control Center, which deals with xorg.conf, but I compared my current version to one from a month ago, and they're the same.

Anyone have this issue before or know of a way to find out why it's missing?  Help is much appreciated, since I use the touchscreen a lot!

edit: I'm on 8.10, not 9.04

---

### Post by Favux on 2009-04-29
Hi corwinspyre,

I don't know what happened.  I don't see why Catalyst would do that.

One thing you could try is "lshal".  There will be a long output so you may want to redirect it.  What I see with my TX20000 is 5 Wacom sections.  One parent and two pairs of daughters.  One pair stylus and the other touch.  If you see that it probably isn't a hardware failure.  Have you tested in Windows?

I've updated gali98's tutorial here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  There are some other things listed you could try like the more command.

Failing all that you could try the Wacom symlinks method suggested in section 2 and demonstrated in appendix 3.

Good luck!

---

### Post by corwinspyre on 2009-04-29
Hi Favux,

Thanks for the reply!

First I tried Appendix 3, but no luck.

Then I tried the other version, the non-xorg one (after purging the two packages, running ./prebuilt/uninstall from the wacom driver, removing all wacom junk from xorg.conf, and restarting).

I believe it is showing up via lshal (I attached the five sections below, but it's the same as the sample .fdi), and now it's showing up in /dev/input too, though still not /dev/input/by-path (actually I'm not sure if it's supposed to with the fdi method):
```

 $ ls -l /dev/input
[...]
lrwxrwxrwx  1 root root      6 2009-04-29 08:48 tablet-tpc93-stylus -> event8
lrwxrwxrwx  1 root root      6 2009-04-29 08:48 tablet-tpc93-touch -> event9
lrwxrwxrwx  1 root root      6 2009-04-29 08:48 wacom -> event8
lrwxrwxrwx  1 root root      6 2009-04-29 08:48 wacom-touch -> event9

```

But otherwise it is the same scenario as before. The cursor will move if I touch my finger to the screen, but it doesn't track underneath, instead mirroring my movements from where ever the cursor is at the time, and for a smaller length and slower than I move.  Could this just be a calibration issue?  Unfortunately now after doing the .fdi file version, wacomcpl won't work:
```

  $ wacomcpl
bash: wacomcpl: command not found

```

I tried using gali98's longer fdi file with calibration settings, but nothing changed.

edit:
I grepped dmesg for wacom (as opposed to Wacom), and noticed there was only one result, not two:
```

  $ dmesg | grep wacom
[   11.836182] usbcore: registered new interface driver wacom
[   11.836186] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver

```
Does this mean that it's only loading the driver for one (stylus)?

---

### Post by Favux on 2009-04-29
Hi corwinspyre,

I'm sorry I am now confused.  The new HOW TO of gali98's on post #104 is for Jaunty.  The HAL/.fdi method only works for the specially patched 0.8.2-2 linuxwacom in Jaunty.  It will only partially work in Intrepid.

I wanted you to try "lshal" and "more /proc/bus/input/devices" to see if the touch screen was being recognized.

So when appendix 3 didn't work I would have wanted to know if it works in Windows?  Which version of linuxwacom are you using (I assume it was installed with gali98's tutorial).  Could I see your xorg.conf?

Recently a couple other TX2500 users have reported touch going AWOL.  That sounded like a problem with compiling 0.8.3-2 in Intrepid and their xorg.conf.  But maybe something else is going on.  Was there an ATI driver update recently or something?

So what version of Ubuntu are you using?  Yes it could be something to do with calibration since you are getting a reaction.  But wacomcpl probably won't work for you if I understand what you've done.

---

### Post by corwinspyre on 2009-04-29
> **Favux said:**
> Hi corwinspyre,

I'm sorry I am now confused.  The new HOW TO of gali98's on post #104 is for Jaunty.  The HAL/.fdi method only works for the specially patched 0.8.2-2 linuxwacom in Jaunty.  It will only partially work in Intrepid.

I wanted you to try "lshal" and "more /proc/bus/input/devices" to see if the touch screen was being recognized.

So when appendix 3 didn't work I would have wanted to know if it works in Windows?  Which version of linuxwacom are you using (I assume it was installed with gali98's tutorial).  Could I see your xorg.conf?

Recently a couple other TX2500 users have reported touch going AWOL.  That sounded like a problem with compiling 0.8.3-2 in Intrepid and their xorg.conf.  But maybe something else is going on.  Was there an ATI driver update recently or something?

So what version of Ubuntu are you using?  Yes it could be something to do with calibration since you are getting a reaction.  But wacomcpl probably won't work for you if I understand what you've done.

That was a mistake then because I'm using 8.10.

I don't think my problem is related to other tx2500 users because it stopped working with 0.8.2-2, and now it's working with 0.8.3-2...

I just wrote a huge post with all kinds of info, but as I was doing it, I noticed in /proc/bus/input/devices that the event numbers had changed, for the first time too, even though I probably set the record for number of reboots in a day today.  The touch event still didn't show up in /dev/input/by-path, but for the heck of it I tried replacing the events in my xorg.conf with the associated events (gathered from /dev/input) and hit ctrl-alt-backspace, and it works!

I really have no idea how that fixed it.  I'm 100% sure they stayed the same eventX's each time until then, so it wasn't pebcak (well, not in that way anyway :P ), so functionally I changed nothing (though I had to use /dev/input/ and not /dev/input/by-path as originally, but /dev/input/ didn't work earlier either).

Now the only thing left is to figure out how to get wacomcpl working again /sigh

---

### Post by Favux on 2009-04-29
Hi corwinspyre,

Weird.  But you got it working, good job.

I should have typed Intrepid/Jaunty.  So you're on Intrepid and compiled 0.8.3-2.  I'm puzzled but I think I know where you are at least.

So was this the same setup that the wacom symlinks failed on?  No new usb hub or docking station?

Regarding wacomcpl let's see what:
```
xsetwacom list
```
and
```
xinput --list
```
looks like.

---

### Post by corwinspyre on 2009-04-30
> **Favux said:**
> Hi corwinspyre,

Weird.  But you got it working, good job.

I should have typed Intrepid/Jaunty.  So you're on Intrepid and compiled 0.8.3-2.  I'm puzzled but I think I know where you are at least.

So was this the same setup that the wacom symlinks failed on?  No new usb hub or docking station?

Regarding wacomcpl let's see what:
```
xsetwacom list
```
and
```
xinput --list
```
looks like.
Hi again, Favux :)

Thank you very much for all the help.  I need the tablet for work, so you've saved me from losing money :)

Yep, it's the same setup the symlinks originally failed on (but I'm using them now) minus the fact that the event numbers changed.  It's a laptop with no extra stuff plugged in, so no new hub or anything.

xsetwacom list:
```

  $ xsetwacom list
stylus           stylus    
touch            touch     
eraser           eraser  

```

xinput --list:
```

"stylus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 225
		Max_value is 26300
		Resolution is 2540
	Axis 1 :
		Min_value is 225
		Max_value is 16375
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
"touch"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 200
		Max_value is 4000
		Resolution is 396
	Axis 1 :
		Min_value is 225
		Max_value is 3875
		Resolution is 633
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
"eraser"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26312
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16520
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

---

### Post by Favux on 2009-04-30
Hi corwinspyre,

According to those outputs wacomcpl should work.  Those are the correct "names" for xsetwacom to work.  What happens when you type "wacomcpl" in a terminal?  Maybe you should have a look at the .xinitrc wacomcpl generates.  It's a hidden file on your /home/username/.

Section 3 here gives a little more information on it:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by corwinspyre on 2009-05-01
Hi Favux,

No luck with wacomcpl
```

  $ wacomcpl
bash: wacomcpl: command not found

```

no xsetwacom lines in .xinitrc
```

  $ cat .xinitrc
# run the primary system script
. /etc/X11/xinit/xinitrc

```

but xsetwacom itself works anyway
```

  $ xsetwacom
Usage: xsetwacom [options] [command [arguments...]]
Options:
 -h, --help                 - usage
 -v, --verbose              - verbose output
 -V, --version              - version info
 -d, --display disp_name    - override default display
 -s, --shell                - generate shell commands for 'get'
 -x, --xconf                - generate X.conf lines for 'get'

Commands:
 list [dev|param]           - display known devices, parameters 
 list mod                   - display supported modifier and specific keys for keystokes
 set dev_name param [values...] - set device parameter by name
 get dev_name param [param...] - get current device parameter(s) value by name
 getdefault dev_name param [param...] - get device parameter(s) default value by name

```

---

### Post by Favux on 2009-05-01
Hi corwinspyre,

OK, that's a big fat clue.  Wacomcpl should start.  But your system doesn't think it is present.

Let me summarize.  You are on Intrepid (8.10) and using linuxwacom 0.8.3-2 compiled from the HOW TO.  Either something went wrong with the compile or it subsequently got corrupted.  Or you have a linuxwacom version conflict.  Both the drivers (xorg-xserver-input-wacom) and wacom-tools have to be the same version.  Perhaps something was left around from the previous install.  Or something happened during the .fdi experiment.

So two options recompile 0.8.3-2 or use 0.8.2-2 (the HOW TO default)  which should give you everything you need for Intrepid.  Purging the old stuff is included in the HOW TO.  But to make sure in a terminal type:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then cd into the unpacked linuxwacom 0.8.3-2 directory you should have from when you compiled it.  Then change directory into the prebuilt folder that should be in it.  Now type:
```
sudo ./uninstall
```
That should get rid of everything except maybe the kernel module.  To check go to "/lib/modules/`uname -r`/kernel/drivers/input/tablet/" and see if "wacom.ko" is present.  If so delete it.

Now go ahead and recompile either 0.8.2-2 or 0.8.3-2.

Good luck!  Boy I hope this works.

---

