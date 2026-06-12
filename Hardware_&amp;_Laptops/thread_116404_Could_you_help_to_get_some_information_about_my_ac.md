---
title: "Could you help to get some information about my acpi events?"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by André on 2006-01-12
Hi everybody,

i am running Ubuntu Breezy on my nice Inspiron 8600.

Suspend - to - RAM works a little bit too well here: When i suspend everything is fine but after a few hours it resumes for itself :-)

I type stopped the acpid deamon and triggered the command ```
acpid -d
``` to get some information about which event may make itself resume. Then i started the acpid daemon again an here is the result:

> root@watson:~# acpid -d
[Thu Jan 12 19:38:21 2006] starting up
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/ac
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/sony-brightne ss-up
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/tosh-brightne ss-down
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/tosh-wireless
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/asus-media-ej ect
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/ibm-wireless
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/tosh-brightne ss-up
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/panasonic-bri ghtness-up
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-u p
[Thu Jan 12 19:38:21 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-d own
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-m ute
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/ibm-videobtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/panasonic-sle epbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-media
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-sleep
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-volume-d own
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/ibm-lockbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-media-pl ay-pause
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-hibernat e
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/ibm-hibernate btn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/panasonic-bri ghtness-down
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/powerbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-sleep
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/lidbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sleepbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-brightne ss-down
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-mute
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-wireless
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-lock
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-next
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-mute
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-play
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-prev
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-stop
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/sony-volume-u p
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-mail
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-lock
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/battery
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-touchpad
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/tosh-hibernat e
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/panasonic-hib ernatebtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-media-ne xt
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-media-pr ev
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-media-st op
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/asus-internet
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/panasonic-loc kbtn
[Thu Jan 12 19:38:22 2006] DBG: parsing conf file /etc/acpi/events/ibm-sleepbtn
[Thu Jan 12 19:38:22 2006] 47 rules loaded
[Thu Jan 12 19:38:44 2006] received event "button/sleep SBTN 00000080 00000001"
[Thu Jan 12 19:38:44 2006] DBG: rule from /etc/acpi/events/sleepbtn matched
[Thu Jan 12 19:38:44 2006] executing action "/etc/acpi/sleep.sh"
[Thu Jan 12 19:38:44 2006] BEGIN HANDLER MESSAGES


All this stuff happens when i suspended at twenty to eight in the evening via my function keys. Then follows:

> screensaver-command: throttled.

xscreensaver-command: activating and locking.

/etc/acpi/resume.sh: line 6: 17092 Speicherzugriffsfehler  vbetool post
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:74:c6:4c
Sending on   LPF/wlan0/00:90:4b:74:c6:4c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.102 -- renewal in 268155 seconds.
xscreensaver-command: deactivating.

grep: /proc/acpi/fan/*/state: Datei oder Verzeichnis nicht gefunden
[Thu Jan 12 20:52:01 2006] END HANDLER MESSAGES
[Thu Jan 12 20:52:01 2006] action exited with status 0
[Thu Jan 12 20:52:01 2006] DBG: 1 total rule matched
[Thu Jan 12 20:52:01 2006] completed event "button/sleep SBTN 00000080 00000001"
[Thu Jan 12 20:52:01 2006] received event "ac_adapter AC 00000080 00000001"
[Thu Jan 12 20:52:01 2006] DBG: rule from /etc/acpi/events/ac matched
[Thu Jan 12 20:52:01 2006] executing action "/etc/acpi/power.sh"
[Thu Jan 12 20:52:01 2006] BEGIN HANDLER MESSAGES
[Thu Jan 12 20:52:01 2006] END HANDLER MESSAGES
[Thu Jan 12 20:52:01 2006] action exited with status 0
[Thu Jan 12 20:52:01 2006] DBG: 1 total rule matched
[Thu Jan 12 20:52:01 2006] completed event "ac_adapter AC 00000080 00000001"
[Thu Jan 12 20:52:01 2006] client connected from 6901[111:111]
[Thu Jan 12 20:52:01 2006] 1 client rule loaded
[Thu Jan 12 20:52:03 2006] received event "button/lid LID 00000080 00000001"
[Thu Jan 12 20:52:03 2006] DBG: rule from 6901[111:111] matched
[Thu Jan 12 20:52:03 2006] notifying client 6901[111:111]
[Thu Jan 12 20:52:03 2006] DBG: rule from /etc/acpi/events/lidbtn matched
[Thu Jan 12 20:52:03 2006] executing action "/etc/acpi/lid.sh"
[Thu Jan 12 20:52:03 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: no response to command.
xscreensaver-command: no response to command.
[Thu Jan 12 20:52:24 2006] END HANDLER MESSAGES
[Thu Jan 12 20:52:24 2006] action exited with status 1
[Thu Jan 12 20:52:24 2006] DBG: 2 total rules matched
[Thu Jan 12 20:52:24 2006] completed event "button/lid LID 00000080 00000001"
[Thu Jan 12 20:52:24 2006] received event "battery BAT0 00000080 00000001"
[Thu Jan 12 20:52:24 2006] DBG: rule from 6901[111:111] matched
[Thu Jan 12 20:52:24 2006] notifying client 6901[111:111]
[Thu Jan 12 20:52:24 2006] DBG: rule from /etc/acpi/events/battery matched
[Thu Jan 12 20:52:24 2006] executing action "/etc/acpi/power.sh"
[Thu Jan 12 20:52:24 2006] BEGIN HANDLER MESSAGES
[Thu Jan 12 20:52:24 2006] END HANDLER MESSAGES
[Thu Jan 12 20:52:24 2006] action exited with status 0
[Thu Jan 12 20:52:24 2006] DBG: 2 total rules matched
[Thu Jan 12 20:52:24 2006] completed event "battery BAT0 00000080 00000001"


There is some stuff about the battery (i had the power cable plugged in and it reloaded so i think these events where triggered.

Now comes the resuming part (i think... but i am not quite sure :-():

> 
[Thu Jan 12 21:04:40 2006] received event "battery BAT0 00000080 00000001"
[Thu Jan 12 21:04:40 2006] DBG: rule from 6901[111:111] matched
[Thu Jan 12 21:04:40 2006] notifying client 6901[111:111]
[Thu Jan 12 21:04:40 2006] DBG: rule from /etc/acpi/events/battery matched
[Thu Jan 12 21:04:40 2006] executing action "/etc/acpi/power.sh"
[Thu Jan 12 21:04:40 2006] BEGIN HANDLER MESSAGES
[Thu Jan 12 21:04:40 2006] END HANDLER MESSAGES
[Thu Jan 12 21:04:40 2006] action exited with status 0
[Thu Jan 12 21:04:40 2006] DBG: 2 total rules matched
[Thu Jan 12 21:04:40 2006] completed event "battery BAT0 00000080 00000001"
[Thu Jan 12 21:04:40 2006] received event "battery BAT0 00000080 00000001"
[Thu Jan 12 21:04:40 2006] DBG: rule from 6901[111:111] matched
[Thu Jan 12 21:04:40 2006] notifying client 6901[111:111]
[Thu Jan 12 21:04:40 2006] DBG: rule from /etc/acpi/events/battery matched
[Thu Jan 12 21:04:40 2006] executing action "/etc/acpi/power.sh"
[Thu Jan 12 21:04:40 2006] BEGIN HANDLER MESSAGES
[Thu Jan 12 21:04:40 2006] END HANDLER MESSAGES
[Thu Jan 12 21:04:40 2006] action exited with status 0
[Thu Jan 12 21:04:40 2006] DBG: 2 total rules matched
[Thu Jan 12 21:04:40 2006] completed event "battery BAT0 00000080 00000001"


There is some stuff about the battery again. But what may have happened there? Any ideas? I am a bit confused. The power cable was plugged in all the time.

When i came back home i reopened the lid and finally got:
> 
[Thu Jan 12 22:26:40 2006] received event "button/lid LID 00000080 00000002"
[Thu Jan 12 22:26:40 2006] DBG: rule from 6901[111:111] matched
[Thu Jan 12 22:26:40 2006] notifying client 6901[111:111]
[Thu Jan 12 22:26:40 2006] DBG: rule from /etc/acpi/events/lidbtn matched
[Thu Jan 12 22:26:40 2006] executing action "/etc/acpi/lid.sh"
[Thu Jan 12 22:26:40 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: not throttled.

xscreensaver-command: deactivating.

[Thu Jan 12 22:26:41 2006] END HANDLER MESSAGES
[Thu Jan 12 22:26:41 2006] action exited with status 1
[Thu Jan 12 22:26:41 2006] DBG: 2 total rules matched
[Thu Jan 12 22:26:41 2006] completed event "button/lid LID 00000080 00000002"


This just seems to be the lid event here.

There are a few messaged about the battery state but i do not really know what they mean. The self resuming also happens when i have no power cable plugged in at all and welcomes me in the morning with a nice and completely discharged battery and some reiserfs partitions who have to repair themselves :-(

I really would like to get this working. Any ideas? Answers are appreciated!!

Greetings
André

---

### Post by André on 2006-01-13
So here comes the same stuff with the power cable unplugged like this (turned on after 20 minutes :-():

> 
root@watson:~# acpid -d
[Fri Jan 13 06:10:31 2006] starting up
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ac
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-brightne ss-up
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-brightne ss-down
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-wireless
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-media-ej ect
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ibm-wireless
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-brightne ss-up
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/panasonic-bri ghtness-up
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-u p
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-d own
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-volume-m ute
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ibm-videobtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/panasonic-sle epbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-media
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-sleep
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-volume-d own
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ibm-lockbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-media-pl ay-pause
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-hibernat e
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ibm-hibernate btn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/panasonic-bri ghtness-down
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/powerbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-sleep
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/lidbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sleepbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-brightne ss-down
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-mute
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-wireless
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-lock
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-next
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-mute
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-play
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-prev
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-stop
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/sony-volume-u p
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-mail
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-lock
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/battery
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-touchpad
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/tosh-hibernat e
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/panasonic-hib ernatebtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-media-ne xt
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-media-pr ev
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-media-st op
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/asus-internet
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/panasonic-loc kbtn
[Fri Jan 13 06:10:31 2006] DBG: parsing conf file /etc/acpi/events/ibm-sleepbtn
[Fri Jan 13 06:10:31 2006] 47 rules loaded
[Fri Jan 13 06:11:27 2006] received event "button/sleep SBTN 00000080 00000001"
[Fri Jan 13 06:11:27 2006] DBG: rule from /etc/acpi/events/sleepbtn matched
[Fri Jan 13 06:11:27 2006] executing action "/etc/acpi/sleep.sh"
[Fri Jan 13 06:11:27 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: throttled.

xscreensaver-command: activating and locking.

/etc/acpi/resume.sh: line 6: 11282 Speicherzugriffsfehler  vbetool post
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:74:c6:4c
Sending on   LPF/wlan0/00:90:4b:74:c6:4c
Sending on   Socket/fallback
xscreensaver-command: deactivating.

grep: /proc/acpi/fan/*/state: Datei oder Verzeichnis nicht gefunden
[Fri Jan 13 06:33:45 2006] END HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] action exited with status 0
[Fri Jan 13 06:33:45 2006] DBG: 1 total rule matched
[Fri Jan 13 06:33:45 2006] completed event "button/sleep SBTN 00000080 00000001"
[Fri Jan 13 06:33:45 2006] received event "ac_adapter AC 00000080 00000000"
[Fri Jan 13 06:33:45 2006] DBG: rule from /etc/acpi/events/ac matched
[Fri Jan 13 06:33:45 2006] executing action "/etc/acpi/power.sh"
[Fri Jan 13 06:33:45 2006] BEGIN HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] END HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] action exited with status 0
[Fri Jan 13 06:33:45 2006] DBG: 1 total rule matched
[Fri Jan 13 06:33:45 2006] completed event "ac_adapter AC 00000080 00000000"
[Fri Jan 13 06:33:45 2006] client connected from 6881[111:111]
[Fri Jan 13 06:33:45 2006] 1 client rule loaded
[Fri Jan 13 06:33:45 2006] received event "ac_adapter AC 00000080 00000000"
[Fri Jan 13 06:33:45 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:33:45 2006] notifying client 6881[111:111]
[Fri Jan 13 06:33:45 2006] DBG: rule from /etc/acpi/events/ac matched
[Fri Jan 13 06:33:45 2006] executing action "/etc/acpi/power.sh"
[Fri Jan 13 06:33:45 2006] BEGIN HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] END HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] action exited with status 0
[Fri Jan 13 06:33:45 2006] DBG: 2 total rules matched
[Fri Jan 13 06:33:45 2006] completed event "ac_adapter AC 00000080 00000000"
[Fri Jan 13 06:33:45 2006] received event "battery BAT0 00000080 00000001"
[Fri Jan 13 06:33:45 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:33:45 2006] notifying client 6881[111:111]
[Fri Jan 13 06:33:45 2006] DBG: rule from /etc/acpi/events/battery matched
[Fri Jan 13 06:33:45 2006] executing action "/etc/acpi/power.sh"
[Fri Jan 13 06:33:45 2006] BEGIN HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] END HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] action exited with status 0
[Fri Jan 13 06:33:45 2006] DBG: 2 total rules matched
[Fri Jan 13 06:33:45 2006] completed event "battery BAT0 00000080 00000001"
[Fri Jan 13 06:33:45 2006] received event "battery BAT0 00000080 00000001"
[Fri Jan 13 06:33:45 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:33:45 2006] notifying client 6881[111:111]
[Fri Jan 13 06:33:45 2006] DBG: rule from /etc/acpi/events/battery matched
[Fri Jan 13 06:33:45 2006] executing action "/etc/acpi/power.sh"
[Fri Jan 13 06:33:45 2006] BEGIN HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] END HANDLER MESSAGES
[Fri Jan 13 06:33:45 2006] action exited with status 0
[Fri Jan 13 06:33:45 2006] DBG: 2 total rules matched
[Fri Jan 13 06:33:45 2006] completed event "battery BAT0 00000080 00000001"
[Fri Jan 13 06:33:45 2006] received event "processor CPU0 00000080 00000007"
[Fri Jan 13 06:33:45 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:33:45 2006] notifying client 6881[111:111]
[Fri Jan 13 06:33:45 2006] DBG: 1 total rule matched
[Fri Jan 13 06:33:45 2006] completed event "processor CPU0 00000080 00000007"
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.102 -- renewal in 259248 seconds.
[Fri Jan 13 06:33:51 2006] received event "button/lid LID 00000080 00000001"
[Fri Jan 13 06:33:51 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:33:51 2006] notifying client 6881[111:111]
[Fri Jan 13 06:33:51 2006] DBG: rule from /etc/acpi/events/lidbtn matched
[Fri Jan 13 06:33:51 2006] executing action "/etc/acpi/lid.sh"
[Fri Jan 13 06:33:51 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: no response to command.
xscreensaver-command: no response to command.
xscreensaver-command: no response to command.
[Fri Jan 13 06:34:12 2006] END HANDLER MESSAGES
[Fri Jan 13 06:34:12 2006] action exited with status 1
[Fri Jan 13 06:34:12 2006] DBG: 2 total rules matched
[Fri Jan 13 06:34:12 2006] completed event "button/lid LID 00000080 00000001"
[Fri Jan 13 06:34:12 2006] received event "processor CPU0 00000080 00000002"
[Fri Jan 13 06:34:12 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 06:34:12 2006] notifying client 6881[111:111]
[Fri Jan 13 06:34:12 2006] DBG: 1 total rule matched
[Fri Jan 13 06:34:12 2006] completed event "processor CPU0 00000080 00000002"
[Fri Jan 13 08:42:44 2006] received event "battery BAT0 00000080 00000001"
[Fri Jan 13 08:42:44 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 08:42:44 2006] notifying client 6881[111:111]
[Fri Jan 13 08:42:44 2006] DBG: rule from /etc/acpi/events/battery matched
[Fri Jan 13 08:42:44 2006] executing action "/etc/acpi/power.sh"
[Fri Jan 13 08:42:44 2006] BEGIN HANDLER MESSAGES
[Fri Jan 13 08:42:44 2006] END HANDLER MESSAGES
[Fri Jan 13 08:42:44 2006] action exited with status 0
[Fri Jan 13 08:42:44 2006] DBG: 2 total rules matched
[Fri Jan 13 08:42:44 2006] completed event "battery BAT0 00000080 00000001"
[Fri Jan 13 08:43:07 2006] received event "button/lid LID 00000080 00000002"
[Fri Jan 13 08:43:07 2006] DBG: rule from 6881[111:111] matched
[Fri Jan 13 08:43:07 2006] notifying client 6881[111:111]
[Fri Jan 13 08:43:07 2006] DBG: rule from /etc/acpi/events/lidbtn matched
[Fri Jan 13 08:43:07 2006] executing action "/etc/acpi/lid.sh"
[Fri Jan 13 08:43:07 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: deactivating.

[Fri Jan 13 08:43:08 2006] END HANDLER MESSAGES
[Fri Jan 13 08:43:08 2006] action exited with status 1
[Fri Jan 13 08:43:08 2006] DBG: 2 total rules matched
[Fri Jan 13 08:43:08 2006] completed event "button/lid LID 00000080 00000002"


No ideas??? Please help...
André

---

### Post by André on 2006-01-13
Hi,

i think i found my error. I only have to slightly touch the backend of my lid and it turns on. Maybe it is some kind of lose lid.

Is there a way to turn off the waking up with the lid event? Would be enough for me to do it with the function key combination or the power button.

Greetings
Andr&#233;

---

### Post by André on 2006-01-13
Hi hi,

so i try to answer this myself:

```
echo 'LID disabled' > /proc/acpi/wakeup
```

This is what i entered nearly at the end of /etc/rc5.d/S10acpid (do not know if this is the right location but at least at works) and in /etc/acpi/resume.sh (because the boot one only worked once. That way i can only wakeup via the power button but that is okay for me.

So i try if this is the problem here and report back.

Greetings
Andr&#233;

---

### Post by André on 2006-01-14
okay,

this really works. No waking up anymore :-)

Happy Greetings
André

---

