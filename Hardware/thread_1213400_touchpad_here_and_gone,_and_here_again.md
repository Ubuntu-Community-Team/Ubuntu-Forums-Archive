---
title: "touchpad here and gone, and here again"
date: 2009-07-14
forum: Hardware
---

### Post by ubuntubrian on 2009-07-14
I have a Toshiba satellite. Touchpad worked fine with Jaunty until some upgraded packages a while back. Then I had no tapping even when I ran gsynaptics and enabled it, logged out/in, rebooted, etc. I found some threads about touchpad problems and ran:
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

Trackpad and touchpad now work fine but if I try to change settings from preferences or gsynaptics in a terminal I get this:
> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I have checked:
```
$ xinput list
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
"PS/2 Synaptics TouchPad"	id=2	[XExtensionPointer]
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
		Resolution is 1

```

But xorg.conf doesn't have an entry for the touchpad and seems pretty scant in any case, unlike many of the threads I've seen. Here's the whole thing (uncommented):
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


But xorg.log finds the trackpad fine:

> (**) PS/2 Synaptics TouchPad: always reports core events
(**) PS/2 Synaptics TouchPad: Device: "/dev/input/event8"
(II) PS/2 Synaptics TouchPad: Found 3 mouse buttons
(II) PS/2 Synaptics TouchPad: Found x and y relative axes
(II) PS/2 Synaptics TouchPad: Configuring as mouse
(**) PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
(**) PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE)
(**) PS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) PS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) PS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) PS/2 Synaptics TouchPad: (accel) set acceleration profile 0 

How do I renable gstnaptics? Why do gsynaptics, syndaemon and synclient now do this?

```
$ gsynaptics-init
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XFree86.conf to use GSynaptics
$ syndaemon
Unable to find a synaptics device.
$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

```

It isn't a big deal yet as I can use the trackpad but I can't adjust it. Also, not knowing why this happened is unsettling and I like to understand these things.

Many thanks

---

### Post by ubuntubrian on 2009-07-14
Forgeot to mention that I do have the synaptics driver installed and I have reinstalled it a couple of times.
:guitar:

---

### Post by ubuntubrian on 2009-07-14
I also tried this:

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

> Note: Tools such as xinput and syndaemon can now alter touchpad settings without needing SHMConfig to be enabled. However, SHMConfig is still required for some functionality.

In order for tools such as synclient, syndaemon, gsynaptics, ksynaptics, and qsynaptics to work, they need access to the synaptics touchpad driver shared memory. This is done by enabling SHMConfig "on" in the X server Synaptics touchpad configuration. With this enabled, these tools can modify the run-time configuration of the touchpad input driver without restarting the X server.

    *

      /!\ Note the warning from the man page for synclient:

      WARNING: This is not secure if you are in an untrusted multiuser
               environment. All local users can change the parameters at any time.

      If this is an issue for you, the touchpad can be configured without enabling SHMConfig by placing the desired options in a HAL fdi file and rebooting. 

In a terminal type (for Gnome/Ubuntu):

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

(for KDE/Kubuntu):

kdesudo kate /etc/hal/fdi/policy/shmconfig.fdi

Put this into the file:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

Save and close that file, reboot, and SHMConfig should be enabled.



As some threads mentioned this possibility, but no luck   ;)

---

### Post by orengolan on 2009-11-19
I am facing similar issue.
 
I try to use syndaemon -t 
so when I type and by mistake move the mouse, the focus of the typing will not change to where the pointer is.

I couldn't find a way to enable SHMConfig - 
my Xorg doesn't have entry for touchpad 
and editing /etc/hal/fdi/policy/shmconfig.fdi  didn't help.

any advice would be great.

---

### Post by thered on 2009-11-30
Me too, I have another post here:

[http://ubuntuforums.org/showthread.php?p=8414933#post8414933](http://ubuntuforums.org/showthread.php?p=8414933#post8414933)

Tried all above.

---

### Post by jwilcox09 on 2009-11-30
I'm having the same issue, except on my Asus 1000HE.  Trackpad was working fine in 9.04 and now not in 9.10....

---

### Post by orengolan on 2009-12-06
[here]("https://bugs.launchpad.net/ubuntu/+s...cs/+bug/132627") is the bug on launchpad, and [here]("http://ubuntuforums.org/showthread.php?p=8454167#post8454167") is a new thread I started.
thanks!

---

