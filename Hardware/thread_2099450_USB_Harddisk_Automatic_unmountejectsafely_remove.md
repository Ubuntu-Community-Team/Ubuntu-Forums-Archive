---
title: "USB Harddisk Automatic unmount/eject/safely remove"
date: 2012-12-29
forum: Hardware
---

### Post by lseg on 2012-12-29
Hi,

I have a server to which I attached a USB Harddisk, on this USB Drive I do some automatic backups using rsync.

I have 2 of these harddisks, and I keep 1 of them at work.
This Home server is in my garage, so when I leave to work I would like to be able to just unplug the USB drive and take it to work and swap the drives.

I know it is not so safe to just unplug a mounted USB harddrive. So I would like to automate the eject/unmount/safely remove hardware option.

In cron I would like to do following (at midnight for example):
1) mount USB drive
2) rsync (backup my most important stuff)
3) umount or whatever is needed so I can safely physically remove the USB harddrive in the morning.

Question is: is umount safe enough (that was my first thought, but I am doubting)? If not how can I do the eject in a terminal/cron? And also: can I remount the drive if it was ejected (I am not swapping it each day)?

Kind regards,

Luc

---

### Post by ahallubuntu on 2012-12-29
Yes, unmount is just fine.  I do something similar with two USB drives.

---

### Post by lseg on 2012-12-30
Will the drive keep on spinning if I do that ?

---

