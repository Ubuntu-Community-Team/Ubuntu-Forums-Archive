---
title: "Kingston USB Flash takes log time to mount"
date: 2014-03-04
forum: Hardware
---

### Post by j3n7il on 2014-03-04
I have 4 16gig flash drives, all mkfs.ext3, these drives each have a 1g truecrypt file on them. I have a powered 12 port usb hub that I use them in. When I first used them they would auto mount quickly, now however it takes 2 - 4 min for the drive to mount. I will see the drive in syslog, but the mount process just hangs.

Thoughts?

---

### Post by sudodus on 2014-03-04
What happens

- after a reboot?

- if you boot the computer from an install CD/DVD/USB drive and run a live session 'try Ubuntu'?

- if you connect directly into the computer (without the USB hub)?

- if you mount the drives manually?

You can find the device with the commands

```
sudo parted -l
```
and
```
sudo blkid
```

Identify the device letter and partition number /dev/sdxy (for example /dev/sdb1)

and mount it with

```
sudo mount /dev/sdxy /mnt
```

unmount later with

```
sudo umount /mnt
```

---

