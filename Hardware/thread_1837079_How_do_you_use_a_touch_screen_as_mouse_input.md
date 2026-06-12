---
title: "How do you use a touch screen as mouse input?"
date: 2011-09-01
forum: Hardware
---

### Post by abtekk on 2011-09-01
Hi, I have just ported Ubuntu 9.10 to my ArmV6 tablet pc.

I have used tslib to get my touch screen working and I have managed to calibrate using ts_calibrate. Ubuntu picks up the touch screen fine in the calibration app but it won't move the mouse or anything, is there anything I must do to "link" them together?

---

### Post by abtekk on 2011-09-01
Is no one able to help? I could really do with getting this working.

---

### Post by PapaGary on 2011-09-01
> **abtekk said:**
> Ubuntu picks up the touch screen fine in the calibration app but it won't move the mouse or anything, 

:confused:
If you have a touch screen then why do you even need the mouse?

---

### Post by abtekk on 2011-09-01
> **PapaGary said:**
> :confused:
If you have a touch screen then why do you even need the mouse?

Sorry, I meant it won't do any mouse functions such as left clicking or even moving the cursor.

---

### Post by Favux on 2011-09-01
What does the touch screen call itself in *lsusb*?  What's the output of *xinput list*?

I'm thinking with a Jaunty ARM port you need to match the appropriate keyword in a HAL .fdi file to the correct X driver.  Maybe evdev, but you'd think evdev would be picking the tablet up by default.

---

### Post by abtekk on 2011-09-02
*lsusb* doesn't show my touch screen as it is built in (I'm porting Ubuntu to a tablet pc, the Zenithink ZT-180) Sorry for not stating that in the original post.

Heres the xinput list output:

```

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
"imapx200_keybd"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"gpio-keys"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PS/2+USB Mouse"	id=4	[XExtensionPointer]
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
"MOSART Semi. Wireless Keyboard & Mouse"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 18
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
"MOSART Semi. Wireless Keyboard & Mouse"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

I also placed all the correct Kernel modules for my tablets hardware into _/lib/modules/2.6.32.9_ and edited my modules file to load these at boot.

---

### Post by Favux on 2011-09-02
Even if built in the touchscreen will have an internal connection.  That should either be usb or serial.  Do you know which?

Not showing up in *lsusb* could indicate that there isn't a driver for it in the kernel or that it is serial.

---

### Post by abtekk on 2011-09-02
It must be serial as someone before me has ported xubuntu to this tablet and he had the touch screen working, he was also using the same Kernel and modules as me. (He won't reply to me emails asking how he did it though).

---

### Post by Favux on 2011-09-02
Alright.  Let's see if we can find out which serial port it is on.
```
dmesg | grep ttyS
```

---

### Post by abtekk on 2011-09-02
I'll be a second, it's crashing on me. I need to un bloat this install severely...

---

### Post by abtekk on 2011-09-02
> **Favux said:**
> Alright.  Let's see if we can find out which serial port it is on.
```
dmesg | grep ttyS
```

OK that command kicked out the following:

```

Kernel command line: console=ttySAC1,115200 rdinit=/init mem=256M android.ril=ttyUSB1
console [ttySAC1] enabled

```

Any ideas?

---

### Post by Favux on 2011-09-02
Nope, not really.  ttySAC1 seems to be the console.  You could see if any serial ports are listed:
```
ls /dev/ttyS*
```
android.ril=ttyUSB1 confuses me.  A serial-to-usb converter shows up as ttyUSB1 I suppose, although if there is just one it is usually ttyUSB0.  You might want to check if there are others:
```
dmesg | grep ttyUSB
```
You could do an attribute walk on it and see what's there:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyUSB1)
```
By the way why are you using Jaunty (9.10)?

---

### Post by abtekk on 2011-09-02
OK I went ahead and ran the dmesg command on it's own, after searching through it I found the section relating to my touch screen. Due to the size of the output I have attached it to a txt file on this post.

EDIT: I'm using 9.10 because as far as I'm aware isn't it the last version to support the ARM6 processor?

EDIT2: I thought Karmic was 9.10?

EDIT3: The android section might confuse you as it is natively an Android device but I modified the initramfs of the kernel to boot Linux from the SDCard ;). However this is temporary and I do plan to get in on the internal NAND.

---

### Post by Favux on 2011-09-02
Karmic is 10.10.  I didn't know ARM6 support was dropped by Natty (11.04).  But I don't follow ARM stuff.

Good, we know its name *TSC2007 Touchscreen*.  Something to google.  A quick one shows Meego bug reports etc.

Looking at a fairly recent linux-input git clone I see tsc2007.c in /drivers/input/touchscreen.  And here's where the dmesg name is coming from:
```
	input_dev->name = "TSC2007 Touchscreen";
```
But why isn't that kernel exported name showing up in *xinput list*?  Do you see it anywhere in /dev/input?

---

### Post by abtekk on 2011-09-03
I know for a fact from previous attempts that the touch screen is connected to:

```

/dev/input/event2

and

/dev/input/input2

```

If I enter the command:
*cat /dev/input/event2*
and press on the screen, I get some garbled output.

---

### Post by abtekk on 2011-09-03
Little bump :)

---

### Post by Favux on 2011-09-03
Hi abtekk,

Good, since it is on event2 we don't have to look for the raw input with evtest then.

I still don't understand why you aren't seeing the touch screen in *xinput list*.  The reason we want that is we need a keyword(s) to construct a .conf file with a match to the appropriate X driver.

If raw data is coming in from the kernel then the missing component is a X driver to translate it into X input events.  What should be happening is the evdev X driver should be picking it up.  Let's look at Xorg.0.log in /var/log and see what's going on.  We should see one of the evdev snippets, presumably the "evdev touchscreen catchall", in 10-evdev.conf located at /usr/share/X11/xorg.conf.d pick up the "TSC2007 Touchscreen".  Go ahead and compress it with right click Create Archive and attach it with Manage Attachments.

---

### Post by abtekk on 2011-09-03
Thanks mate, while I go collect them files, maybe you should have a look at [This](http://www.slatedroid.com/topic/8543-debian-on-epad-worked/page__st__120__p__94231#entry94231)

---

### Post by Favux on 2011-09-03
We should look at:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event2)
```
also.

Great link.  It indicates the evdev X driver will actually work!  That was an old problem with the Synaptic driver.  It was too "grabby".  We had to fix it with a pre-probe .fdi to get the N-trig touch screen working, for example.  That was fixed upstream so it isn't a problem now.  What's useful to us is it has the coordinates:
```
26 3844 -37 3631
```
Also from:
```
<match key="info.product" contains="TSC2007 Touchscreen">
```
we may have our keyword to do an evdev match.

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> We should look at:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event2)
```

Doing that command gave the error:
```

device node not found
info: option requires an argument -- 'p'

```

EDIT: I modified the command and put the command in brackets in '' instead, then the error kicked out:
```

device path not found

```
--------------------------------

I have no xorg.conf or xorg.conf.d in /usr/share/x11, so I couldn't find the 10-evdev.conf file you wanted. However I have attached the xorg.0.log file you wanted.

EDIT: After looking through the log, I think we will have to do what mozzwald did on that link I gave you.

---

### Post by Favux on 2011-09-03
Are you actually on Jaunty?  What's the output of?
```
Xorg -version
```

---

### Post by Favux on 2011-09-03
Hmmm.  From the Xorg.0.log:
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.28-14-lange51 armv7l Ubuntu
Current Operating System: Linux zt180 2.6.32.9 #1818 Thu Oct 14 19:38:13 CST 2010 armv6l
Kernel command line: console=ttySAC1,115200 rdinit=/init mem=256M android.ril=ttyUSB1
Build Date: 26 October 2009  05:21:20PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
```
You have X server 1.6.4 on the Lucid 2.6.32 kernel.  So since you are pre-1.7 you still use HAL/.fdi.  That sucks, I promptly started forgetting all that .fdi abomination as quickly as I could.

So you're right you still have the buggy Synaptics driver:
```
(II) config/hal: Adding input device TSC2007 Touchscreen
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event2"
(--) TSC2007 Touchscreen: no supported touchpad found
(EE) TSC2007 Touchscreen Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "TSC2007 Touchscreen"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (8)
```
If so it probably won't let go of the touchscreen even if we set up a .fdi to explicitly match it.  Well maybe not, the module fails after all.

Is your plan to continue with this hybrid port?  Is there some reason you couldn't use a more recent version?  Say based on Lucid, since it is a long term support release?

Edit:  If so now we need a lshal to make a .fdi to match:
```
lshal > lshal.txt
```

---

### Post by Favux on 2011-09-03
Alright, cleaning up the garbled syntax this is the 50-tsc2007.fdi:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="TSC2007 Touchscreen">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.calibration" type="string">26 3844 -37 3631</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
they want at /usr/share/hal/fdi/policy/20thirdparty/50-tsc2007.fdi.

Edit:  Here's how to fix the synaptic.fdi.  You nest a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
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

Use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
to edit, and then reboot.

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> Are you actually on Jaunty?  What's the output of?
```
Xorg -version
```

I'm on Karmic, 9.10.

Output: 
```

Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.28-14-lange51 armv7l Ubuntu
Current Operating System: Linux zt180 2.6.32.9 #1818 Thu Oct 14 19:38:13 CST 2010 armv6l
Kernel command line: console=ttySAC1,115200 rdinit=/init mem=256M android.ril=ttyUSB1
Build Date: 26 October 2009  05:21:20PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 

```

> **Favux said:**
> Hmmm.  From the Xorg.0.log:
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.28-14-lange51 armv7l Ubuntu
Current Operating System: Linux zt180 2.6.32.9 #1818 Thu Oct 14 19:38:13 CST 2010 armv6l
Kernel command line: console=ttySAC1,115200 rdinit=/init mem=256M android.ril=ttyUSB1
Build Date: 26 October 2009  05:21:20PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
```
You have X server 1.6.4 on the Lucid 2.6.32 kernel.  So since you are pre-1.7 you still use HAL/.fdi.  That sucks, I promptly started forgetting all that .fdi abomination as quickly as I could.

So you're right you still have the buggy Synaptics driver:
```
(II) config/hal: Adding input device TSC2007 Touchscreen
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event2"
(--) TSC2007 Touchscreen: no supported touchpad found
(EE) TSC2007 Touchscreen Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "TSC2007 Touchscreen"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (8)
```
If so it probably won't let go of the touchscreen even if we set up a .fdi to explicitly match it.  Well maybe not, the module fails after all.

Is your plan to continue with this hybrid port?  Is there some reason you couldn't use a more recent version?  Say based on Lucid, since it is a long term support release?

Edit:  If so now we need a lshal to make a .fdi to match:
```
lshal > lshal.txt
```

Yes I want to keep with this port, but I could implement it to different ports.

> **Favux said:**
> Alright, cleaning up the garbled syntax this is the 50-tsc2007.fdi:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="TSC2007 Touchscreen">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.calibration" type="string">26 3844 -37 3631</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
they want at /usr/share/hal/fdi/policy/20thirdparty/50-tsc2007.fdi.

I have attached the lshal.txt, what to do next?

---

### Post by abtekk on 2011-09-03
> Edit:  Here's how to fix the synaptic.fdi.  You nest a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
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

I don't have the synaptics .fdi on my system o.O

---

### Post by Favux on 2011-09-03
You are correct, you are on Karmic i.e. X server 1.6.4.  I had a brain fart.  Sorry.

I've forgotten which kernel Karmic had.  2.6.31?  The 2.6.32 kernel is the Lucid kernel though.

Here's the relevant HAL section:
```
udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'TSC2007 Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'TSC2007 Touchscreen'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'  (string)
```
So we should be good from the look of things.

There must be a synaptic .fdi somewhere since it is trying to match and failing.  And this is why it is trying to match:
```
  info.capabilities = {'input', 'button', 'input.touchpad'} (string list)
```
It thinks it is a touchpad.

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> You are correct, you are on Karmic i.e. X server 1.6.4.  I had a brain fart.  Sorry.

I've forgotten which kernel Karmic had.  2.6.31?  The 2.6.32 kernel is the Lucid kernel though.

Here's the relevant HAL section:
```
udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'TSC2007 Touchscreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'TSC2007 Touchscreen'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'  (string)
```
So we should be good from the look of things.

There must be a synaptic .fdi somewhere since it is trying to match and failing.

The reason the Kernel is 2.6.32.9 is because it was originally the kernel that Zenithink used to boot Android on the system but the initramfs has been modified to boot Linux from the SDCard.

Anyway, catfish isn't returning any results. I created a blank synaptic .fdi file and just entered what you had in the code tags, but I don't know if it did anything.

---

### Post by Favux on 2011-09-03
Well it is possible to have a synaptic section in the xorg.conf (/etc/X11) also but that seems unlikely.

Something created the attempt to match we saw in the Xorg.0.log.  But since the match didn't take I was hoping the tsc2007 .fdi would work.  No luck?

---

### Post by abtekk on 2011-09-03
No, no response from the touch screen. xinput_calibrator keeps claiming there is a "Segmentation fault"...
Plus I can't compile mozzwalds version, it keep kicking me an error :(

This is really baffling me...

---

### Post by Favux on 2011-09-03
Does the Xorg.0.log or Xorg.0.log.old show the segmentation fault?  Can you tell what is throwing the segmentation fault?

I'm wondering about an ABI mismatch between X server 1.6.4 and the driver and/or kernel 2.6.32.

---

### Post by abtekk on 2011-09-03
I couldn't see anything, there were 5 logs this time. I've attached them :/.

---

### Post by Favux on 2011-09-03
I'm wondering if it is the wireless keyboard.  I can't really tell.  Do you need it?
```
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(II) MOSART Semi. Wireless Keyboard & Mouse: Close
(II) UnloadModule: "evdev"
(II) MOSART Semi. Wireless Keyboard & Mouse: Close
(II) UnloadModule: "evdev"
(II) imapx200_keybd: Close
(II) UnloadModule: "evdev"
(II) gpio-keys: Close
(II) UnloadModule: "evdev"
(II) PS/2+USB Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```
Seems to be blowing evdev up?

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> I'm wondering if it is the wireless keyboard.  I can't really tell.  Do you need it?
```
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(WW) config/hal: device MOSART Semi. Wireless Keyboard & Mouse already added. Ignoring.
(II) MOSART Semi. Wireless Keyboard & Mouse: Close
(II) UnloadModule: "evdev"
(II) MOSART Semi. Wireless Keyboard & Mouse: Close
(II) UnloadModule: "evdev"
(II) imapx200_keybd: Close
(II) UnloadModule: "evdev"
(II) gpio-keys: Close
(II) UnloadModule: "evdev"
(II) PS/2+USB Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```
Seems to be blowing evdev up?

Yeah I need to able to log in and type commands, I don't have a wired keyboard.

---

### Post by Favux on 2011-09-03
Appropo of not much, what is in your xorg.conf?  Does the touchscreen tablet have a Synaptic touchpad?

By the way what is the name of the thing?  It isn't a tablet PC really, it's an ARM tablet or slate correct?

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> Appropo of not much, what is in your xorg.conf?  Does the touchscreen tablet have a Synaptic touchpad?

By the way what is the name of the thing?  It isn't a tablet PC really, it's an ARM tablet or slate correct?

I don't have an xorg.conf stupidly.
Yes it is an ARM slate, the Zenithink ZT-180.

---

### Post by abtekk on 2011-09-03
Not given up on me, have you? ;)

---

### Post by Favux on 2011-09-03
Nope, but you need to figure out where the Synaptic match in the first Xorg.0.log you posted is coming from.  I'm hoping, in the abscence of more concrete evidence, that that is the problem.  That despite the Synaptic module not taking up the touch screen it is somehow interfering with the tsc2007.fdi and causing the segmentation fault.  We need to rule that out anyway.  Which directories have you looked in?

---

### Post by abtekk on 2011-09-03
Well I used LXDE's built in program for finding files/folders and it didn't find the synaptic fdi.

So I removed the package with apt-get remove and it didn't make a difference.
(I think the package was xserver-xorg-xinput-synaptics or something like that)

EDIT: I have realised that the TSC2007 fdi is looking for the xinput calibration settings, however mozzwald on slatedroid said that his version on xinput-calibrator works and others didn't, however I can't compile the source he posted.

---

### Post by Favux on 2011-09-03
Well what source and what errors is it throwing up.

If this line:
```
        <merge key="input.x11_options.calibration" type="string">26 3844 -37 3631</merge>
```
is invoking xinput_calibrator and that is what is causing the seg fault just remove it.  Then check the Xorg.0.log and see if evdev wants the coordinates.  We should be able to do that through TopX&Y and BottomX&Y settings.  We don't need xinput_calibrator once we have the coordinates.

---

### Post by Favux on 2011-09-03
It would then look something like:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="TSC2007 Touchscreen">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.TopX" type="string">26</merge>
        <merge key="input.x11_options.TopY" type="string">-37</merge>
        <merge key="input.x11_options.BottomX" type="string">3844</merge>
        <merge key="input.x11_options.BottomY" type="string">3631</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by abtekk on 2011-09-03
> **Favux said:**
> Well what source and what errors is it throwing up.

If this line:
```
        <merge key="input.x11_options.calibration" type="string">26 3844 -37 3631</merge>
```
is invoking xinput_calibrator and that is what is causing the seg fault just remove it.  Then check the Xorg.0.log and see if evdev wants the coordinates.  We should be able to do that through TopX&Y and BottomX&Y settings.  We don't need xinput_calibrator once we have the coordinates.

OK xinput_calibrator has been removed, here's my Xorg log.

Could it be the wireless keyboard screwing me over?

---

### Post by Favux on 2011-09-03
That's a bummer, no touchscreen at all now.  I'll look over the txc2007.fdi and see if there's and obvious mistake.  Double check on its installation.
> Could it be the wireless keyboard screwing me over? 
I have no idea.


Edit:  As far as I can tell the .fdi aligns with what lshal shows us so it should be working.  What kernel and X server version was he using?

---

### Post by abtekk on 2011-09-03
The .fdi is in the correct dir. But, when I run the dmesg command now, it doesn't show near as much information about the touch screen as it did before.

EDIT: The kernel was the same as mine, as for xserver, I'm not sure. I have his rootfs on my computer so I'll check his logs.


That's the top of the other guys Debian RootFS Xorg.0.log
```

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-rc9 armv5tel Debian
Current Operating System: Linux debian-epad 2.6.32.9 #1806 Mon Sep 27 11:25:47 CST 2010 armv6l
Kernel command line: console=ttySAC1,115200 rdinit=/init mem=192M android.ril=ttyUSB1
Build Date: 20 September 2010  06:21:45PM
xorg-server 2:1.7.7-7 (Julien Cristau <jcristau@debian.org>) 
```

Shall I update my xorg-core to 1.7.7?

---

### Post by Favux on 2011-09-03
Alright.  Debian and Ubuntu use a hybrid X server 1.7.  It has a backport of an early version of X server 1.8 in it.  That way they could dump HAL/.fdi and go to udev/.conf files.  Vanilla 1.7 still uses HAL/.fdi.

Before we try upgrading the X server see if the TSC2007 is still in lshal and if it is, has it changed?

If there was a change in the tsc2007.c in the kernel then maybe there is an ABI mismatch between the 2.6.32 kernel and the 1.6.4 evdev X driver.  2.6.32 is usually paired with X server 1.7 that I've seen.

---

### Post by abtekk on 2011-09-03
Wow, this is strange, I have NO idea what has changed but the touch screen is now working. (However it is slightly off calibration to the right). THANK YOU! :)

*Now I must get this xinput_calibrator compiled*

What could have been the last step that made it work?
(I think it must have been when I used the .fdi file you "ungarbled")

---

### Post by Favux on 2011-09-03
Outstanding!  :D

Sometimes it takes a few reboots for things to shake out.

---

### Post by abtekk on 2011-09-03
Thank you so much for your help, Favux.

---

### Post by Favux on 2011-09-03
Sure.  Are you going to throw together a HOW TO?  I'm sure others with a "TSC2007 Touchscreen" would appreciate it.

By the way the .conf file, if you ever update the X server, would probably be something like:
```
Section "InputClass"
        Identifier "TSC2007 touchscreen class"
	MatchProduct "TSC2007 Touchscreen"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "TopX" "26"
        Option "TopY" "-37"
        Option "BottomX" "3844"
        Option "BottomY" "3631"
EndSection
```
Using whatever coordinates you end up with of course.

---

### Post by abtekk on 2011-09-04
Yeah I would be happy to write up a tutorial, thanks again.
Also will updating the xserver to 1.7.7 finally give me an xorg.conf?

---

### Post by Favux on 2011-09-04
Great!

No.  Updating makes the xorg.conf less likely.  They're trying to do all the configuration automatically in udev and xorg.conf.d (with .conf files).  Actually now days it is the video driver that usually determines it.  The Nvidia proprietary driver will install an xorg.conf.  You can still use a xorg.conf but there aren't many reasons to do so.

Basically the system starts reading the xorg.conf and sort of immediately goes over to xorg.conf.d.  So the .conf files can sort of be thought of as xorg.conf sections.  Then when finished with them it goes back to the xorg.conf and finishes by reading it.  So if you have entries in it they control.  Whatever runs last controls.

---

