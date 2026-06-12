---
title: "Natty Narwhal on Lenovo ThinkPad X220T"
date: 2011-06-17
forum: Hardware
---

### Post by unclepedro on 2011-06-17
I just got a ThinkPad X220T in the mail yesterday -- Lenovo's brand new convertible tablet offering. Since this is new hardware with some special characteristics, I thought it might be worthwhile to start a thread for experiences and ideas. Eventually, when this is more fleshed out, I'll write a tutorial.

This is my first new post to UF -- if this isn't the right place for this kind of thread, please let me know and I'll move it.

---

### Post by unclepedro on 2011-06-17
Some pretty reasonable progress so far on the basics. The NN Desktop amd64 iso worked well. Of course, the X220T does not have an optical drive, so I used unetbootin to put the ISO onto a USB thumbdrive. I had to use the F12 boot menu to select the USB device.

I used the basic installer to repartition the disk, shrinking my Windows 7 partition down to 50GB. After repartitioning, the first time you boot Windows, you'll need to run a filesystem check (which Windows will do automatically).

Other than that, the basic installation process proceeds normally and flawlessly. Wifi, network, sound all work out of the box. The pen works, although I think I need to do a little calibration. The finger touching "works" in the sense that the computer is getting the touch signals, but acts extremely weirdly. I'll be looking for a fix for this.

The screen rotation button on the panel does not work by default, although the screen rotation in the Display Settings widget works well enough. (I added the widget to the panel.) However, when the screen is rotated, the pen input seems to be rotated as well (and as I said the finger input is not right). I have hopes that these have already been resolved but haven't tried yet.

So basically, all the non-tablet features work fine; the pen works fine in landscape mode, and (out of the box) finger is "working" but goofy and in rotated mode both are unusable but should be fixable.

I'll report more as I continue to goof around with it.

---

### Post by unclepedro on 2011-06-17
Oh yeah, You'll need to enable the virtualization extensions in the BIOS if you plan to use them in VM software.

---

### Post by Favux on 2011-06-17
Hi unclepedro,

> The finger touching "works" in the sense that the computer is getting the touch signals, but acts extremely weirdly. I'll be looking for a fix for this.

That's because while the product ID 0xE6 is in the 2.6.38 kernel's wacom.ko and in xf86-input-wacom-0.10.11's wcmUSB.c it isn't in wcmValidateDevices.c so the driver doesn't realize it is dealing with a tablet PC with 2FGT.  That is fixed on 0.11.1.  See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part II. b) to update xf86-input-wacom.  That will also get you the cw and ccw rotation fix, so a twofer.
> The screen rotation button on the panel does not work by default, although the screen rotation in the Display Settings widget works well enough. (I added the widget to the panel.) However, when the screen is rotated, the pen input seems to be rotated as well (and as I said the finger input is not right). I have hopes that these have already been resolved but haven't tried yet.
You might want to consider Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by unclepedro on 2011-06-17
Cool. When I searched for X220T in the forums I thought I saw a blurb about fixes helping the X220T but I didn't go further since it wasn't a specific "experience report" with the machine. I will check that stuff out tomorrow and report back.

Thanks!

---

### Post by unclepedro on 2011-06-19
So, I followed the steps in II.b of the link posted above (compiling and installing xf86-input-wacom 0.11.1), and installing magick-rotate. (And installing CellWriter as suggested.) I also did an update/upgrade of all packages and rebooted.

Magick-rotate does indeed rotate magically (based on the hinge of course, the X220T does not have screen rotation accelerometers). Very cool.

Unfortunately, the pen/touch issues I was having before persist. 

The pen works correctly in landscape mode, but is very confused when rotated, as is rotated touch. Touch in landscape is odd; I can move icons with a single finger, but when I try to move windows, the window "jumps" to the left side of the screen (sometimes resizing) when I let go. I assume this is related to the multitouch issues you mentioned before.

Do you know if this is something I can fix with the xsetwacom scripts (described in step III), or is this possibly some other problem? I'm happy to dig around for answers, but if you know off the top of your head it would be very helpful!

---

### Post by Favux on 2011-06-19
Sounds like good progress.

I'm not aware of any issues once rotated in Natty anymore, once xf86-input-wacom is updated to fix the cw and ccw swap.  The fix for Nvidia portrait rotation came through a week or longer ago.  But you're the first X220t reporting I think.  As the first usb Thinkpad tablet, instead of serial ISDV4 like the previous Thinkpad tablets, I guess you're a pioneer.  :)

What outputs do you get with *xinput list* and *xsetwacom list* in a terminal?

What video chip set do you have?  *lspci | grep VGA*

---

### Post by unclepedro on 2011-06-19
> **Favux said:**
> Sounds like good progress.

I'm not aware of any issues once rotated in Natty anymore, once xf86-input-wacom is updated to fix the cw and ccw swap.  The fix for Nvidia portrait rotation came through a week or longer ago.  But you're the first X220t reporting I think.  As the first usb Thinkpad tablet, instead of serial ISDV4 like the previous Thinkpad tablets, I guess you're a pioneer.  :)

Well, I/we'll get it figured out... I hadn't seen any documentation on this hardware, so that's exactly why I figured working through this on the forum would be a good idea.

> **Favux said:**
> 
What outputs do you get with *xinput list* and *xsetwacom list* in a terminal?

What video chip set do you have?  *lspci | grep VGA*

xinput list:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen                              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=15	[slave  keyboard (3)]

```

xsetwacom list returns nothing.

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

If you have any ideas, I'm all ears. I'm happy to do any testing or anything you think would be useful... or, if there are lists or projects I should get in touch with, or subscribe to, etc. I'm happy to do that, too.

---

### Post by Favux on 2011-06-19
Alright since xsetwacom list is blank you're not on the Wacom drivers for whatever reason.  You can confirm that by posting the output of:
```
xinput list-props "ISD-V4 Pen"
```
First let's make sure the 2.6.38 kernel's wacom.ko (the usb kernel driver/module) is auto-loading.  It doesn't on some systems:
```
lsmod | grep wacom
```

The ThinkWiki site has been the go to site for Thinkpads on Linux.  But maybe not quite as up to date as it was and your tablet isn't there yet I don't think:  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by unclepedro on 2011-06-19
Here is the ```
xinput list-props "ISD-V4 Pen"
``` output:

```
Device 'ISD-V4 Pen':
	Device Enabled (127):	1
	Coordinate Transformation Matrix (129):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (249):	0
	Device Accel Constant Deceleration (250):	1.000000
	Device Accel Adaptive Deceleration (251):	1.000000
	Device Accel Velocity Scaling (252):	10.000000
	Evdev Axis Inversion (253):	0, 0
	Evdev Axis Calibration (254):	<no items>
	Evdev Axes Swap (255):	0
	Axis Labels (256):	"Abs X" (245), "Abs Y" (246), "Abs Pressure" (247), "Abs Misc" (248)
	Button Labels (257):	"Button Unknown" (244), "Button Unknown" (244), "Button Unknown" (244), "Button Wheel Up" (133), "Button Wheel Down" (134), "Button Horiz Wheel Left" (135), "Button Horiz Wheel Right" (136)
	Evdev Middle Button Emulation (258):	0
	Evdev Middle Button Timeout (259):	50
	Evdev Wheel Emulation (260):	0
	Evdev Wheel Emulation Axes (261):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (262):	10
	Evdev Wheel Emulation Timeout (263):	200
	Evdev Wheel Emulation Button (264):	4
	Evdev Drag Lock Buttons (265):	0

```

And the wacom.ko module is being loaded automatically:

```
wacom                  42238  0 
```

I did not do anything to try to install wacom drivers or anything like that -- I literally just installed Natty. Since the pen/touch kind of worked, i didn't look any further into that.

And ThinkWiki doesn't have any matches for x220t -- I will probably post a recap there once I find success.

---

### Post by Favux on 2011-06-19
The digitizer is on the evdev X driver.

Did I misunderstand?
> So, I followed the steps in II.b of the link posted above (compiling and installing xf86-input-wacom 0.11.1),
I thought you installed an updated Wacom X driver (xf86-input-wacom 0.11.1) like I suggested in post #4.  Did you?

---

### Post by unclepedro on 2011-06-19
I'm sorry, you're absolutely right. I did recompile and install the xf86-input-wacom-0.11.1 as you suggested. What I meant was that I did not do any configuration or set up any other scripts, nor had I intentionally installed or configured any wacom drivers before I started posting. 

When I read this:

> 
Because xf86-input-wacom doesn't have wacomcpl (Wacom Control Panel) you'll have to set up a script of xsetwacom commands to run when the system starts, like wacomcpl's .xinitrc (see IV. below). ...


I thought maybe I needed to set up some init scripts, but the fact that it was already partially working made me think that the configurations were already in place and the upgrade to .11.1 was all that was necessary.

If I need to look at section IV and play around with some init scripts I'd be happy to do that. Again, I don't expect you to solve this for me, but I appreciate your help thus far. Thanks again!

---

### Post by Favux on 2011-06-19
Well right now the scripts aren't going to help us because it looks like something went wrong with your compile of xf86-input-wacom-0.11.1.

First check if there is a wacom.conf to match the digitizer to the Wacom X driver in xorg.conf.d.  Check in /usr/share/X11/xorg.conf.d.  That's part III. a).

You can see if it is attempting to load the wacom X module in /var/log/Xorg.0.log.  It should have the version number too.

If not why don't you repeat the compile.  See if any errors pop up when you do *./configure --prefix=/usr*, *make*, and *sudo make install*.

---

### Post by unclepedro on 2011-06-20
> **Favux said:**
> First check if there is a wacom.conf to match the digitizer to the Wacom X driver in xorg.conf.d.  Check in /usr/share/X11/xorg.conf.d.  That's part III. a).

There is:

```
$ ls /usr/share/X11/xorg.conf.d/ -al
total 32
drwxr-xr-x 2 root root 4096 2011-06-20 07:44 .
drwxr-xr-x 5 root root 4096 2011-04-25 16:01 ..
-rw-r--r-- 1 root root 1099 2011-05-21 04:56 10-evdev.conf
-rw-r--r-- 1 root root  254 2011-04-16 08:01 11-evdev-quirks.conf
-rw-r--r-- 1 root root  171 2011-06-07 22:36 50-synaptics.conf
-rw-r--r-- 1 root root  115 2011-02-23 07:58 50-vmmouse.conf
-rw-r--r-- 1 root root  833 2011-06-20 07:44 50-wacom.conf
-rw-r--r-- 1 root root  622 2011-06-07 22:36 51-synaptics-quirks.conf

```

Note the current time on the 50-wacom.conf -- it was put in place by the install.

> You can see if it is attempting to load the wacom X module in /var/log/Xorg.0.log.  It should have the version number too.

It does not seem to be loading. At least "wacom" does not appear in the log. See the attached Xorg.0.log, around line 368.

> If not why don't you repeat the compile.  See if any errors pop up when you do *./configure --prefix=/usr*, *make*, and *sudo make install*.

Attached is the build log; there are a number of warnings, but it seems to build properly.

I did not customize my X config at all -- so everything is being loaded based on the default Natty install. (In case that helps.)

---

### Post by Favux on 2011-06-20
Yep, compile looks OK.  Xorg.0.log doesn't have any sign of wacom, just the digitizer being set up by evdev.

Let's check the match in the wacom.conf.  Please post the contents.  I'll see if I can find if the X220t who set up in Arch a couple of weeks ago mentioned anything about needing a new identifier.


Edit:  Oops, not serial it's usb.  So no new identifier since it will use the usb snippet.  Well, still should look at the wacom.conf.

---

### Post by unclepedro on 2011-06-20
Here's the 50-wacom.conf from the install. I didn't realize anyone had been successful before on other 'nixes -- I'll also look at the Arch post.

---

### Post by Favux on 2011-06-20
Everything looks good except you don't seem to be getting a match.  We probably need to look at udevadmin info at some point.

Anyway it looks like a keyword is "ISD-V4", and that appears to be a parent device for both the stylus and touch.  Let's try adding that to the match in the wacom.conf usb snippet.  So it becomes:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|ISD-V4|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
Then restart of course.

---

### Post by unclepedro on 2011-06-20
Now we're cooking with gas!

Adding ISD-V4 to the MatchProduct directive did the trick. Both finger and pen work for basic input, like moving windows, clicking, etc. I can do at least some gestures, such as right clicking with "press-tap" -- although as this is my first touch device for Linux, I am sure I haven't tested the whole gamut, and I haven't tested things like the eraser. (Now that the hardware appears to be working, I will read the standard documentation and see what I need to do.)

magick-rotate works as I described before, and the input rotates with the screen properly. However, I am now noticing that something weird happens to the screen when I rotate it. I've attached screenshots, which (surprisingly) show the effect.

Roughly, part of the desktop is blacked out, although the title bar and dock appear normally. This is a display issue, and happens regardless of the wacom.conf settings or whether magick-rotate is running. I'm sure it was happening from the get-go but I just thought it was a resized black terminal window (especially since formerly, touching windows made them jump around and resize erratically).

Any hot ideas on what might be going on here? If not I will dig around more... as always, I appreciate your expert help. You seem to be the go-to person for Linux touch support -- thanks!

---

### Post by Favux on 2011-06-20
Great!  :)

That looks to be a problem with your:
> Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
chipset Xorg Intel video driver.  You can enable proposed in software sources and see if there's an update available.

Another possiblity I suppose is if the Xorg driver needed to set up a xorg.conf in /etc.  Then maybe you need an:
```
	Option		"RandRRotation"  "on"
```
in the Video Device section.  I don't know if that option is suppose to be automatic on current Intel drivers.  It sure looks like it isn't resizing x and y on rotation though.

Either way since you have the chipset's name you have something to google with.


By the way what does *xinput list* and *xsetwacom list* look like now?

---

### Post by unclepedro on 2011-06-20
```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen stylus                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger touch                     	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen eraser                       	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)]

```

and...

```
$ xsetwacom list
ISD-V4 Pen stylus               	id: 10	type: STYLUS    
ISD-V4 Finger touch             	id: 11	type: TOUCH     
ISD-V4 Pen eraser               	id: 15	type: ERASER 
```

I'll look into the video issues and report back here. I also just subscribed to linuxwacom-devel in case people need me to do any testing.

Thank you!

---

### Post by unclepedro on 2011-06-20
This bug may be relevant:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/793764](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/793764)

Although it seems odd to me that the xserver can display information there perfectly well, but the interface is not utilizing it properly. Could it be a higher level issue, like Unity?

---

### Post by Favux on 2011-06-20
Sure.  When you boot into 11.04 on the log in screen at the bottom is an option to start classic.  Try that and see if it rotates right with classic instead of Unity.

---

### Post by unclepedro on 2011-06-20
Ah, thank you -- that's it. It works perfectly well in classic mode, so it's probably a Unity bug, not an Intel graphics bug.

---

### Post by Favux on 2011-06-20
Outstanding!

So you need to post a Launchpad bug report against Unity and also mention on the bug report you joined that it is Unity.  If they feel the new one is a duplicate they'll let you know.

Not being an Intel video bug saves you from a whole lot of potential hassle, so that is very good.  :)

---

### Post by unclepedro on 2011-06-20
> **Favux said:**
> Outstanding!

So you need to post a Launchpad bug report against Unity and also mention on the bug report you joined that it is Unity.  If they feel the new one is a duplicate they'll let you know.

Not being an Intel video bug saves you from a whole lot of potential hassle, so that is very good.  :)

Yes indeed. Here's the bug -- it was already known for users who wanted two monitors, one rotated and the other not:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/773487](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/773487)

I installed Unity from natty-proposed and that fixed my issue. I responded to that thread, and to the Toshiba portege M400 users (bug linked above) who were having similar issues.

So for now, I think everything actually works... now to figure out how to tweak it the way I like it :) If things remain stable, I'll write up a condensed version of this exchange and we can post it around.

Thanks again for all your help!

---

### Post by Favux on 2011-06-21
Hi again unclepedro,

Could you please post the output of *lsusb* in a terminal?  I want to see if the Wacom Vendor ID is used along with the 0x0E6 Product ID or if it is a Lenovo Vendor ID.  Thank you.

---

### Post by unclepedro on 2011-06-21
> **Favux said:**
> Hi again unclepedro,

Could you please post the output of *lsusb* in a terminal?  I want to see if the Wacom Vendor ID is used along with the 0x0E6 Product ID or if it is a Lenovo Vendor ID.  Thank you.

[pedro@roboto:~]$ lsusb
Bus 002 Device 003: ID 056a:00e6 Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[pedro@roboto:~]$ 

I've posted this to the linuxwacom-devel list as well.

---

### Post by Favux on 2011-06-21
Thank you.

---

### Post by unclepedro on 2011-06-21
So, while I will eventually write up a tutorial for here and elsewhere, here are the basic steps to getting Natty working on the X220T:

1. Install Natty! You'll want to download the amd64 Desktop installer and put it on a USB stick using unetbootin. I had to use the F12 boot menu to select the USB stick. However, the installer resized my Windows 7 partition perfectly well and Windows still works (following the requisite chkdsk). [If you plan to use VM software like VirtualBox, you will want to enable the CPU extensions in the BIOS.]

2. Download the newest source for xf86-input-wacom-0.11.x and extract it. You can find it by following the instructions in section II.b, at the link below. HOWEVER, before building and installing, you need to (as of 0.11.1 -- 6/21/2011) update a configuration file in the sourcecode.

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562). 

In the source tree, find the file ```
.../conf/50-wacom.conf
``` and change the line:

```

       MatchProduct "Wacom|WACOM|Hanwang"

```

... to read:

```

        MatchProduct "Wacom|WACOM|ISD-V4|Hanwang"

```

Then, continue the instructions in Favux' HOWTO for compilation and installation. You should not need to modify any other configuration files. (And I'm sure that this will be fixed in the near future.)

3. There is currently a bug in Unity (again, 6/21/2011) that causes screen display rotation issues. However, if you install the natty-proposed updates to Unity, this is fixed. You can see how to do that by following the directions here: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) Obviously, this could cause some other unanticipated problems for you, but that's just the cost of being such a pioneer. (I only installed the proposed Unity updates.)

4. Install Magick-Rotation, which senses state change in the LCD hinge and automatically rotates the screen. I set it to rotate to the left (instead of the right) so that the rubberized battery "handle" is on the left side, so that I can use it as a grip while writing. (But I'm a righty, so YMMV.) Make sure you follow the directions, as you'll need to confirm to magick-rotation that you want it to load automatically in the future. 

OPTIONAL: Install fingerprint scanner support (requires proprietary library from UPEK)

There is a PPA for fingerprint-gui, a fingerprint scanner supporting the UPEK print scanner in the X220T, available here:

[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

Follow the instructions for installation there. I don't recommend installing from source on 11.04, due to some library issues. Also, there is a bug which throws an error when using sudo in the terminal. It does not seem to cause any real issues though, and will be fixed in the future.

Once these things are installed, your tablet will be working pretty much just as you would expect, including multitouch, pen, (even optional fingerprint scanning!) etc. Pressure sensitivity even works in Gimp (although you have to enable pen input in the Preferences), and I had a relaxing time this morning playing Mahjongg using my fingers. Imagine that.

Two pen input tools I have installed but haven't played with much is gok, the GNOME Onscreen Keyboard, and CellWriter, which is a handwriting recognition/onscreen keyboard tool. So far, I'd recommend CellWriter, but I haven't trained the handwriting tool enough to know how I like it yet.

I'm also planning to do a roundup of note taking tools such as Jarnal, Gournal, Xournal, and NoteLab. Only Xournal is in Ubuntu; Jarnal and NoteLab require Java, and Gournal requires some Perl libraries that are not available in Natty (but you can install manually with a little futzing). So far, Jarnal seems to be the most mature, and it works following installation of the Sun^H^H Oracle JVM (and may work with other JVMs).

Thanks again to Favux and everyone contributing their valuable time and energy to making these deices work -- not to mention answering questions. It's pretty unbelievable that I can put Linux on a brand-new convertible tablet and literally within a week, everything I care about working seems to be working. Kudos!

---

### Post by parzan on 2011-06-22
Thanks for the excellent work!
I am getting a X220t soon, and this thread will be of great value.
Please continue to update on your finds and tweaks!

---

### Post by unclepedro on 2011-06-22
Will do! Eventually I'm planning to put something up on ThinkWiki as well.

---

### Post by Favux on 2011-06-22
A little update.

Apparently the ISD-V4 keyword is coming from a Ubuntu patch to the 2.6.38 kernel.  Ping says the generic 2.6.38 kernel does not have the E6 in it.  And whoever applied the patch to enable the E6 (X220t) didn't use standard Linux Wacom nomenclature.  However Ping says the 3.0 (?) kernel does have the E6 in it and Wacom will work as a keyword.

So for Natty you'll need to add ISD-V4 to the usb snippet in the 50-wacom.conf.  I doubt it is worth filing a bug report over this.  And if the kernel team does backport in the correct descriptor it shouldn't suddenly stop working because you'll still have the Wacom keywords in the 50-wacom.conf.

---

### Post by unclepedro on 2011-06-22
I like to have my screen lock when idle, but that's pretty annoying when in tablet mode. Fortunately, fingerprint scanner support and integration into pam, gdm, and gnome-screensaver can be installed using the fingerprint-gui tool, available in PPA form here:

[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

I do not recommend installing from source. However, you should be warned that fingerprint-gui requires a proprietary thumbprint scanner driver from UPEK. There's also a bug which throws an error when using sudo from the terminal, but it should be fixed in the future, and doesn't seem to cause any real problems.

---

### Post by kcin on 2011-06-25
Well, I have been trying to get the stylus working in NN without much luck.  I made the changes to the conf file before configuring/making the xf86-input-wacom package.  The wacom module shows up in lsmod and the "ISD-V4 Pen stylus" shows up in xinput.  Unfortunately I have had absolutely no luck getting the pen to move the cursor or anything else.  Any ideas?  

I didn't install any scripts/other setting files since I just wanted to get the stylus running and I gathered they weren't necessary when I read the installation instructions.

---

### Post by Favux on 2011-06-25
Hi kcin,

Welcome to Ubunut forums!

> I made the changes to the conf file before configuring/making the xf86-input-wacom package.
xf86-input-wacom-0.11.1 will install a 50-wacom.conf when compiled in every release but Lucid.  So check your wacom.conf and see if the ISD-V4 keyword is still there.  It probably isn't as it was likely over written.  If it isn't add it back in.

---

### Post by unclepedro on 2011-06-25
Yeah, we'll get this figured out... Maybe I left something out of the instructions. It could be worth reading the thread from the beginning to see if I did.

---

### Post by PickleHead on 2011-06-29
Hi I just installed ubuntu on my x220t to try it out after using windows for so long. I followed your instructions and everything works great except for the unity utouch multitouch features. Anything involving more than one finger doesn't seem to work at all in unity. Pinch zoom kind of works in firefox though. Any ideas?

---

### Post by unclepedro on 2011-06-30
> **PickleHead said:**
> Hi I just installed ubuntu on my x220t to try it out after using windows for so long. I followed your instructions and everything works great except for the unity utouch multitouch features. Anything involving more than one finger doesn't seem to work at all in unity. Pinch zoom kind of works in firefox though. Any ideas?

Hi, you know, I was just reading about that stuff the other day. I seem to have pinch zooming in Firefox, Evince, and Nautilus, but it is somewhat hard to use -- I find it easier to use two hands, one finger stationary, and the other moving... not the most user friendly.

But I haven't specifically messed around with utouch or any other touch related tools. I'm definitely planning to but haven't had time. It'd be great if you would report any experiences you have, here, and we'll go from there.

---

### Post by unclepedro on 2011-07-01
The Ricoh card reader is not fully operational in stock Natty. I will report on the fix for this ASAP.

[https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/790754](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/790754)

---

### Post by Mr. Code Depot on 2011-07-06
Hi on another similar thread [[http://ubuntuforums.org/showthread.php?t=1797487](http://ubuntuforums.org/showthread.php?t=1797487)] User nmaster paste this link [[http://www.ubuntu.com/certification/hardware/201103-7377]](http://www.ubuntu.com/certification/hardware/201103-7377]) -  I think it is relevant.

---

### Post by spikn on 2011-07-07
unclepedro and Favux,

Many thanks for all this.  I've been using an X40t for years now but am ready to upgrade.  When I get the new machine I will use your instructions and send you feedback.

---

### Post by Zta on 2011-07-07
This thread's a keeper!!

Thanks guys for all this wonderful and exact information on getting the X220T Ubuntufied!  I'm currently looking for a replacement for my T61, and preferably something closer to my old and oh-so-lovely X30, which was small, light and silent.  This tablet thing sounds interesting, but only if it works.  Thanks to this thread I'm now this > < close to buying a X220T! =)

I have a few specific questions, some about the very hardware, so this is to Uncle Pedro I guess:

[LIST=1]
[*]**Rotation:**  I didn't understand the part where you said the screen didn't have rotation accelerometers ... only hinges.  Two question:  Could you please elaborate on that?   And: Does this mean, that Ubuntu does not rotate the screen graphics, when you physically rotate the machine, e.g. from landscape to portrait?

[*]**Screen Rotation Buttons:**  You mentioned the screen rotation button doesn't work.  It should force the screen to rotate, right?  Have you made it work in the mean time?  Can you pick up events from this button?  Maybe a simple hack could make it work.  I hate dead keys =)

[*]**Web Camera:**  Does it work?  How have you tested it?  Does it work in Skype?

[*]**Eraser:**  What's this?  Literally using the other end of the stylus on the screen?  What is it used for? =)

[*]**WWAN:**  Did you machine come with 3G or WiMax or any other WWAN device?  And if so, does it work?

[*]**Screen:**  Did you pick the old-school non-glossy anti-reflective coating? (I've heard Lenovo ship them with Mac-like coating too).  Are you satisfied with the viewing angles?  My old X30 and even the T61 are quite bad for editing photos.  I plan on getting an "external monitor" as well, but still it would be neat, if the laptop could do the job.

[*]**Screen Hinge:**  Does it seem robust enough?  Does it wobble a lot so you have to re-adjust it, if you sit with the machine on your lap and move?  The the machine sturdy enough built, or do you think the screen will break off any day soon? =)

[*]**Noise and Heat:**  Of course, I don't know how sensitive you are to this, but I personally can't stand the sound of a fan =).

[*]**Card Reader:**  Any news?  It does read SD cards, right?

[*]**Calibration:**  Can Linux calibrate the stylus input?  Have you tried it?  Or found it necessary?
[/LIST]

Sorry if some are a tad off-topic, but I'm really excited about all the new goodies in this thread! =)

---

### Post by contactez on 2011-07-14
> **unclepedro said:**
> Hi, you know, I was just reading about that stuff the other day. I seem to have pinch zooming in Firefox, Evince, and Nautilus, but it is somewhat hard to use -- I find it easier to use two hands, one finger stationary, and the other moving... not the most user friendly.

But I haven't specifically messed around with utouch or any other touch related tools. I'm definitely planning to but haven't had time. It'd be great if you would report any experiences you have, here, and we'll go from there.

I'm in the same boat as Picklehead here, nothing multi touch besides a little pinch zooming and the right click (two finger second finger double tap).  Would love to get the gestures to work!

On the bright side though single touch accuracy is imo much better than Windows, not as many missed clicks.  Thanks you guys for getting it this far though, big improvement over plain install.  :D

EDIT: Oh, I forgot to mention there's also two finger scroll that works on firefox,nautilus,libreoffice etc. but it is even buggier than the pinch zoom T_T

---

### Post by unclepedro on 2011-07-14
> **Zta said:**
> This thread's a keeper!!

Thanks guys for all this wonderful and exact information on getting the X220T Ubuntufied!  I'm currently looking for a replacement for my T61, and preferably something closer to my old and oh-so-lovely X30, which was small, light and silent.  This tablet thing sounds interesting, but only if it works.  Thanks to this thread I'm now this > < close to buying a X220T! =)

I have a few specific questions, some about the very hardware, so this is to Uncle Pedro I guess:

Whoops, sorry on the delay. I forgot I had to check back in to get new updates.

> **Zta said:**
> 
**Rotation:**  I didn't understand the part where you said the screen didn't have rotation accelerometers ... only hinges.  Two question:  Could you please elaborate on that?   And: Does this mean, that Ubuntu does not rotate the screen graphics, when you physically rotate the machine, e.g. from landscape to portrait?


What I mean is that the hinge and lid has sensors to indicate the state. So if you use Magick-Rotation (as specified in this thread), it will rotate for you when you change the screen. However, it does not orient the picture based on the relationship between the screen and the ground (like a digicam or iphone with rotation sensor [an accelerometer]).

> **Zta said:**
> 
**Screen Rotation Buttons:**  You mentioned the screen rotation button doesn't work.  It should force the screen to rotate, right?  Have you made it work in the mean time?  Can you pick up events from this button?  Maybe a simple hack could make it work.  I hate dead keys =)


A fix for this is in the works, but does not appear to be in Natty Proposed as of yet. I'm sure it will be, because you can get events from the keys.

> **Zta said:**
> 
**Web Camera:**  Does it work?  How have you tested it?  Does it work in Skype?


It works in Cheese with no problem; I did not test it with Skype but I expect it will work.

> **Zta said:**
> 
**Eraser:**  What's this?  Literally using the other end of the stylus on the screen?  What is it used for? =)


The other end of the stylus has a big red button; the screen can identify which tip you're using, so programs like Gimp can set different tools to each end. It's pretty handy, but it's not exactly clear to me how it all works. Jarnal (the notetaking app I have been using) does not currently support it, but eventually I'll probably try hacking it in.

> **Zta said:**
> 
**WWAN:**  Did you machine come with 3G or WiMax or any other WWAN device?  And if so, does it work?


I did not purchase it with those options so I can't answer this question.

> **Zta said:**
> 
**Screen:**  Did you pick the old-school non-glossy anti-reflective coating? (I've heard Lenovo ship them with Mac-like coating too).  Are you satisfied with the viewing angles?  My old X30 and even the T61 are quite bad for editing photos.  I plan on getting an "external monitor" as well, but still it would be neat, if the laptop could do the job.


Good question. I got the non-glossy, matte screen. The x220t comes in matte, with multitouch, and gorilla glass, which is PEN ONLY, repeat PEN ONLY. The gorilla glass is advertised as "outdoor visible," although in my experience, the matte screen is pretty well visible outdoors with the brightness turned up. I probably wasn't sitting in direct, high-noon sunlight, but are you really going to take your X220t to the beach? In my estimation, the screen is MUCH brighter than my old T43, which basically unusable outside.

> **Zta said:**
> 
**Screen Hinge:**  Does it seem robust enough?  Does it wobble a lot so you have to re-adjust it, if you sit with the machine on your lap and move?  The the machine sturdy enough built, or do you think the screen will break off any day soon? =)


I have not had a tablet before, but it really does seem like a pretty solid piece of equipment and I like the magnetic latch better than the old tab designs I've seen on older ones.

> **Zta said:**
> 
**Noise and Heat:**  Of course, I don't know how sensitive you are to this, but I personally can't stand the sound of a fan =).


Well, it's much quieter than my T43. The fan seems to blow pretty steadily, but it seems like this may be an IBM ACPI issue. Not sure. It's not the quietest machine, but I'm pretty happy with it on that point.

> **Zta said:**
> 
**Card Reader:**  Any news?  It does read SD cards, right?


Integrated Ricoh cardreader. Apparently the fix is in, but not yet to natty.

> **Zta said:**
> 
**Calibration:**  Can Linux calibrate the stylus input?  Have you tried it?  Or found it necessary?


This is actually one of my proto-gripes so far. Sometimes the pen accuracy near the edge of the screen is goofy, like it hovers inside about a cm until you put the pen down, when it jumps to the edge. I'm not sure if this is a calibration issue, a driver issue, or a hardware issue. Eventually I'll look into it, but it really only comes up when you are writing right up to the edge of the screen. I've seen some mention of this online, too, but I'm not sure what the fix is/isn't.

> **Zta said:**
> 
Sorry if some are a tad off-topic, but I'm really excited about all the new goodies in this thread! =)

No, those are all really good questions, and now that I've used the machine for a while I feel like I can answer them.

A couple other things. The keyboard is great; and it has an extra large delete key, which at first I thought was annoying, but I now like. The "click pad" behavior is a little odd (e.g., right click does not work by default), but it's possible that this is a configuration issue. 

It includes a wifi/bluetooth hard switch, which I like for power saving purposes. 

It drives an external monitor quite well; I currently use a Dell 1680x1050 as my separate screen when on my desk.

The speakers are pretty good; nothing fancy but better than the old laptop.

Another thing you didn't ask about is battery life -- I don't have a specific answer yet, but it's not bad. (I completely disregard stated battery life estimates from manufacturers.) I'm not sure what a full drain would take, maybe some time I will tell it not to sleep and just run it for several cycles to see how long it runs.

---

### Post by unclepedro on 2011-07-14
Yeah, I agree, the multitouch stuff is disappointing right now, but it seems to me to be "almost there." It's not something I have time to monkey with right now, but if anyone has a solution, please let me know!

---

### Post by unclepedro on 2011-07-14
One last thing -- I honestly think my biggest gripe about the X220T is the 1366x768 screen. I wish it was at least 1024. But so many comparable machines out there have this resolution, and I like so much about the X220T I went with it anyway.

---

### Post by Favux on 2011-07-14
Chris is working on gesture improvement:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_YVbcRFBexAsK%2B4xULs8gW25xJbmyLTiq5-868aMSLYGA%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_YVbcRFBexAsK%2B4xULs8gW25xJbmyLTiq5-868aMSLYGA%40mail.gmail.com&forum_name=linuxwacom-devel)

So hopefully something is not too far off.

---

### Post by contactez on 2011-07-14
> **unclepedro said:**
> One last thing -- I honestly think my biggest gripe about the X220T is the 1366x768 screen. I wish it was at least 1024. But so many comparable machines out there have this resolution, and I like so much about the X220T I went with it anyway.

Ditto

I'm pretty much sure I won't be using it in portrait mode for anything besides pdf reading.  Even full screen without task bars, it's just too narrow for even single-page web browsing.

Landscape mode is fine though.  I find that turning the laptop around and then turning the screen back to face you makes for a nice, easy on-the-couch surfing experience.  :popcorn:  The popcorn helps grease up the screen for gestures ;)

What might (with luck) save portrait mode is *smooth zoom* like in Opera Mobile 11, and every phone/ipod browser out there.  The jerky zoom is just too jarring and inadequate when you're trying to find that sweet spot.  Opera Mobile 11 is available for Windows, but it only runs full screen and uses its own gesture set, so it doesn't really cater well to multitasking needs.

We will get there eventually :)

---

### Post by unclepedro on 2011-07-15
> **contactez said:**
> Ditto

I'm pretty much sure I won't be using it in portrait mode for anything besides pdf reading.  Even full screen without task bars, it's just too narrow for even single-page web browsing.


I also use it for note taking.

> **contactez said:**
> Landscape mode is fine though.  I find that turning the laptop around and then turning the screen back to face you makes for a nice, easy on-the-couch surfing experience.

Agreed. I'm planning to submit a patch to Magick-Rotation at some point to select specific rotations manually -- so if I normally want it to be in portrait, but occasionally want to select "normal" or "flipped" for "couch mode" I can.

I also wish there were easily accessible brightness settings.

> **contactez said:**
> What might (with luck) save portrait mode is *smooth zoom* like in Opera Mobile 11, and every phone/ipod browser out there.  The jerky zoom is just too jarring and inadequate when you're trying to find that sweet spot.  Opera Mobile 11 is available for Windows, but it only runs full screen and uses its own gesture set, so it doesn't really cater well to multitasking needs.

Yeah, that would be pretty cool. You'd think they could get something like that going with Compiz.

---

### Post by karlkoch23 on 2011-07-24
Loving it...I just got a 240GB SSD thist weekend which will replace the normal 5400rpm hard drive. I installed Natty and had no major problems....only, my touchpad isn't working...it actually also did not work with windows. Both touchpad and trackpoint are enabled in bios. No combination of enabling or disabling worked. Could therefore any of you guys give me your devices output? Below is mine....
Was anyone able to configure your buttons on the tablet screen?
Thank you all for this nice write up.


```
cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0003 Vendor=056a Product=00e6 Version=0139
N: Name="ISD-V4 Pen"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=b
B: KEY=1c03 0 0 0 0 0
B: ABS=10001000003

I: Bus=0003 Vendor=04f2 Product=b217 Version=0854
N: Name="Integrated Camera"
P: Phys=usb-0000:00:1a.0-1.6/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input7
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=33
B: KEY=18040000 0 10000000000000 0 1501b00102004 8000000001104000 e000000000000 0
B: MSC=10
B: SW=a

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=056a Product=00e6 Version=0139
N: Name="ISD-V4 Finger"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: PROP=0
B: EV=1b
B: KEY=6400 0 0 0 0 0
B: ABS=10001000003
B: MSC=1

```

---

### Post by karlkoch23 on 2011-07-24
Me again...
I just reduced some problems I had with the fan. It was constantly running full speed and pitching to even higher speed every 6 seconds...
Seems to be a common problem: 
[http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-fan-constantly-on-revving-up-and-down/td-p/425965/page/60](http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-fan-constantly-on-revving-up-and-down/td-p/425965/page/60)

A workaround was found here:

[http://ubuntuforums.org/archive/index.php/t-1750934.html](http://ubuntuforums.org/archive/index.php/t-1750934.html)

But this only reduces fan-speed. The pitch every 6 seconds is still there, just not as audible.
I hope Lenovo will be able to fix this issue, because it is really anoying.

Another issue remaining is that my wlan keeps on droping. It seems to be a Natty bug.
Switching of Power Management as suggested elsewhere did not help.
Will maybe try to compile new drivers as suggested here:
[http://ubuntuforums.org/showthread.php?t=1753298](http://ubuntuforums.org/showthread.php?t=1753298)

Happy about any input.

---

### Post by unclepedro on 2011-07-24
> **karlkoch23 said:**
> Loving it...I just got a 240GB SSD thist weekend which will replace the normal 5400rpm hard drive. I installed Natty and had no major problems....only, my touchpad isn't working...it actually also did not work with windows. Both touchpad and trackpoint are enabled in bios. No combination of enabling or disabling worked. Could therefore any of you guys give me your devices output? Below is mine....

<scooby>Ruhroh, Raggy...</scooby> I don't see your Synaptics Touchpad in your list. Are you sure its enabled in the bios? If so then it's probably disconnected inside the case. 

```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=056a Product=00e6 Version=0139
N: Name="ISD-V4 Pen"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=b
B: KEY=1c03 0 0 0 0 0
B: ABS=10001000003

I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input5
U: Uniq=
H: Handlers=rfkill kbd event5 
B: PROP=0
B: EV=33
B: KEY=18040000 0 10000000000000 0 1501b00102004 8000000001104000 e000000000000 0
B: MSC=10
B: SW=a

I: Bus=0003 Vendor=056a Product=00e6 Version=0139
N: Name="ISD-V4 Finger"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=0
B: EV=1b
B: KEY=6400 0 0 0 0 0
B: ABS=10001000003
B: MSC=1

I: Bus=0003 Vendor=04f2 Product=b217 Version=0854
N: Name="Integrated Camera"
P: Phys=usb-0000:00:1a.0-1.6/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: PROP=5
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input10
U: Uniq=
H: Handlers=mouse3 event10 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

```

> 
Was anyone able to configure your buttons on the tablet screen?


I haven't yet; it should work in some future kernel. I think there is probably a way to map the events but I just haven't spent much time. If you figure it out, please post it here. The thing is that there *are* mappings for other Thinkpad lid buttons in the kernel, but they are not getting used by the X220. Some ID must not be right. I dunno.

This is also a bizarre thought, but I wonder if the fingerprint reader couldn't be abused to serve as a pageup/pagedn sensor. Likewise, I may see if I can re-purpose the lid power button at some point... I think it would be more useful for some other purpose. 

Anyhoo... good luck!

---

### Post by parzan on 2011-07-27
**xrotate**

In magick-rotation there is a script called xrotate.py, which basically does what the rotation button on the tablet does in windows (it can also switch to a specific rotation using parameters). You can bind it to a launcher on your panel, and have a nice substitute for the tablet button (it would be better of course if someone finds how to bind it to the button!)

Here's the rub: to get it working on the x220t you need to edit the file (xrotate.py) and replace all LVDS with LVDS1 (or better, replace ["LVDS", "DFP"] with ["LVDS", "LVDS1", "DFP"] to keep compatibility with other machines).

---

### Post by unclepedro on 2011-07-27
> **parzan said:**
> **xrotate**

In magick-rotation there is a script called xrotate.py, which basically does what the rotation button on the tablet does in windows (it can also switch to a specific rotation using parameters). You can bind it to a launcher on your panel, and have a nice substitute for the tablet button (it would be better of course if someone finds how to bind it to the button!)

Here's the rub: to get it working on the x220t you need to edit the file (xrotate.py) and replace all LVDS with LVDS1 (or better, replace ["LVDS", "DFP"] with ["LVDS", "LVDS1", "DFP"] to keep compatibility with other machines).

Nice! Thanks.

---

### Post by karlkoch23 on 2011-07-27
Will try the magick-rotation trick and set a launcher for nowe...thx.
I just wanted to look into remaping the buttons...I am no expert by any means
First thing was trying to see the keycode by using

```
xev
```

But this showed no signal at all for any of the tablet-buttons....so I think pushing the button is currently not even recognized....
Any ideas?

---

### Post by mateolan on 2011-07-28
> **unclepedro said:**
> So, while I will eventually write up a tutorial for here and elsewhere, here are the basic steps to getting Natty working on the X220T:

1. Install Natty! You'll want to download the amd64 Desktop installer and put it on a USB stick using unetbootin. I had to use the F12 boot menu to select the USB stick. However, the installer resized my Windows 7 partition perfectly well and Windows still works (following the requisite chkdsk). [If you plan to use VM software like VirtualBox, you will want to enable the CPU extensions in the BIOS.]

2. Download the newest source for xf86-input-wacom-0.11.x and extract it. You can find it by following the instructions in section II.b, at the link below. HOWEVER, before building and installing, you need to (as of 0.11.1 -- 6/21/2011) update a configuration file in the sourcecode.

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562). 

In the source tree, find the file ```
.../conf/50-wacom.conf
``` and change the line:

```

       MatchProduct "Wacom|WACOM|Hanwang"

```... to read:

```

        MatchProduct "Wacom|WACOM|ISD-V4|Hanwang"

```Then, continue the instructions in Favux' HOWTO for compilation and installation. You should not need to modify any other configuration files. (And I'm sure that this will be fixed in the near future.)

3. There is currently a bug in Unity (again, 6/21/2011) that causes screen display rotation issues. However, if you install the natty-proposed updates to Unity, this is fixed. You can see how to do that by following the directions here: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) Obviously, this could cause some other unanticipated problems for you, but that's just the cost of being such a pioneer. (I only installed the proposed Unity updates.)


Firstly, thanks so much for this--it couldn't be more timely for me.  I just received my 220t a few days ago, and fortunately, you have saved me a lot of work...I still have a few issues though, even though I swear I have followed your instructions explicitly.  
1)  My stylus pen and touch were both working (albeit inaccurately as you described--previous to the wacom.conf updates.  Once I added the ISD-V4 line and recompiled, although my touch works alright (even with multitouch), my stylus pen has stopped working completely.
What have I missed?  Is it possible that there was another mod that you forgot to document?
2)  I tried to update unity through the proposed repository, but there was no package unity found inside of the proposed reposiitory (yes, I added it to my sources). thoughts?
3) WRT the fingerprint scanner, when I rebooted after install, and logged-in via fingerprint, I received a pop-up from Natty saying that my gnome-keyring was not unlocked via log-in...and then when I tried to use my password, it would still not authenticate...any ideas?

Thanks again!

---

### Post by parzan on 2011-07-29
**rotation and subpixel smoothing**

If in nonstandard orientations the display seems less crisp, it probably means ubuntu is relying on the subpixel order of colors (red-green-blue) for font rendering (check System -> Preference -> Appearance -> Fonts -> Details).
To set the correct order each time you can make a script:
```
#!/bin/bash

orientation=$(xrandr -q --verbose  | grep connected|grep -v disconnected | awk '{print $5}')
case $orientation in
    normal) subpixel=rgb ;;
    left) subpixel=vrgb ;;
    inverted) subpixel=bgr ;;
    right) subpixel=vbgr ;;
    *) notify-send "could not determine orientation for antialiasing" ;;
esac
gconftool-2 --type string --set /desktop/gnome/font_rendering/rgba_order $subpixel &
# notify-send "subpixel order set to $subpixel"

```save it (say, as "after_rotation.sh") and place it in magick-rotation setup, both in "Run after switch to tablet" and in "Run after switch to normal". When magick-rotation is running it calls these scripts both after manual rotation (via xrotate.py) and after automatic rotation.
If you are not sure if it is running uncomment the last line in the script to get a message each time it is called (or open System -> Preference -> Appearance -> Fonts -> Details and see whether the subpixel order changes).
I'll be happy to get any tips - I am a novice scripter.

---

### Post by Favux on 2011-07-29
Nice script but does this really make things clearer?  I would like opinions.

It seemed like this was an issue with older releases but not so much anymore.  Of course I have an older tablet PC and it may just be my display isn't good enough for me to notice the issue.

Typo, should read:
```
    normal) subpixel=rgb ;;

```

---

### Post by parzan on 2011-07-29
Thanks for the correction, Favux. I edited my post so people do not suffer from my typo.
As to the effect - I see it most clearly in terminals (white font against this eggplant hue ubuntu is so fond of).

---

### Post by wcunning on 2011-07-29
I just got my X220T a few days ago, and I've spent this week trying to get Linux up and running. I started with openSUSE (my preferred distro), followed by Fedora, followed by Kubuntu, since this is where I get the tablet functionality. 

On a fresh install of Kubuntu 11.04 64bit, the tablet works out of the box, but the touch does not (as has been stated before). So, I've done what this post suggests and installed the most recent version of xf86-input-wacom, which is still 0.11.1. On a fresh install of this, I lose the tablet, multitouch works better but not correctly and I need to figure out why it's not working and how to fix it. I've attached my xinput --list output and will provide anything else that people recommend.

```

wcunning@dahak:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen eraser                         id=10   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen cursor                         id=11   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen touch                          id=12   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen pad                            id=13   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen stylus                         id=14   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger eraser                      id=15   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger cursor                      id=16   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger touch                       id=17   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger pad                         id=18   [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger stylus                      id=19   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=21   [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                     id=23   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                         id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=20   [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                    id=22   [slave  keyboard (3)]


```

---

### Post by beckzar on 2011-07-30
What battery life do you see in your X220T's running 11.04 and a 6 cell battery? I only get around 3 hours...not happy with that.

/Beckz

---

### Post by Favux on 2011-07-30
Hi Beckz,

[QUOTE=beckzar]What battery life do you see in your X220T's running 11.04 and a 6 cell battery? I only get around 3 hours...not happy with that.[/QUOTE]
The Leading Cause Of The Recent Linux Kernel Power Problems:  [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=2)
Linux kernel 2.6.38 and 2.6.39 power regression workaround:  [http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972)

---

### Post by beckzar on 2011-08-01
> **Favux said:**
> Hi Beckz,


The Leading Cause Of The Recent Linux Kernel Power Problems:  [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=2)
Linux kernel 2.6.38 and 2.6.39 power regression workaround:  [http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/#more-1972)

I tried the above suggestions and it didn't change much really. My system went from 20W to 18W power consumption. Yesterday I worked with a collegue running an Acer system (workstation laptop much like W510). After two hours I hade to plugin my power adapter and he still had about 1,5 hours left on his battery. 

I love Ubuntu but I've had it with its lack of hardware support for newer laptops. I'll probably go back to Windows 7 with this one.

/Beckz

---

### Post by karlkoch23 on 2011-08-01
Hi everyone,

resolved my wlan drop problems. They could be resolved by compiling and installing the latest drivers from realtek.

Determine what card you are using:
```
jfk@jfk-ThinkPad:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        EC::D:F9::PFC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


jfk@jfk-ThinkPad:~$ 

```

Download according driver (e.g. rtl8192ce):

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

compile and install:

```
jfk-ThinkPad:~$ make 
```

```
jfk-ThinkPad:~$sudo make install 
```

Reboot and wireless works fine.

---

### Post by unclepedro on 2011-08-01
> **mateolan said:**
> 
1)  My stylus pen and touch were both working (albeit inaccurately as you described--previous to the wacom.conf updates.  Once I added the ISD-V4 line and recompiled, although my touch works alright (even with multitouch), my stylus pen has stopped working completely.
What have I missed?  Is it possible that there was another mod that you forgot to document?

Hmmm.... that seems pretty odd to me. Did you modify anything else, like the xorg.conf or anything like that? Has anyone else had this problem? I don't think there's anything missing from the instructions.

[/QUOTE]2)  I tried to update unity through the proposed repository, but there was no package unity found inside of the proposed reposiitory (yes, I added it to my sources). thoughts?[/quote]

Hmmm... it's possible that the package I got, which *was* in proposed, is now in the main branch.

> 3) WRT the fingerprint scanner, when I rebooted after install, and logged-in via fingerprint, I received a pop-up from Natty saying that my gnome-keyring was not unlocked via log-in...and then when I tried to use my password, it would still not authenticate...any ideas?

Not sure. is this consistently a problem?

---

### Post by unclepedro on 2011-08-01
> **beckzar said:**
> I tried the above suggestions and it didn't change much really. My system went from 20W to 18W power consumption. Yesterday I worked with a collegue running an Acer system (workstation laptop much like W510). After two hours I hade to plugin my power adapter and he still had about 1,5 hours left on his battery. 

I love Ubuntu but I've had it with its lack of hardware support for newer laptops. I'll probably go back to Windows 7 with this one.

/Beckz

Pretty much all Linux flavors have worse power management than Windows. I haven't tried a head-to-head power drain on both Windows and Linux, so I can't really comment for the X220T.

I have been tweaking mine for power consumption a bit, but I'm not sure what it's currently drawing. A few things I did:

[LIST]
[*]install noflushd (warning: may cause data loss but I'm not worried)
[*]put /tmp and /var/log and /var/lib/sudo on tmpfs ramdisks
[*]disabled bluetooth
[*]installed powertop and investigated its suggestions
[/LIST]

As an aside, I like that the machine has a hardware switch for wireless.

---

### Post by unclepedro on 2011-08-01
> **karlkoch23 said:**
> I installed Natty and had no major problems....only, my touchpad isn't working...it actually also did not work with windows. Both touchpad and trackpoint are enabled in bios. No combination of enabling or disabling worked. 

Did you get this issue resolved?

---

### Post by karlkoch23 on 2011-08-01
> **unclepedro said:**
> Did you get this issue resolved?

Yeah...it was rellay unpluged... I have to admit though that changing any hardware parts is extremly easy with the thinkpad line. With my Vaio Z21 it always was a fight...
I am currently trying to get the tablet buttons to work.
I can get them recognized by first determining their value through first pushing the key and then running 

```
jfk@jfk-ThinkPad:~$ sudo dmesg -c
[ 3082.836813] atkbd serio0: Unknown key pressed (translated set 2, code 0x6c on isa0060/serio0).
[ 3082.836823] atkbd serio0: Use 'setkeycodes 6c <keycode>' to make it known.

```

This tells me that the keyvalue for the rotate button is 6c. By running

```
sudo getkeycodes
```
Tells what keys are free

```
sudo setkeycodes 6c 158
```

I can assign it to keycode 165, there is a funny bug which adds 8 to every keycode you enter...took me a while to figure that out.

Now pushing the button is registered with 

```
xev
```

this is where I have to stop, since it's time to sleep...

---

### Post by parzan on 2011-08-02
Here are my findings playing with karlkoch23's observations:

It turns out that 162 is the keycode for XF86RotateWindows, and ```
sudo setkeycodes 6c 154
``` (recall that 154=162 due to the 8 bug) makes the rotation button rotate the screen _even when magick-rotation is not running_. The rotation is weird - the modes appear in a strange order. When magick-rotation is running, the "before rotation" and "after rotation" commands are triggered, but the rotation order is still the weird one so it seems that the rotation itself is not done by magick-rotation, even in this case.

Since this is rather annoying, my solution is running ```
sudo setkeycodes 6c 149
``` instead, which maps the rotation button to XF86Launch2 (XF86Launch1 is already bound to the ThinkVantage button), and binding XF86Launch2 to xrotate.py in gnome-keybinding-properties. It makes sense to do also ```
sudo setkeycodes 67 202
``` which binds the other tablet button to XF86Launch3. 

To see the various keycodes available, run ```
xmodmap -pke | grep XF86
``` but remember to subtract 8 when running setkeycodes!

---

### Post by Karenin on 2011-08-08
> **unclepedro said:**
> Hmmm.... that seems pretty odd to me. Did you modify anything else, like the xorg.conf or anything like that? Has anyone else had this problem? I don't think there's anything missing from the instructions.


I have a similar problem. Actually, everything worked (I followed your instructions), but after installing kubuntu-desktop the stylus pen stopped working.

This is my xinput --list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=9    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen stylus                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen eraser                           id=15    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger touch                         id=16    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

``` xinput list-props  11:

```
Device 'ISD-V4 Pen stylus':
    Device Enabled (127):    1
    Coordinate Transformation Matrix (129):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (253):    0
    Device Accel Constant Deceleration (254):    1.000000
    Device Accel Adaptive Deceleration (255):    1.000000
    Device Accel Velocity Scaling (256):    10.000000
    Wacom Tablet Area (277):    0, 0, 27760, 15694
    Wacom Rotation (278):    0
    Wacom Pressurecurve (279):    0, 0, 100, 100
    Wacom Serial IDs (280):    230, 0, 2, 0
    Wacom Capacity (281):    -1
    Wacom Pressure Threshold (282):    27
    Wacom Sample and Suppress (283):    2, 4
    Wacom Enable Touch (284):    0
    Wacom Hover Click (285):    0
    Wacom Enable Touch Gesture (286):    0
    Wacom Touch Gesture Parameters (287):    50, 20, 250
    Wacom Tool Type (288):    "STYLUS" (270)
    Wacom Button Actions (289):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (290):    0, 0

```and running lsmod | grep wacom results in:
```
wacom                  42238  0 
```

---

### Post by unclepedro on 2011-08-09
> **Karenin said:**
> I have a similar problem. Actually, everything worked (I followed your instructions), but after installing kubuntu-desktop the stylus pen stopped working.


I have no idea... so it was working, but then *after* installing kubuntu-desktop it stopped?

---

### Post by Karenin on 2011-08-11
> **unclepedro said:**
> I have no idea... so it was working, but then *after* installing kubuntu-desktop it stopped?

Yes, it happened after kubuntu-desktop. Though it is possible, that I installed something before I installed kubuntu-desktop. However, I'm not shure if tested the pen after installing these other packages.

Anyway, installing ccsm solved my problems.

---

### Post by unclepedro on 2011-08-11
> **Karenin said:**
> Yes, it happened after kubuntu-desktop. Though it is possible, that I installed something before I installed kubuntu-desktop. However, I'm not shure if tested the pen after installing these other packages.

Anyway, installing ccsm solved my problems.

Great. Glad you got it sorted out.

---

### Post by beckzar on 2011-08-16
> **unclepedro said:**
> Pretty much all Linux flavors have worse power management than Windows. I haven't tried a head-to-head power drain on both Windows and Linux, so I can't really comment for the X220T.

I have been tweaking mine for power consumption a bit, but I'm not sure what it's currently drawing. A few things I did:

[LIST]
[*]install noflushd (warning: may cause data loss but I'm not worried)
[*]put /tmp and /var/log and /var/lib/sudo on tmpfs ramdisks
[*]disabled bluetooth
[*]installed powertop and investigated its suggestions
[/LIST]

As an aside, I like that the machine has a hardware switch for wireless.

I tried Win 7 for a few days and I just didn't feel very happy. The battery time was ok, but that was just about the only thing that was better. So today I re-installed Ubuntu despite the power problem. The strange thing is that the battery consumption is down to around 10W instead of 20W like before. I.e. quite acceptable battery time, even a bit better that Win 7 and I havn't started tweaking yet.

As far as I can tell the only difference is that I'm running Unity instead of Classic and have installed a 64-bit beta version of the Flashplugin for Firefox. 

I'm running 2.6.38-10 and Gnome 2.32.1

---

### Post by unclepedro on 2011-08-16
> **beckzar said:**
> I tried Win 7 for a few days and I just didn't feel very happy. The battery time was ok, but that was just about the only thing that was better. So today I re-installed Ubuntu despite the power problem. The strange thing is that the battery consumption is down to around 10W instead of 20W like before. I.e. quite acceptable battery time, even a bit better that Win 7 and I havn't started tweaking yet.

As far as I can tell the only difference is that I'm running Unity instead of Classic and have installed a 64-bit beta version of the Flashplugin for Firefox. 

I'm running 2.6.38-10 and Gnome 2.32.1

My guess is that as software support for sandybridge gets better, the runtime and performance will improve. But that's great! There was a hangcheck timer issue for sandybridge that was going crazy in Unity, but that has been fixed -- I imagine that may have been draining the battery somewhat (but I don't really know).

---

### Post by beckzar on 2011-08-17
> **unclepedro said:**
> My guess is that as software support for sandybridge gets better, the runtime and performance will improve. But that's great! There was a hangcheck timer issue for sandybridge that was going crazy in Unity, but that has been fixed -- I imagine that may have been draining the battery somewhat (but I don't really know).

The 2.6.38-10 kernel does not allow me to use an external monitor in the Ultrabay dock, so I compiled and installed 3.0.2. Now its working fine. However, battery drain is up to around 20W again. So the problem is probably introduced in newer kernels. Have a look at Powertop below for the two kernels:

[ATTACH]200254[/ATTACH]
[ATTACH]200255[/ATTACH]

---

### Post by unclepedro on 2011-08-18
> **beckzar said:**
> The 2.6.38-10 kernel does not allow me to use an external monitor in the Ultrabay dock, so I compiled and installed 3.0.2. Now its working fine. However, battery drain is up to around 20W again. So the problem is probably introduced in newer kernels. Have a look at Powertop below for the two kernels:

[ATTACH]200254[/ATTACH]
[ATTACH]200255[/ATTACH]

Hmm... if you compiled 3.0.2 yourself, is it possible that you missed some energy-saving options or something like that? Otherwise, I would probably file a bug.

---

### Post by spikn on 2011-08-21
Hi unclepedro and favux,

I finally got my beautiful new Lenovo.  I followed unclepedro's guide from June 21st: it worked fairly well (though it wasn't clear how to do the "EnableProposed" part.  I did something else by following Favux's post, which I hope is equivalent).

My problem is with Magick-Rotation: I followed the installations one the website carefully, several times (including reboot), and I still have never seen a green rotation icon appear in the Unity toolbar.  Any idea what I might be doing wrong?  The install_log reads:[INDENT]File to install in /etc/udev/rules.d:
62-magick.rules

Ok to install?
Compiling check.c
gcc -lX11 -lXrandr /home/jeanluc/magick-rotation/check.c -o /home/jeanluc/magick-rotation/checkmagick64
0

Copying
cp 62-magick.rules /etc/udev/rules.d/
0

Removing installed filecheck
rm /home/jeanluc/magick-rotation/firstrun
0
[/INDENT]**[update**: after posting I tried running the installation under "Ubuntu Classic" and it worked!  Then I switched back to Unity and the green Magick-Rotation icon is still there!  So it seems to be some incompatibility of the installation with Unity, at least on my system.  BTW, does anybody know whether it's safe to delete the magick-rotation folder from my home dir, or how to move it elsewhere?]

So far I like the computer but the screen is a little disappointing.  So much beveling makes it look behind the times, and the resolution is pretty low.  I also turned off the trackpad for now.  You can't beat that Thinkpad keyboard, though!  The multitouch doesn't seem so useful for now, and the misalignment of the pen near the edges is really annoying.  But overall, I like it a lot as a laptop.

Many thanks for your great work,

Jean-Luc

---

### Post by Favux on 2011-08-21
Hi spikn,

Good, problem solved.  Not sure why you had to use Classic.

You need to keep the magick-rotation folder.  It contains most of the program.  We haven't set the installer up yet to do anything different.

For future reference there is a little gui for gsettings called dconf-editor, which you may need to install.  When you run the command in the gui go to desktop > unity > panel and that's where the systray-whitelist is.  Remember it is a work in progress so for some stuff you still need to use gconf-editor.

---

### Post by spikn on 2011-08-23
Hi Favux,

Why do I need to use gconf-editor?  Do I need to add magick-rotate to the menubar whitelist?

Speaking of which: today I was all set to use my X220t to take notes for the first time during a seminar.  Upon rotating the screen at first things went well but after some writing (and turning on the touchscreen) the pen completely lost the position, and the magick-rotate icon vanished from the toolbar.  Upon rotating back the pen still doesn't track properly (though I'm sure a reboot will fix it).  Anybody have any ideas?  I'm pretty sure I have the most current version of the drivers installed (but am not sure how to check).

Does anybody know how to disable the touchscreen semi-permanently?  For now it's basically useless.  I looked in the BIOS but there seems to be no such setting.

Cheers,

sp

**update:** the tray icon is weird... it seems to sometimes be there and sometimes not.  As for the pen problem, I think maybe I fixed it: when I re-installed the wacom drivers from source it overwrote the old 50-wacom file with the changes.

---

### Post by Xeovke on 2011-08-24
Hello all,
  I'm also a happy owner of a new X220t and I also decided to install ubuntu except I changed my mind at the last minute and install kubuntu instead. I'm not too sure if this is the source of my problems (or if it stems simply from my incompetence) but the stylus pen never did work. [Edit: after a simple reboot today it started to work... this feels sligthtly silly since I did wait and try a lot before posting this... it seems the god of Kubuntu was simply pleased that I posted something.]

There are still a few issues I haven't been able to resolve...

1- Magick rotation does not really work, i.e. it does not rotate automatically upon tablet mode (but it's possible to disable touch with it).

2- the camera in Skype is upside down (found quite a few threads about that but none solved the problem)

would appreciate any help!

 best,
 X

---

### Post by unclepedro on 2011-08-24
> **Favux said:**
> Hi spikn,
For future reference there is a little gui for gsettings called dconf-editor, which you may need to install.  When you run the command in the gui go to desktop > unity > panel and that's where the systray-whitelist is.  Remember it is a work in progress so for some stuff you still need to use gconf-editor.

I've had an issue where the green arrow icon disappears after a time, but where magick-rotation is clearly still running/working in the background. It may have to do with having a second monitor connected.

Any thoughts?

---

### Post by unclepedro on 2011-08-24
> **spikn said:**
> Hi Favux,
**update:** the tray icon is weird... it seems to sometimes be there and sometimes not.  As for the pen problem, I think maybe I fixed it: when I re-installed the wacom drivers from source it overwrote the old 50-wacom file with the changes.

I have been using Jarnal for note-taking. Every once in a while it gets confused about pen input. And I've seen the Xorg be briefly confused about the pen location a few times -- but these are rare, transient problems. I've never had the pen just "stop working" for any reason. So hopefully it was that code problem and not something chronic.

---

### Post by unclepedro on 2011-08-24
> **Xeovke said:**
> Hello all,
  I'm also a happy owner of a new X220t and I also decided to install ubuntu except I changed my mind at the last minute and install kubuntu instead. I'm not too sure if this is the source of my problems (or if it stems simply from my incompetence) but the stylus pen never did work. [Edit: after a simple reboot today it started to work... this feels sligthtly silly since I did wait and try a lot before posting this... it seems the god of Kubuntu was simply pleased that I posted something.]

I can't speak to Kubuntu at all -- I've never tried it. But I'm glad that it started to work for you.

> 
1- Magick rotation does not really work, i.e. it does not rotate automatically upon tablet mode (but it's possible to disable touch with it).

Huh. I don't know why this would be. Favux?

> 
2- the camera in Skype is upside down (found quite a few threads about that but none solved the problem)


Haven't tried this -- it seems to work in cheese so I haven't looked further.

---

### Post by Xeovke on 2011-08-24
Hello UnclePedro,
  thanks a lot for your message (and all the previous work).

> **unclepedro said:**
> 
Haven't tried this -- it seems to work in cheese so I haven't looked further.

Vertical flip is unfortunately absent in Skype. However, feeling heartened by the success of the stylus, I tried again to start skype with the command line

> 
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
and now standing on my head requires much more effort.

Which only leaves the magick-rotate problem [Edit: i.e. 
  a- no rotation on passing to tablet mode and 
  b- there is an x-axis distortion factor when the screen is rotated by 90 and 270 degrees. The y-axis is ok, but the x-axis is about 2 as much (pointing at the middle of the screen with the stylus responds with a pointer icon already on the boundary)]
Any idea welcome!
  X

---

### Post by spikn on 2011-08-25
H unclepedro,

I've had both the same issues as you:

1) the magick-rotation tray icon sometimes disappears, but the program is still running.

2) When using xournal, sometimes the pen stops working for anywhere from 1 to 10 seconds.

Regarding (1), note that I don't have an external monitor, so that's not the problem here.  I've been using Ubuntu Classic w/o effects for a couple of days now and I don't remember the m-r icon ever disappearing.  Are you using Classic or Unity?

Overall I find the machine a little difficult to work with: the pen seems much less well calibrated than it was with my old X41t, so it's hard to have good handwriting when writing lecture notes.

sp

---

### Post by unclepedro on 2011-08-25
> **spikn said:**
> H unclepedro,

I've had both the same issues as you:

1) the magick-rotation tray icon sometimes disappears, but the program is still running.

2) When using xournal, sometimes the pen stops working for anywhere from 1 to 10 seconds.

Regarding (1), note that I don't have an external monitor, so that's not the problem here.  I've been using Ubuntu Classic w/o effects for a couple of days now and I don't remember the m-r icon ever disappearing.  Are you using Classic or Unity?

Overall I find the machine a little difficult to work with: the pen seems much less well calibrated than it was with my old X41t, so it's hard to have good handwriting when writing lecture notes.



I am using Unity with effects -- and I'm not surprised that it disappears with Classic mode... there are a number of little paper cuts like that with Unity, I feel.

I don't know what the old X41t was like; in general, I find the pen to be pretty great, with the exception of the edges of the panel. Is this a calibration or driver issue? Or is this a physical issue? I've heard almost everyone complain about this... I have been hoping that it's something that could be fixed down the road... because it *is* extremely annoying and makes the device seem cheap. Which as you know it is not. (I should boot into Windows and try it out.)

Another issue I have had is that the left mouse button seems to "bounce click" -- by which I mean, sometimes when I single click with the left mousepad button, I get a doubleclick. I'm not sure if this is some sensitivity calibration issue, or if it's a hardware issue... but I've been too busy to try to figure it out.

---

### Post by spikn on 2011-08-25
> **unclepedro said:**
> I am using Unity with effects -- and I'm not surprised that it disappears with Classic mode... there are a number of little paper cuts like that with Unity, I feel.

Yep.  I gave up on it because of incompatibility, but also strange behavior that is hard to modify -- such as the 'maximize snap-to-top' which was driving me crazy.

> **unclepedro said:**
> I don't know what the old X41t was like; in general, I find the pen to be pretty great, with the exception of the edges of the panel. Is this a calibration or driver issue? Or is this a physical issue? I've heard almost everyone complain about this... I have been hoping that it's something that could be fixed down the road... because it *is* extremely annoying and makes the device seem cheap. Which as you know it is not. (I should boot into Windows and try it out.)

The edges were not great on the X41t either.  What worries me is that I feel the pen is less accurate everywhere on the screen.  Yes, you should try it in Windows, at least to get a reference level for what to expect.

> **unclepedro said:**
>  Another issue I have had is that the left mouse button seems to "bounce click" -- by which I mean, sometimes when I single click with the left mousepad button, I get a doubleclick. I'm not sure if this is some sensitivity calibration issue, or if it's a hardware issue... but I've been too busy to try to figure it out.

You mean with the touchpad?  I've been using the nub + buttons (the X41t didn't have a touchpad, so I got used to the nub.)  Do you left-click/right-click by the location of your finger?

---

### Post by unclepedro on 2011-08-25
> **spikn said:**
> Yep.  I gave up on it because of incompatibility, but also strange behavior that is hard to modify -- such as the 'maximize snap-to-top' which was driving me crazy.

There's a thread on this. The issue is with the Grid plugin for compiz. You can make it waaaay less sensitive so it doesn't grab windows and think for you. But it also does awesome window placement stuff with keybindings. So I bound the "keypad keys" (789uiojkl) to places windows in those corners/sides of windows with the modifier <ctrl><alt><shift>. I have a binding <c><a>x to make a new terminal, so to put two windows side by side I can do c-a x, c-a-s u, c-a x, c-a-s o. It's pretty sweet. You can also make each side grow or shrink (say to have a 1/3 by 2/3 split) by repeating the combo.

> 
The edges were not great on the X41t either.  What worries me is that I feel the pen is less accurate everywhere on the screen.  Yes, you should try it in Windows, at least to get a reference level for what to expect.

I find that incredibly disappointing. Pen input should be 100% up to the edge of the screen. Seriously. I'll test this in windows and report.

[quote]You mean with the touchpad?  I've been using the nub + buttons (the X41t didn't have a touchpad, so I got used to the nub.)  Do you left-click/right-click by the location of your finger?

No, the actual buttons. The left button will sometimes doubleclick when I only intend to single click.

---

### Post by Xeovke on 2011-09-01
Hello again,     Just wondering if anyone had an idea about some small annoyances:

 I tried to map the special tablet keys to the xrotate.py script (associating them using setkeycodes to some launch buttons, and then configuring in system setting -> global shortcuts) but a strange thing keeps happening. Basically, tough I press only once on the key the script is invoked always 2-3 times. If the script is used from console there is however no problem.   

The micro on/off button has a scancode 248, using xmodmap I associated it to some other launch button. The "global shortcuts" GUI recognises the input, but when I press on it, nothing happens. 

Is there a direct method of assigning global shortcuts? 

Magick-rotation still does not detect tablet mode, any clues?

Thanks in advance...

---

### Post by altercation on 2011-09-04
Just wanted to touch base in this thread regarding power regression.

I think my previous correspondence with Favux was referenced in this thread already. I previously worked with the linuxwacom folks (Favux was awesome) to get my x220t touchscreen recognized under Arch Linux.

I wanted to play around with utouch so I'm going to try getting it working under Ubuntu first before trying to get the whole utouch stack to play nice under Arch.

I'm running 11.10 and like every other 3.0 kernel experience on the x220, power consumption out of the box is ridiculous. It may have been noted on this thread elsewhere but I wanted to confirm that the following kernel boot parameter cuts my power consumption by about 40%. (~20W to ~12W).

If anyone else is on 11.10 and interested, here's a walkthrough. Apologies if this seems offtop to Natty.

1. edit /etc/default/grub ```
sudo vi /etc/default/grub
``` or other editor.

2. edit the GRUB_CMDLINE_LINUX_DEFAULT by adding the following option:

```
i915.i915_enable_rc6=1
```so the entire line will look something like:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
```3. After saving, rebuild the grub boot*config:

```
sudo update-grub
```You can then confirm that the kernel param has been picked up **after a reboot** by:

```
dmesg | grep 915
```and you should see it in there near the top of the grepped output.

---

### Post by parzan on 2011-09-05
> **Xeovke said:**
> Hello again,     Just wondering if anyone had an idea about some small annoyances:

 I tried to map the special tablet keys to the xrotate.py script (associating them using setkeycodes to some launch buttons, and then configuring in system setting -> global shortcuts) but a strange thing keeps happening. Basically, tough I press only once on the key the script is invoked always 2-3 times. If the script is used from console there is however no problem.   

The micro on/off button has a scancode 248, using xmodmap I associated it to some other launch button. The "global shortcuts" GUI recognises the input, but when I press on it, nothing happens. 

Is there a direct method of assigning global shortcuts? 

Magick-rotation still does not detect tablet mode, any clues?

Thanks in advance...

The reason you get two rotations is probably that you bound the button to XF86RotateWindows, which  rotates the screen by itself. if you turn off magic rotation you'll get only one rotation, but I didn't like the way it behaves. See my solution in message #69 in this thread.

---

### Post by Xeovke on 2011-09-07
> **parzan said:**
> The reason you get two rotations is probably that you bound the button to XF86RotateWindows, which  rotates the screen by itself. if you turn off magic rotation you'll get only one rotation, but I didn't like the way it behaves. See my solution in message #69 in this thread.

Thanks for your answer, but as you remarked this problem in your post, I bound it to XF86Launch3. Prior to creating the shortcut I checked that there was not anything else associated to it. Any other idea?

The "solution" I found was to associate this Lauch button to "/.../xrotate.py left" instead, and find another button for "/.../xrotate.py normal".

By the way, since I plugged an external monitor, the magick-rotation icon disappeared (even after many reboot without external monitor). Since it did not work, that's not much of a problem. However, the "disable/enable touch" feature was handy. Does anyone have an idea (e.g. a simple script) to do this?

---

### Post by maxxum on 2011-09-18
> **unclepedro said:**
> So, while I will eventually write up a tutorial for here and elsewhere, here are the basic steps to getting Natty working on the X220T:
...
...
4. Install Magick-Rotation, which senses state change in the LCD hinge and automatically rotates the screen. I set it to rotate to the left (instead of the right) so that the rubberized battery "handle" is on the left side, so that I can use it as a grip while writing. (But I'm a righty, so YMMV.) Make sure you follow the directions, as you'll need to confirm to magick-rotation that you want it to load automatically in the future. 

Thanks for being a pioneer in this and helping us out. Sorry for the dumb question that is to follow. I got up to the point where I installed and configured magik rotation. But the screen does not rotate. I see the green arrow icon and have set it to start automatically at boot and rotate left. But there is no rotation. I am logging in to Ubuntu classic, not unity. 
Secondly, I see pinch zooming working (though jerky) in firefox. How can I use flicks (I want to scroll using an upward flick, for example).

---

### Post by unclepedro on 2011-09-18
> **maxxum said:**
> Thanks for being a pioneer in this and helping us out. Sorry for the dumb question that is to follow. I got up to the point where I installed and configured magik rotation. But the screen does not rotate. I see the green arrow icon and have set it to start automatically at boot and rotate left. But there is no rotation. I am logging in to Ubuntu classic, not unity. 
Secondly, I see pinch zooming working (though jerky) in firefox. How can I use flicks (I want to scroll using an upward flick, for example).

You're welcome. Thanks to Favux and the rest for all their hard work.

I don't have a lot of answers for you, unfortunately.

1. Try running xrotate.py in the Magick-rotation sources (see the docs for arguments). Does that properly rotate your screen?

2. I have not ended up using the touch gestures, etc. very much because I agree that they are a big coarse and jerky. I'm hoping that this will improve in the future... or someday when I have a little more free time I may look into it.

Has anyone here found touch settings that they like?

---

### Post by Favux on 2011-09-18
Hi everyone,

Chris Bagwell has submitted a bunch of Gesture patches to improve gestures.  A lot of them have been committed to the xf86-input-wacom repository now so you might want to clone it and test them out.  I've tested his first version of the patch for scroll and zoom and it worked great.  Scroll was a little slow but we've figured out a new default and now it's the best I've seen.  Zoom was more sensitive and he thinks he's figured out a fix for the cursor jump when you add the second finger.  Unfortunately the scroll patch hasn't been committed yet.  Soon hopefully.


Hi maxxum,

As unclepedro suggested go into the magick-rotation folder and first make sure xrotate.py is executable and then run:
```
./xrotate.py left
```
Does it rotate?

If it does check in the folder that, depending on whether you have a 32-bit or 64-bit install, a binary executable called checkmagick32 or checkmagick64 has appeared.  In other words the installer compiled it successfully.

Also check if thinkpad_acpi is auto-loading:
```
lsmod | grep thinkpad
```

---

### Post by maxxum on 2011-09-18
It does not rotate :(
```
@x220t:~$ cd ./Desktop/magick-rotation/
@x220t:~/Desktop/magick-rotation$ ./xrotate.py left
Traceback (most recent call last):
  File "./xrotate.py", line 846, in <module>
    r.rotate(direction)
  File "./xrotate.py", line 770, in rotate
    display.direction = display.rotate(direction)
AttributeError: 'NoneType' object has no attribute 'rotate'
```
-----------------------------------------------------------------
```
x220t:~/Desktop/magick-rotation$ lsmod | grep thinkpad
thinkpad_acpi          81587  0 
nvram                  14419  1 thinkpad_acpi
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device

```

---

### Post by Favux on 2011-09-18
So the module is loaded.

Hmmm.  Does:
```
xrandr -o left

```
get the screen orientation to rotate left?  By the way use *normal* to get it back.

What's your video chipset?
```
lspci | grep VGA
```

---

### Post by maxxum on 2011-09-18
It did rotate with xrandr -o left
I was able to rotate it back to normal (thanks for mentioning that!!).

```
@x220t:~/Desktop/magick-rotation$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

---

### Post by Favux on 2011-09-18
Alright, then the video driver doesn't need anything to configure rotation.  What is the output of the following command?
```
xrandr -q --verbose
```
Really just need the first few lines so the line that the next command deals with is in it, i.e. the one that has *connected* in it.  And then the command:
```
xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)'

```

---

### Post by maxxum on 2011-09-18
```
@x220t:~/Desktop/magick-rotation$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (0x49) normal (normal left inverted right x axis y axis) 277mm x 156mm
	Identifier: 0x41
	Timestamp:  10549034
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0030e4d80200000000
		00140103801c1078ead4e59559578b28
		20505400000001010101010101010101
		010101010101601d56d8500018303040
		4700159c1000001b0000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fe
		004c503132355748322d534c42310084
	BACKLIGHT: 7 (0x00000007)	range:  (0,15)
	Backlight: 7 (0x00000007)	range:  (0,15)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1366x768 (0x49)   75.2MHz +HSync -VSync *current +preferred
        h: width  1366 start 1414 end 1478 total 1582 skew    0 clock   47.5KHz
        v: height  768 start  772 end  779 total  792           clock   60.0Hz
  1360x768 (0x4a)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x4b)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1024x768 (0x4c)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4d)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4e)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4f)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x42
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
HDMI2 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x45
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
HDMI3 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x46
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
DP2 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x47
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)
DP3 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x48
	Timestamp:  10549034
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	force_audio: 0 (0x00000000)	range:  (-1,1)

```
Response to the command below was "normal".
```
@x220t:~/Desktop/magick-rotation$ xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)'
normal
```

---

### Post by Favux on 2011-09-18
Whew, that looks good too.  When you're rotated left or ccw the long command should say left.  So did you check if there was a checkmagic executable?

---

### Post by maxxum on 2011-09-18
Yes, I do see a checkmagic64 executable in the Magik Rotation folder. What might be stopping it from rotating then, when I flip to the tablet mode?

---

### Post by Favux on 2011-09-18
Alright.

Not sure.  I don't see why it is complaining about an AttributeError at line 770.  It seems like it should be populated.  I'm guessing it has something to do with the CTM changes jayhawk made.

What is your output of?
```
xinput list
```

---

### Post by maxxum on 2011-09-18
> **Favux said:**
> 
What is your output of?
```
xinput list
```
It is:```
@x220t:~/Desktop/magick-rotation$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger touch                     	id=13	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen stylus                       	id=14	[slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen eraser                       	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-09-18
Alright then touch is on the Wacom X driver too since touch is appended to Finger.  That shoots that idea down.

I don't understand why Magick Rotation 1.4 is working on my usb tablet PC with touch and other X220t's but not some X220t's.

We'll need jayhawk aka Ayuthia to figure this out it looks like.  I'll see if he has some time.

---

### Post by maxxum on 2011-09-18
Thanks. I will wait.

---

### Post by Ayuthia on 2011-09-18
> **maxxum said:**
> Thanks. I will wait.

I think that this link has the solution to the error that you are getting for xrotate.py.  Please replace the current file with the one in this [link]("http://ubuntuforums.org/showpost.php?p=11064598&postcount=1562").  There was an issue with the script not accepting LVDS1 because of the number at the end.

Please let us know if it helps.

---

### Post by maxxum on 2011-09-19
hi,
I renamed the original xrotate.py to xrotate-orig.py and put the new file in the folder and rebooted. Still nothing happens when the hinge is rotated to the tablet mode. 
Am I making a stupid mistake of not knowing to make one of the scripts executable? or are they supposed to work just like that?

---

### Post by Ayuthia on 2011-09-19
> **maxxum said:**
> hi,
I renamed the original xrotate.py to xrotate-orig.py and put the new file in the folder and rebooted. Still nothing happens when the hinge is rotated to the tablet mode. 
Am I making a stupid mistake of not knowing to make one of the scripts executable? or are they supposed to work just like that?

Is the xrotate.py script working from the Terminal?  If it isn't, can you post the error message?

It also sounds like we might be dealing with a couple of issues.  One is with xrotate.py having an error when it is called and the other is with the tablet not rotating.  Magick_rotation does auto rotate some tablets that have the wmi module but if I recall correctly, the ThinkPad has an acpi script that does it.  I will need to look into that a little further.

---

### Post by maxxum on 2011-09-19
Running xrotate in terminal rotates the screen. I repeatedly run it to see the screen make one full rotation.
```
@x220t:~/Desktop/magick-rotation$ ./xrotate.py 
going: inverted
xinput set-prop 16 'Coordinate Transformation Matrix' -0.562225475842 -0.0 1 0.0 -1.0 1 0.0 0.0 1.0
inverted:  [-0.5622254758418741, -0.0, 1, 0.0, -1.0, 1, 0.0, 0.0, 1.0]
@x220t:~/Desktop/magick-rotation$ ./xrotate.py 
going: right
xinput set-prop 16 'Coordinate Transformation Matrix' 0.0 1.0 0.0 -0.562225475842 0.0 1 0.0 0.0 1.0
right:  [0.0, 1.0, 0.0, -0.5622254758418741, 0.0, 1, 0.0, 0.0, 1.0]
@x220t:~/Desktop/magick-rotation$ ./xrotate.py 
going: normal
xinput set-prop 16 'Coordinate Transformation Matrix' 0.562225475842 0.0 0.0 0.0 1.0 0.0 0.0 0.0 1.0
normal:  [0.5622254758418741, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]

```

---

### Post by Ayuthia on 2011-09-19
Good.  That means that it is now working.  The next part is to see if the /dev/input/lenovo-acpi file is there.  Can you check and see if it is there?

---

### Post by maxxum on 2011-09-19
> **Ayuthia said:**
> Good.  That means that it is now working.  The next part is to see if the /dev/input/lenovo-acpi file is there.  Can you check and see if it is there?
No that file is not there.

---

### Post by Favux on 2011-09-19
Check in /etc/udev/rules.d/ for a file called 62-magick.rules.  Is it there?

---

### Post by maxxum on 2011-09-20
> **Favux said:**
> Check in /etc/udev/rules.d/ for a file called 62-magick.rules.  Is it there?
No. That folder has only 4 files. 

10-vboxdrv.rules
70-persistent-cd.rules
70-persistent-net.rules
README

---

### Post by Favux on 2011-09-20
Ah, then that is likely the remaining problem.

Create the file with:
```
gksudo gedit /etc/udev/rules.d/62-magick.rules
```
Copy and paste the entire contents of the attached file into it.  Save and reboot.

You should now have the /dev/input/lenovo-acpi file and rotation should work.  Let me know.

---

### Post by maxxum on 2011-09-20
That did it!! Thanks.
Phew! now that the rotation works, I would like to get more tablet functionality in.

How do you guys get a software keyboard? When one clicks in a place like a browser address bar, how can one have a keyboard pop up or one that can be slid into the screen from the side (like the original win7 app had in x220t)?

---

### Post by Favux on 2011-09-20
Great!  Nice job handling that double whammy.  :)

Say, can you check in the magick-rotation folder and see if the file 62-magick.rules is there and has the contents?  I'm wondering if the installer_gtk.py not installing it for you is a onetime deal or is there an intermittent bug?  I guess we'll have to see if it happens to others.

Magick is designed to work with CellWriter so that CellWriter shows in tablet mode and hides in laptop.  You can use another on screen keyboard if you want.  But since CellWriter has both the keyboard and the letter recognition it seems like the best choice.  You should be able to install it through the Software Center.

---

### Post by maxxum on 2011-09-20
Yes the 62-magik.rules is there in hte magik-rotation folder. It has the contents:
```
# udev rules for tablet pc's using an OEM-WMI or OEM-ACPI
#
# These rules were compiled for the Ubuntu/Debian GNU/Linux distribution, but others may,
# and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS to 62-magick.rules with
# Jayhawk so that we can try to present users with a standard set of device nodes which
# they can rely on across the board.

KERNEL!="event[0-9]*", GOTO="oem-wmi_end"

# The symlinks constructed by the following rules are used in Magick Rotation's oem_wmi.py.
ATTRS{name}=="HP WMI hotkeys", SUBSYSTEM=="input", MODE="644" SYMLINK+="input/hp-wmi"
ATTRS{name}=="Dell WMI hotkeys", SUBSYSTEM=="input", MODE="644" SYMLINK+="input/dell-wmi"
ATTRS{name}=="ThinkPad Extra Buttons", SUBSYSTEM=="input", MODE="644" SYMLINK+="input/lenovo-acpi"

LABEL="oem-wmi_end"
```

---

### Post by maxxum on 2011-09-20
I am using cellwriter now. I would like to have its keyboard bigger. Is there such an option? 
The tablet is very much usable now, thanks to you helpful folks. I'm loving the two finger scroll from the touchpad though. So much better than having to find the edge to scroll. The scrolling is smooth as well. Ubuntu as always is fast up on its feet and quick to shut down. Suspend on lid close/open works great as well. 
Now if only we can swipe-to-scroll and pinch to zoom. Do we have anything to look forward to in 11.10 in terms of tablet-features?

---

### Post by Favux on 2011-09-21
[QUOTE=maxxum]I am using cellwriter now. I would like to have its keyboard bigger. Is there such an option? [/QUOTE]
Sure switch to the keyboard by pressing *Keys* on the bottom if you're not already in keyboard mode.  Enter *Setup* and adust *Keyboard:  pixels wide*.  You can watch it dynamically resize.
[QUOTE=maxxum]Now if only we can swipe-to-scroll and pinch to zoom. Do we have anything to look forward to in 11.10 in terms of tablet-features? [/QUOTE]
As I mentioned a patch to help scroll/zoom is pending.  Chris is reworking some of the driver code flow which I guess is taking some time.  I sort of doubt the gesture improvements will land in Oneiric.  I'm not sure which version of xf86-input-wacom it has as default but I'm thinking they're too recent to have landed in Oneiric.

Oneiric has GNOME 3.2 and so now we see the first rudimentary Wacom cpanel applet for the gnome control center.  Early days and it only deals with the stylus.  There was suppose to be a left handed feature and a hidden calibration button but I don't think they made it.  Maybe Oneiric will still get them?

Peter added hooks to the gnome-settings-daemon to make the cpanel applet possible.  But that can trip you up because its settings can override your settings in xorg.conf.d or xorg.conf and you need to be aware of that.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

---

### Post by maxxum on 2011-09-25
I'm having a new issue now. The left mouse click often stops working, both on the touchpad and the dedicated button. The right click works. If I switch to the tablet mode and return to laptop mode, the button starts working again.

---

### Post by parzan on 2011-10-07
> **maxxum said:**
> It does not rotate :(
```
@x220t:~$ cd ./Desktop/magick-rotation/
@x220t:~/Desktop/magick-rotation$ ./xrotate.py left
Traceback (most recent call last):
  File "./xrotate.py", line 846, in <module>
    r.rotate(direction)
  File "./xrotate.py", line 770, in rotate
    display.direction = display.rotate(direction)
AttributeError: 'NoneType' object has no attribute 'rotate'
```-----------------------------------------------------------------
```
x220t:~/Desktop/magick-rotation$ lsmod | grep thinkpad
thinkpad_acpi          81587  0 
nvram                  14419  1 thinkpad_acpi
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device

```

This looks like the bug I had - see my post #53 in this thread.

---

### Post by parzan on 2011-10-07
**Calibration and orientation**

I played lately with xinput_calibrator  - it's great, with the following exceptions:
1. You have to tell it your current calibration
2. It does not set the new calibration, only prints it
3. It gives wrong coordinates in inverted mode
4. It practically doesn't work at all in left/right modes
currently I have a script which deals with the first three issues (the most problematic was inverted mode - my solution is a weird workaround):
```
#!/usr/bin/env python
import re
from subprocess import *

PEN = 'ISD-V4 Pen stylus'
ERASER = 'ISD-V4 Pen eraser'
TOUCH = 'ISD-V4 Finger touch'
TRACKPOINT = 'TPPS/2 IBM TrackPoint'
COORDMAT = "Coordinate Transformation Matrix" #"129"

# Get Trackpoint transformation matrix
MAT = Popen(["xinput","list-props",TRACKPOINT],stdout=PIPE).communicate()[0]
MAT = [x for x in MAT.splitlines() if COORDMAT in x][0]
MAT = [eval(x) for x in MAT[MAT.find(':')+1:].strip().replace(',',' ').split(' ') if x]
# Store pen matrix
OLDMAT = Popen(["xinput","list-props",PEN],stdout=PIPE).communicate()[0]
OLDMAT = [x for x in OLDMAT.splitlines() if COORDMAT in x][0]
OLDMAT = [eval(x) for x in OLDMAT[OLDMAT.find(':')+1:].strip().replace(',',' ').split(' ') if x]
# Set pen matrix
call(["xinput","set-prop",PEN,COORDMAT]+map(str,MAT))
try:
    # Get old coordinates
    T = Popen(["xsetwacom","get",PEN,"Area"],stdout=PIPE).communicate()[0]
    x1,y1,x2,y2 = map(int,T.strip().split(' '))
    print "OLD AREA:",x1,y1,x2,y2
    # Get points
    T = Popen(["xinput_calibrator","--device",PEN,"--precalib",`x1`,`x2`,`y1`,`y2`],stdout=PIPE).communicate()[0]
    x1,x2,y1,y2 = [int(re.search('Option\s*"%s"\s*"([-0-9]*)"'%x,T).group(1)) for x in ["MinX","MaxX","MinY","MaxY"]]
    print "NEW AREA:",x1,y1,x2,y2
    # Apply calibration
    call(["xsetwacom","set",PEN,"Area",`x1`,`y1`,`x2`,`y2`])
    call(["xsetwacom","set",ERASER,"Area",`x1`,`y1`,`x2`,`y2`])
except Exception,e:
    print "CALIBRATION FAILED!\n"+T+`e`
# Restore old pen matrix
call(["xinput","set-prop",PEN,COORDMAT]+map(str,OLDMAT))

```Currently the script calibrates both pen and eraser according to the input but it would be easy to make the behavior (set only one of them, or finger touch) flag-dependent.
I might get to try to store the calibration (currently it is lost when rebooting) and make separate calibrations for normal and inverted modes (with switching  triggered by magic-rotation afterrotate).
Comments are welcome!

---

### Post by karlkoch23 on 2011-10-17
Hi again,

I switched to Oneric, and although this thread is about Natty I feel it has somehow become the central resource for "touch ubuntu x220t" related problems.

Problem is as follows:

Rotating the x220t into potrait mode somehow inverses the input with pen and touch, meaning up is down and left ist right....
If I use the rotate script and go to any orientation landscape mode, everything is fine again.

Besides this bug Oneric works like a charm and makes unity quiet a bit more usable.

Greetz,
Bert

---

### Post by Favux on 2011-10-17
Hi karlkoch23,

That's been fixed upstream at the Linux Wacom Project and is in the xf86-input-wacom-0.11.1 tar.  Unfortunately Ubuntu chose the 0.11.0 release which still has the bug.  Feel free to join the Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/857647)  Or at least confirm it affects you.

So the solution is to upgrade your xf86-input-wacom to at least 0.11.1.  See part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by maxxum on 2011-10-21
I upgraded to 11:10 as well. Currently I have only firefox running and it has only 3 tabs open. Yet, the fan is blowing pretty loud and if I keep my hand on the left, near the vent, I can feel the wind blowing and it makes even louder wooosh as it hits my fingers. Can't be good.:(

---

### Post by altercation on 2011-10-21
@maxxum, try the tweaks in this article:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

I'm using the the first two tweaks listed on that page and results are good (lvds tweak causes resolution problems on the x220t).


and additionally try installing thinkfan

Once thinkfan is installed you will need to set a sensor line in it to:

sensor /sys/devices/virtual/thermal/thermal_zone0/temp

(just above the temp list arrays is fine)

and you'll want to edit /etc/default/thinkfan and change start to 'yes' once you confirm it's working.


11.10 is running cool and quiet with moderately heavy use. Ask if you don't get the above to work.

---

### Post by aldebarn42 on 2011-10-25
> **maxxum said:**
> I'm having a new issue now. The left mouse click often stops working, both on the touchpad and the dedicated button. The right click works. If I switch to the tablet mode and return to laptop mode, the button starts working again.

I'm having a very similar issue, but I didn't realise it's related to switching in and out of tablet mode. Have you got any further information about this? From using xev, it seems to me that the left click on the touchpad is inverted, so it's as if you are clicking-and-dragging constantly. I suppose this is what blocks further left click signals from the dedicated buttons and pen.

Can you confirm similar behaviour? 
Are you using that magickrotation program to deal with moving from tablet/normal mode? 

As an aside, a big thank you to everyone in this thread, it's an invaluable source of information for getting the x220t up and running!

---

### Post by spikn on 2011-11-03
Hi everbody,

A few quick questions:

1) Someone mentioned upgrading to 11.10 above... do people mostly have a positive experience?  I'm running 11.04 and everything works pretty well (in Classic!), so I'm reluctant to upgrade if it will just break everything.

2) Is anybody else experiencing random lock-ups?  Every few days the screen will freeze and I have to reboot.  I use wake/sleep a lot, but it's not obviously correlated to that.

3) Regarding 2) above: I still have to do a BIOS update (requires being in Windows... grrr).  Maybe that will help.

Best,

-s

---

### Post by aldebarn42 on 2011-11-07
> **spikn said:**
> Hi everbody,

A few quick questions:

1) Someone mentioned upgrading to 11.10 above... do people mostly have a positive experience?  I'm running 11.04 and everything works pretty well (in Classic!), so I'm reluctant to upgrade if it will just break everything.

2) Is anybody else experiencing random lock-ups?  Every few days the screen will freeze and I have to reboot.  I use wake/sleep a lot, but it's not obviously correlated to that.

3) Regarding 2) above: I still have to do a BIOS update (requires being in Windows... grrr).  Maybe that will help.

Best,

-s

I've been using Xubuntu 11.10 with no freeze-ups or anything else since it came out. Very pleased with performance etc. You could always try 11.10 on the usb stick with persistence to get a feel for it if you don't want to commit to a full install.

---

### Post by dsalac on 2011-11-10
So here's a question for everyone. I hooked up my X220T to a projector and cloned the display. For smaller screen resolutions the picture shows centered on the LCD.
The problem is that the touch screen acts as if display was stretched. So as you move from the center to the left or right edge of the screen the cursor is farther and farther from the pen. You can verify this by just changing you screen resolution to 800x600. Anyone know of a fix for this?

---

### Post by rgbrown on 2011-11-12
> **dsalac said:**
> So here's a question for everyone. I hooked up my X220T to a projector and cloned the display. For smaller screen resolutions the picture shows centered on the LCD.
The problem is that the touch screen acts as if display was stretched. So as you move from the center to the left or right edge of the screen the cursor is farther and farther from the pen. You can verify this by just changing you screen resolution to 800x600. Anyone know of a fix for this?

Yes - had the same problem with my HP2710p. Easy fix:

```
xrandr --output LVDS1 --set "scaling mode" "Full Aspect"
```

I'm not sure what the screen name is on the X220t (I'm getting mine in a week), but just substitute that for LVDS1 and you should be good to go. 

Hmmm, now that I mention it it might be "Full" rather than "Full Aspect" - if it doesn't work try that!

---

### Post by dsalac on 2011-11-12
> **rgbrown said:**
> Yes - had the same problem with my HP2710p. Easy fix:

```
xrandr --output LVDS1 --set "scaling mode" "Full Aspect"
```I'm not sure what the screen name is on the X220t (I'm getting mine in a week), but just substitute that for LVDS1 and you should be good to go. 

Hmmm, now that I mention it it might be "Full" rather than "Full Aspect" - if it doesn't work try that!

Thanks for that. I didn't know about that option for xrandr. It's LVDS1 and "Full" btw.

---

### Post by karlkoch23 on 2011-11-14
Hi everyone,

I keep on reading that the current powermanagement in the Linux Kernels is ineffective.
Details can be found here:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)
 and here:
[http://http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1]("http://http//www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1")

I very much would like fix this. But I am not very confident about applying the provided kernel patch ([https://lkml.org/lkml/diff/2011/11/10/467/1](https://lkml.org/lkml/diff/2011/11/10/467/1)). Is anyone here maybe experienced in adding kernel patches in ubuntu?
I have googled a little bit but did not really find a solutions for patching ubuntu kernels.
I also thought most x220t users should be interested in this.
Greetz,
Bert

---

### Post by karlkoch23 on 2011-11-16
I wasn't brave enough yet adn therefore chose the "chicken"-path. Making changes to your /etc/default/grub 

to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i915.i915_enable_rc6=1**"

activates the sandy bridge power features. It may result in graphic issues on
some machines (e.g glitches), but I did not have any troubles yet. To the
contrary I feek like my x220t is running cooler.

Source for all this: [http://thinkpad-wiki.org/TLP_Einstellungen](http://thinkpad-wiki.org/TLP_Einstellungen) (german)
There also some other tools for powermanagement (tlp and co.)
which for one thing allow modified charging behaviour to reduce stress on the
battery.

---

### Post by Ghost Rider on 2011-11-17
> **karlkoch23 said:**
> Hi everyone,

I keep on reading that the current powermanagement in the Linux Kernels is ineffective.
Details can be found here:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)
 and here:
[http://http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1]("http://http//www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1")

I very much would like fix this. But I am not very confident about applying the provided kernel patch ([https://lkml.org/lkml/diff/2011/11/10/467/1](https://lkml.org/lkml/diff/2011/11/10/467/1)). Is anyone here maybe experienced in adding kernel patches in ubuntu?
I have googled a little bit but did not really find a solutions for patching ubuntu kernels.
I also thought most x220t users should be interested in this.
Greetz,
Bert

Hi,
here: [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement) you can find a patched Kernel for Oneiric and Precise. For me, this patch reduced consumption by 3 W, that means 12 hours instead of 7 hours.

Ghost Rider

---

### Post by The Wish Within on 2011-11-18
Hi.

I've installed Kubuntu 11.10 on my X220T and I've install xf86-input-wacom drivers.

The pen is working, but there is one problem:

When I click with the pen, the click is recognized as "grab" and so I can't really click.

What can I do?

---

### Post by Zta on 2011-11-23
Hey,

I've [heard that stylus accuracy is bad]("http://forums.lenovo.com/t5/X-Series-Tablet-ThinkPad-Laptops/Questions-regarding-X220-tablet-before-I-buy-one/td-p/599771") on the X220t.  Can anyone confirm or whether this is true for Ubuntu 11.10 too?

I'd like to use my X220t for photo editing in Darktable, but are its [controls too small]("http://www.darktable.org/wp-content/uploads/2011/07/screenshot-2.png") for **practical use** with the stylus and its accuracy?  I assume finger-touchy-touchy is out of the question here?

Finally, an icon just because I can: :roll:

-- 
Zta

---

### Post by Favux on 2011-11-23
Hi Zta,

Right now at least Gimp in Oneiric is broken for any tablet:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  Don't know about Darktable but given the last report on Krita I'd be careful about upgrading to Oneiric.

Gestures work.  As a matter of fact...

**[SIZE="4"]FYI everyone[/SIZE]**:  Chris just submitted what looks to be the final round (for now) of his gesture improvements.  This includes the scroll and zoom improvements.  If things go well they should be committed soon and available if you clone the xf86-input-wacom git repository.

---

### Post by Zta on 2011-11-24
Okay, thanks for the heads up on Oneiric+Gimp+tablet.  This is clearly broken.

I haven't read all posts in this thread, so I don't know whether there are big differences in Natty or Oneiric, or whether I should use the word "tablet", "multi-touch", "stylus" or whatever when I ask...

The thing is that I'm in the process of deciding whether I want a X220 or X220T.  After browsing and pdf reading, I think the only serious use I'll make of the tablet, is sorting and editing photos.

In essence, I just want to know, if I'll be able to use Darktable using the stylus on the screen of a Thinkpad X220 tablet with Ubuntu, or if the stylus is too unpredictable.

Anyone got any experience or care to make a quick test, please?

---

### Post by Ghost Rider on 2011-11-25
Hi there,

I use my X220T for Photo-Editing in GIMP in Oneiric (it works for me!) and i try right now Darktable. The Pointer react, if you hould the Stylus just 1 cm above the panel (that's normal). After certain time, it's greath.

Best regards.
Ghost Rider

> **Zta said:**
> Okay, thanks for the heads up on Oneiric+Gimp+tablet.  This is clearly broken.

I haven't read all posts in this thread, so I don't know whether there are big differences in Natty or Oneiric, or whether I should use the word "tablet", "multi-touch", "stylus" or whatever when I ask...

The thing is that I'm in the process of deciding whether I want a X220 or X220T.  After browsing and pdf reading, I think the only serious use I'll make of the tablet, is sorting and editing photos.

In essence, I just want to know, if I'll be able to use Darktable using the stylus on the screen of a Thinkpad X220 tablet with Ubuntu, or if the stylus is too unpredictable.

Anyone got any experience or care to make a quick test, please?

---

### Post by Favux on 2011-11-29
Hi everyone,

The **[SIZE="3"]gesture improvements[/SIZE]** I mentioned have been **committed** to the repository **now**.  So you can get them by cloning the xf86-input-wacom git repository.  See part II. c) of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Chris is asking for some feed back on the default settings:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_aZ6%3Di1cFMMSK9v9jhb98LX%2Bh-0rkhdjdhqixMXfV3t7g%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_aZ6%3Di1cFMMSK9v9jhb98LX%2Bh-0rkhdjdhqixMXfV3t7g%40mail.gmail.com&forum_name=linuxwacom-devel)  If you have suggestions post them here or on the linuxwacom-devel thread.

---

### Post by unclepedro on 2011-12-12
Hey all, LTNS.

Favux, is this still accurate for limiting pen/touch input to one display?

[http://ubuntuforums.org/showpost.php?p=10297093&postcount=1](http://ubuntuforums.org/showpost.php?p=10297093&postcount=1)

I'd like to be able to use my pen on the x220T display in a 1-to-1 fashion while also using a second monitor (of different dimensions).

I thought I'd ask in case that info is not valid for Oneiric.

Thanks!

---

### Post by Favux on 2011-12-12
Good to hear from you again unclepedro.

Yes that should still be accurate.  I updated it for the new Nvidia TwinView support for MapToOutput.

---

### Post by unclepedro on 2011-12-12
Great -- thanks. I'll report back on my progress once I have time to do it.

---

### Post by SaintDanBert on 2012-02-01
> **unclepedro said:**
> 
...
I used the basic installer to repartition the disk, shrinking my Windows 7 partition down to 50GB. After repartitioning, the first time you boot Windows, you'll need to run a filesystem check (which Windows will do automatically).
Did you blow away and re-purpose the as-built "recovery" partition?
Does all of the Lenovo boot stuff continue to work after the Linux install?
> **unclepedro said:**
> ...
The screen rotation button on the panel does not work by default, although the screen rotation in the Display Settings widget works well enough. (I added the widget to the panel.) However, when the screen is rotated, the pen input seems to be rotated as well (and as I said the finger input is not right). I have hopes that these have already been resolved but haven't tried yet.
Karl Hegbloom has a PPA with a package **tablet-screen-rotation-support** that is worth the effort.

The bezel orientation button does not throw an ACPI event -- based on 'acpi-listen' output -- I've heard it needs to be enabled but have not learned how.
> **unclepedro said:**
> So basically, all the non-tablet features work fine; the pen works fine in landscape mode, and (out of the box) finger is "working" but goofy and in rotated mode both are unusable but should be fixable.
...

The Hegbloom package sorts much of this out.

---

### Post by SaintDanBert on 2012-02-01
> **unclepedro said:**
> 
...
Adding ISD-V4 to the MatchProduct directive did the trick. Both finger and pen work for basic input, like moving windows, clicking, etc. I can do at least some gestures, such as right clicking with "press-tap" -- although as this is my first touch device for Linux, I am sure I haven't tested the whole gamut, and I haven't tested things like the eraser. (Now that the hardware appears to be working, I will read the standard documentation and see what I need to do.)
...


What do you mean by "standard documentation"?

I've not found much.  Look!  There goes that loose nut in the operators chair again.

Where did you find "standard documentation" about all of this?

~~~ 8d;-/ Dan

---

### Post by unclepedro on 2012-02-03
Hi SaintDanBert -- welcome. No, when I did my original install I just squeezed down the Windows partition. I have since backed up my recovery partition and original partition tables and wiped both the recovery and Windows 7 partitions off the laptop. Windows in VirtualBox (with the HW virtualization enabled) works well enough that I don't need to be able to dual boot anymore.

What I meant by "standard documentation" was the documentation (anywhere) that explains how to use pen or touch input for any given app -- once drivers and input software for the hardware are working. 

Thanks for the heads up on the rotation support PPA. I haven't had much time to play with my system's configuration, but when I get a chance, I will.

---

### Post by SaintDanBert on 2012-02-04
I have been over at [_Advanced Buttons ... On G40_](http://ubuntuforums.org/showthread.php?t=1914360&highlight=x220t) posting away about my X220t efforts.  Also, I'm working on Ocelot as well as Narwhal. If someone will explain how, I'll gladly MOVE my posts over here.

Sorry that I forgot to tighten the loose nut in my operator's chair.

Cheers,
~~~ 0;-Dan

---

### Post by unclepedro on 2012-02-05
AFAIK, there's no way to "move" the posts. You can re-post them verbatim here, or, better yet, link to the specific posts or re-post your specific questions.

---

### Post by axtimwalde on 2012-02-17
Thanks for the elaborate thread---it serves as a nice documentation on  how to get smooht experience on the X220T.  Tiny addition:  I found the  trackpoint responding to mechanical shear motions of the screen in  tablet mode (it's the convex finger piece which touches the monitor  back-side then).  Very annoying to see the pointer moving when grabbing  the tablet differently.  The issue can be solved by disabling the  trackpoint in tablet mode.  In magick-rotation Advanced Setup, add into  "Run before switch to tablet:"

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 0

and into "Run before switch to normal:"

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 1

Good luck.

---

### Post by forlackofabettername on 2012-03-01
Is there a way to scroll/pan with the touch screen? It works very smoothly in Windows 7 and is one of the few things holding me back from Ubuntu.

---

### Post by Favux on 2012-03-01
Yes.  Scroll should be working now.  But you may want to update your xf86-input-wacom X driver to the latest release (0.13.0) as that has some gesture improvements that are worthwhile, including scroll and zoom.  And version 0.14.0 is about to be released in a week or two since Jason just put out 0.13.99.1.  That will get you my fantastic gesture description section added to *man wacom*.  Highly worth the read.  ;)

---

### Post by mscion on 2012-03-11
Hi. Great thread. Just ordered the X220T and am expecting its arrival in a few weeks. Looking forward to installing ubuntu. Was a wiki ever made for this? Perhaps this thread is it!  Anyways, hope to learn as much as possible about it before it arrives. Thanks to all that contributed.

---

### Post by rgbrown on 2012-03-11
Anyone here running Precise and managed to use the Calibration tool in the Wacom Graphics Tablet section of the System Settings? It looks tantalisingly useful, but doesn't do anything on my x220t

---

### Post by unclepedro on 2012-03-14
Favux: sounds great. I've been hoping to get decent gesture support on here for a while.

mscion: I haven't looked very hard for a wiki on this machine -- the Thinkpad Linux people used to be pretty good about getting up howtos, etc. I just noticed that Googling for "linux thinkpad x220t" gets you here, so I'm thinking that this thread is kind of the de facto source of information right now. Cool. Nice work, everyone!

rgbrown: I have no experience with that tool. What is it?

Here's a question for the thread -- anyone having issues with screen corruption following disconnection of an external monitor? I had this problem early on, then it went away, and now it seems to be back again. If I have a 2nd monitor on, and I turn it off in the dialog or unplug the VGA cable, the screen on the laptop becomes white vertical bars, although the mouse pointer is still visible and uncorrupted.

I'm using the kernel tweaks as suggested previously, but I did not *notice* that the reappearance of this issue was related to those changes.

---

### Post by Ghost Rider on 2012-03-16
> **unclepedro said:**
> ..
Here's a question for the thread -- anyone having issues with screen corruption following disconnection of an external monitor? I had this problem early on, then it went away, and now it seems to be back again. If I have a 2nd monitor on, and I turn it off in the dialog or unplug the VGA cable, the screen on the laptop becomes white vertical bars, although the mouse pointer is still visible and uncorrupted.

I'm using the kernel tweaks as suggested previously, but I did not *notice* that the reappearance of this issue was related to those changes.

Hi,
same problem here, but it was always there for me. An external monitor with display port does not work with 1920x1080, there is just a blank screen even if I unplug it. The only resolution for me, is to use the ugly vga. Before unplugging it, I have to shutdown, otherway the screen goes black, only the pointer is there, and nothing can solve it not Magic SysRQ either.

Best Gost Rider

---

### Post by mscion on 2012-03-16
Has anyone tried to install ubuntu on X220t via WUBI. Pros? Cons?

---

### Post by SaintDanBert on 2012-03-17
Can someone explain how I get this entire thread to appear as a single page?

I want to export to PDF so that I can work through it step by step.
I've tried PrintThread but only get parts of the postings. Are there 
other settings I need to tinker?

[color=green]
_**Follow-up -- **_I discovered that I had my DisplayMode set to "hybrid" as an ubuntuforums.org option.  (Who knows when I made that setting or why.) 

Changing this to "linear" I could then get a max of 75 postings per page in mostly chronological order. I'll have to harvest any attachments individually, but much better than before.
[/color]

Thanks,
~~~ 8d;-/ Dan

---

### Post by unclepedro on 2012-03-17
> **Ghost Rider said:**
> Hi,
same problem here, but it was always there for me. An external monitor with display port does not work with 1920x1080, there is just a blank screen even if I unplug it. The only resolution for me, is to use the ugly vga. Before unplugging it, I have to shutdown, otherway the screen goes black, only the pointer is there, and nothing can solve it not Magic SysRQ either.


My external monitor is 1680x1050, and I get the white and black bars with cursor, not a black screen. It is seeming like I may be able to "overcome" the problem by switching to a pty (ctrl-alt-f1) and back to X (c-a-f7). I'm not sure if that works all the time, or just coming out of hibernation. I'd be curious if that trick helps you.

---

### Post by unclepedro on 2012-03-17
> **Favux said:**
> Yes.  Scroll should be working now.  But you may want to update your xf86-input-wacom X driver to the latest release (0.13.0) as that has some gesture improvements that are worthwhile, including scroll and zoom.  And version 0.14.0 is about to be released in a week or two since Jason just put out 0.13.99.1.  That will get you my fantastic gesture description section added to *man wacom*.  Highly worth the read.  ;)

I just tried out 0.14.0 and the gestures are definitely much better than before! Thanks! Although for my machine, /usr/lib is 64-bit and /usr/lib32 is the older 32-bit code. It's sorta the reverse of what's in the documentation.

---

### Post by Ghost Rider on 2012-03-18
> **unclepedro said:**
> My external monitor is 1680x1050, and I get the white and black bars with cursor, not a black screen. It is seeming like I may be able to "overcome" the problem by switching to a pty (ctrl-alt-f1) and back to X (c-a-f7). I'm not sure if that works all the time, or just coming out of hibernation. I'd be curious if that trick helps you.

Hi,
thanks for your reply. I tried this before, but really nothing helps. I can't switch to console by pressing strg+alt+F1, nothing happens.

Best 
Ghost Rider

---

### Post by FelixWinter on 2012-03-19
Hi everyone.

This is my first post on ubuntuforums and I just wanted to thank everybody who contributed to this thread so far. I just installed the 12.04 Beta on a new X220t and thanks to the advice I found here managed to install all the tablet/touchpad-related stuff quite easy. 

Thank you very much for the time and effort you spend on helping people like me.

And if I might dare to add one question: Does anyone know how to disable or modify the behaviour of the SAS key (Security Attention Sequence), on the left side of the 'rotate screen' key?

Whenever I accidentally happen to push this button the screen turns black and the only way to shutdown safely is after login via virtual console.  I don't know how to track the error. The only thing I did find so far is the last line of the dmesg output:

```
gnome-settings-[1681] trap int3 ip:7f8ab74a413b sp:7fff620864ao error:0
```I tried to find out which signal this key does send with xbindkeys but did not get any output. When I use "read" at a virtual console the result is 
```
user@x220t:~$ read
^@
```If there is anything I can do about this, I would be glad to hear about.

Felix

---

### Post by unclepedro on 2012-03-27
> **unclepedro said:**
> 
Favux, is this still accurate for limiting pen/touch input to one display?

[http://ubuntuforums.org/showpost.php?p=10297093&postcount=1](http://ubuntuforums.org/showpost.php?p=10297093&postcount=1)

I'd like to be able to use my pen on the x220T display in a 1-to-1 fashion while also using a second monitor (of different dimensions).
Thanks!

Favux replied that yes, this information was still accurate, and I'm here to confirm that it works in Oneiric. It's incredibly easy since the x220t uses the wacom drivers, which means you can use "Method I" in the above HOWTO.

The way I have my tablet set up is that I use magick-rotation to handle normal tablet usage, where I use my tablet as a notebook in portrait rotation. I typically use Jarnal for notetaking, and this has allowed me to basically stop using pen and paper for meetings and sketching ideas.

But at my desk, I used to have my x220t set up in "laptop mode" as a second screen to the right of my LCD. This meant that while I could read my Jarnal notes I couldn't really interact with it as a tablet. I would have to disconnect it if I wanted to sketch ideas, or use paper (which would not be integrated into my files).

I set up my desk so that I could have my tablet below my LCD (instead of next to it) folded backwards (in "inverted landscape" mode) and propped up at an angle. I set up the screens using the typical Ubuntu "Displays" dialog. But by default, the pen and touch spanned the entire desktop, which doesn't work well for writing and sketching. 

Well, the following xsetwacom lines did the trick:

```

$ xsetwacom set "Wacom ISDv4 E6 Pen stylus" MapToOutput LVDS1
$ xsetwacom set "Wacom ISDv4 E6 Finger touch" MapToOutput LVDS1
$ xsetwacom set "Wacom ISDv4 E6 Pen eraser" MapToOutput LVDS1

```

Now, my tablet is a little "sketchpad" underneath my main screen. The pen/touch input is limited to the laptop display, while the mouse works across both displays. Awesome!

Going forward, I will work on scripting this stuff to work automatically.

Thanks, Favux!

---

### Post by mscion on 2012-03-30
Hi. Got my x220t in the mail and it is quite nice. I'm trying to decide whether to duel boot mint/ubuntu or use Vmware (or Parallels) to run linux. I currently have a netbook that I duel boot windows xp and Mint linux with no serious problems. Just wondering if anyone could share  experience using vmware or parallels on x220t. For example, would there be any advantage to preserving use of touch screen capabilities when going one route or another? How well does the VKB work for these set ups?

Thanks!

---

### Post by rgbrown on 2012-04-01
> **unclepedro said:**
> 
rgbrown: I have no experience with that tool. What is it?

Sorry, didn't catch this reply - I'd forgotten to subscribe to the thread! It's part of the Gnome settings - you'll have it, just search for Wacom in Unity. As far as I can tell, the tablet is not recognised by the tool for calibration. The pen sensitivity settings work, though.

After being frustrated for quite a while, I've finally figured out a reasonable method for calibrating my X220t manually. I was initially trying to use the values output from xinput_calibrator, but this wasn't working very well for me because of the distortion around some of the edges of the screen. And it gave simply wrong numbers for portrait mode. So what I do now is to esentially just adjust the four numbers of the "Area" parameter of the devices using xsetwacom one at a time. These numbers each loosely correspond to one of the edges of the screen - so if adjusting, e.g. x1, you use test points near the left edge of the screen. I adjusted initially in steps of 100, then 50 to find the right values. Once you iterate around all the edges a couple of times you end up with a pretty good screen calibration. I do this for each orientation I use and then put the relevant commands into a couple of scripts. 

I'm planning to put the relevant bits and pieces into an simple indicator applet when I find the time.

Keep up the useful info everyone!

---

### Post by unclepedro on 2012-04-02
> **mscion said:**
> Hi. Got my x220t in the mail and it is quite nice. I'm trying to decide whether to duel boot mint/ubuntu or use Vmware (or Parallels) to run linux. I currently have a netbook that I duel boot windows xp and Mint linux with no serious problems. Just wondering if anyone could share  experience using vmware or parallels on x220t. For example, would there be any advantage to preserving use of touch screen capabilities when going one route or another? How well does the VKB work for these set ups?


I use VirtualBox in Ubuntu on my i7 x220t to run XP for a few apps and it works well. I would expect either VMWare or Parallels to work as well or better for you. However, it does depend on what kind of processor your x220t has, as I don't think all the CPUs (e.g., i3) have hardware virtualization support. (Also note that hardware virtualization may be turned off in your BIOS if it exists in the hardware.)

Since the pen/touch input is a USB device, I'd think that it would work reasonably well in full-screen virtualization, but that is just a guess. It could be a little sluggish, I suppose. I haven't tried using the pen in XP.

Whether you should dual boot or use a VM really depends on what you want to get out of your machine, and how often you think you'll want to use both operating systems side by side.

---

### Post by mscion on 2012-04-03
> **unclepedro said:**
> I use VirtualBox in Ubuntu on my i7 x220t to run XP for a few apps and it works well. I would expect either VMWare or Parallels to work as well or better for you. However, it does depend on what kind of processor your x220t has, as I don't think all the CPUs (e.g., i3) have hardware virtualization support. (Also note that hardware virtualization may be turned off in your BIOS if it exists in the hardware.)

Since the pen/touch input is a USB device, I'd think that it would work reasonably well in full-screen virtualization, but that is just a guess. It could be a little sluggish, I suppose. I haven't tried using the pen in XP.

Whether you should dual boot or use a VM really depends on what you want to get out of your machine, and how often you think you'll want to use both operating systems side by side.

Thanks for the info. My x220t uses i7. Will give the VMWare a try first. Hopefully it is not too laggy.. Boot-up with windows takes less than 30 seconds with SSD. So firing up linux via VMWare may not be too bad. Just wish I had more memory with SSD.  That is why I'm a little reluctant to do the duel boot as that will split up the 160 GB.

Anyone have luck running android OS on top of windows?

---

### Post by mscion on 2012-04-06
Well, I tried a few versions of MINT 12 (gnome,kde,lxde) using VMware. When starting out I didn't have any success with the 64bit version gnome. So stuck to 32bit for all. The gnome version seemed a little bit easier to play with and to find and start up apps. The touch screen worked well so that I could pull up applications and start for example libre office by just touching screen. While the HWKB seemed to work fine. I could not get Lenovo's VKB to enter text. Perhaps someone can give me some pointers on this. The KDE version has a vkb application. It was having a problem with repeating letters but I think I can fix that in settings. On gnome version I downloaded wxmaxima and it worked to a point. It solved a simple problem but if I tried to make a plot it could not make the window to show the plot. Will play with it some more... Suggestions of things to try are welcome!

EDIT:Was able to get wxmaxima to make 3d plot. I think I might have made a mistake when I set up plot parameters. One cool thing about having the touch screen is that you can actually make the image rotate by just touching the screen and moving your finger over the image. I still have had no success with Lenovo's VKB but I tried xvkbd and was able to enter text in terminal.  One thing I was surprised was how long it took to save a simple document made with libre office. Maybe this is the price you pay for sitting on top of windows...

EDIT YET AGAIN: I tried installing 64bit versions (gnome and kde) again and it worked this time.

---

### Post by SwingTime on 2012-04-08
Apologies if this issue had been solved before. Just installed 11.10 on my x220 tablet. Touchpad works great, but mousepad does not work at all. How can I get it working?

---

### Post by rgbrown on 2012-04-10
> **SwingTime said:**
> Apologies if this issue had been solved before. Just installed 11.10 on my x220 tablet. Touchpad works great, but mousepad does not work at all. How can I get it working?

Have you tried Fn+F8?

---

### Post by Wayneoween on 2012-04-12
Hi

thanks for all the information gathered in this thread.

I just happen to have a weird problem with the stylus:

If I get close to the screen with the correct (thin, Pen) side the mouse starts instantly a left-click-and-drag as if I wanted to mark multiple files on the Desktop.
With this behaviour it is not possible to use cellwriter or the whole tablet with the stylus at all.

When the Eraser-Side is used the behaviour is just what I would expect for the Pen side!
Nothing happens except the mouse moving until I touch the screen.

This behaviour is identical on Windows 7, too. Touch works somewhat ok.

I never used a tablet before but I don't think this is correct.
Is this probably a technical issue e.g. hardware related?

If you need further information just say what you need.

---

### Post by mscion on 2012-04-12
> **Wayneoween said:**
> Hi

thanks for all the information gathered in this thread.

I just happen to have a weird problem with the stylus:

If I get close to the screen with the correct (thin, Pen) side the mouse starts instantly a left-click-and-drag as if I wanted to mark multiple files on the Desktop.
With this behaviour it is not possible to use cellwriter or the whole tablet with the stylus at all.

When the Eraser-Side is used the behaviour is just what I would expect for the Pen side!
Nothing happens except the mouse moving until I touch the screen.

This behaviour is identical on Windows 7, too. Touch works somewhat ok.

I never used a tablet before but I don't think this is correct.
Is this probably a technical issue e.g. hardware related?

If you need further information just say what you need.

Hi. I have no clue how to help on this but if this behavior is a consequence of trying to enable and improve various touch screen features described in this thread it might be a good argument for one of the more experienced users to make a step by step instruction to do so. Right now, I'm just using VMware which is not very adventuresome but more or less ok. I would consider dualbooting or wiping windows off completely if there was such instruction set.

My only major problem (at this time!) is that I can't get xvkbd to work to my liking. It actually works fine if I use the stylus but if I press one of xvkbd's keys with my finger instead of the stylus the character does not appear unless  I press a key again. In fact it doesn't have to even be the same key. For example, if I press the letter d once nothing happens. But if I now press t, d appears on the screen. Now press another letter, say, y, then t appears and so forth. Also, xvkbd does work with the touch pad but that kind of defeats the purpose as I want to use linux in tablet mode. So my question is can I change a setting somewhere in regards to the touch screen, so that when I touch a character on xvkbd it selects and "clicks" it as if I'm using the stylus or touchpad? 

For those that are dual booting or have a linux only device what are you using for a virtual keyboard?

Anyways, thanks to all that have contributed to this thread!

---

### Post by Wayneoween on 2012-04-13
As I found out my stylus is the problem.
Lenovo support says that probably dust or something became stuck in the sensor thingy that sends the left-click signal. :lolflag:
I will get an replacement through warranty so this should be allright.

Anyhow I messed about with the xsetwacom command and now lost the ability to left-click with touch.
And as it happens to be, I don't remember where I changed lines, it doens't need to be xsetwacom :

The relevant part I think is this:
```
## two finger (2FG) or multitouch
## touch = "Wacom ISDv4 E6 Finger touch" = ID 11
xsetwacom set 11 Touch "on" # default,  or "off"
xsetwacom set 11 Gesture "on"  # or "off"
xsetwacom set 11 Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set 11 RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set 11 Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 11 Mode "Absolute"  # or Relative cursor movement; is Relative needed for gestures? 
xsetwacom set 11 TapTime "250"  # default is 250 ms
xsetwacom set 11 Button "1"  #  needed for 2FG touch?
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 15 ZoomDistance "50"  # default is 50
xsetwacom set 15 ScrollDistance "20"  # default is 20
xsetwacom set 15 TapTime "250"  # 2FG R click, default is 250 ms
```

If someone could tell me the places where I should take a look I'd be very thankfull!


[COLOR=Red]**Edit**[/COLOR]:
Okay if I do not change the Mode (Relative/Absolute) at all after a reboot, left click works but its in relative mode. Is there a fix for that?

---

### Post by mscion on 2012-04-18
> **Wayneoween said:**
> As I found out my stylus is the problem.
Lenovo support says that probably dust or something became stuck in the sensor thingy that sends the left-click signal. :lolflag:
I will get an replacement through warranty so this should be allright.

Anyhow I messed about with the xsetwacom command and now lost the ability to left-click with touch.
And as it happens to be, I don't remember where I changed lines, it doens't need to be xsetwacom :

The relevant part I think is this:
```
## two finger (2FG) or multitouch
## touch = "Wacom ISDv4 E6 Finger touch" = ID 11
xsetwacom set 11 Touch "on" # default,  or "off"
xsetwacom set 11 Gesture "on"  # or "off"
xsetwacom set 11 Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set 11 RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set 11 Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 11 Mode "Absolute"  # or Relative cursor movement; is Relative needed for gestures? 
xsetwacom set 11 TapTime "250"  # default is 250 ms
xsetwacom set 11 Button "1"  #  needed for 2FG touch?
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 15 ZoomDistance "50"  # default is 50
xsetwacom set 15 ScrollDistance "20"  # default is 20
xsetwacom set 15 TapTime "250"  # 2FG R click, default is 250 ms
```If someone could tell me the places where I should take a look I'd be very thankfull!


[COLOR=Red]**Edit**[/COLOR]:
Okay if I do not change the Mode (Relative/Absolute) at all after a reboot, left click works but its in relative mode. Is there a fix for that?

Hi. You probably know this but The Linux Wacom Project site has many commands in re stylus to play with that might solve your issue.

[http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom)

---

### Post by mscion on 2012-04-21
Just a quick note that the VMware allows you to connect wacom to the guest while disconnecting the host. When I connected wacom to the guest (mint linux) the virtual keyboard worked fine just using touch. But now the stylus didn't work! Probably the answer lies in the earlier posts here....

---

### Post by karlkoch23 on 2012-05-24
Dear all,

I had to reinstall Ubuntu 12.04 and then went on to getting the tablet function to work.
Downloaded newest xwacom, changed the config file as required compiled and rebootet. I saw my login screen for a second, then everything went dark. When I reboot I see the splashscreen, but now I do not even reach my login screen. strg+alt+F1 does not work, external monitor shows no signal.
Now it gets worse, I am not able to access the grub screen and recovery modus by pressing the shift key, ssh access is disabled.....
Help is urgently needed, I need this computer for a job interview next week...
I have a good backup system in place, so if I have to reinstall it should not be a problem... just wastes time I currently do not have...

[EDIT] I am able to go to root recovery console now... nothing else is possible (e.g. failsafe graphics mode). Having my home directory encrypted surely does not make thinks easier...
[EDIT] Case resolved I was able to access my encrypted home directory , make the filesystem writeable ```
mount -o remount,rw /
``` and run a ```
make uninstall
``` in the xf86wacom Directory.

After that I was brave and retried installing with a ```
sudo make install
```and ended up with a broken system again.

I tried using xf86-input-wacom-0.15. Any suggestions on how to get this working.

Thanx

---

### Post by Ghost Rider on 2012-06-08
> **karlkoch23 said:**
> Dear all,

I had to reinstall Ubuntu 12.04 and then went on to getting the tablet function to work.
Downloaded newest xwacom, changed the config file as required compiled and rebootet. 

Hi there,
I have Ubuntu 12.04, and all works out of the box, so why do you have downloaded the newest xwacom? Try the packages in the repo and all is fine.

Best Regards
Ghost Rider

---

### Post by mscion on 2012-06-08
> **Ghost Rider said:**
> Hi there,
I have Ubuntu 12.04, and all works out of the box, so why do you have downloaded the newest xwacom? Try the packages in the repo and all is fine.

Best Regards
Ghost Rider

Hi Ghost Rider. I just tested Ubuntu 12.04 using a live CD version and I was quite impressed. It does seem to work quite well out of the box. The only issue I had, when using Ubuntu 12.04 with x220t as a tablet, is that there was a slight jerking motion of the screen when touching it. Maybe shifting about 1 mm or so. Not sure if anyone has had this problem but is there a way to correct this behavior?

Thanks!

EDIT: I tried starting up the live CD version again and this time there is no problem. Now I'm really impressed!
EDIT AGAIN: I just installed Ubuntu 12.04  using wubi as I wanted to have some of the MS applications available. So far it its working very well. Touch screen has no problems.

---

### Post by Ghost Rider on 2012-06-10
Yeah, 12.04 works great, but I'm not able to rotate with a key, like parzan. In 11.04 it works for me, but since 11.10 it doesn't...

> **parzan said:**
> Here are my findings playing with karlkoch23's observations:

It turns out that 162 is the keycode for XF86RotateWindows, and ```
sudo setkeycodes 6c 154
``` (recall that 154=162 due to the 8 bug) makes the rotation button rotate the screen _even when magick-rotation is not running_. The rotation is weird - the modes appear in a strange order. When magick-rotation is running, the "before rotation" and "after rotation" commands are triggered, but the rotation order is still the weird one so it seems that the rotation itself is not done by magick-rotation, even in this case.

Since this is rather annoying, my solution is running ```
sudo setkeycodes 6c 149
``` instead, which maps the rotation button to XF86Launch2 (XF86Launch1 is already bound to the ThinkVantage button), and binding XF86Launch2 to xrotate.py in gnome-keybinding-properties. It makes sense to do also ```
sudo setkeycodes 67 202
``` which binds the other tablet button to XF86Launch3. 

To see the various keycodes available, run ```
xmodmap -pke | grep XF86
``` but remember to subtract 8 when running setkeycodes!

---

### Post by mscion on 2012-06-12
> **Ghost Rider said:**
> Yeah, 12.04 works great, but I'm not able to rotate with a key, like parzan. In 11.04 it works for me, but since 11.10 it doesn't...
Ah, yes, right. I hadn't checked the rotation. Thanks for the info. Will give it a try.

---

### Post by mscion on 2012-06-13
> **Ghost Rider said:**
> Yeah, 12.04 works great, but I'm not able to rotate with a key, like parzan. In 11.04 it works for me, but since 11.10 it doesn't...
Yes, having the rotation key work would be nice. From settings you can rotate the screen but then you also need to do some xsetwalcom commands  to  rotate control of stylus, touch and eraser. For now, I'd be happy to just have a script to do all this from a terminal. Would someone know how to rotate the screen as is done in settings but from the terminal? I can then combine those commands with the xsetwalcom commands in a script.

Thanks!

---

### Post by Favux on 2012-06-13
Hi mscion,

See the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") for rotation scripts and key binding.

---

### Post by mscion on 2012-06-13
> **Favux said:**
> Hi mscion,

See the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") for rotation scripts and key binding.

Awesome! Thanks Favux!

---

### Post by mscion on 2012-06-14
> **mscion said:**
> Awesome! Thanks Favux!

Worked like a charm. The first set of scripts are nice because you can just rotate to portrait and then back using the same script. I just had to replace touch, eraser, and stylus with id numbers 14, 15, and 16.

Thanks again!

---

### Post by Favux on 2012-06-14
Good.  :)

Fair warning though, the ID number can change if you hotplug a usb device.  Not so likely on a tablet PC, but if the device is plugged in when you boot or restart maybe.  So using the <device name> from **xinput list** in quotes is safer.

Also with recent xf86-input-wacoms you no longer need to list every input tool.  Since a X220t is usb you need stylus and touch in the script.  The stylus line will automatically rotate the eraser with it now.

---

### Post by mscion on 2012-06-15
> **Favux said:**
> Good.  :)

Fair warning though, the ID number can change if you hotplug a usb device.  Not so likely on a tablet PC, but if the device is plugged in when you boot or restart maybe.  So using the <device name> from **xinput list** in quotes is safer.

Also with recent xf86-input-wacoms you no longer need to list every input tool.  Since a X220t is usb you need stylus and touch in the script.  The stylus line will automatically rotate the eraser with it now.

Spot on! The ID numbers changed the next time I booted up Followed you instructions using device name from xinput as you describe and all is well.
Now, would it be too greedy to ask if there a way to get rotation via accelerometer!!!

---

### Post by Ghost Rider on 2012-06-15
> **mscion said:**
> Spot on! The ID numbers changed the next time I booted up Followed you instructions using device name from xinput as you describe and all is well.
Now, would it be too greedy to ask if there a way to get rotation via accelerometer!!!

I use magick-rotation, and it works great, but I want to rotate with one of the keys right under the screen, so I can hold my X220T up-right-down...

---

### Post by Favux on 2012-06-15
Hi Ghost Rider,

You can bind the bezel key you want to a script for Magick's xrotate.py.  It takes command line arguments.  For e.g. to rotate right portrait:
```
/usr/share/magick-rotation/xrotate.py right
```
and then back to laptop:
```
/usr/share/magick-rotation/xrotate.py normal
```
Described in the Magick_README.txt.  Or just use a script like one of the one's in the Rotation HOW TO.

---

### Post by Ghost Rider on 2012-06-15
Hi Favux,
thanks, but magick-rotation works very well for use in portrait mode, but I want to flip the display  and use it like a tablet in landscape mode. In Ubuntu 11.04 I deactivated magick-rotation and binds one of the tablet keys to  XF86RotateWindows...

---

### Post by Favux on 2012-06-15
Why not just select inverted in Setup?

---

### Post by Ghost Rider on 2012-06-15
> **Favux said:**
> Why not just select inverted in Setup?
because I want both ;) I want to use magick-rotation to read in portrait mode, and the key, to surf in the internet in landscape inverted mode.

---

### Post by Favux on 2012-06-15
Ah, I see.  You don't want to right click on the Magick tray icon and select inverted and hit Save.  And then the reverse for portrait again.  You just want to hit a button for landscape.  Makes sense.  That way both options are set and forget.

---

### Post by Ghost Rider on 2012-06-17
> **Favux said:**
> Ah, I see.  You don't want to right click on the Magick tray icon and select inverted and hit Save.  And then the reverse for portrait again.  You just want to hit a button for landscape.  Makes sense.  That way both options are set and forget.
Hi,
yeah, exactly. But since 11.10 my X-Server crashes when I bind the XF86RotateWindows to a key an press it.

---

### Post by mscion on 2012-06-18
Hi.

Is it possible to map the rotate button on the X220t bezel to do the CW rotation and back? I've checked around a little but with no luck. Also it would be cool to make a double click option for the 180 degree if possible.

---

### Post by Favux on 2012-06-19
Sure, you place the bezel rotate button to a unused XF86 key sym and then bind that whatever rotation script you want.  That's mostly what the button stuff on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") is showing you.  See "Implementing a Script with a Launcher or Key Binding".  And for the 360 put the 360 script in a launcher.  I have my bezel button bound to a 360 degree script and use Magick Rotation for the portrait and back.

---

### Post by mscion on 2012-06-19
> **Favux said:**
> Sure, you place the bezel rotate button to a unused XF86 key sym and then bind that whatever rotation script you want.  That's mostly what the button stuff on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") is showing you.  See "Implementing a Script with a Launcher or Key Binding".  And for the 360 put the 360 script in a launcher.  I have my bezel button bound to a 360 degree script and use Magick Rotation for the portrait and back.

Thanks! Will check it out.

---

### Post by jpc2769 on 2012-06-21
Hi all, thanks for such a great thread. 

Does this work for Kubuntu as well? I installed Kubuntu 12.04, it works fine out of the box but I can't get magick-rotate to work. When I try to install it, I get a prompt for my password but then nothing happens. 

Is magick-rotate only for Ubuntu? If so is there a similar fix for Kubuntu?

Thanks in advance for your help.

Jason

---

### Post by Favux on 2012-06-21
Hi jpc2769,

Which version of Magick Rotation did you use?  1.5?

Last I checked Kubuntu it was installing.  If I know the version I can test it.

That should install in Kubuntu.  But you don't need the Installer to run to get it working.  The Installer just saves you time.  The minimum for it to work is adding the udev rule to /etc/udev/rules.d and compiling checkmagick.  Instructions are in the INSTALLER.txt.

The 1.6 Installer (out soon) should run on Unity, Gnome2, and KDE and Fedora, Mint, openSUSE, and Ubuntu.

---

### Post by jpc2769 on 2012-06-21
Favux,

Thanks for the quick response. I am using (or rather trying to use) magick-rotation 1.5. Just for grins I tried downloading it onto another, non-tablet computer I have running Ubuntu 12.04, extracting and double-clicking on the magick-rotation script, and it prompted me to accept it installing a list of packages (what I would expect).

I followed the instrucitons in the INSTALLER.txt file (to the best that I could understand them) and it still doesn't work.

Jason

---

### Post by Favux on 2012-06-21
Well it installed on Kubuntu 11.10.

Let me see what the issue/problem is.  Might take a while.

---

### Post by Favux on 2012-06-21
Found the problem right away.  The Python module gtk isn't installed so the **import gtk** lines fail as to the lines with **gtk** in them.  However can't find any explanation of why it isn't available or what alternative is suppose to be used.  Weird since **import pygtk** works.

Alright with the udev rules installed and checkmagick compiled, in a terminal go into the magick-rotation folder and run the following command:
```
python magick-rotation
```
If there is an error you should see an error message output.  What is it?

---

### Post by Favux on 2012-06-21
Hi jpc2769,

Think I've solved the problem.  From this Launchpad bug I confirmed the gtk package isn't installed in Kubuntu Precise: [https://bugs.launchpad.net/ubuntu/+source/screen-resolution-extra/+bug/673733](https://bugs.launchpad.net/ubuntu/+source/screen-resolution-extra/+bug/673733)

So run the following in a terminal:
```
sudo apt-get install python-gtk2
```
Then install from a fresh Magick Rotation 1.5.

Although if you compiled checkmagick correctly and put the udev rules in place your current magick-rotation should also start working since magick-rotation itself requires the python-gtk2 package for its gui_gtk.py module.

---

### Post by jpc2769 on 2012-06-21
Thanks Favux, I'll give it a shot and let you know how it goes.

Jason

---

### Post by jpc2769 on 2012-06-22
Success! Thanks so much for your help Favux, I really appreciate it.

I have another question about magick-rotate. In the &#8220;advanced settings&#8221; option, I noticed that there are areas where you can enter commands to be executed before and after the switch to tablet mode; currently it is set up to open cell-writer. 

Is there a command that I can put in there to make it switch between desktops when I rotate the screen? What I'd like to do is have two desktops, one more &#8220;pc-like&#8221; for normal mode, and one more &#8220;tablet-like&#8221; for tablet mode with more plasma widgets instead of the normal menus. 

Jason

---

### Post by Favux on 2012-06-22
Good.

No, to change Desktops you have to log out.  What there was were some tweaks to Gnome 2.  For example increase the panel width when going to tablet mode.  That would make the panel icons larger and more touch friendly.  Haven't tried to find the equivalent in Gnome 3 or Unity.  One of the FAQ's may have those commands.

---

### Post by jpc2769 on 2012-06-22
Favux,

I think I misspoke. I was referring to the "virtual desktops" you can set up, where you can have more than one screen space with different windows open, and switch between them by moving the mouse to the edge of the screen. There is the option in KDE to have different plasma widgets on the different virtual desktops, so my idea was to have magick-rotate switch between two virtual desktops when it rotates.

Jason

---

### Post by Favux on 2012-06-22
Hi Jason,

Looks like you want wmctrl since you have kwin:  [http://tomas.styblo.name/wmctrl/](http://tomas.styblo.name/wmctrl/)

Install it either through Software Center or apt-get.

Then use it as in these examples:
[http://stackoverflow.com/questions/4643528/unix-shell-command-that-make-the-virtual-desktop-spin](http://stackoverflow.com/questions/4643528/unix-shell-command-that-make-the-virtual-desktop-spin)
[http://www.artificialworlds.net/blog/2011/03/04/switching-workspace-in-gnome-via-the-command-line/](http://www.artificialworlds.net/blog/2011/03/04/switching-workspace-in-gnome-via-the-command-line/)

---

### Post by jpc2769 on 2012-06-22
Favux,

Thanks, this is exactly what I wanted! 

Jason

---

### Post by mscion on 2012-06-27
> **Favux said:**
> Sure, you place the bezel rotate button to a unused XF86 key sym and then bind that whatever rotation script you want.  That's mostly what the button stuff on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") is showing you.  See "Implementing a Script with a Launcher or Key Binding".  And for the 360 put the 360 script in a launcher.  I have my bezel button bound to a 360 degree script and use Magick Rotation for the portrait and back.

Hi. I was wondering if instead of running rotation script with usual Launcher or Key Binding, that one could control the rotation from the top panel where the username, battery usage, bluetooth symbols (icons? not sure what they are called) are located. This might be nice aesthetically with use of good choice of symbol.

Thanks!

---

### Post by Favux on 2012-06-27
Sort of like Magick Rotation?

In Gnome2 you used to be able to drag a launcher up into the top panel, but not in the system tray.  It would then launch its script with a single click instead of a double click.

I don't know if someone has written a tweak or extension (depending on your Desktop) to duplicate that yet.

---

### Post by mscion on 2012-06-27
> **Favux said:**
> Sort of like Magick Rotation?

In Gnome2 you used to be able to drag a launcher up into the top panel, but not in the system tray.  It would then launch its script with a single click instead of a double click.

I don't know if someone has written a tweak or extension (depending on your Desktop) to duplicate that yet.

Oops! I had not checked out Magick Rotation as I was quite happy with the scripts given in method 1 of the How to Rotate Screen thread. Just thought it would be nice to have a little symbol in the top panel to control each rotation option (cw,ccw...). The idea of it being part of the system tray makes sense in that just as one adjusts sound volume one might want to set screen orientation. Having a general rotation applet in top panel is fine too. Is this what Magic Rotation does?

---

### Post by Favux on 2012-06-27
Exactly.  You set what orientation you want in tablet mode and you can toggle touch on and off and also run shell commands.

While sprucing up the gui, something I should have done before releasing 1.6 (oh well), I discovered a bug that I think has been there a while.  I'm looking into it.  You probably won't run into it because it basically involves a legacy use case that doesn't matter much now that Magick is installed.

But I might bring out a 1.6.1 bug fix version for it which would also include a bit "nicer" gui.

---

### Post by mscion on 2012-06-28
> **Favux said:**
> Exactly.  You set what orientation you want in tablet mode and you can toggle touch on and off and also run shell commands.

While sprucing up the gui, something I should have done before releasing 1.6 (oh well), I discovered a bug that I think has been there a while.  I'm looking into it.  You probably won't run into it because it basically involves a legacy use case that doesn't matter much now that Magick is installed.

But I might bring out a 1.6.1 bug fix version for it which would also include a bit "nicer" gui.

Sounds good. Will check it out. Looking forward to 1.6.1!

---

### Post by mscion on 2012-07-02
> **Favux said:**
> Exactly.  You set what orientation you want in tablet mode and you can toggle touch on and off and also run shell commands.

While sprucing up the gui, something I should have done before releasing 1.6 (oh well), I discovered a bug that I think has been there a while.  I'm looking into it.  You probably won't run into it because it basically involves a legacy use case that doesn't matter much now that Magick is installed.

But I might bring out a 1.6.1 bug fix version for it which would also include a bit "nicer" gui.

I just installed version 1.6 (I had downloaded it a couple of days ago). Seems to work fine. But too late... I see there is version 1.6.1! Guess I have to uninstall and try again!

---

### Post by Favux on 2012-07-02
Hi mscion,

Let me know if 1.6.1 works for you.  :)

---

### Post by mscion on 2012-07-02
> **Favux said:**
> Hi mscion,

Let me know if 1.6.1 works for you.  :)

So far no problems with 1.6.1. I use it for portrait (right option in magick menu) in tablet. In case I want tablet in landscape I can disable magick rotation before I go into tablet mode  or  use the cw script which puts it back to normal (I currently have it as a desk icon I double click).  May try keybinding of cw next.

Thanks for your help!

---

### Post by Favux on 2012-07-02
Good deal.  Happy to hear it is working.

You probably don't even notice the gui tweaks.  But they jump out at me.  It feels like I finally have it right.

---

### Post by mscion on 2012-07-03
> **Favux said:**
> Good deal.  Happy to hear it is working.

You probably don't even notice the gui tweaks.  But they jump out at me.  It feels like I finally have it right.

Well, I only used version 1.6 one day. Perhaps my memory is bad but I didn't notice any new features. It did seem organized a little different. 

On another note. I was wondering if the name of this thread could be modified to account for later versions of ubuntu on ThinkPad X220T.

---

### Post by mscion on 2012-07-21
Hi. 

Been rather quiet here of late. I had been having difficulty finding a way to put a GUI on desktop for rotation script where I control its appearance.
 I stumbled upon an approach that  is rather simple so I thought I would share. 

Here is the link.

[http://superuser.com/questions/347443/unity-how-to-add-a-shell-script-to-the-dock](http://superuser.com/questions/347443/unity-how-to-add-a-shell-script-to-the-dock)


The only problem I had with this approach is that the instructions say to put the myGUIapp.desktop script (see link) in ~/.local/share/applications/ 
However nothing happened. Perhaps I need to set a permission to make it work here?

What I did notice is it works fine if you instead put it in the Desktop directory. Of course make sure you set the permissions! 
I found a curled arrow png image that looks similar to the magick rotation image on google images which makes a nice icon.

Perhaps for ubuntu 12.04 there is a different location that is equivalent to ~/.local/share/applications/
Anyways, for linux aficionados that find putting the desktop script in Desktop offensive, please do chime in!

EDIT: Just wanted to add that the post I provided the link for was describing how to set up desktop GUI using svg image. I used png. Not sure if that makes any difference.

---

### Post by Favux on 2012-07-21
Hi mscion,

Not sure I follow.  Are you saying you wanted to put a launcher for your script on your Precise Unity Desktop?  Where you could specify the icon for it?

---

### Post by mscion on 2012-07-21
> **Favux said:**
> Hi mscion,

Not sure I follow.  Are you saying you wanted to put a launcher for your script on your Precise Unity Desktop?  Where you could specify the icon for it?

Hi Favux. I'm sure what I'm saying is just revealing what a noob I am! Previously, when I set up the rotate script to run from the Precise Unity Desktop the default icon that appeared looked like that associated with a text file which is not suitable for this function. I wanted it to look something like the curled arrow that Magick rotation uses.  So I made a file like that described in the link

[Desktop Entry]
 Name=My GUI App
  Exec=/path/to/shellscript.sh
 Icon=/path/to/you/icon.svg
 Terminal=false
  Type=Application
 StartupNotify=true

where I put the path to the rotate script in Exec and a png file for Icon. But for some reason it didn't work if I put this file in the directory ~/.local/share/applications/ as  specified in the link. But it does work if I put it in the directory Desktop. First it appeared like the text icon on the ubuntu desktop but then, once I made it executable the png file became the icon (maybe that was just timing). And it works fine. However, my ultimate preference is to use one of the buttons on the bezel. Just haven't tried it yet.

---

### Post by Favux on 2012-07-21
That's interesting.

I still haven't quite figured out how to put a launcher/app/icon I've created into Unity's taskbar.  Getting closer I think.

Anyway there are several ways to create a .desktop file.  You can use alacarte.  Probably spelled that wrong.  But what I've done is the following.
> CREATE LAUNCHER
Install the 'gnome-panel' package through software center (also called the "launcher and docking facility for GNOME"):
    sudo apt-get install gnome-panel

Open a new text file and name it 'Create Launcher'.  Into the text file add the following 2 lines:
#!/bin/bash

gnome-desktop-item-edit --create-new $(pwd) &

Make the text file executable by right clicking on it and in Properties choose the Permissions tab and check the Execute box.  Move the 'Create Launcher' script into the ~/.gnome2/nautilus-scripts directory (which is hidden).  Then right-click on the Desktop and from the pop-up menu choose Scripts > Create Launcher.  A dialog very similar to the one in Gnome 2 (where the icon name, command, icon, etc. can be specified) pops up.  Fill in the details as usual for a Launcher.

Desktop icons have to be enabled, if they aren't gnome-tweak-tool can fix that.  They should be by default in Precise.  If you can right-click the Desktop and make a folder or file then Desktop icons are enabled.
Then for the icon you click on the generic icon in the launcher and choose the path to the one you want to use.  That gave me back the ability to create launchers like we used to be able to do in Gnome2.

There might be more elegant solutions out there but I don't know them.

---

### Post by mscion on 2012-07-22
> **Favux said:**
> That's interesting.

I still haven't quite figured out how to put a launcher/app/icon I've created into Unity's taskbar.  Getting closer I think.

Anyway there are several ways to create a .desktop file.  You can use alacarte.  Probably spelled that wrong.  But what I've done is the following.

Then for the icon you click on the generic icon in the launcher and choose the path to the one you want to use.  That gave me back the ability to create launchers like we used to be able to do in Gnome2.

There might be more elegant solutions out there but I don't know them.

It would be great if one could run rotate scripts form taskbar.

Any familiarity with tint2. I just came across it.

tint2 makes panel/taskbar that is customizable and has  autohide feature.

[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

---

### Post by bobsan on 2012-07-22
Did you make the .desktop file executable? (Right click, choose Properties, then go to Permission and check the box allowed executed as a program)

After you put the .desktop file to ~/.local/share/applications you have to  drag and drop the the icon from there to the Unity bar, that should work.

---

### Post by Favux on 2012-07-22
I've read about Tint before but that's all.

Rather than Tint what I've used on my Desktop is Cairo/Glx Dock.  I set it up on the right opposite of the Unity launcher and tweaked it to look like the Unity launcher.  Then I removed duplicate stuff and added things, which could have included a launcher (just drag and drop), to supplement the launcher.  For example the Cairo Dock Ubuntu symbol isn't Dash it is the Main Menu.  And so on.  Basically I have everything I had in Gnome2 back.

That might be a good solution for you at least in laptop mode, given how wide your screen is.  Rotated in Portrait orientation you would probably either need to kill or rotate the Dock to the bottom or maybe hide it with Magick Rotation's Advanced Setup.


@ bobsan,

Yeah, but dragging and dropping the app on the Unity launcher is cheating.  How do you do it from the command line, that's my question.  I can add an icon to hicolor and rerun the cache and then see the icon in Cairo Dock for example.  But still the icon is not there in the Unity laucher.

---

### Post by mscion on 2012-07-22
> **bobsan said:**
> Did you make the .desktop file executable? (Right click, choose Properties, then go to Permission and check the box allowed executed as a program)

After you put the .desktop file to ~/.local/share/applications you have to  drag and drop the the icon from there to the Unity bar, that should work.

Thanks! I had made it executable after moving it to Desktop. After reading your post I just moved it back to ~/.local/share/applications/ and put it in the Unity bar as you suggested. Now my Desktop is nice and clean! Although my Unity bar is getting a bit crowded... Hopefully the rotation script can eventually be run from the task bar.
Appreciate everyone's help!

---

### Post by mscion on 2012-09-03
Hi, I guess I'm a bit slow but I recently noticed that you can scroll, when using a browser, by swiping up or down on the screen with two fingers. (In contrast you can scroll using one finger when running windows 7 ).  Also, it seems that you can  zoom by using three fingers but it does not seem too effective.  Any pointers or reference on multitouch gestures  when running ubuntu on X220t.

Thanks!

---

### Post by Favux on 2012-09-03
My timeless prose on gestures is in 'man wacom', so just enter that in a terminal.  Also see part VI. on the [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=dda4abbcf436707d72b2231a069ee372").

---

### Post by jpc2769 on 2012-09-04
All,

Not sure if this is the case anymore, but I remember in previous versions of Ubuntu, when you clicked the mouse wheel and moved the mouse up or down, it would scroll the active window up or down. 

Is there a way to map this function to the "eraser" end of the stylus? I would like to be able to use the point for clicking and the "eraser" for scrolling.

Jason

---

### Post by mscion on 2012-09-06
> **Favux said:**
> My timeless prose on gestures is in 'man wacom', so just enter that in a terminal.  Also see part VI. on the [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=dda4abbcf436707d72b2231a069ee372").

Thanks Favux! Your prose is epic! The reason zooming with three fingers was ineffective was because I should have only used two!

---

### Post by fmelo79 on 2012-10-23
Hi there,

first, thanks for all the work! This thread was really important in my decision to buy a x220t, which I'll get by tomorrow.

I wonder if a tutorial has been written about all the discussions here, has it? Any experience with ubuntu 12.10?

Cheers.

---

### Post by rgbrown on 2012-10-26
> **fmelo79 said:**
> Hi there,
Any experience with ubuntu 12.10?
Cheers.

I'm running 12.10 at the moment. The main thing I notice is increased power consumption - no matter how I fiddle with powertop, I can't get the computer to idle at less than about 13W. Under precise it could get down as low as about 7W. Under normal usage, the power consumption is generally higher than 12.04, and the fan is more active. If I can't sort this out, I'm going to have to revert.

Anyone else noticed this?

---

### Post by fmelo79 on 2012-11-02
Hi rgbrown,

I installed 12.10 in my x220t and I also have basically no problems with it. I only had to install magick-rotation and everything works. I'd like to be able to calibrate the stylus a little better, and I'm looking at how to do it. Any hints?

About the power consumption, I cannot compare it with previous versions since 12.10 was the only one I've installed in my computer. I do, however, confirm that the fan is on very often. 
I found this link [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1) with some tweaks to increase battery life, but I didn't try them myself.

Cheers.

---

### Post by fmelo79 on 2012-11-03
Hi,

I noticed something else: If I'm using a program in tablet mode and I switch to normal mode, then the pen goes crazy. It doesn't happen if I open the program in the mode I will actually use it. Would you know how to solve that?

Cheers.

---

### Post by unclepedro on 2012-11-20
Hi all, LTNS. Glad to see the thread is still going strong.

I am still running on Oneiric, and I'm still having a video issue where when I disconnect from an external monitor the video goes to black and white bars with the mouse pointer still visible. I can usually work around this by switching to a console and back, or by suspending the latop and waking it, but that does not always work. Occasionally when this happens the whole system freezes and I have to do a hard reboot.

Does anyone else have this problem? I've been considering upgrading to 12.04 or .10, but mostly in the hopes that this issue will go away. 

If nobody else has this issue (I tried looking for a bug report but didn't find one) I'm going to assume that it's related to some configuration choice I've made.

Any advice would be greatly appreciated.

---

### Post by Favux on 2012-11-20
Hi unclepedro,

Maybe a glitch in xrandr?

What happens if instead of just disconnecting you use a xrandr command?  Something like:
```
xrandr --output VGA-1 --off --output LVDS-1 --auto --mode 1280x800
```
You'd want to run the **xrandr** command with and without the monitor attached to find the name of the connected monitor and your tablet's monitor if you don't already know them.  And the same for the preferred tablet resolution (mode).

---

### Post by unclepedro on 2012-11-20
Good idea. I'll try that and report back. Thanks.

---

### Post by Ghost Rider on 2012-11-25
> **unclepedro said:**
> 
If nobody else has this issue (I tried looking for a bug report but didn't find one) I'm going to assume that it's related to some configuration choice I've made.

Any advice would be greatly appreciated.

Hi unclepedro,
i had the same behavior with Oneiric as well. With 12.04 and 12.10 I think it is gone, but since Kernel 3.2.27 there are stripes when using an external monitor connected to the display port. Since I have installed 12.10, I use the vga connection, but this is not a real solution for me...

---

### Post by unclepedro on 2012-11-27
Yeah -- I'm having the same experience. I don't have a DP connector right now, so it's no problem. Thanks!

---

### Post by mscion on 2013-02-03
Hi. Haven't been around in awhile but I happen to notice something kinda neat so thought I'd share. One thing I was never happy with, using ubuntu on my thinkpad, was its responsiveness at scrolling. But today,  when moving the cursor via the touch pad, I happen to be touching the right edge where the touch pad meets the palm rest area.  By moving along on that vertical edge I could scroll up and down rapidly. This  only works on the right edge. Anyways this made my day! If this is something that everyone knows please excuse my being a noob and feel free to chime in if you know some other tricks to the trade!

---

