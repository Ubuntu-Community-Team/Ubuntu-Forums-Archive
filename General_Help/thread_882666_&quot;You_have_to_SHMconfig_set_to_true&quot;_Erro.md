---
title: "&quot;You have to SHMconfig set to true&quot; Error When I already did it. Gsynaptics"
date: 2008-08-07
forum: General Help
---

### Post by kidwithshirt on 2008-08-07
Hey guys I got Ubuntu a couple days ago. Great stuff.

Anyway I am on a dell laptop (xps m1530) and I am trying to get the touchpad to be a bit more sensitive.

I discovered the [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) Tool and I followed the steps to "Enable SHMConfig"

Doesn't matter what the xorg is it always display the error. I tried "true" and "on" they both didnt work. I also messed with Kubuntu yesterday, did the same procedure. Didn't work. 

Sorry for being such a noob but this seems like a simple deal however I am just not getting it. 

Here's my xorg, take a look thanks =)

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
[COLOR="Red"]        Option          "SHMConfig"             "on"[/COLOR]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by kerry_s on 2008-08-07
have you restarted X after adding it to xorg.conf? (logout press ctrl+alt+backspace)

---

### Post by kidwithshirt on 2008-08-07
yes... like. right away. after saving.

---

### Post by kerry_s on 2008-08-07
> **kidwithshirt said:**
> yes... like. right away. after saving.

try checking your /var/log/Xorg.0.log for errors, (WW) or (EE)

---

### Post by Zorael on 2008-08-07
Does your /var/log/Xorg.0.log mention shared memory being enabled? (in this synaptics context.)

---

### Post by kidwithshirt on 2008-08-07
hey guys thanks for the replies

I am totally new so I don't know how to look for shared memories being enabled

But check this out

```

Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"

```

I dont know if this is relevant. Well nevertheless, I am just trying to get gsynaptic to work.


Oh odd phenomenon. After I posted this thread i went to sleep. I put the laptop in suspend. And when I booted it up again, the touchpad is smooth enough at a usable level. Weird eh?

---

### Post by kerry_s on 2008-08-07
da, quick google and it points me back here, i should have googled your model in the first place. :lolflag:
[http://ubuntuforums.org/showthread.php?p=4770585](http://ubuntuforums.org/showthread.php?p=4770585)

---

### Post by DagMan on 2008-08-07
from the log file, it doesn't detect a synaptics device and is probably using a normal mouse driver.
searching shows that it's most likely an alps touchpad, which I don't have any experience with but they can use the synaptics driver and take advantage of the features you're wanting to use.
Assuming it's an alps pad, here's some posts regarding it
[http://ubuntuforums.org/showthread.php?t=763043](http://ubuntuforums.org/showthread.php?t=763043)
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)

try adding the kernel paramater mentioned in those posts, though they might be outdated.


Assuming that works, and I don't know if it matters or not, but I've been using "true" rather than "on" for my SHMConfig value.

---

### Post by kidwithshirt on 2008-08-07
> **DagMan said:**
> from the log file, it doesn't detect a synaptics device and is probably using a normal mouse driver.
searching shows that it's most likely an alps touchpad, which I don't have any experience with but they can use the synaptics driver and take advantage of the features you're wanting to use.
Assuming it's an alps pad, here's some posts regarding it
[http://ubuntuforums.org/showthread.php?t=763043](http://ubuntuforums.org/showthread.php?t=763043)
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)

try adding the kernel paramater mentioned in those posts, though they might be outdated.


Assuming that works, and I don't know if it matters or not, but I've been using "true" rather than "on" for my SHMConfig value.

Thanks sir this helped my touchpad to work properly. Before, the touch pad behaves erratically when i first start up ubuntu, such as at places like the log in screen. However now it works perfectly

Yet the Gsynaptic still does not work =\ I want to change some options of my touchpad. Even though it functions okay right now

New log, sort of the same. A bit changes.

```
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "true"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
```

---

### Post by xavi1337 on 2008-08-18
I got synaptics working on the dell M1530 by adding this to /boot/grub/menu.lst in with the kernel parameters "i8042.nomux=1"

---

### Post by MooseMagnet on 2009-01-03
Trying to set SHMConfig to 'true'  - I followed these instructions on editing the hal file, but had no luck.

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

When the instructions told me to restart after editing the hal file, I thought they meant to 'just' restart the laptop.

I issued this command

sudo /etc/init.d/hal restart

and restarted my laptop again, and now my SHMConfig is set to 'true' and I DO have the Touchpad GUI under System > Preferences. And my touchpad works great.

Hope this helps.

---

### Post by Frost1013 on 2009-01-23
Thank you! this worked great!

---

### Post by Lizzy on 2009-01-27
Thank you ever so much for the link, this realy saved my day. I thought i'm going GOOGOO reaguarding my touchpad. Now everything works perfect :D !!

---

