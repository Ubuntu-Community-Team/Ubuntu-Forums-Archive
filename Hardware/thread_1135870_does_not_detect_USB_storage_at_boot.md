---
title: "does not detect USB storage at boot"
date: 2009-04-24
forum: Hardware
---

### Post by wriggary on 2009-04-24
Hi, just updated to 9.04 stable, and so far it isn't too shabby.  Much better than the beta.  Up to this point (since 8.04, my first dive into linux), i've been able to figure out most of my own problems either by tinkering, forum search, or google search, but this one gets me.

My usb drives, one 8GB usb flash stick, and one usb external HDD, don't seem to be detected by jaunty on initial login. They are detected, however, when I remove the flash stick and replug it, suggesting that udev? may be the culprit.  Not sure, however, since I need a bit more time to digest how the heck udev works, debugging, etc.  

Strange thing is, when I do a lsusb right after boot, its lists the drives and their bus locations, but are not available in the places -> removable media folder in gnome.  Then I open a term and look in /dev/disk/by-label , and no WD or MEMOREX type entries are visible.

I'll be back after a reboot where I haven't tinkered with it.

---

### Post by Gladk on 2009-04-25
I have exactly the same problem and dont know how to fix it :(

---

### Post by wriggary on 2009-04-26
helpful people abound on answers.launcpad.com/ubuntu!

check out these links, Gladk.  Get back with us if you need any help doing what the post tells you to do.

[https://answers.launchpad.net/ubuntu/+question/68752]("https://answers.launchpad.net/ubuntu/+question/68752")

and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364933]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364933")

G

---

### Post by Gladk on 2009-04-26
Thank you! It solved my problem.

---

