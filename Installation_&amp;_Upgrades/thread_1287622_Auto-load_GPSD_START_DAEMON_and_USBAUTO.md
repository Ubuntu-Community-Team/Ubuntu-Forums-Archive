---
title: "Auto-load GPSD START_DAEMON and USBAUTO"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by ray.foulkes@attglobal.net on 2009-10-10
I am trying to make the GPSD daemon load automatically on plugging in a usb based gps receiver on Jaunty. /lib/udev/gpsd.hotplug.wrapper has two problems for me; the first is the missing /lib/udev/hotplug.functions which is being solved in karmic:
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/karmic/gpsd/karmic/annotate/head%3A/debian/gpsd.hotplug.wrapper]("http://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/karmic/gpsd/karmic/annotate/head%3A/debian/gpsd.hotplug.wrapper")
I have changed the .wrapper on jaunty to incorporate this change.

Automounting only happens if two environment variables contain "true"; these are START_DAEMON and USBAUTO
They are set to false in the current version of /etc/default/gpsd which is executed by .wrapper
There it says not to edit this file but to use 'dpkg-reconfigure gpsd' to change the options. So 2 questions:
1. do I really have to use a command line on Ubuntu to configure gpsd or is there another way (I cannot find anything obvious in the menus)?
2. when I do run 'dpkg-reconfigure gpsd' (sudoed from a command line) the only question it asks me is whether I want it to be run at boot time (I don't). i.e. I cannot change START_DAEMON and USBAUTO anyway. So what am I doing wrong?

---

