---
title: "How do I get USB devices to mount automatically?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by skywatcher on 2007-03-26
I recently installed kernel version 2.6.20.3 on Dapper, and everything works fine, except for one problem. When I plug in any USB device such as an iPod or a Flash drive, it mounts automatically, which is great. But once I remove it by selecting 'eject' in that device's dropdown menu on the desktop, it doesn't automatically mount the next time I plug it in, unless I reboot.

Please can someone tell me how to fix this problem. I would prefer not to have to manually mount devices.

Thanks.

---

### Post by moore.bryan on 2007-03-26
[I]you shouldn't have to reboot to make it mount.  mounting for removable devices is handled by pmount/punmount...

how long have you waited after ejecting to reconnect?  and then, how long have you waited after reconnect to see if it's recognized?
[/I]

---

### Post by skywatcher on 2007-03-26
OK, I ran a test: Plug in USB Flash, icon appears on desktop, File Browser opens and shows USB. I open and close some folders on the Flash, then eject same from the desktop and remove device. Icon disappears, so does USB from File Browser. I then go and make a cup of coffee (~5 min.) and plug USB Flash in again.

Nothing - dead as a Dodo.

---

### Post by moore.bryan on 2007-03-26
*that's really a little strange; in fact, never heard of this problem before right now.  are you running the default gnome or are you kde?*

---

### Post by moore.bryan on 2007-03-26
*if you're running gnome, try running ```
sudo gnome-volume-properties
``` and make sure the explore function is set for usb devices...*

---

### Post by s0cket on 2007-03-26
> **moore.bryan said:**
> [I]you shouldn't have to reboot to make it mount.  mounting for removable devices is handled by pmount/punmount...

how long have you waited after ejecting to reconnect?  and then, how long have you waited after reconnect to see if it's recognized?
[/I]

It's actually a combination of UDEV, HAL, pmount, and gnome-mount that makes it possible.  This is why people are always having so many problems with this feature... too many hands in the pot I'm afraid.

---

### Post by moore.bryan on 2007-03-26
> **s0cket said:**
> too many hands in the pot I'm afraid.
*i completely agree.*

---

### Post by kevinlyfellow on 2007-04-24
Your not alone skywatcher.  My usb does the same thing :-(

---

### Post by kevinlyfellow on 2007-04-24
I found that killing /usr/sbin/hald and running the program again solves the problem, thus it is for sure a hald problem.

---

