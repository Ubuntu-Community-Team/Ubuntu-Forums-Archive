---
title: "Hal ghosts in my Feisty scanner"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by fotakis on 2007-04-21
Hello all,

I just did a fresh install on my PC to feisty, and I have an hp4370 scanner connected via
usb.

I am using the following sane [URL="https://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&release_id=499156"]backend 
[/URL]. I can scan using xsane and kooka, but the problem is that my scanner keeps making the initialization sound all the time, as if some service is querying it.

I tailed /var/log/syslog and unplugged replugged my scanner and this is what came up:
```

Apr 21 15:59:49 fotis NetworkManager: <debug info>^I[1177160389.420525] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4105_CN59MA253J04CM_if0'). 
Apr 21 15:59:49 fotis NetworkManager: <debug info>^I[1177160389.423411] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4105_CN59MA253J04CM'). 
Apr 21 15:59:49 fotis NetworkManager: <debug info>^I[1177160389.425413] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4105_CN59MA253J04CM_usbraw'). 
Apr 21 16:00:13 fotis NetworkManager: <debug info>^I[1177160413.859314] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4105_CN59MA253J04CM'). 
Apr 21 16:00:13 fotis NetworkManager: <debug info>^I[1177160413.923301] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4105_CN59MA253J04CM_if0'). 


```

Two things from these messages, 1. what does NetworkManager have to do with my scanner? 2.) What the hell is HAL doing?

So I tried the following:

I added a policy to hal in /etc/hal/fdi/policy which set that device as a scanner and nothing happened it still made that noice.

I removed NetworkManager completely and it still makes that noice.


I totally installed the previous drivers, and it is still doing it

Right now I don't know where to look to solve my problem but it is definately with this hal crap.

Anyways I hope someone can shed some light on this.

uname -r: 2.6.20-15-generic
Distro: Ubuntu Feisty
Scanner: hp 4370
Sane Backend: hp3900


Best Regards,
Fotis

---

### Post by fotakis on 2007-04-23
anyone?

---

### Post by fotakis on 2007-05-04
Hello again,

I am sorry to be bumping this up all the time.

If anyone with some udev, usb knowlegde can at least point me in the right direction to further understand
the current problem.

Thanks

---

