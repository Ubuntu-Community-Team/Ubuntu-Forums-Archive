---
title: "Wacom Bamboo Pen can't drag through air after tap"
date: 2011-04-15
forum: Hardware
---

### Post by Thryn on 2011-04-15
So it's been a while since I used my tablet, a Wacom Bamboo Pen, with Ubuntu (I used it on the 1st with Windows 7, no problems whatsoever, so I don't think the issue is the tablet).

I knew I had to re-add (or whatever the correct term is) the wacom module, due to having a new kernel. So I went to do that, and saw that there was a new method, as follows:

```
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms
```

So I did this, and also installed some other updates at the same time (including some GIMP updates), and used Ubuntu Tweak to remove all but the newest and second-newest kernels. Then I restarted.

And my tablet works, except that when I tap something and lift the stylus, I can't move the cursor for a little while unless I use a different method (my laptop's touchpad, say). I can move it if I drag the tip of the stylus across the surface of the tablet, but not if I lift it and try to move the cursor by dragging through the air, no matter how close the stylus tip is to the tablet. This happens regardless of the program I'm using. Eventually it goes back to normal though, but it seems to take a couple seconds, which is irritating.

I've never had this issue before. Any ideas? What exactly does that script do? Is it at fault?

FYI I'm running 64-bit Lucid with 2.6.32-30-generic on an ASUS UL30a. 4 GB RAM, 1.3 GHz dual-core Intel processor (forget the name).

If there's any more info you need about my computer, please ask. :)
Thanks so much in advance.

---

### Post by Favux on 2011-04-15
Hi Thryn,

> What exactly does that script do? Is it at fault?
You installed DoctorMO's PPA (personal package archive).  It updates the default wacom.ko (usb kernel driver) from the default linuxwacom-0.8.4-1 wacom.ko in Lucid to a more recent 0.8.8-10 wacom.ko.  The current one is 0.8.8-11 and we've kinda of switched over to using the input-wacom wacom.ko, see:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

It also installed a dkms (dynamic kernel module support) version of the wacom.ko.  See:  [http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)  What that means is you would no longer have to compile a new wacom.ko for each kernel update, it will automatically do it for you.  The drawback with it is you need to uninstall the the dkms wacom.ko if you want to install a new wacom.ko because otherwise the dkms version will override it.

Don't know if the PPA is the problem.  It's not clear if it also update the X driver xf86-input-wacom for you too.  That may be the problem.  On the other hand it is possible your Bamboo Pen is not on the wacom driver.  To find out enter in a terminal:
```
xinput list
```
In the output find the "device name" for the stylus and enter it in the following command with the quotes:
```
xinput list-props "device name"
```
You could also use the ID # for the device.  The output should tell you what driver it is on.

---

### Post by Thryn on 2011-04-15
I checked what you said, and I'm not sure what I'm supposed to look for. But here's the output:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 UVC 0.3M Webcam                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=13	[slave  keyboard (3)]

```
I'm not sure why there's a listing for finger - my tablet does not have a touch feature, just the stylus.
So here's the output for xinput list-props "Wacom Bamboo 4x5 Pen"
```
Device 'Wacom Bamboo 4x5 Pen':
	Device Enabled (123):	1
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (244):	1.000000
	Device Accel Velocity Scaling (245):	10.000000
	Evdev Reopen Attempts (239):	10
	Evdev Axis Inversion (246):	0, 0
	Evdev Axis Calibration (247):	<no items>
	Evdev Axes Swap (248):	0
	Axis Labels (249):	"Abs X" (410), "Abs Y" (411), "Abs Pressure" (412), "None" (0)
	Button Labels (250):	"Button Unknown" (240), "Button Unknown" (240), "Button Unknown" (240), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
	Evdev Middle Button Emulation (251):	2
	Evdev Middle Button Timeout (252):	50
	Evdev Wheel Emulation (253):	0
	Evdev Wheel Emulation Axes (254):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (255):	10
	Evdev Wheel Emulation Timeout (256):	200
	Evdev Wheel Emulation Button (257):	4
	Evdev Drag Lock Buttons (258):	0

```
And for xinput list-props "Wacom Bamboo 4x5 Finger"
```
Device 'Wacom Bamboo 4x5 Finger':
	Device Enabled (123):	1
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (244):	1.000000
	Device Accel Velocity Scaling (245):	10.000000
	Synaptics Edges (413):	19, 461, 17, 303
	Synaptics Finger (414):	99, 119, 1023
	Synaptics Tap Time (415):	180
	Synaptics Tap Move (416):	25
	Synaptics Tap Durations (417):	180, 180, 100
	Synaptics Tap FastTap (418):	0
	Synaptics Middle Button Timeout (419):	75
	Synaptics Two-Finger Pressure (420):	1126
	Synaptics Two-Finger Width (421):	7
	Synaptics Scrolling Distance (422):	11, 11
	Synaptics Edge Scrolling (423):	1, 0, 0
	Synaptics Two-Finger Scrolling (424):	0, 0
	Synaptics Move Speed (425):	0.400000, 0.700000, 0.086806, 40.000000
	Synaptics Edge Motion Pressure (426):	119, 639
	Synaptics Edge Motion Speed (427):	1, 46
	Synaptics Edge Motion Always (428):	0
	Synaptics Button Scrolling (429):	1, 1
	Synaptics Button Scrolling Repeat (430):	1, 1
	Synaptics Button Scrolling Time (431):	100
	Synaptics Off (432):	0
	Synaptics Guestmouse Off (433):	0
	Synaptics Locked Drags (434):	0
	Synaptics Locked Drags Timeout (435):	5000
	Synaptics Tap Action (436):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (437):	1, 3, 2
	Synaptics Circular Scrolling (438):	0
	Synaptics Circular Scrolling Distance (439):	0.100000
	Synaptics Circular Scrolling Trigger (440):	0
	Synaptics Circular Pad (441):	0
	Synaptics Palm Detection (442):	0
	Synaptics Palm Dimensions (443):	10, 799
	Synaptics Coasting Speed (444):	0.000000
	Synaptics Pressure Motion (445):	119, 639
	Synaptics Pressure Motion Factor (446):	1.000000, 1.000000
	Synaptics Grab Event Device (447):	1
	Synaptics Gestures (448):	1
	Synaptics Capabilities (449):	0, 0, 0, 1, 1
	Synaptics Pad Resolution (450):	1, 1
	Synaptics Area (451):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (452):	0

```

When I have more time (possibly tomorrow) I'll try replacing wacom.ko manually and see if the results are better. Unless of course anyone has a better idea by then.

Also, just noticed that I can't seem to get the GIMP set up to use the pressure sensitivity. Hmmm.

---

### Post by Favux on 2011-04-15
You did it right.  You found the Pen, which should have stylus after it and the Finger line.  And your correct you don't have touch.

And we see the reason why there is no stylus in the *xinput list* output.  The tablet is on the evdev X driver in the list-props output.  The spurious touch is on the Synaptic driver.

This leads me to think there is something wrong with either the wacom.ko and/or the 10-wacom.conf.  Let's check the wacom.conf first since that is most likely the problem.  See if there is one at /usr/lib/X11/xorg.conf.d.  If there is post the contents so we can check if something is wrong with it.

---

### Post by lgiordani on 2011-04-17
Hi all,

I'm experiencing the same after the last upgrade yesterday, on a 32-bit architecture.
I tried to run the previous kernel and even reinstalled the doctormo module with the new and old kernel, but the result is always the same, no movement for a while after tapping.

Anyone has a solution? I'm going to contact Martin Owens (doctormo) on the topic.

Regards

Leo

---

### Post by Favux on 2011-04-17
Did you check your wacom.conf?

Have you confirmed your tablet is on the wacom X driver?

---

### Post by lgiordani on 2011-04-18
Well, no.

When I first installed the tablet 2 weeks ago, I just added the repository and installed the package wacom-dkms (as described by Thryn in the first post). It worked perfectly without any adjustment, so I didn't dig more in the configuration.

Since the problem comes after a simple upgrade (kernel and 70 other packages) probably something changed. What? The Wacom driver? Kernel? XOrg?

As soon as possible I'll check the configuration as you suggest and post my configuration.

Thank you

Leo

---

### Post by Turbie on 2011-05-05
Hi all!

I have the same problem as Thryn with my Bamboo Pen. It worked perfectly before the last updates. I followed the steps that Favux said and my output is similar than the one of Thryn, (although I'm 32 bit). 

I haven't any wacom.conf in /usr/lib/X11/xorg.conf.d. In fact, a  find / -name "wacom.conf" has no results. Any idea?

$ xinput list-props 9
Device 'Wacom Bamboo 4x5 Pen':
    Device Enabled (117):    1
    Device Accel Profile (239):    0
    Device Accel Constant Deceleration (240):    1.000000
    Device Accel Adaptive Deceleration (242):    1.000000
    Device Accel Velocity Scaling (243):    10.000000
    Evdev Reopen Attempts (234):    10
    Evdev Axis Inversion (244):    0, 0
    Evdev Axis Calibration (245):    <no items>
    Evdev Axes Swap (246):    0
    Axis Labels (247):    "Abs X" (236), "Abs Y" (237), "Abs Pressure" (238), "None" (0)
    Button Labels (248):    "Button Unknown" (235), "Button Unknown" (235), "Button Unknown" (235), "Button Wheel Up" (121), "Button Wheel Down" (122), "Button Horiz Wheel Left" (123), "Button Horiz Wheel Right" (124)
    Evdev Middle Button Emulation (249):    2
    Evdev Middle Button Timeout (250):    50
    Evdev Wheel Emulation (251):    0
    Evdev Wheel Emulation Axes (252):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (253):    10
    Evdev Wheel Emulation Timeout (254):    200
    Evdev Wheel Emulation Button (255):    4
    Evdev Drag Lock Buttons (256):    0

---

### Post by gbegin on 2011-05-05
Hello,

I have experienced the same problem a about a month ago. The problem is not a kernel update but an update to wacom-dkms and/or xserver-xorg-input-wacom. I manually installed older versions of these packages: 0.8.8-0ubuntu3 and 1:0.10.6-0ubuntu6 respectively, and everything works as before. I'm using the tablet right now. I sent a bug report. 

Bamboo pen, Ubuntu 10.04

Hope this helps.

---

### Post by Turbie on 2011-05-06
Thanks, gbegin! You were right, I removed that both packages, reinstalled old versions and works fine again. 

If anyone also needs it, here I found everything, together with the steps for installing (in Spanish):
[http://www.muylinux.com/2010/07/06/como-instalar-una-tableta-wacom-bamboo-pen-en-ubuntu/](http://www.muylinux.com/2010/07/06/como-instalar-una-tableta-wacom-bamboo-pen-en-ubuntu/)

Regards

---

### Post by daniel3ub on 2011-05-09
Hi!

tried everything in this topic and no joy. The same problem: the pen works fine until it touches the tablet, then it freezes the cursor.

Actually I coudn't find the versions you are talking about here, guys.

Could someone please post the URL's to them, please?

Any other idea? Couldn't find any solution.

My tablet is a Wacom Bamboo MTE-450 and I am using Ubuntu 10.04.

Thanks

---

### Post by Favux on 2011-05-09
Hi daniel3ub,

The default Lucid Wacom drivers should work for a Bamboo MTE.  You should not need a newer wacom.ko.

Is the 10-wacom.comf present at /usr/lib/X11/xorg.conf.d?  If it is what is in it?

Right now my guess is you are not on the wacom X driver, but probably the evdev driver.  To find out enter in a terminal *xinput list* and then see if you see the same tablet input devices in *xsetwacom list*.

---

### Post by daniel3ub on 2011-05-30
> **Favux said:**
> Hi daniel3ub,

The default Lucid Wacom drivers should work for a Bamboo MTE.  You should not need a newer wacom.ko.

Is the 10-wacom.comf present at /usr/lib/X11/xorg.conf.d?  If it is what is in it?

Right now my guess is you are not on the wacom X driver, but probably the evdev driver.  To find out enter in a terminal *xinput list* and then see if you see the same tablet input devices in *xsetwacom list*.

Hi.

thanks for your help. My tablet WAS working, but today it decided to stop working, after xserver-something update.

There is no 10-wacom.conf file in that dir.
xinput gives me
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Mouse                               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo                            	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
```

xsetwacom list gives me nothing

and a ls /usr/lib/X11/xorg.conf.d
gives me
```
05-evdev.conf  10-synaptics.conf  10-vmmouse.conf
```

So I assume you are right, I have the evdev drivers. Why is it here and why it has changed?

How to get things back to normal, please?

Thanks!

---

### Post by Favux on 2011-05-30
Hi daniel3ub,

Great!  Not that it happened but that we caught it in the act.  Could you please post on this Lauchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+bug/770082](https://bugs.edge.launchpad.net/ubuntu/+bug/770082)

As you can see I'm the sole poster so we need more people affected by this to post before they'll pay attention and fix this packaging error.  Just say what you just told me, namely an update to xserver-xorg-core (and one or two other xserver packages) today deleted your 10-wacom.conf.  And because that broke your Wacom Bamboo MTE-450 you had to manually put it back in.

To put it back in see part III. a) at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Just copy & paste the contents of the example wacom.conf into the empty file the gedit command for Lucid will bring up for you, Save, and reboot.

---

### Post by daniel3ub on 2011-05-31
Thanks, Favux.

It's working now, but the buttons on the tablet cannot be recognized anymore. At least I can get back to work!

```
daniel@:~$ xsetwacom set "Wacom Bamboo pad" Button1 "core key ctrl alt Left"
Paramater 'Button1' is no longer in use. It was replaced with 'Button'.
daniel@:~$ xsetwacom set "Wacom Bamboo pad" Button3 "core key ctrl alt Right"
Paramater 'Button3' is no longer in use. It was replaced with 'Button'.
```

I know I need to enter the correct parameters from man wacom into the wacom.conf, but I have no idea what they are.

Thanks!

---

### Post by Favux on 2011-05-31
Hi daniel3ub,

Thank you for posting on the bug report.

Is the pad's "device name" "Wacom Bamboo pad" in the output of *xinput list* in a terminal?

Core is deprecated so "core key ctrl alt Left" becomes "key ctrl alt Left".

Also I'm guessing you are no longer using the Lucid default xf86-input-wacom-0.10.5 (xserver-xorg-wacom-input package).  Did you upgrade to 0.10.11 or better?  If so the syntax for buttons has changed and *Button1* becomes *Button 1*, etc.  In other words there is a space before the number.

---

### Post by Turbie on 2011-06-10
Thanks both of you for the explanations. I also had the same problem again, although I've been avoiding the updating of xserver-xorg-input-wacom and wakom-dkms packages. But after a general update it began to fail again. I reported the bug, too. 

I reinstalled previous versions of these packages, as before. That was not a solution now, but it created the  /usr/lib/X11/xorg.conf.d/wacom.conf
I tried then to install the newest versions directly in Synaptic, and now it works again. 

See you in some months, I supose. ;)

---

