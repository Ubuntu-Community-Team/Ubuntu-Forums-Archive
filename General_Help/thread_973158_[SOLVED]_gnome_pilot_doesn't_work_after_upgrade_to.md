---
title: "[SOLVED] gnome pilot doesn't work after upgrade to 8.10"
date: 2008-11-06
forum: General Help
---

### Post by underdog512 on 2008-11-06
After performing a fresh install of 8.10 I have found that I can no longer sync my palm centro w/ evolution using gnome-pilot.  I cannot get past the initial sync.  It ask me to plug the device in and press the hot sync button so it can detect setting from my device.  I do so and the computer never picks it up.

---

### Post by underdog512 on 2008-11-06
bump

---

### Post by plain_jim on 2008-11-06
First, make sure you have pilot-link installed (you can get it in the "Synaptic Package Manager" under "System/Administration").  It was installed by default in Hardy, but NOT in my Ibex install. The one you get from Synaptic works.

Then, look at this page:

[http://kaybyrd.com/?p=56](http://kaybyrd.com/?p=56)

I use jpilot (also available from Synaptic Package Manager).  I found that if I did the stuff on that page under "JPilot" and "Automatic Modprobe Visor", jpilot did fine (you have to start the sync at the handheld first, then click the jpilot sync icon).  On my last install, I also got Evolution to sync, but I had duplicate-entry weirdness, so I went back to jpilot.  The only thing I wish jpilot had is datebook categories, but I'm not able to program 'em myself, and I don't know how to ask for 'em (for a reasonable amount of $$$, I might even pay for the feature!).

Anyway, enough rambling and malcontentery.  Make sure pilot-link is installed, and then do the stuff on the kaybyrd page.  (My "serial port" under the jpilot file/preferences/settings is /dev/ttyUSB1, but YMMV.)

---

### Post by underdog512 on 2008-11-08
This is a reported bug in intrepid. I am posting the link to the bug report below. It contains a workaround for this issue.

[https://bugs.launchpad.net/gnome-pilot/+bug/282491](https://bugs.launchpad.net/gnome-pilot/+bug/282491)

Be advised that when you restart, you will have to apply this fix again.  Monitor the report for more info.

---

### Post by celem on 2008-11-09
[NOT SOLVED] as far as I can tell.

I have loaded the proposed version of gnome-pilot 2.0.15-2ubuntu4. I set the gnome-pilot Device Settings to Type USB and Device usb: When I hotsync nothing happens. The system does see the PDA - see pasted lsusb output below.

FOLLLOWING: output of lsusb when HotSync is pressed on Clie PEG SJ-22/U
ecomer@squirrel:~$ lsusb
Bus 004 Device 002: ID 18e3:9101 Fitipower Integrated Technology Inc 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 054c:0066 Sony Corp. Clie PEG-N7x0C/PEG-T425 PalmOS PDA Serial
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any ideas?

---

### Post by wyrless2002 on 2008-11-09
Have you rebooted? It didn't actually work properly for me until I rebooted last night, but it did work. The one guy in the launchpad thread said the same thing. I also went back and removed visor from /etc/modules because I got an error message, **after** a successful 'sync, saying (from what I remember) that I was trying to connect with USB, but had loaded the "old" visor module unnecessarily. What are you seeing in your syslog? (/var/log/syslog)

---

### Post by celem on 2008-11-09
Yes, I have rebooted - no change in behavior. I did try modprobe visor and that permitted me to sync to jpilot via /dev/ttyUSB1 but gpilot failed. It would start, fetched the PDA name and then aborted. I removed visor and all is as it was, i.e., no sync possible with jpilot of gnome-pilot.

When I press HotSync /var/log/syslog tails the following:

Nov  9 18:37:05 squirrel kernel: [  341.940028] usb 2-3: new full speed USB device using ohci_hcd and address 8
Nov  9 18:37:06 squirrel kernel: [  342.153980] usb 2-3: configuration #1 chosen from 1 choice
Nov  9 18:37:18 squirrel kernel: [  354.474584] usb 2-3: USB disconnect, address 8
Nov  9 18:37:48 squirrel kernel: [  384.284028] usb 2-3: new full speed USB device using ohci_hcd and address 9
Nov  9 18:37:48 squirrel kernel: [  384.498009] usb 2-3: configuration #1 chosen from 1 choice

---

### Post by underdog512 on 2008-11-09
try the following and see if you can sync

```
sudo /etc/init.d/hal stop
killall gpilotd
/usr/bin/gpilotd 
sudo /etc/init.d/hal start
```

this will not work after a restart but it give you an idea if the proposed fix will work or not.

---

### Post by celem on 2008-11-09
No. I tried it twice, and all that happens is that the following as output from gpilotd:

...
(gpilotd:6936): libgpilotdcm-WARNING **: Number of PDAs is configured to 0
gpilotd-Message: Watching Cradle (usb:)
gpilotd-Message: corba: set_user_info(cradle=Cradle,survival=0,timeout=0
gpilotd-Message: corba:               device = Cradle,
gpilotd-Message: corba:               user_id = 1000,
gpilotd-Message: corba:               user    = Edward Comer)
gpilotd-Message: assigned handle num 2
gpilotd-Message: Found 4766, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0502, 0736
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 091e, 0004
...
gpilotd-Message: setting PILOTRATE=57600

(gpilotd:6936): gpilotd-WARNING **: An error occurred while getting the PDA's system data

(gpilotd:6936): gpilotd-WARNING **: error -201 from pi_close.
gpilotd-Message: setting PILOTRATE=57600

(gpilotd:6936): gpilotd-WARNING **: An error occurred while getting the PDA's system data
...

---

### Post by echovolutionx on 2008-11-09
:confused:

---

### Post by underdog512 on 2008-11-09
is this your first time syncing this device a PC?

---

### Post by celem on 2008-11-09
This Sony Clie SJ-22 syncs just fine to a Windows machine, and continues to do so. Also, if I modprobe visor, jpilot will sync to it at ttyUSB1. However, the usb: does not work with jpilot and nothing works with gnome-pilot with either the 8.10 release gnome-pilot 2.0.15-2ubuntu3 or the intrepid-proposed gnome-pilot 2.0.15-2ubuntu4.

As reported above in this thread, the device is seen by the kernel but gnome-pilot remains blind to it.

---

### Post by celem on 2008-11-09
Back in Dapper, or maybe earlier, I was able to get my Clie (yes, it is that old) to sync only after modifying /etc/udev/rules.d/60-symlinks.rules. This was because the Clie's string is different than what was in the rules:

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", SYMLINK+="pilot"

However, this doesn't seem to utilized by the new HAL arrangement. I say this because if this rule was used, the link would be ttyUSB*, which it is not for a usb: sync. I am afraid that I don't know where to look now that the usev rules.d pattern doesn't seem to even be used??

---

### Post by underdog512 on 2008-11-10
I was just taking another look at the bug report and seems someone else is having the same problem you having.  They just posted about an hour ago.  It might be worth a look.

[https://bugs.launchpad.net/gnome-pilot/+bug/282491](https://bugs.launchpad.net/gnome-pilot/+bug/282491)

---

### Post by celem on 2008-11-10
I am among the posters to that launchpad thread (Ed Comer there). So far, no solution has been identified.

---

### Post by celem on 2008-11-11
[WORKAROUND-BUT NOT SOLVED] The launchpad reported bug ( [http://tinyurl.com/56ndem](http://tinyurl.com/56ndem) ) has been recently expanded but is, currently, not fixed for USB: device name and Clie SJ-22 PDA.

However, with Matt Davey's help, I have a functional workaround for the broken "usb:" device.

This setup works with my Sony SJ-22 and gnome-pilot:
- visor module was loaded.
- the USB radio button pressed
- the device name is /dev/ttyUSB1

I'll use this method until "usb:" is less buggy. I still would like for it to work the "right" way, namely "usb:", if only to make Ubuntu a more "ready for the masses" OS and will stand ready to try any other tests.

---

