---
title: "how can I install a driver without using /sbin/hotplug ? (not existing in ubuntu ?)"
date: 2019-02-18
forum: Hardware
---

### Post by hyliancloud on 2019-02-18
[SIZE=2][FONT=arial]Hi,
I am working on a lubuntu laptop and I need to install an USB driver manually. The instructions are the following :

> USB hotplug requires two configuration files which are available on the software CD, and also listed on the website for download. These files are: driver and driver.usermap. Please follow the following steps to enable hotplugging.[/FONT][/SIZE]> 
[LIST=1]
[*][SIZE=2][FONT=arial]As superuser, unpack driver and driver.usermap to /etc/hotplug/usb[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]chmod 755 /etc/hotplug/usb/driver[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]chmod 644 /etc/hotplug/usb/driver.usermap[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Unplug and replug your driver adapter(s)[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Set the environment variable USB_DEVFS_PATH to /proc/bus/usb[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial]
However, when I try to follow the instructions, it tells me that the /etc/hotplug directory does not exist (I can't create it either). After doing some research I saw an old article saying that ubuntu (and therefore lubuntu too I guess) handles the USB hot/cold plugging through /etc/udev and not hotplug anymore. Is that still true today ?

Is there any way to install the driver using udev ? (do I only need to follow these steps in /etc/udev or is there another way ?)

Another thing I had to do before that was to add a driver.rules into the /etc/udev/rules and make it executable. That worked fine.

Thank you in advance.[/FONT][/SIZE]

---

### Post by TheFu on 2019-02-18
USB devices are handled differently dependent on the Ubuntu release you are using. Since 16.04, systemd-udev handles them, so starting with the guides for that project would be best.  [https://www.freedesktop.org/software/systemd/man/udev.html](https://www.freedesktop.org/software/systemd/man/udev.html) and [https://www.freedesktop.org/software/systemd/man/systemd-udevd.service.html](https://www.freedesktop.org/software/systemd/man/systemd-udevd.service.html)

I doubt the instructions are new enough to be useful. Those directories aren't likely used anymore, but without knowing the specific release, cannot tell.

Also, learning about Unix file and directory permissions is strongly suggested. The issue where you cannot create directories is purely an issue of that sort and you will have lots of problems using any Unix-like OS due to it until you learn how permissions work. BTW, this applies to almost every OS in the world today, except 1. I bet you can guess which 1 doesn't use Unix file permissions. Just know that every other OS you are likely to use/touch/see does use Unix permissions.  iOS, Android, OSX, any Linux, any UNIX, and any BSD ... they all use Unix permissions.  Google "ubuntu permissions" to find a tutorial.

---

### Post by hyliancloud on 2019-02-19
For the permissions, that was an error of mine, I was denied the permission (I am sudoer and forgot to use sudo ...) and I thought I couldn't create the directory because I had to install the hotplug to be able to create those directories. My bad (and thank you for pointing this out).

That was my main mistake.

Thank you for your response :)

---

