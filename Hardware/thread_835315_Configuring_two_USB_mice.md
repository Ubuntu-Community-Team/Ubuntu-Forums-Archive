---
title: "Configuring two USB mice"
date: 2008-06-20
forum: Hardware
---

### Post by jsundqui on 2008-06-20
I've got two mice, and both work, but one has way too much acceleration.  I can't set the acceleration separately.

I've searched quite a bit, and everyone suggests setting up separate mouse sections (e.g. mouse0 and mouse1) in xorg.conf.  Right now, I only have one setting:

```
Section "InputDevice"
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

I can add a second stanza, but here's where I am confused.

First of all, the first mouse I had (when I set up the box) was always a USB (this box doesn't even have PS/2 ports), but xorg calls it /dev/psaux anyways, and it works.

Second, what would the second mouse be anyway?  I have a /dev/input/mice and /dev/input/mouse0 through /dev/input/mouse3

I don't think I should pick randomly ;-) 

I'm an old school linux-er and not too up on event-driven devices (it's a great feature; need to learn more).

under /dev/input/by-id I have:

```
user@box:/dev/input/by-id$ ls
usb-Dell_Dell_USB_Keyboard-event-kbd
usb-Logitech_USB_RECEIVER-event-mouse
usb-Logitech_USB_RECEIVER-mouse
usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-event-mouse
usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-mouse

```

Don't know if this helps any.  Obvviously one of the mice is a wireless.

Thanks in advance.

---

### Post by jsundqui on 2008-06-24
It seems I need to use udev to set a persistent device mount.

However, the stuff I see in my searches doesn't seem to work, I guess basically because of what I see here:

[http://marc.info/?l=linux-hotplug&m=118414294516395&w=2](http://marc.info/?l=linux-hotplug&m=118414294516395&w=2)

> On Tue, 2007-07-10 at 17:39 +0200, Kay Sievers wrote:

> On 7/10/07, Andreas Jellinghaus <aj@dungeon.inka.de> wrote:
> > I finally figured out what is wrong with udev on ubuntu.
> >
> > ubuntu mounts usbfs as /proc/bus/usb/.usbfs
> > and has udev create /dev/bus/usb and bind-mounts that as /proc/bus/usb.
> 
> What are theses guys smoking? That's so sick to bind-mount
> /dev-directories to /proc! I wouldn't support such a system at all. It
> is totally broken.
> 
It works <g>

What we do is mount the usbfs filesystem on /dev/bus/usb/.usbfs, and
symlink the devices file from that into the parent directory (so
that /dev/bus/usb/devices exists).

The whole lot is then bind-mounted to /proc/bus/usb; so an application
using /proc/bus/usb sees the same tree as a fixed one.

We would fix the apps, but unfortunately we don't have the source to
VMware!

Scott
-- 
Scott James Remnant
Ubuntu Development Manager
[email]scott@ubuntu.com[/email]

So I am still kind of stuck.

Any help is appreciated.

---

