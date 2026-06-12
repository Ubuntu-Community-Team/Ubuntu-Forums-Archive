---
title: "Can't boot after installing evms-gui"
date: 2008-08-30
forum: General Help
---

### Post by jonface on 2008-08-30
Just installed 8.04 with software raid 1. Installed evms-gui 'cos I thought I'd be lazy and see the status of the array but I wish I never bothered now. 

Get the error message now on boot,

device-mapper: table: 254:1: linear: dm-linear: Device lookup failed
device-mapper: ioctl: error adding target to table

ref: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616)

How can I mount the raid 1 array via the live cd? I tried mounting /dev/md0 (ext3) but it doesn't exist. I tried mounting a single drive of the array but I didn't expect that to work, and, it doesn't.

I just want to remove evms. I can't seem to find a google article on mounting a software raid array manually. When the machine boots normally it doesn't get far enough to switch to a console. Tried in vein booting with irqpoll, noacpi, pci=noacpi.

Thanks.

---

### Post by fjgaude on 2008-08-31
Well, you can mount the array from liveCD by installing **mdadm** while in the CD. Then using the terminal command:

```
sudo mdadm --assemble --scan
```

That should do it. I'm not sure about the sudo, if it is needed.

Let us know what happens.

---

### Post by jonface on 2008-09-01
Ahh nice one, mounted the array, genius. Removing EVMS seems like a problem as well though.

Would be nice to be able to do 'apt-get remove evms' but I'm not sure how to tell apt to use a different installation (I'm booting from the live-cd)?

I've tried removing everything related to evms I can find but no joy. Thats everything in /usr/sbin , /etc/init.d/ and anything else I can find. I don't understand how it's still starting? Unless some other problem can cause this error?

---

### Post by jonface on 2008-09-01
Ha, didn't realise it would be this easy.

- Mounted array in dir array.
- chroot array/
- apt-get remove evms

Boots up fine now. All this because I thought a gui would be easier.

Thanks for the above help :)

---

