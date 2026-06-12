---
title: "Sycning Palm Zire 72 -almost- works -- Please help!"
date: 2010-02-10
forum: Hardware
---

### Post by mpemburn on 2010-02-10
Hi All,

Trying to get a Ubuntu 9.10 (Studio) laptop to work for my wife to use as her main machine so, you know, it's got to *work*.  Latest problem is with syncing a Palm device.

She has an old Palm Zire 72 that uses a USB to sync.  I set up the System/Preferences/PalmOS Devices as follows:

Type: USB
Timeout: 2
Device: /dev/pilot
Speed: 57600

On first try, it complained that 'visor' wasn't loaded so after adding this to /etc/modules and restarting, I was able to get it to sync in JPilot.  Great!, sez I.  Except, compared with what she's used to, JPilot is pretty amateur looking (sorry, it's true).  I looked around a little and found Kontact and KPilot.  KPilot is set up as:

Device: /dev/pilot
Speed: 57600
Workarounds: Zire 31, 72, Tungsten T5
Pilot user: <her Palm username>

When I first tried KPilot, it caused the Zire to crash with a Fatal Exception.  I've been able to get this to stop after a couple of 'warm' resets, but the KPilot still complains that it can't see the device /dev/pilot.  Any advice?

Thanks in advance,

Mark

---

### Post by mpemburn on 2010-02-13
Anyone?

---

### Post by celem on 2010-06-04
While you may not like jpilot, they are the most active group currently involved with the Palm devices. Personally I love jpilot and use it every day, many times a day. Its interface is pretty much a copy of Palm's desktop client, as far as functionality goes. Jpilot has something that no other solution offers that is critical for me and is a major reason why I use it - it provides desktop support for the Keyring for Palm OS Palm software ([http://gnukeyring.sourceforge.net/]("http://gnukeyring.sourceforge.net/")). This password manager is critical for me as I have hundreds of passwords to keep track of. Jpilot flawlessly synce with the Palm and keeps the KeyRings on the desktop and the Palm in sync, in addition to syncing the calendar, etc. Go to [http://www.jpilot.org/]("http://www.jpilot.org/") and read the mailing list archive, or join the maining list and post your questions.

---

