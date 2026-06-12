---
title: "Tablet PC digitizer not working"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by kellcomnet on 2007-01-21
I have an Averatec C3500, i have gotten everything but the tablet functionality working. The digitizer is made by UC-Logic. using lshal I have managed to get the following information

udi = '/org/freedesktop/Hal/devices/pnp_UCL0200'
  info.udi = '/org/freedesktop/Hal/devices/pnp_UCL0200'  (string)
  linux.subsystem = 'pnp'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  info.product = 'PnP Device (UCL0200)'  (string)
  pnp.id = 'UCL0200'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.bus = 'pnp'  (string)
  linux.sysfs_path_device = '/sys/devices/pnp0/00:09'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)

My understanding is that there is an aiptek driver that might work but it requires the tablet to be on either a serial or USB port. any help is appreciated as this is the last step I have to get e laptop working completely in Linux

---

### Post by kellcomnet on 2007-01-29
<bump>

---

### Post by kellcomnet on 2007-02-05
<bump>

---

### Post by jml on 2007-02-05
Tablet/digitizer support in Linux is very poor.  Here is a post I found on this forum by searching on the term tablet digitizer.  I don't have any direct experience with it myself.

[http://www.ubuntuforums.org/showthread.php?t=104750&highlight=tablet+digitizer+drivers](http://www.ubuntuforums.org/showthread.php?t=104750&highlight=tablet+digitizer+drivers)

Hope it helps.

Joe

---

### Post by jml on 2007-02-05
Check out this post I found by searching this forum with the terms tablet digitizer.

[http://www.ubuntuforums.org/showthread.php?t=104750&highlight=tablet+digitizer+drivers](http://www.ubuntuforums.org/showthread.php?t=104750&highlight=tablet+digitizer+drivers)

Joe

---

### Post by jml on 2007-02-05
sorry for the double post, my workstation went a bit wonky.

Joe

---

