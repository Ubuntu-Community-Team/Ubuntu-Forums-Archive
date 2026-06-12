---
title: "palmOne Treo 650 not showing up as USB in /dev"
date: 2009-05-20
forum: Hardware
---

### Post by brian47 on 2009-05-20
For days now I have been trying to sync my Treo 650 with no success.

The connection is with a USB cable and I am using Ubuntu 9.04.

From what I have read in other threads, I expect to see nodes like ttyUSB0 and ttyUSB1 show up when I press the HotSync button on the cable.  This does not happen, even though it did when I first started trying to get this all to work.

The computer is obviously seeing the device because as soon as I press the sync button I see messages like:

May 19 20:52:44 Lunar-Night kernel: [10292.044017] usb 4-1: new full speed USB device using uhci_hcd and address 12
May 19 20:52:44 Lunar-Night kernel: [10292.236917] usb 4-1: configuration #1 chosen from 1 choice

in the log and entries like:

crw-rw-r--  1 root   dialout   252,  32 2009-05-19 20:52 usbdev4.12_ep00
crw-rw-r--  1 root   dialout   252,  28 2009-05-19 20:52 usbdev4.12_ep81
crw-rw-r--  1 root   dialout   252,  30 2009-05-19 20:52 usbdev4.12_ep86
crw-rw-r--  1 root   dialout   252,  29 2009-05-19 20:52 usbdev4.12_ep02
crw-rw-r--  1 root   dialout   252,  31 2009-05-19 20:52 usbdev4.12_ep07

show up in /dev.

Questions:

1. Why do I see nodes like usbdev* rather than ttyUSB*?

2. How do I get it to add ttyUSB nodes so that I can write a udev rule to create a /dev/pilot link?

Any help to bring down my frustration level would be greatly appreciated.

Brian

---

### Post by kwtm2 on 2010-03-16
I have a related but not identical problem.  I plug my Treo650 into the USB port and sync (using pilot-xfer or J-pilot) but it just waits and then gives an error message, which varies depending on the situation.

At first I thought it was a timing thing: when I press the Hotsync button (either on the special USB cable or on the Treo Hotsync screen), only then does the USB port appear.  (Actually, two USB ports appear: /dev/ttyUSB0 and /dev/ttyUSB1.)  So I tried running J-pilot/pilot-xfer anywhere from -2 to +2 seconds after I press Hotsync, but no dice.  Then I modified the /etc/udev/rules.d/50-MyOwnRules to say:

BUS="usb", ATTRS{product}="Palm*", KERNEL="ttyUSB*", NAME{ignore_remove}="%k", SYMLINK{ignore_remove}="treo", MODE="666"

When I did this, the first time after rebooting that I plugged in the Treo, the two ports ttyUSB0 and ttyUSB1 appeared and did not disappear afterward as it usually did.  I was able to sync!  But then when I plugged in the Treo again, this time ttyUSB2 and ttyUSB3 appeared, and then disappeared after.  And of course I failed to sync.

I even wrote a script to check 10 times a second to see if the new ttyUSB ports appeared, and then as soon as they appeared, the computer would sync!  But then a new error message came: I didn't have permission to use the ports.  Yes, I am a member of group plugdev, as well as: "adm dialout cdrom floppy audio dip video plugdev users scanner lpadmin crontab admin mythtv"

Someone please help.  I am desperate to sync my Treo (which worked before, actually).  I am using Hardy Heron, for which there should be support until at least next year.

Also, if you don't mind, I'd like to ask a favour of those who do help me, just so I can gain the most benefit from your effort.  For some people there will be the temptation of telling me to use a newer version of Ubuntu, and everything will be fine, or something to that effect.  Please resist that temptation.  I am using the newest LTS version already.  Thanks.

Also, I use KDE3 on Kubuntu, so it would be great if you could describe the solution in terms of command-line/bash commands, it would be applicable to both GNOME and KDE (3 and 4).

---

