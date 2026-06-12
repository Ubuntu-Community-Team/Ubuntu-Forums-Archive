---
title: "Screen brightness is low when starting up on Dell Inspiron 1370 / 13z (Ubuntu 14.04)"
date: 2014-05-15
forum: Hardware
---

### Post by ralphm2 on 2014-05-15
I recently installed Ubuntu 14.04 LTS on my Dell Inspiron 1370 (13z) laptop, next to Windows7. Everything works flawlessly, however, the boot-startup screen (GRUB) has very low brightness, and also when Ubuntu starts (login screen) the brightness is extremely low. By repeatedly tapping the "brightness up" key, the screen turns to normal brightness, so one can work around it, but it is inconvenient, and annoying to have to do this every time starting Ubuntu.

I have read posts reporting related issues and tried out the GRUB_CMDLINE_LINUX="acpi_backlight=vendor" option, but this only makes things worse: then I can't normally turn up brightness any more (brightness still starts off being very low, however now accompanied by very instable response to brightness-keys). By the way: if I choose for Win7 in GRUB, the brightness is immediately as it should be once Windows starts up.

Should I report this as a bug? Is there a solution?

---

### Post by Oni45 on 2014-07-19
Hi ralpm2, it is not an answer to your message, but it can help you. Before, I was in the same case, and I solve it with this solution: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489397/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489397/comments/16) even on Ubuntu 14.04.

Recently, I have to move my laptop (some, inspiron 13z) to Linux Mint 17, but I have got the same problem with the brightness... Maybe that come from an update?

---

### Post by jeremy31 on 2014-07-19
> **Oni45 said:**
> Hi ralpm2, it is not an answer to your message, but it can help you. Before, I was in the same case, and I solve it with this solution: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489397/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489397/comments/16) even on Ubuntu 14.04.

Recently, I have to move my laptop (some, inspiron 13z) to Linux Mint 17, but I have got the same problem with the brightness... Maybe that come from an update?

Oni, what is your issue with brightness as the original post is a few months old?  If your keyboard hotkeys work, get the brightness to the level you want and then run this in terminal
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; done
```

And then we can find a way to get your laptop to start at the brightness you want

---

