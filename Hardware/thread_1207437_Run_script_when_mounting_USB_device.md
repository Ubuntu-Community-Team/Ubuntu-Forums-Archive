---
title: "Run script when mounting USB device"
date: 2009-07-08
forum: Hardware
---

### Post by infinitejones on 2009-07-08
I have a Nokia N95 that I use as a music player. I just plug it in via USB and it mounts at /media/N95 (because that's what I called the microSD card, I assume).

I wrote a little bash script that uses rsync to copy the contents of a folder in my home drive over to the microSD card, so it automatically syncs my music when I plug the phone in. The script works - not quite as I expected, but that's a different thread - but anyway, when I invoke it manually, it works.

I saved the script at /usr/local/syncN95 and did sudo chmod +x /usr/local/syncN95.

As per [this thread]("http://ubuntuforums.org/showthread.php?t=502864") I then put together the following rule which I saved as /etc/udev/rules.d/85-my_rule.rules:

```
ACTION=="add", ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04ed", RUN+="/usr/local/syncN95"
```

Long story short, my script doesn't get invoked when I plug the phone in. Here's what I've done to debug so far:

[LIST]
[*]Manually restarted udev (sudo /etc/init.d/udev restart)
[*]Double checked the idVendor and idProduct using lsusb
[*]Made sure /etc/udev/rules.d/85-my_rule.rules has the same permissions as the other rules
[/LIST]
No joy! When invoked manually after the N95 is mounted, the script works fine.

Any other suggestions? This is all on jaunty, by the way.

---

### Post by infinitejones on 2009-07-14
Bump! Any ideas, anyone?

---

### Post by trogper on 2012-07-29
try to use SYSFS instead of ATTRS

ACTION=="add", ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04ed", RUN+="/usr/local/syncN95"

ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="04ed", RUN+="/usr/local/syncN95"

---

