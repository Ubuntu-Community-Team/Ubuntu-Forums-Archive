---
title: "Ubuntu 8.04 on toshiba satellite: touchpad and usb mouse conflict"
date: 2008-05-05
forum: Hardware
---

### Post by elgaelo on 2008-05-05
Hi all,

I'd like to share some problems regarding the touchpad on my toshiba satellite laptop running Ubuntu Hardy Heron.

I installed Ubuntu having a usb mouse plugged-in. Everything worked fine, and I can use both touchpad and usb mouse. However, I realized that if the usb mouse is not connected on startup, then Ubuntu hangs sometimes before and sometimes once you login.

I have been researching about xorg.conf, because I think is the root of the problem and it's not clear for me why the default xorg.conf configuration don't let me use the laptop without the usb mouse connected. I read about the "InputDevice" section, the "Core Pointer" option and some other features from the "man xorg.conf" page but I can't figure it out.

I've been testing the startup with and without the usb mouse, also changing the xorg.conf file and I can't extract any conclusion. The only one is that I want to have Ubuntu running I have to connect the usb mouse.

If I look up the Xorg.0.log file, the hardware detects both touchpad and usb mouse.

Any comments or suggestions? I really appreciate any of your thoughs guys cause it's probably a misconfiguration which is taking lots of hours and it's getting me very pissed off :-(

Thanks!

---

### Post by pistos on 2008-05-05
I had the same problem with my laptop, which is an Acer TravelMate 8003, with an ATI Mobility 9700 128 graphics card built in. I thought it was a problem with the xorg.conf at first too. But, I think the problem has something to do with the graphics driver. I installed the newest ATI driver and the problem was resolved on my machine.

However, I have also been having problems with the newest ATI driver. When my screen blanks, my system will lock up and I have to force a reboot. So, I have uninstalled the ATI driver and giving the basic one a try to see if I can get a "healthy" machine back.

---

### Post by elgaelo on 2008-05-06
Thanks for your reply, pistos.

Actually, I also had problems during the installation with the video chipset (also ATI Radeon 9600) until using the "graphics safe mode" (which probably uses the xforcevesa kernel option). Once booted, then installing the ATI restricted drivers works fine for me.

Definitely, symptoms are clear now. **I need the usb mouse plugged in, otherwise ubuntu hangs.** Pistos, how close where your symptoms to mine?

There are good news though. Yesterday night I found a bug description that really seems to be what it happens to me. I quote it right here:

> On some laptops when you start the machine with an external mouse connected, that mouse reserves the first event-file at /dev/input and the synaptics touchpad (perhaps others too) has to take the second. This makes configuring the mouse impossible, because the xorg-synaptics driver won't find the correct device.

I've fixed this by creating a udev rule in /etc/udev/rules.d and writing this one line there:
BUS="serio", SYSFS{description}="i8042 Aux-3 Port", KERNEL="event?", SYMLINK="input/touchpad"

Then just make the Device option inside Synaptics input-device section point to the correct place:
Option "Device" "/dev/input/touchpad"

Now both the mouse and the touchpad work fine. The only variable here is the sysfs-description which could be different on different computers. If the /dev/input/mouse?-file is known, the correct sysfs-description can be found with the command:
udevinfo -a -p `udevinfo -q path -n /dev/input/mouse1`

Extracted from [https://bugs.launchpad.net/ubuntu/+source/xorg-driver-synaptics/+bug/28914]("https://bugs.launchpad.net/ubuntu/+source/xorg-driver-synaptics/+bug/28914")

I'm trying to contact the author to check if the problem has been solved since 2006.

I'll keep you informed.

---

### Post by pistos on 2008-05-06
> **elgaelo said:**
> Definitely, symptoms are clear now. **I need the usb mouse plugged in, otherwise ubuntu hangs.** Pistos, how close where your symptoms to mine?

Exactly the same as yours. I have since uninstalled the ATI drivers  and my laptop appears to be functioning correctly in regards to the touchpad and the mouse.

---

### Post by elgaelo on 2008-05-06
Right on, I will uninstall the ATI drivers and see what's going on.

---

### Post by pistos on 2008-05-06
I should have probably said earlier what my sequence of installs etc was. So, here is how it all went down for me...

When I first upgraded to 8.04 from 7.10, I installed the ATI drivers that came with the upgrade. That is when I had my problems with the touchpad and the USB mouse. The computer would only do a clean boot-up if I had teh USB mouse plugged in. If the USB mouse was not present the computer would fail to boot up somewhere in the process and lock up.

I then tried uninstalling the ATI drivers, but the problem persisted, appearing as though the ATI drivers were still in effect. So, I then went the "other direction" by installed EnvyNG and installing the latest ATI drivers through EnvyNG.

That fixed the touchpad/USB mouse problem, but it created more serious problems for me. Every time my screen would blank via the screensaver, it would lock up my computer and require a reboot. As long as my screen stayed on all the time, everything would function, but with a laptop that is not going to be acceptable for very long.

So, then, I uninstalled the ATI drivers completely via EnvyNG, and am now running the generic vesa drivers and it appears that I now have a happy touchpad and USB mouse and suspend/hiberate also working. I don't have 3D acceleration at this point, but I would rather have a computer that works reliably than one with compiz and unpredictable behavior. I am hoping that ATI will resolve the conflicts in their driver, and then I will give it another try at that point.

---

### Post by elgaelo on 2008-05-06
I tried to reboot uninstalling before the ATI restricted drivers. So I was booting with this default xorg.conf (automatically generated when uninstalling the xorg-conf-fglxr package):

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Unfortunately, booting without the usb mouse connected didn't work for me. The system hangs (but the touchpad was moving, no button hit detected though). Is this the same xorg.conf you are using now?

Thanks for your post pistos!

---

### Post by pistos on 2008-05-07
Here is my current xorg.conf. It is very similar to yours, except for the the driver is set to "vesa" for the Configured video device. Remember, in my last post I said that I used EnvyNG to remove the ATI drivers, and it was then EnvyNG that created the xorg.conf that I currently have. Hope this helps you.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection

```

---

### Post by luopio on 2008-05-07
I'm the guy that wrote the bug/solution on LP. I'm sorry to say that I don't have any further info on the bug. I haven't actually bumped into it since Edgy.

AFAIK the original problem sounds like a core pointer missing issue even though the xorg.conf seems fine.

I don't see how ATI drivers could be related to input.

I'd try to change the psaux-repeater device to another device. Perhaps an event device. If you're lucky you might have ended with a event device called "touchpad" under /dev/input/, otherwise you'll find the touchpad in one of the /dev/input/event* nodes. You can find which one it is by running "sudo cat PATH_TO_DEVICE_FILE". Then if you tap your touchpad you'll see output on the console. 

Once you find the correct event device you can set it up on in the xorg.conf by replacing the psaux value with it.

The problem I originally described is however related to your mouse taking the first place in the event files and thus changing the event-number of your touchpad (if the mouse is connected on bootup). The solution is to use an UDEV rule that reads device descriptions and always gives your touchpad a distinct device node (like I said, you might already have this as input/touchpad or something). Using a distinct name is preferred since it won't change (unless you unplug your touchpad ;) )

Good luck!

---

### Post by pistos on 2008-05-07
> **luopio said:**
> I don't see how ATI drivers could be related to input.

First, thanks for your input. Second, I don't know nearly as much as you do about computers/linux, since I can't even understand half of what you posted. :) Third, I agree that the interaction between ATI drivers and the input devices seems very unusual.

But, what led me to suspect the driver is the screen image corruption that would occur when the system lock-ups happened. Also, lock-ups would occur when attempting to pull down a menu. That sort of thing. Lock-ups were occurring during times when "input" and "video output" were interacting with one another (at least from the user perspective).

So, when I uninstalled the ATI drivers, the problem immediately disappeared.

If there is some other explanation other than the ATI drivers I would love to learn it. I would very much like to use the ATI drivers if possible.

---

### Post by elgaelo on 2008-05-07
Thanks luopio for your contribution.

This is the output of "ls /dev/input/by-path" command:
```
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 pci-0000:00:1d.1-usb-0:2:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 pci-0000:00:1d.1-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 platform-i8042-serio-4-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 platform-i8042-serio-4-mouse -> ../mouse3
lrwxrwxrwx 1 root root 9 2008-05-08 00:21 platform-pcspkr-event-spkr -> ../event6
```

As you mentioned, event2 and mouse1 are related to the usb mouse and I can see garbage on the terminal using "sudo cat PATH_TO_DEVICE_FILE". However, it didn't work for mouse3 and event9, which I presume are the device files for the touchpad.

Does that mean anything for you?
Thanks!

---

### Post by luopio on 2008-05-08
if you run *sudo cat /dev/input/mouse3* and fumble around with your touchpad you should see garbage in the console. This would indicate that mouse3 is your touchpad. The same should happen with event9. The event bit is just a different protocol to the same device.

Now the issue is that your touchpad should be found on each bootup and your mouse optionally if it's connected or not.

To achieve this you need an address in xorg.conf that will stay and point to your touchpad regardless of the mouse. In the good old days you would've had to write an UDEV-rule (like I mentioned in the bug), but it seems that now in the *by-path* you already have filenames that will stick.

Try replacing the psaux-path in your xorg.conf synaptics section with /dev/input/by-path/platform-i8042-serio-4-event-mouse and after saving restart your xorg with ctrl+alt+backspace or rebooting

good luck!

---

