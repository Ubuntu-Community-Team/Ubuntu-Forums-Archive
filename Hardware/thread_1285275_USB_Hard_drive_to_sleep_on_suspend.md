---
title: "USB Hard drive to sleep on suspend"
date: 2009-10-07
forum: Hardware
---

### Post by Mjoln on 2009-10-07
I have an external Buffalo usb drive connected to my laptop with Ubuntu 9.04. Usually I don't bother shutting down my laptop so I just suspend it. The problem is that my usb drive won't shut down when I do that. Can I somehow make my usb drive to shut down/sleep/something like that when I suspend my laptop and then automatically wake up when I turn it back on?

---

### Post by Mjoln on 2009-10-11
Bump. Anyone?

---

### Post by Mjoln on 2009-11-29
Solved this. Just needed to make a script that unmounts the hard drive, tells it to stop spinning and then suspends the usb-port the hard drive is plugged in (because for some reason the usb-drive starts again after about a second) on suspend. And of course the same in reverse order when the laptop resumes from suspend.

In case someone else needs this, here's the script to spin down the hard drive:
```
umount -a /dev/your_hard_drive_here
sg_start --stop /dev/your_hard_drive_here && echo suspend > /sys/bus/usb/devices/the_usb_where_hdd_is_plugged_in_here/power/level
```

And here's the script to resume my hard drive when the laptop wakes up again:
```
echo on > /sys/bus/usb/devices/the_usb_where_hdd_is_plugged_in_here/power/level && sg_start --start /dev/your_hard_drive_here && mount /dev/your_hard_drive_here /mount_point_here
```

---

