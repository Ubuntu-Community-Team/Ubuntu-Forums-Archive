---
title: "M1530 Trackpad scrolling"
date: 2008-06-30
forum: Hardware
---

### Post by OMGsplosion on 2008-06-30
Hi. When I first installed 64-bit Hardy onto this machine the trackpad initially wasn't working. After a bit of googling I found out I had to add i8042.nomux=1 to the kernel cause mine was BIOS vesion A08.
Well everything went fine for a while and then suddenly I couldn't scroll by dragging along the edge anymore.  The scrolling area now just acts as a regular trackpad. Also, the Trackpad settings tab under 'Mouse' had disappeared in System->Preferences->Mouse.

Is there anyway to make Ubuntu recognise my trackpad and its scrolling function again (or force it to)? I've tried various xorg configs but no luck so far.
Here's what it looks like right now anyway.

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

I was wondering because I occasionally use an ordinary USB mouse maybe that affects it. I have the synaptics driver installed according to the synaptic package manager. When I run the command below, I see its an ALPS glidepoint, is that different from a Synaptics trackpad?

```
delicious@Tachikoma:~$ sudo cat /proc/bus/input/devices
I: Bus=0011 Vendor=0002 Product=0001 Version=7321
N: Name="PS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3


```

I would really appreciate some help.

---

### Post by kessaris on 2008-06-30
In my version of Ubuntu (Hardy Heron/Gnome), there is a separate control panel for the touchpad, it's in System->Preferences->Touchpad.

Although vertical scrolling should be enabled by default, if that control panel refuses to load, it's a sign that something is fishy.

Try checking that control panel.

Additionally, I did find that my touchpad didn't work properly until I added the kernel boot option i8042.noloop=1

Just for the record, vertical scrolling is actually quite fickle, I'd say it works about half the time on my machine for whatever reason.  I've gotta really concentrate for it to work properly.

I'd be very interested to know if this information is helpful, because it seems that these touchpads are one of the major small frustrations that plague a large number of laptop users.

Here is a thread you might find interesting! [http://ubuntuforums.org/showthread.php?t=840596](http://ubuntuforums.org/showthread.php?t=840596)

---

### Post by OMGsplosion on 2008-06-30
Thanks for the reply.

I had tried to open system->preferences->touchpad but it gave me this error:
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```
I had added a new line to my xorg to set SHMConfig to true at the synaptics input device, yet to no avail.
In addition, I added i8042.noloop=1 to GRUB's menu.lst but that didn't work either :(
With regards to [the thread you had suggested]("http://ubuntuforums.org/showthread.php?t=840596") it also didn't work.
I have a feeling I must have messed up somewhere real bad...

---

