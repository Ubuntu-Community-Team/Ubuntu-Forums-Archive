---
title: "Bluetooth Input Devices (Edgy)"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Roger Mudd on 2006-10-26
I have a Logitech MX5000 bluetooth keyboard/mouse combo that worked perfectly in Dapper. Just upgraded to Edgy and now neither will work. I attempted to follow the instructions [here]("https://help.ubuntu.com/community/BluetoothSetup"), but was unable to detect either of these devices. Anybody have any experience with a similar issue? Any solutions out there. My searches of this forum turned up little. Mostly posts about pairing phones, etc.

Thanks,
Roger

---

### Post by Roger Mudd on 2006-10-27
Quick update...
Still trying. Downloaded the install CD with the intention of attempting a fresh install. When the Live CD loaded I was able to use my bluetooth mouse but not my keyboard. Couldn't get my machine to detect the keyboard despite my best efforts. Halfway there, but a bit of a disappointment that hardware detection has regressed from Dapper to Edgy (in my case).
Any input is greatly appreciated.

---

### Post by Roger Mudd on 2006-10-28
Another update...
Looks like this is a relatively common issue. And a [bug report]("https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415") has already been filed. My "solution" was to revert back to Dapper with a fresh install. My bluetooth keyboard/mouse combo are working perfectly again (aside from not being recognized in GRUB). Hopefully this gets sorted out.

---

### Post by seaward on 2006-10-29
I have the exact mouse / keyboard combination as you.  Neither were working when I first reached the Ubuntu login screen.  I managed to sort of fix the issue by pulling out my bluetooth dongle and then reinserting it into a different USB port.  For some reason this causes Edgy to then recognise my input devices.

Very odd indeed.

Whats even weirder is that running "hcitool scan" gives me an error message:
"Device is not available: No such device"

What on earth is going on here?

---

### Post by didobuntu on 2006-10-29
> **seaward said:**
> I have the exact mouse / keyboard combination as you.  Neither were working when I first reached the Ubuntu login screen.  I managed to sort of fix the issue by pulling out my bluetooth dongle and then reinserting it into a different USB port.  For some reason this causes Edgy to then recognise my input devices.

Very odd indeed.

Whats even weirder is that running "hcitool scan" gives me an error message:
"Device is not available: No such device"

What on earth is going on here?

I have this message too .. but my bluetooth mouse runs ...
Did you follow [this]("https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29") howto ? for it helped me to install my mouse

---

### Post by Roger Mudd on 2006-10-29
Didobuntu,
Thanks for the response. I linked to that page in my original post. I could not get my machine to recognize the mouse or keyboard using those instructions. A fresh install of Edgy enabled my mouse, but not the keyboard. I have read that people are able to get temporary functionality by unplugging the Bluetooth dongle and plugging it back in. For me, however, this is more of a workaround than a fix. I don't want to have to go through this each time I boot my machine.

---

### Post by The J on 2006-10-31
I have this problem too with my MX5000 set.  I can unplug the Bluetooth dongle from its port and plug it back in to get things working again.

Oddly enough, the keyboard and mouse both work fine if I start in Recovery Mode and then start gdm.

---

### Post by pimlottc on 2006-11-06
I'm also using the MX 5000 keyboard/mouse combo (any one get theirs off woot? :) ) and having problems, but not quite the same.

In general, they work.  The main problem is at times the mouse will just stop working for a minute or two, and then it just starts back up.  This is very irritating and obviously a big impairment to getting things done.

I also find that the keyboard seems somewhat "laggy", in that there is seems to be a decent amount of jitter in when the characters actually arrive on the screen.  Typing fast exacerbates the problem.  It might be a cpu usage problem; it feels similar to when you try to type on a wired keyboard when a computer is severely overloaded, but this occurs at all times, most of which have a low overall cpu usage going on.

Since this thread has attracted a fair number of us using the same hardware, I'd be interested to see if anyone else is seeing these other symptoms.

I'll try the suggestion of getting rid of those additional bluez packages.  I really don't want to have to go back to Dapper, though...

---

### Post by stfu on 2006-11-06
I have MX5000 desktop and it's been working in edgy for some time. The mouse tends to lag a lot and keyboard gives an extra symbol after "waking up" after a pause in typing. Latter problem is reported to be a feature in windows too. I haven't had disconnected mouse or keyboard with MX5000. Used to have MX900 desktop which I was perfectly happy with. This new one sucks compared to the old one.

Anyways, have you added your devices in you /etc/default/bluetooth
like so:
```

HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:01:02:03:04:05 --connect 00:01:02:03:04:05 --master --server"

```

and same thingies in /etc/rc.local if for some reason they're not detected in bootup.
```

hidd --server --connect 00:00:00:00:00:00 --connect 00:00:00:00:00:00

```

---

### Post by thelostsoul on 2006-11-16
I've tried just about everything, but Ubuntu won't detect my bluetooth dongle.  Lsusb shows it there:
Bus 004 Device 018: ID 046d:c70a Logitech, Inc. 
Bus 004 Device 017: ID 046d:c70e Logitech, Inc. 
Bus 004 Device 016: ID 046d:0b02 Logitech, Inc. 

(2 are the mouse and keyboard, one is the dongle.)

But hcitool dev is empty, and -s gives a no such device error.

I don't know what to do, at all.

---

### Post by jrickard on 2006-12-10
Good fix.  I had the same problem.  I could link up with keyboard and mouse (once new batteries were installed) but it wouldn't come up that way.

HIDD-1 in file /etc/default/bluetooth fixed it completely.  Apparently this file replaces /etc/default/bluez-pan which was used in previous releases.  If you upgraded, you will need to DELETE the bluez-pan file for the bluetooth file to have effect.

Jack Rickard

---

### Post by matt221984 on 2007-01-21
If you have a problem with the MX5000 bluetooth keyboard/mouse combo try removing the bluez packages

sudo apt-get remove bluez-cups bluez-pcmcia-support bluez-pin bluez-utils

worked for me.

---

