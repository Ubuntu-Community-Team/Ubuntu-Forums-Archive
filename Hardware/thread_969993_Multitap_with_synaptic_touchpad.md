---
title: "Multitap with synaptic touchpad"
date: 2008-11-03
forum: Hardware
---

### Post by cmatheson on 2008-11-03
Hello,

I've read in the synaptics(4) manpage that the synaptic touchpads support multi-tap/scrolling for most models (as far as I can tell, recent synaptics touchpads are supported, but Alps are not).  I have a synaptics touchpad in a new HP 550 laptop.  I'm pasting the relevant parts of my Xorg.0.log below, but I'll post my questions here:

1 - I don't see any acknowledgement of the multitap options in the log--why is that?
2 - Am I safe to assume that my hardware supports multitap?  How can I know for sure?
3 - Is there anything else I need to do to make this work?

Xorg.0.log output:

(II) Synaptics touchpad driver version 0.15.2
(II) Touchpad: x-axis range 1472 - 5472
(II) Touchpad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event7"
(**) Option "SHMConfig" "true"
(--) Touchpad touchpad found
(**) Option "SendCoreEvents"
(**) Option "CorePointer"
(**) Touchpad: always reports core events
(II) evaluating device (Touchpad)
(II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
(II) Touchpad: x-axis range 1472 - 5472
(II) Touchpad: y-axis range 1408 - 4448
(--) Touchpad touchpad found
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.0.99
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event7"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(WW) SynPS/2 Synaptics TouchPad can't grab event device, errno=16
(--) SynPS/2 Synaptics TouchPad touchpad found


TIA,
Cam

---

### Post by wgrant on 2008-11-03
What do you mean by multi-tap?

---

### Post by cmatheson on 2008-11-03
> **wgrant said:**
> What do you mean by multi-tap?

Sorry, I mean tapping with two or three fingers to simulate right/middle mouse clicks, and also using two-fingers to scroll (like on a mac).

---

### Post by wgrant on 2008-11-03
Two- and three-finger tapping are on by default. You can use [the HAL example in the X config documentation](https://wiki.ubuntu.com/X/Config#hal) to enable two-finger scrolling.

---

### Post by cmatheson on 2008-11-03
Thanks for the response.  I wasn't aware that these things were configured in HAL now.  Anyway, I've created the following file (/etc/hal/fdi/policy/synaptics.fdi):

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">true</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
    </match>
  </device>
</deviceinfo>


This isn't working either (also, the SHMConfig option definitely isn't taking hold, because synclient no longer works).  Is there a way to check that hal is passing the right parameters along to X?

Thanks

---

### Post by wgrant on 2008-11-03
You will have to at least restart X, and possibly your whole system.

---

### Post by cmatheson on 2008-11-04
Ok, I logged out of X, and restarted HAL.  I do see the VertTwoFingerScroll option in my Xorg.0.log now, and synclient is working.  Unfortunately, the two finger scroll still doesn't work.  I've tried running synclient -m and using two fingers on the pad, but it the 'f' column doesn't ever register 2.  Any other ideas?

Thanks again,
Cam

---

### Post by wgrant on 2008-11-04
It looks like your touchpad doesn't report multiple fingers - are you sure it's physically capable of it?

---

### Post by cmatheson on 2008-11-04
I'm not sure--how can I know if my touchpad is capable or not?  It's a synaptic brand touchpad manufactured this year.  Everything I've read in the docs leads me to believe this should work--but I haven't been able to find out how to know whether or not this touchpad supports two-finger input for sure.

Thanks.

---

### Post by wgrant on 2008-11-04
It looks very unlikely that it does, but perhaps check in Windows just to be sure?

---

### Post by cmatheson on 2008-11-05
I don't have a windows partition, but I've gotten over the fact that it doesn't support the two-finger mode.  I looked for a spot on the wiki that might be documenting which synaptic models support this feature, but I didn't see one.  Is there an appropriate place to document this?

---

### Post by kybKenny on 2008-12-10
Just my two cents:
I'd love a resource of some kind to check which Pads support multiple touching.

I'm about to return my (brand new and otherwise nice) Sony SR because of that.
Maybe it works on Machine level:
Sony VGN-SR19XN apparently doesn't support multiple fingers (this goes out to the googlers). 

Regards,
kybKenny

---

### Post by kybKenny on 2009-01-27
Me again.

Sony successfully returned to vendor to be replaced with the Samsung x460 i'm writing this.

No two-finger tap either.

Touchpad model is:

```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003
```

It has these xinput properties:```

Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled:		1
	Synaptics Edges:		1632, 5312, 1575, 4281
	Synaptics Finger:		25, 30, 256
	Synaptics Tap Time:		180
	Synaptics Tap Move:		220
	Synaptics Tap Durations:		180, 180, 100
	Synaptics Tap FastTap:		0
	Synaptics Middle Button Timeout:		75
	Synaptics Two-Finger Pressure:		257
	Synaptics Scrolling Distance:		100, 121
	Synaptics Edge Scrolling:		1, 1, 0
	Synaptics Two-Finger Scrolling:		0, 0
	Synaptics Edge Motion Pressure:		30, 160
	Synaptics Edge Motion Speed:		1, 400
	Synaptics Edge Motion Always:		0
	Synaptics Button Scrolling:		1, 1
	Synaptics Button Scrolling Repeat:		1, 1
	Synaptics Button Scrolling Time:		100
	Synaptics Off:		0
	Synaptics Guestmouse Off:		0
	Synaptics Locked Drags:		0
	Synaptics Locked Drags Timeout:		5000
	Synaptics Tap Action:		2, 3, 0, 0, 1, 2, 3
	Synaptics Click Action:		1, 1, 1
	Synaptics Circular Scrolling:		0
	Synaptics Circular Scrolling Trigger:		0
	Synaptics Circular Pad:		0
	Synaptics Palm Detection:		1
	Synaptics Palm Dimensions:		10, 200
	Synaptics Pressure Motion:		30, 160
	Synaptics Grab Event Device:		1
```

Does anybody know a place where these are documented?

I do have a windows partition and there i can use a pinch gesture to zoom in and out of things (IPhone style). So the touchpad **is** somehow able to distinguish multiple inputs.

Maybe via the changed capacity/width of the one "finger" it sees.

$ synclient -m 100
```
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
```
1 Finger: 
```
 821.327  4042 2838  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0
```
2 Fingers:
```
 824.635  4095 1936  73 1  8  0 0 0 0 0  00000000   0  0  0   0   0
```
3 Fingers:
```
 827.141  1985 4579  72 1 15  0 0 0 0 0  00000000   0  0  0   0   0
```

Well, i'll keep looking. It's just too stupid trying to find these little clicking areas for middle click...

---

### Post by CaptainPedro on 2009-03-29
> **kybKenny said:**
> Me again.

Sony successfully returned to vendor to be replaced with the Samsung x460 i'm writing this.

No two-finger tap either.

Touchpad model is:

```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003
```


My touchpad seems to have the same info as yours in /proc/bus/input/devices

Im on a new Toshiba Satellite e105-s1402 (running Arch Linux, but that shouldnt matter too much) and I'm getting the same sort of problems with the F***ING touchpad ](*,)

edit:
kybKenny, as far as the width with multiple fingers, I seem to be getting 4 - 8 with 1 finger, and 11 - 15 with two or more.

---

### Post by CaptainPedro on 2009-03-29
Actually, I think I might have found something...

[http://mydellmini.com/forum/multitouch-touchpad-t770s0.html#p8999](http://mydellmini.com/forum/multitouch-touchpad-t770s0.html#p8999)

Ive got the 7.0 firmware on mine.
You should be able to find out what version yours is by doing
```
dmesg | grep Touchpad
```

---

### Post by kybKenny on 2009-04-20
I found out that i can do (using Vista) a "pinch" gesture to zoom stuff.
You place your thumb and a second finger in the corners of the pad and pretend to grab some salt off it. That works in windows. 
Doesn't that mean my pad is physically capable of recognizing multiple fingers.

In related news:

```
$ dmesg |grep Touchpad
[   10.975929] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000

```

So, according to above mentioned thread about a Dell, i shouldn't be able to use multi touch features even in windows. But i am.

Regards,
kybKenny

---

### Post by fathomssen on 2009-05-10
Hi,

I found a solutions (or workaround?):

The latest version of the synaptics driver supports two finger emulation. I think that it is something like the palm recognition. There are two parameters in 1.1.0: EmulateTwoFingerMinZ and EmulateTwoFingerMinW. The first says how much you have to press to activate the emulation and the second one how thick your fingers have to be to be recognised as two instead of one.

Here are some instructions:

1) Install the latest synaptics driver. You can get a .deb from Debian unstable: [http://packages.debian.org/sid/xserver-xorg-input-synaptics](http://packages.debian.org/sid/xserver-xorg-input-synaptics) (you will need the latest driver because the previous versions did not support EmulateTwoFingerMinW and thus were not flexible enought when it comes to different finger sizes).

2) Create a file /etc/hal/fdi/policy/99-x11-synaptics.fdi and fill it with
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      <merge key="input.x11_options.TapButton1" type="string">1</merge>
      <merge key="input.x11_options.TapButton2" type="string">2</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">10</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">10</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
    </match>
  </device>
</deviceinfo>
```

3) Restart HAL: /etc/init.d/hal restart

4) Restart X: Ctrl+Alt+Backspace or whichever way you prefer.

Explaining the FDI file:
* SHMConfig=On enables synclient to be used
* TapButtonX=X allows you to just tap on the pad instead of pressing a button below the pad
* Emulate...Z=10 says that you have to press with a strength of 10 (how much ever it is) to achieve emulation of two fingers
* Emulate...W=10 says that your fingers (both put together) must be 10 units wide for emulation
* VertTwoFingerScroll=1 turns on scrolling with (emulated) two fingers
* VertEdgeScroll=0 turns off scrolling on the right side of the pad

Hope this will help and that it will make its way into Ubuntu Karmic!

I use an Acer Aspire 3935 with just the same abovementioned Synaptics touchpad (firmware 7.2).

Best regards,
Freddy

---

### Post by fathomssen on 2009-05-10
Still a small problem: When I click e. g. a link with two fingers, sometimes the scrolling sets in before my click. So when I click a link in a list, it scrolls away and I will click the wrong link.

What we need here, is a possibilty to check if i wanted to click (which I do by pressing hard with the two fingers => higher Z value) or to scroll (smooooooth movement over the pad).

Freddy

---

### Post by STEELBAS on 2009-05-14
> **fathomssen said:**
> 
1) Install the latest synaptics driver. You can get a .deb from Debian unstable: [http://packages.debian.org/sid/xserver-xorg-input-synaptics](http://packages.debian.org/sid/xserver-xorg-input-synaptics) (you will need the latest driver because the previous versions did not support EmulateTwoFingerMinW and thus were not flexible enought when it comes to different finger sizes).
Hi,

How do you go about obtaining the .deb file from Debian Unstable?
Though I suppose the fact that I don't know how already indicates I shouldn't be messing around with unstable releases anyway... Is this unstable release useable or am I better off waiting for a stable release of this input-synaptics driver?

---

### Post by fathomssen on 2009-05-14
On the linked page,

1) scroll down and choose your architecture (most probably i386 or amd64),
2) click on a mirror in your country.

Then the file will be downloaded. You can choose your home directory as a destination.

In a terminal, do
# sudo dpkg -i <filename>.deb

After that, do the edits from my previous post.

---

### Post by kybKenny on 2009-05-14
Or, 
2) click the mirror-link
3) when (if) asked if you want to download or start the file, choose "GDebi installer" (if it is given in the dialog), that will give you a nice graphical user interface. But it does the same as above stated terminal command .

---

### Post by STEELBAS on 2009-05-15
Ah, yes, only finding the location of the .deb file was what bothered me, but thank you. To be complete: vertical scrolling needs to be enabled under the touchpad options.

Can't say I'm mighty convinced of this multi-touch usability myself, though. But then, a Mac probably offers a better first experience with it.

---

### Post by FokkerCharlie on 2009-07-16
Hi

I seem to have got this working (need to tweak the settings a little) on my touchpad- firmware v6.2

Would anyone like to share their fdi MinW and MinZ settings with me?

Cheers!
Charlie

---

### Post by kybKenny on 2009-07-19
Here you go, that's my .fdi (but it doesn't work too well i'm afraid:

```
~$ cat /etc/hal/fdi/policy/synapticprefs.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->
    </match>
  </device>
</deviceinfo>

```

---

### Post by akarun on 2009-08-10
> **FokkerCharlie said:**
> Hi

I seem to have got this working (need to tweak the settings a little) on my touchpad- firmware v6.2

Would anyone like to share their fdi MinW and MinZ settings with me?

Cheers!
Charlie

Hi FokkerCharlie,
I have a v6.2 firmware 
```

arun@arun-laptop:~$ dmesg | grep Touchpad
[   12.098304] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa580b1, caps: 0xa04711/0x200000

```

However when I do a synclient -m 15 and check the 'f' column, I get only 1 registered even with multi-finger touch. Could you get around this? If so can you please tell me?

Thanks,
Arun

---

### Post by FokkerCharlie on 2009-08-11
Akarun

It probably means that your touchpad doesn't support two-finger stuff.  You can try to force an emulation with lines like:

<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">70</merge>
<merge key="input.x11_options.EmulateTwoFingerMinW" type="string">4</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

However, I couldn't get it working consistently enough to be worthwhile.

Good luck!
Charlie

---

### Post by akarun on 2009-08-11
> **FokkerCharlie said:**
> Akarun

It probably means that your touchpad doesn't support two-finger stuff.  You can try to force an emulation with lines like:

<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">70</merge>
<merge key="input.x11_options.EmulateTwoFingerMinW" type="string">4</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

However, I couldn't get it working consistently enough to be worthwhile.

Good luck!
Charlie


Cheers Charlie.. I am not sure if want to do this. I'll probably survive with single touch and I am quite comfortable with the edge scroll. Pinch might have been good but I doubt if the "emulation" can do any good for pinch gesture..

---

### Post by kybKenny on 2009-08-12
With above mentioned settings, i'm getting at least a middle click by using middle and ring finger for tapping.
That said, my synclient mentions not more than 1 finger at all times.

---

### Post by miegiel on 2009-08-13
> **fathomssen said:**
> Hi,

I found a solutions (or workaround?):

The latest version of the synaptics driver supports two finger emulation. I think that it is something like the palm recognition. There are two parameters in 1.1.0: EmulateTwoFingerMinZ and EmulateTwoFingerMinW. The first says how much you have to press to activate the emulation and the second one how thick your fingers have to be to be recognised as two instead of one.

Here are some instructions:

1) Install the latest synaptics driver. You can get a .deb from Debian unstable: [http://packages.debian.org/sid/xserver-xorg-input-synaptics](http://packages.debian.org/sid/xserver-xorg-input-synaptics) (you will need the latest driver because the previous versions did not support EmulateTwoFingerMinW and thus were not flexible enought when it comes to different finger sizes).

2) Create a file /etc/hal/fdi/policy/99-x11-synaptics.fdi and fill it with
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      <merge key="input.x11_options.TapButton1" type="string">1</merge>
      <merge key="input.x11_options.TapButton2" type="string">2</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">10</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">10</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
    </match>
  </device>
</deviceinfo>
```

3) Restart HAL: /etc/init.d/hal restart

4) Restart X: Ctrl+Alt+Backspace or whichever way you prefer.

Explaining the FDI file:
* SHMConfig=On enables synclient to be used
* TapButtonX=X allows you to just tap on the pad instead of pressing a button below the pad
* Emulate...Z=10 says that you have to press with a strength of 10 (how much ever it is) to achieve emulation of two fingers
* Emulate...W=10 says that your fingers (both put together) must be 10 units wide for emulation
* VertTwoFingerScroll=1 turns on scrolling with (emulated) two fingers
* VertEdgeScroll=0 turns off scrolling on the right side of the pad

Hope this will help and that it will make its way into Ubuntu Karmic!

I use an Acer Aspire 3935 with just the same abovementioned Synaptics touchpad (firmware 7.2).

Best regards,
Freddy

Thanks man, especially for explaining the .fdi file, exactly what I was looking for. That .deb with the newer synaptics driver is already in karmic (alpha4), so soon people won't need to do that any more. I removed the *TapButton* lines, it seems like they're not necessary.

I'm guessing it's because of some stupid patent licence this touchpad has the 2 finger sensor turned off in the firmware (in making it cheaper for cheap laptops). I'm hoping there will be a way to change the firmware, I'm gessing the patent isn't valid here anyway :twisted:

But I'm happy now. The 2nd mouse button and two finger scrolling biting eachother doesn't bother me much.

```
:~$ dmesg | grep ouchpad
[    9.824740] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa44000
```

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
    </match>
  </device>
</deviceinfo>
```
Still trying different *MinZ* values with some help of
```
synclient -m 10
```

---

### Post by miegiel on 2009-08-15
> **kybKenny said:**
> Here you go, that's my .fdi (but it doesn't work too well i'm afraid:

```
~$ cat /etc/hal/fdi/policy/synapticprefs.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        **<!--** Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. **-->**
        **<!--** EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
	<merge key="input.x11_options.SHMConfig" type="string">true</merge>

	Maximum movement of the finger for detecting a tap
	<merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

	Enable vertical scrolling when dragging along the right edge
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

	Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

	Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

	If on, circular scrolling is used
	<merge key="input.x11_options.CircularScrolling" type="string">true</merge>

	For other possible options, check CONFIGURATION DETAILS in synaptics man page
        **-->**
    </match>
  </device>
</deviceinfo>

```

I figured out why it doesn't work :) Stuff between ***<!--*** and ***-->*** are notes.

---

### Post by wanchai on 2009-09-04
Does anyone know of a list that specifies which Synaptics device is capable of what?

I have two laptops, both running 9.04. The older one (HP Compaq NC6000) shows the following in dmesg:
```
Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1b6eb1, caps: 0xa84793/0x100000
```
Two-finger scrolling works fine. synclient shows f=2 when I touch it with two fingers. The width parameter w stays more or less constant.

The newer machine (HP EliteBook 6930p) has the following:
```
Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000
```
On this machine, I can't get the two-finger business to work. synclient always shows f=1. However, the w parameter increases significantly when I touch with two or three fingers. z stays more or less the same.

This sounds like a case where EmulateTwoFingerMinW could help, However, my synclient version 0.99.3 doesn't recognize it and putting it into the fdi file as mentioned in earlier posts here doesn't have any effect.

EDIT: read this thread again and found the bit about xserver-xorg-input-synaptics from Debian Sid. Installed that, and it works! Great  :-)

---

### Post by aurelieng on 2009-09-26
I managed to get something out of my Dell Precision M6400:

* hardware
```

Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd44791/0xf0040d

```* xserver-xorg-input-synaptics was installed from debian unstable
```

dpkg -l xserver-xorg-input-synaptics
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  xserver-xorg-input-syn 1.1.2-1                Synaptics TouchPad driver for X.Org server

```* my /usr/share/hal/fdi/policy/20thirdparty$ 11-x11-synaptics.fdi
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">10</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">10</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
    </match>
  </device>
</deviceinfo>

```* /var/log/Xorg.0.log:
```

(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.1.901, module version = 1.1.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(**) Option "SHMConfig" "On"
(**) Option "EmulateTwoFingerMinZ" "10"
(**) Option "EmulateTwoFingerMinW" "10"
(**) Option "VertEdgeScroll" "0"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found

```

That's not as smooth as a real multi-finger device, but better than nothing.

---

### Post by miegiel on 2009-09-26
> **aurelieng said:**
> ...
That's not as smooth as a real multi-finger device, but better than nothing.

A few days ago I added this merge line :
```
      <merge key="input.x11_options.JumpyCursorThreshold" type="string">100</merge>
```
It improved things a lot with regard to the jumpiness. It's just a hunch, but reasonable values are between 50 and 300.

To check your current value run ```
synclient -l
```

---

