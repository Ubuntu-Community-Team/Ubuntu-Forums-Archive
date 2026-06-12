---
title: "Mounting a USB external tera byte HD"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Silvernail on 2009-11-01
I have just upgraded from 9.04 to .10.

Under 04, icon on desktop and my USB external hard drive was mounted such:
dafy@Dafy: /media/disk$

Under 10, no icon and it is mounted such:
dafy@Dafy:/media/44fb04a3-444f-411c-8b07-98c4fd58686f$ 
*Let meedit this, No icons after upgrade and restart. This morning, icons on desktop*

If I am using a GUI, this is not such a problem. If I am using command line, then this can be a hassle.

How/What do I need to do to make this more usable?

TIA
Dave

---

### Post by Silvernail on 2009-11-01
Never mind on this question. I was having trouble with some other apps so I reinstalled Jackalope 04.

---

### Post by HandLotion on 2009-11-01
I'd like to know why my usb external hard drive no longer auto-mounts on startup in Karmic as it did in Jaunty.  I have to toggle the off/on switch on the external hard drive after startup for the drive to be autodetected.  Can I just add the external usb hard drive to /etc/fstab to force the issue, and will this cause a problem when the external usb hard drive is not physically attached to the computer?

---

### Post by Silvernail on 2009-11-02
I don't have the knowledge to answer your question. Perhaps others can help.
It might pay to start a new thread.

---

### Post by FredBarns on 2009-11-03
Hi Everyone,

I am suddenly having a problem mounting external media, both HD and USB,  They won't auto mount in Karmic.

I get this message:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I look at the syslog, I get this:

[   94.984580] UDF-fs: No VRS found
[   94.984587] UDF-fs: Rescanning with blocksize 2048
[   95.035606] UDF-fs: No VRS found
[   95.035611] UDF-fs: No partition found (1)
[   95.213321] ISOFS: Unable to identify CD-ROM format.
[  124.025876] UDF-fs: No VRS found
[  124.025883] UDF-fs: Rescanning with blocksize 2048
[  124.070522] UDF-fs: No VRS found
[  124.070527] UDF-fs: No partition found (1)
[  124.102541] ISOFS: Unable to identify CD-ROM format.

Which suggests to me, the system thinks they are CD's not HD or thumb drives.

Any ideas how to fix this?

Thanks,

Fred

---

