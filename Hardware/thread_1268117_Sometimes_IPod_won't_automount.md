---
title: "Sometimes IPod won't automount"
date: 2009-09-16
forum: Hardware
---

### Post by Farfurkis on 2009-09-16
Sometimes, without any sequence my IPod nano 2Gb not automounted after connectiong. The follow message appears:

**    Can't mount the volume**
    Cant mount 'IPOD FARFURK'
Details:
  mount: /dev/sdc2 already mounted or /media/IPOD FARFURK busy

[IMG]http://farfurkis.googlepages.com/Cant_mount_the_volume.png[/IMG]

===== syslog =====
[FONT=Courier New]Sep 16 08:48:30 farfurkis-desktop kernel: [  407.669049] usb 1-7: new high speed USB device using ehci_hcd and address 3
Sep 16 08:48:30 farfurkis-desktop kernel: [  407.811684] usb 1-7: configuration #1 chosen from 2 choices
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.007816] Initializing USB Mass Storage driver...
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.009178] scsi4 : SCSI emulation for USB Mass Storage devices
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.011424] usb-storage: device found at 3
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.011428] usb-storage: waiting for device to settle before scanning
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.011438] usbcore: registered new interface driver usb-storage
Sep 16 08:48:31 farfurkis-desktop kernel: [  408.011441] USB Mass Storage support registered.
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.016024] usb-storage: device scan complete
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.018737] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.020728] sd 4:0:0:0: [sdc] 991232 2048-byte hardware sectors: (2.03 GB/1.89 GiB)
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.022720] sd 4:0:0:0: [sdc] Write Protect is off
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.022722] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.022724] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.024612] sd 4:0:0:0: [sdc] 991232 2048-byte hardware sectors: (2.03 GB/1.89 GiB)
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.025720] sd 4:0:0:0: [sdc] Write Protect is off
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.025722] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.025724] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.025727]  sdc: sdc1 sdc2
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.028793] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Sep 16 08:48:36 farfurkis-desktop kernel: [  413.028859] sd 4:0:0:0: Attached scsi generic sg3 type 0
Sep 16 08:50:01 farfurkis-desktop /USR/SBIN/CRON[5110]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)[/FONT]

IPod mounting will work when i do it manually:
[FONT=Courier New]sudo mount /dev/sdc2 /tmp/ipod[/FONT]
After this command ipod automouted correctly.

What shall I do with my Ubunttu 9.04 to make IPod automounting work fine?

---

### Post by Farfurkis on 2009-09-30
I founded that each time when I connect my IPod and it's fails, the follow lines appears in auth.log:
[FONT=Courier New]
Sep 30 08:45:46 farfurkis-desktop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=4343 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.53" (uid=1000 pid=6120 comm="gnome-mount -b -d /dev/sdc2 "))
Sep 30 08:45:46 farfurkis-desktop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=4343 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.54" (uid=0 pid=6121 comm="/usr/lib/hal/hal-storage-mount "))[/FONT]

Problem is solved simply by wait a few minutes - and retry to mount the device.

---

