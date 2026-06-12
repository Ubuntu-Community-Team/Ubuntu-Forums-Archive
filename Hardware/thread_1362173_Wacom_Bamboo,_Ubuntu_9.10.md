---
title: "Wacom Bamboo, Ubuntu 9.10"
date: 2009-12-22
forum: Hardware
---

### Post by walterw on 2009-12-22
Hi all,

I am having issues with getting my Wacom Bamboo tablet working.  For starters, the wacom module is not installed/enabled by default.  Once I enable it, if I run dmesg, it appears the driver applies to the tablet.

However, once I open up GIMP, I don't see any options to configure the tablet, and the tablet itself does not control GIMP at all.

I have tried various posts to no avail.  Should wacom configuration be this difficult, what else am I missing?


Thanks,
Walter

---

### Post by ElSlunko on 2009-12-22
I just want to ask and make sure that you're correctly setting it up inside gimp.

In preferences did you go to Input Devices > Configure Extended Input Devices > and set the Wacom related stuff to Screen?

Also, Bamboo drivers were installed by default for me.

---

### Post by Favux on 2009-12-22
Hi walterw,

Which Bamboo model do you have?  Is it one of the new Bamboo Pen and Touch's?

---

### Post by walterw on 2009-12-25
Hi all,

It is the Bamboo Fun, about paper letter size, and it does come with a pen.

I read some posts that I should be able to see the device in xsetwacom or the xorg utility, but didn't see anything there.

I updated the fdi according to a post, but still no change.  The wacom driver is not loaded automatically so I am guessing something with my hal or dbus is not setup properly.


Yeah, I noticed by default all the drivers were installed.  That is something I like and both dislike about Ubuntu.  I wish it would auto-detect what you had and only installed what was needed.  Having all those extra drivers can lead to conflicts (in my opinion).

So, I cannot currently see the device in xsetwacom and the xlist or whatever command it is.  I don't believe I can see the device in the GIMP either (even if I manually modprobe wacom).  I can see that when I modprobe wacom and connect the device, dmesg reports the device correctly and appears wacom is the correct driver.  I just don't see any device nodes to actually read from the device?


This is one of the posts I followed.  The thing is, I followed several posts and tried to back out the changes after I didn't see the device with xsetwacom or in the GIMP.  This is where I am currently at, I followed these instructions, but am not sure if something else I did is preventing this from working:


[http://ubuntuforums.org/showpost.php?p=7234134](http://ubuntuforums.org/showpost.php?p=7234134)


Any ideas?


Walter

---

### Post by Favux on 2009-12-25
Hi walterw,

I'm trying to find out the model number because it is important.  Do you have the new Bamboo P & T?:
```
Bamboo Fun (CTH661)	 	stylus, eraser, pad, touch
	Product ID = 0xd3
```

---

### Post by walterw on 2009-12-25
Sorry to ask a dumb question, but I can't seem to tell.  I tried lspci, dmesg and that doesn't seem to list it.

I'll look around in the meantime.

Walter

---

### Post by walterw on 2009-12-25
Even better, I turned the tablet over ...


CTH-661/S

---

### Post by Favux on 2009-12-25
Hi walterw,

OK, that's what we needed to know.  What's going on is that it is a Bamboo P & T.  They are so new that the default 0.8.4-1 linuxwacom in Karmic doesn't support them, which is why nothing works.  The 0.8.5-8 linuxwacom is just starting to introduce support for them.

But Ayuthia and company have pretty much everything working.  See his patches and instructions in [post #1]("http://ubuntuforums.org/showthread.php?t=1321238") on the " Wacom Bamboo Pen and Touch Series Development".  Those are the patches that are being submitted and accepted by linuxwacom (LWP).

---

### Post by walterw on 2009-12-25
Hi Favux,

Thanks for your help and patience.


Walter

---

### Post by walterw on 2009-12-25
Okay, this is one of the threads I tried, I am getting this error:

```

make[2]: *** [hal-setup-wacom.o] Error 1
make[2]: Leaving directory `/home/walterjwhite/Downloads/linuxwacom-0.8.5-4/src/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/walterjwhite/Downloads/linuxwacom-0.8.5-4/src'
make: *** [all-recursive] Error 1

```



I am getting the same issue as before, I just thought that there must have been a binary driver for it.  I just need to resolve this compilation error.

I am on an AMD64.


Walter

---

### Post by walterw on 2009-12-25
I see there are some other posts with the same error and there are 715 pages total.  Looks like I have a bit of reading ahead of me :)


Walter

---

### Post by Favux on 2009-12-25
Hi walterw,

I haven't seen that error before.  You can post on that thread for help.

But first you might want to try step 2) Section 1 of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Just this part:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get install libhal-dev

sudo apt-get upgrade
```
And then try to patch and compile Ayuthia's instructions in the first post.

---

### Post by walterw on 2009-12-25
Hi Favux,

Thanks for your reply, with the latest driver, I can at least now see the stylus, tablet, and eraser.  I'm not getting anything yet in the GIMP, but I'll keep reading.


Walter

---

### Post by Favux on 2009-12-25
Hi walterw,

Great!  Progress.

You should have touch and tablet buttons if you are using the rc2 .fdi linked at the bottom of Ayuthia's post.

To get Gimp working you need to configure it's extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by walterw on 2009-12-25
Favux,

Thanks much.

Okay, so like I said I have them properly configured in both the GIMP and Inkscape.

If I cat the device and try clicking buttons or pressing on the pad, I get nothing even with the stylus and pressing buttons on the stylus.

/dev/input/wacom
/dev/input/wacom-touch

At least both of them exist now so that is a good thing.

I'm trying to configure my xorg.conf with the hopes that I just need to update that so it is detected/configured properly.

Rebooting.

Walter

---

### Post by walterw on 2009-12-25
Still nothing.

I still have to manually modprobe the driver otherwise it is not automatically loaded.

I am guessing my hal/dbus isn't properly configured.

Even after I modprobe the driver/kernel module, GIMP or Inkscape don't seem to get any input even though the devices are there (stylus, eraser, ...).


Walter

---

### Post by Favux on 2009-12-25
Hi walterw,

OK, I'm confused.  You can use xorg.conf (just don't have a 10-linuxwacom.fdi installed) if you want to.  But you don't need to.  You can use the rc2 .fdi in [post #579]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579") in Ayuthia's thread.  A sample xorg.conf is in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") in the original "New Wacom Bamboo not working" thread.

If you have more than one wacom.fdi or a .fdi and xorg.conf that could be the problem.

Or am I misunderstanding you?

---

### Post by walterw on 2009-12-25
Hi Favux,

Ok, 1 or the other, but not both.  Let me give that a try.

:)

Walter

---

### Post by walterw on 2009-12-25
Favux,

Thanks for being patient with me.

Ok, when I changed my configuration and restarted, the wacom module is again not automatically inserted.  After I insert it (modprobe wacom), I now see 6 devices in the GIMP instead of 3.

When I change the configuration from disabled to screen (for the other devices), it still doesn't appear to work.


Walter

---

### Post by walterw on 2009-12-25
Playing around some more, at least the buttons kinda work.  One button registers as a right, and another as a left mouse click.

Now to figure out the touchpad area ...


Walter

---

### Post by Favux on 2009-12-25
Hi walterw,

On some systems the wacom.ko won't autoload.  So add "wacom" (without the quotes) to the end of the 'modules' file in '/etc/':
```
gksudo gedit /etc/modules
```

One pair of buttons is touch on/off and the other pair left/right mouse click.  At least that's how I understand it.

---

### Post by walterw on 2009-12-25
Ok, I'll give that a try.


Thanks again for your patience.


Walter

---

### Post by walterw on 2009-12-25
Hi Favux,

I can get the cursor to move, but I can't seem to control it very well yet.  I am guessing I might have the wrong fdi configuration.  I'll try again tomorrow.


Walter

---

### Post by walterw on 2009-12-27
Hi Favux,

Here is what I seem to observe.

I can get the cursor to move sporadically at best.  The rightmost button is a middle mouse click, the middle right button is a right mouse button click.  The leftmost button makes the current window scroll down and the middle left button makes the page scroll back up.

I have no clue how to get the cursor to move in a controlled fashion.


Walter

---

### Post by Favux on 2009-12-27
Hi walterw,

Hmmm.  No I don't think anyone else is reporting that with Ayuthia's -34 patches to 0.8.5-4.  The cursor is jumpy with the stylus is what you are saying, correct?

Let's look at the output of this command in a terminal:
```
xinput --list
```
and then:
```
xsetwacom list
```

---

### Post by walterw on 2009-12-27
Favux,

```

walterjwhite@laptop:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
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
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 16
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
"Sony Vaio Keys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"UVC Camera (05ca:183d)"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
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
"AlpsPS/2 ALPS GlidePoint"	id=10	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 767
		Resolution is 1
"PS/2 Mouse"	id=11	[XExtensionPointer]
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
"Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"	id=12	[XExtensionPointer]
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
"eraser"	id=13	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 21648
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 13530
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 1023
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
"stylus cursor"	id=14	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 21648
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 13530
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"stylus pad"	id=15	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 21648
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 13530
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"stylus"	id=16	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 21648
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 13530
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 1023
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
"pad"	id=17	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 11
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 740
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 500
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"touch"	id=18	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1024
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is 1024
		Resolution is 0
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

```

walterjwhite@laptop:~$ xsetwacom list
eraser           eraser    
stylus           stylus    
pad              pad       
touch            touch     

```


Walter

---

### Post by Favux on 2009-12-27
Hi walter,

The xsetwacom looks good.  The xinput looks a little funky.  With all the changes I guess I'm not 100% sure it's right, but I think it is.

Have you tried configuring and calibrating your tablet with 'wacomcpl' yet?  It's the LWP's calibration and configuration gui.  You just type "wacomcpl" (without the quotes) in a terminal and the gui pops up.  To set it up so it's settings last through a reboot see "Section 3: Calibrating your Tablet" on the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

If you haven't used it maybe running through it will straighten your stylus out.

---

### Post by walterw on 2009-12-27
Favux,

I don't know if I mentioned this, but I cannot configure any devices with that command:

Whenever I execute it and click on any item, say stylus, I get this error:

```

can't read "hasTouch(211)": no such element in array
can't read "hasTouch(211)": no such element in array
    while executing
"if { $hasTouch($model) } {
		createPanel 1 0 0 1
	    }"
    (procedure "updateDevice" line 29)
    invoked from within
"updateDevice"
    (command bound to event)

```



Walter

---

### Post by Favux on 2009-12-27
Hi walter,

That's kind of sounding like you installed linuxwacom 0.8.5-8 or something.  When you said you tried a bunch of things did that include installing and compiling a version of linuxwacom?  Which one?  You maybe need to run through that for me.

We could be looking at a version conflict.  Either part of a previous install or a mismatch between xserver-xorg-input-wacom and wacom-tools (which has wacomcpl).

---

### Post by walterw on 2009-12-27
The driver I installed is:

8.5-4

I completely uninstalled any system provided wacom package.  In addition, I deleted the wacom.ko module.

I am running 2.6.31-16-generic and I see the source I compiled for for 2.6.28 which seems like it could be an issue.


Walter

---

### Post by Favux on 2009-12-27
> I see the source I compiled for for 2.6.28 which seems like it could be an issue.
If you are talking about the cp command for wacom.ko that's correct.  That's a quirk in linuxwacom.

So you patched with the patches?  No noticeable errors during that?

So let's look at your Xorg.0.log in /var/log

---

### Post by walterw on 2009-12-27
mmm - patches.  Let me check that.

---

### Post by walterw on 2009-12-27
Uh, I downloaded this, I thought it was already patched:

[http://linuxfans.keryxproject.org/packages/wacom/builds/linuxwacom-0.8.5-4-bamboo-34.tar.bz2](http://linuxfans.keryxproject.org/packages/wacom/builds/linuxwacom-0.8.5-4-bamboo-34.tar.bz2)



Walter

---

### Post by walterw on 2009-12-27
Favux,

It looks fine, the serial error I am guessing is because this is a USB and not serial tablet?

```

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) eraser: always reports core events
(**) eraser device is /dev/input/event14
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/input/event14"
eraser Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
(II) config/hal: Adding input device stylus cursor
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/input/event14
(**) stylus cursor is in relative mode
(**) WACOM: suppress value is 2
(**) stylus cursor: reading USB link
(**) stylus cursor: threshold = 61
(**) stylus cursor: max x set to 21648 by xorg.conf
(**) stylus cursor: max y set to 13530 by xorg.conf
(**) stylus cursor: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(==) Wacom device "stylus cursor" top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
(II) config/hal: Adding input device stylus pad
(**) stylus pad: always reports core events
(**) stylus pad device is /dev/input/event14
(**) stylus pad is in relative mode
(**) WACOM: suppress value is 2
(**) stylus pad: reading USB link
(**) stylus pad: threshold = 61
(**) stylus pad: max x set to 21648 by xorg.conf
(**) stylus pad: max y set to 13530 by xorg.conf
(**) stylus pad: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus pad: serial speed 9600
(II) XINPUT: Adding extended input device "stylus pad" (type: Wacom Pad)
(==) Wacom device "stylus pad" top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
(II) config/hal: Adding input device stylus
(**) stylus: always reports core events
(**) stylus device is /dev/input/event14
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) stylus: reading USB link
(**) stylus: threshold = 61
(**) stylus: max x set to 21648 by xorg.conf
(**) stylus: max y set to 13530 by xorg.conf
(**) stylus: max z = 1023
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=21648 bottom Y=13530 resol X=1016 resol Y=1016
(II) config/hal: Adding input device pad
(**) pad: always reports core events
(**) pad device is /dev/input/event15
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) pad: serial speed 9600
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(**) Option "Device" "/dev/input/event15"
pad Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=740 maxY=500 maxZ=255 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "pad" top X=0 top Y=0 bottom X=740 bottom Y=500 resol X=1016 resol Y=1016
(II) config/hal: Adding input device touch
(**) touch: always reports core events
(**) touch device is /dev/input/event15
(**) touch is in absolute mode
(**) WACOM: suppress value is 2
(**) touch: reading USB link
(**) touch: threshold = 15
(**) touch: max x set to 740 by xorg.conf
(**) touch: max y set to 500 by xorg.conf
(**) touch: max z = 255
(**) Option "BaudRate" "9600"
(**) touch: serial speed 9600
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
(==) Wacom device "touch" top X=0 top Y=0 bottom X=1024 bottom Y=1024 resol X=0 resol Y=0
touch - usbParse: dropping empty event for serial 240

```


Walter

---

### Post by Favux on 2009-12-27
Hi Walter,

I'm not sure.  Can I see the whole thing?  Right click on it compress it with Create Archive.  Then attach it to your next post with Manage Attachments.  Thanks.

---

### Post by walterw on 2009-12-27
Please find attached the Xorg.0 log file.


Walter

---

### Post by Favux on 2009-12-27
Hi Walter,

OK, it looks like something went wrong with your patching and compile.  That line repeats many times, which shouldn't happen, and ends with:
```
Error reading wacom device : No such device
(II) config/hal: removing device stylus
(II) UnloadModule: "wacom"
Error reading wacom device : No such device
(II) config/hal: removing device touch
(II) UnloadModule: "wacom"
```

Before you recompile could you show me the contents of your 10-linuxwacom.fdi file?

---

### Post by walterw on 2009-12-27
That is because I just unplugged my tablet from the computer - I think.  Uh, maybe you're right, I plugged it in and out a few times and didn't see any change in Xorg.


Walter

---

### Post by Favux on 2009-12-27
Try rebooting.

---

### Post by walterw on 2009-12-27
Hehe - it works.  I guess it needs to be plugged in on startup otherwise Xorg doesn't acknowledge it or something?


Now, I just have to figure out how to get it working in the GIMP.  One step at a time.

Walter

---

### Post by Favux on 2009-12-27
Great!  That sure makes it simple!

---

### Post by walterw on 2009-12-27
Sure does, the 'click' doesn't appear to work.  I have everything setup in the GIMP / Inkscape identically and can't seem to get a line drawn.

I also cannot click on any buttons with it, but it is much more precise than my mouse.

Walter

---

### Post by Favux on 2009-12-27
Hi Walter,

Well wacomcpl should work for you.  You can configure the stylus button there.  Try it again now that touch is working (i.e. you booted with tablet plugged in).

---

### Post by walterw on 2009-12-27
I don't see any devices there now.  The interesting thing is I had to reinstall that wacom tools to get that application back.


Walter

---

### Post by Favux on 2009-12-27
Hi Walter,

Bad news.  You definitely have a version mis-match now if you installed the 0.8.4-1 default Karmic linuxwacom wacom-tools with the 0.8.5-4 linuxwacom you compiled.  :(

---

### Post by walterw on 2009-12-27
I just rebuilt the wacom stuff and ran sudo make install.  I get the same thing with that version.


Walter

---

### Post by Favux on 2009-12-27
Hi Walter,

Darn.  We must be missing something.

One other thing you could try is ob1kenobe's -35 patches.  He fixed some minor issues.  But as you'll see in his post he alter the architecture some.  I've been expecting Ayuthia to include his fixes into a new set of patches (and remove the debugging code) but it hasn't happened yet.  They're at [post #586]("http://ubuntuforums.org/showpost.php?p=8376047&postcount=586") on the same thread.

---

### Post by TechGeek22 on 2009-12-29
Let me start by saying I love Ubuntu and the community.  Most everyone is so nice and helpful.

I like some advice on how to get beck to a known state to try re-installing from and what method will have the highest likelihood of success for this tablet.

Ubuntu 9.10 64bit (2.6.31-16-generic)
Wacom BambooFun CTH-661

Got the tablet just before xmas and have been trying for days/week to get it working.  Tried so many methods I'm not sure I backed out all the changes properly.

Some methods tried (there were more):
1) [http://ubuntuforums.org/showpost.php?p=7234134](http://ubuntuforums.org/showpost.php?p=7234134)
2) [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)
3) [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) (option B)

Command: lsmod | grep wacom
Output:      wacom                  25992  0 

Command: modinfo -d wacom
Output:      USB Wacom Graphire and Wacom Intuos tablet driver
                 USB Wacom Graphire and Wacom Intuos tablet driver

Strange that it show up twice.

Not sure what else to include to help you help me...

Thanks in Advance for you help.

---

### Post by Favux on 2009-12-29
Hi TechGeek22,

> I like some advice on how to get beck to a known state to try re-installing from and what method will have the highest likelihood of success for this tablet.
That's currently a problem in Karmic because in Karmic purge or removal of xserver-xorg-input-wacom causes purge or removal of xserver-xorg-input-all (new dependency?).  And reinstalling xserver-xorg-input-all brings along xserver-xorg-input-wacom.  I don't know if that's a bug or not.

Otherwise if you have compiled linuxwacom you could follow Appendix 4 on this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Actually I guess you could do it anyway and then just reinstall xserver-xorg-input-all.

The patches and instructions to get your Fun working are here:  [http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

Good luck!

---

### Post by TechGeek22 on 2009-12-30
I'm sooo close.

I followed the instructions ([http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)).  Both the pen and touch are now controlling the cursor.  

But using: 
xsetwacom set touch Mode Relative

I get errors:
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'

Touch seems to be not using the whole pad in Absolute mode... but pen is okay.  Touch click is super sensitive and I am left clicking without wanting to.

Is there a GUI to adjust these?

---

### Post by Favux on 2009-12-30
Hi TechGeek22,

The calibration and configuration gui is wacomcpl.  Just enter it in a terminal.  It sounds like maybe you don't have the right .fdi.  Try new-generic rc2 here:  [http://ubuntuforums.org/showpost.php?p=8367378&postcount=579](http://ubuntuforums.org/showpost.php?p=8367378&postcount=579) or here:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)  If you haven't already.  Instructions in Section 2 b) of the second link.

---

### Post by TechGeek22 on 2009-12-30
[Favux]("http://ubuntuforums.org/member.php?u=699990") do you ever sleep? Seems every time I post a question you are there to answer. thanks so much for your help. 

The touch bottom right region is still not picking up in touch mode... but I've switched to relative and now it not as noticable.  Are there any Gestures supported?  anything to simulate scroll wheel? rotate etc...

---

### Post by Favux on 2009-12-30
Hi TechGeek22,

Yes, there are a few gestures supported.  I forget which.  Unfortunately I think some of them came after 0.8.5-4.  You may have pinch zoom and two finger scroll though.

---

### Post by TechGeek22 on 2009-12-30
Hi Favux,

I assume I will have to manually update as new versions come out... are there instructions to do that or is it running through the entire process as before?

I also noticed touch mode relative doesn't seem to persist after reboot.  Can I set that in a config file some where?

Again... very grateful for people like you to help the ubuntu community.... wish I were more knowledgeable so I could help others

Cheers,
William

---

### Post by TechGeek22 on 2009-12-30
Noticed another strange thing.  I use touch to navigate around the desktop... while navigating web pages in firefox as I quickly move my finger across the pad to click on another window or access a link it zooms firefox like CTRL + Scroll wheel would.  

Is this a gesture I'm accessing by mistake?  if yes seems too easily accessed.

---

### Post by julieta_ on 2010-09-26
Hi.
First, I must apologize for my bad english - I am brazilian. It is my first time here and I would like to have some help with my tablet Wacom Bamboo Touch CTT460 (only touch, not mouse or pen)  in Ubuntu 9.10, 64 bits (it works with Windows XP - dual boot).
I have wacom-tools and xserver-org-input-wacom (both 1:0.8.4.1 Oubuntu4) installed; 
the command* lsmod |grep wacom* gives me "wacom    25992    0"     (the word wacom is in red);
 the Bamboo's led is on but it does not work. 
I am not advanced in Linux but , Ubuntu is the operating system that I am using and I would like to continue with it.
Thanks for any help.

---

### Post by Favux on 2010-09-26
Hi julieta_,

Welcome to Ubuntu forums!

The default linuxwacom 0.8.4-1 wacom.ko (the usb kernel driver) is too old to support usb communication to your tablet.

You need to compile a newer linuxwacom to get a working wacom.ko.  I'd suggest linuxwacom 0.8.8-8.

See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), section 1.  Or you could use the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") for Lucid if you did a 'sudo make install' after 'make' and before the copy (cp) command.  You would also skip the second step (II.) because you do not need xf86-input-wacom with Karmic.

Hope this helps.

Good luck!

---

### Post by julieta_ on 2010-09-27
Hi, Favux.
Thank you for help me.

I followed the procedures in the site - Section 1, Section 3, letter b, but still does'nt work. In section 4 (Calibrating you tablet..) when I type wamcpl in the teminal I get the reply 'wacomcpl: using TCLLIBPATH="
[list  /usr/lib ]", then  a dialog box is openned :
'Wacom Control Panel'  - with the options: Select the Device (but no  device to select) and Exit.
Is it correct?

---

### Post by Favux on 2010-09-27
Hi julieta_,

It doesn't sound like you compiled and installed linuxwacom 0.8.8-8.

Wacomcpl being blank indicates an earlier linuxwacom that can't read the "Device names" that the kernel (xinput --list) returns.  The 0.8.8-8 linuxwacom would be able to read the new names.

Please try again:
```
cd ./Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-8.tar.bz2

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev libxrandr-dev libhal-dev

sudo apt-get upgrade

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.8-8.tar.bz2

cd linuxwacom-0.8.8-8

./configure --enable-wacom --prefix=/usr

make

sudo make install

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

(After rebooting if not working check if the wacom.ko is auto-loading with lsmod.)

lsmod | grep wacom

(you should see 'wacom' with some other stuff, the size should be different too)
```

---

### Post by julieta_ on 2010-09-27
Hi.

I must add this that I realized after I post the message:
The tablet has one active area and four bottons. The active area that is to move the cursor and click, is not working. But the four bottons are working (I don't know if correctly): two move the page up and down and  two (with small clicks) left and right. Thanks again.

---

### Post by julieta_ on 2010-09-27
Hi, Favux.
I did all the procedures again, as you asked me to.
The previous time I did the procedures I found some errors that I ignored, (as in apt-get update (duplicate sources lists...)); and in apt-get upgrade (   	 	 	 	   	 	 	 	p { margin-bottom: 0.21cm; }   dpkg: erro processando /var/cache/apt/archives/linux-firmware_1.33_all.deb (--unpack):  
   tentando sobrescrever '/lib/firmware/korg/k1212.dsp', que também está no pacote alsa-firmware 0:1.0.17-0medibuntu2.9.10.1))

I did not know if they were relevant (now I know they were, sorry).

This time I stopped at any error message and search internet for the solutions. I guess the result is better now, but  the Bamboo's active area is still not working.
The command* ls mod |grep wacom* returns  Wacom    37152    0
and  *wacomcpl* now  has 4 devices to select.
Thank you.
 
 p { margin-bottom: 0.21cm; }   [COLOR=White]d[/COLOR]

---

### Post by Favux on 2010-09-28
Hi julieta_,

Very well done.  I'm sorry it's not working right.  I don't know why.  Does the cursor follow the stylus at all?  How big a part of the tablet does the stylus work on?

What is the output of?:
```
uname -a
```
and
```
xinput --list
```
and
```
xsetwacom list
```
Let's look at your Xorg.0.log, located in /var/log.  Right click on it and compress it with Create Archive and attach it to your next post using Manage Attachments below.

---

### Post by julieta_ on 2010-09-28
Hi Favux..

My tablet doesn't have a stylus. It has only a pad and I move the cursor (like I do with a mouse) touching with one or two fingers. As you aked:

uname -a 
    Linux ju-ubuntu 2.6.31-22-generic #65-Ubuntu SMP Thu Sep 16 16:21:34 UTC 2010 x86_64 GNU/Linux

xsetwacom list
   Wacom_Bamboo_2FG_Finger     stylus
Wacom_Bamboo_2FG_Finger_touch     touch


xinput --list       (it's too big; here I past only the part related to wacom)

        "Wacom Bamboo 2FG Finger"    id=4    [XExtensionPointer] 
      Type is TOUCHPAD 
      Num_buttons is 12 
      Num_axes is 2 
      Mode is Relative 
      Motion_buffer is 256 
      Axis 0 : 
          Min_value is 0 
          Max_value is 480 
          Resolution is 0 
      Axis 1 : 
          Min_value is 0 
          Max_value is 320 
          Resolution is 0 
  "Wacom Bamboo 2FG Pen pad"    id=5    [XExtensionKeyboard] 
      Type is Wacom Pad 
      Num_keys is 248 
      Min_keycode is 8 
      Max_keycode is 255 
      Num_buttons is 32 
      Num_axes is 6 
      Mode is Relative 
      Motion_buffer is 256 
      Axis 0 : 
          Min_value is 0 
          Max_value is 14720 
          Resolution is 2540 
      Axis 1 : 
          Min_value is 0 
          Max_value is 9200 
          Resolution is 2540 
      Axis 2 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 3 : 
          Min_value is -1 
          Max_value is -1 
          Resolution is 0 
      Axis 4 : 
          Min_value is -1 
          Max_value is -1 
          Resolution is 0 
      Axis 5 : 
          Min_value is 0 
          Max_value is 71 
          Resolution is 1 
  "Wacom Bamboo 2FG Finger pad"    id=6    [XExtensionKeyboard] 
      Type is Wacom Pad 
      Num_keys is 248 
      Min_keycode is 8 
      Max_keycode is 255 
      Num_buttons is 32 
      Num_axes is 6 
      Mode is Relative 
      Motion_buffer is 256 
      Axis 0 : 
          Min_value is 0 
          Max_value is 480 
          Resolution is 2540 
      Axis 1 : 
          Min_value is 0 
          Max_value is 320 
          Resolution is 2540 
      Axis 2 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 3 : 
          Min_value is -1 
          Max_value is -1 
          Resolution is 0 
      Axis 4 : 
          Min_value is -1 
          Max_value is -1 
          Resolution is 0 
      Axis 5 : 
          Min_value is 0 
          Max_value is 71 
          Resolution is 1 
  "Wacom Bamboo 2FG Pen cursor"    id=7    [XExtensionKeyboard] 
      Type is Wacom Cursor 
      Num_keys is 248 
      Min_keycode is 8 
      Max_keycode is 255 
      Num_buttons is 32 
      Num_axes is 6 
      Mode is Relative 
      Motion_buffer is 256 
      Axis 0 : 
          Min_value is 0 
          Max_value is 14720 
          Resolution is 2540 
      Axis 1 : 
          Min_value is 0 
          Max_value is 9200 
          Resolution is 2540 
      Axis 2 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 3 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 4 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 5 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
  "Wacom Bamboo 2FG Finger cursor"    id=8    [XExtensionKeyboard] 
      Type is Wacom Cursor 
      Num_keys is 248 
      Min_keycode is 8 
      Max_keycode is 255 
      Num_buttons is 32 
      Num_axes is 6 
      Mode is Relative 
      Motion_buffer is 256 
      Axis 0 : 
          Min_value is 0 
          Max_value is 480 
          Resolution is 2540 
      Axis 1 : 
          Min_value is 0 
          Max_value is 320 
          Resolution is 2540 
      Axis 2 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 3 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 4 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1 
      Axis 5 : 
          Min_value is 0 
          Max_value is 2048 
          Resolution is 1

Thanks

---

### Post by Favux on 2010-09-28
Hi julieta_,

Right, you have the Bamboo touch.

It looks like the synaptic touchpad .fdi/driver is grabbing your touchpad.  We need to alter the Synaptic .fdi so it isn't so grabby.  To do that nest a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
```
    <match key="info.product" contains="Synaptics">

    </match>
```
So it looks like:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">

......

    </match>
    </match>
  </device>
</deviceinfo>
```
To edit it use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
and then reboot.  Hopefully that will fix things.

---

### Post by julieta_ on 2010-09-28
Hi Favux...

I did as you suggested, but did not work. Now even the express key (the four bottons) stop working. When I touch the active area (or the express key) in  the tablet the led flashes but the cursor doesn't move.

---

### Post by Favux on 2010-09-28
OK, we need to look at those outputs again, except uname-a.

---

### Post by julieta_ on 2010-09-29
Hi Favux,
Today when I turn on my computer  something was missing about wacom. Like this:

*xsetwacom list*           returns nothing

*xinput -- list*               has nothing about wacom

*wacomcpl*                 no devices

Any idea what could have happened?  Thanks.

---

### Post by Favux on 2010-09-29
Hi julieta_,

I believe there was a new kernel update offered for Karmic.  Did you let Update Manager update your kernel?

If so then the new kernel's modules directory has a copy of the old, non-working wacom.ko, not the new one you compiled.  You have to compile linuxwacom against the new kernel and copy the newly compiled wacom.ko into place over the default one.

---

### Post by julieta_ on 2010-10-03
Hi Favux.

I am not sure about kernel update, I don't think I run the  Update Manager. So, I did all the procedures (The LWP' s Linuxwacom) again, Section 1 and Section 3b (configuring only the 10-linuxwacom.fdi). After reboot, the Bamboo Touch was working - only the active area ( the ExpressKeys stop working). But it's better this way, cause that is what I need most (the active area). I will  work in calibratin later.
It worked for two day (PC turned off, turned on) but today when I turned the PC on, the tablet doesn't work anymore. Could you help me one more time, please? Thanks.

---

### Post by Favux on 2010-10-03
Hi julieta_,

I'd be happy to.  I'm not sure what's going on.

I'm worried there is a hardware problem.  Is the tablet plugged into a hub?  In other words is it getting enough power through the usb line?  If it is on a hub can you plug it directly in?

Does the tablet work OK in Windows?

---

### Post by julieta_ on 2010-10-04
Hi Favux.

Today, I turned the computer on and the tablet is working again. It works fine in Windows XP - yesterday I tested it for about one hour without any problem. The tablet is not  plugged into a hub. I don't know what could be happening either, but I will keeping trying. Next step is to calibrate it!!
Thank you for being so nice and patient.

---

### Post by Favux on 2010-10-04
Check the usb cord and make sure it's firmly connected on both ends.  It could be a problem with the usb cable itself.  Or possibly the power demands of an extra device (the tablet) connected are exceeding your power supplies capabilities.

---

### Post by julieta_ on 2010-10-09
Hi, Favux.
I  have no problem in turning off/on the computer any more: the tablet is still there and working. Not so good as in Windows - unhapily - cause I have problems with scroll page up and down and the ExpressKeys don't work yet. But I believe it is a matter of time.
Thank you again.

---

### Post by julieta_ on 2010-11-08
Hi, Favux. How are you?
 
I need your help again, please.
My tablet Wacom Bamboo is still working but this way: every time I turn my computer on I must type the commands "sudo rmmod wacom" and "sudo modprobe wacom" for the tablet work. 
The wacomcpl used to show 5 devices: 
Wacom_Bamboo_2FG_Pen_pad
  Wacom_Bamboo_2FG_Pen_cursor
  Wacom_Bamboo_2FG_Finger_touch 
Wacom_Bamboo_2FG_Finger_pad
  Wacom_Bamboo_2FG_Finger_cursor

The 2FG_Finger_pad is the 4 buttons - the expresskeys;
the 2FG_Finger_touch and/or Finger_cursor are the cursor.
Lately, the wacomcpl shows sometimes 2, sometimes 3 devices. For example: yesterday I didn't have the 2FG_Finger_pad in the wacomcpl (only the 2FG_Finger_cursor), so the expresskeys buttons didn't work. Today, it has the 2FG_Finger_pad and 2G_Finger_touch, but not the 2FG_Finger_cursor.
And I have had some difficult to move the cursor from left to right.
What could I do to solve this?

---

### Post by Favux on 2010-11-08
Hi julieta_,

There was a kernel update today for Karmic.  Have you done that yet?  Once that's done you'll need to recompile linuxwacom.  The linuxwacom version is now 0.8.8-10.

After that try entering:
```
xinput --list
```
and
```
xsetwacom list
```

Part of your problem may be the default linuxwacom.fdi that linuxwacom now installs when you compile it.  It didn't use to install a .fdi.

---

