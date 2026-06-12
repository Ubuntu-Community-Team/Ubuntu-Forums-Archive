---
title: "Error mounting..."
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by akromm on 2009-09-02
here is the error i get...

<code>
Can't mount device /org/freedesktop/Hal/devices/volume_uuid_EEFA95F4FA95B8F3 /media/S3A6747D002 org.freedektop.Hal.Device.PermissionDeniedByPolicy org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always
</code>

my best guess is that i need to be root to mount that drive (its the windows partition)  but its not in mstab or fstab (and not too sure how to add it)

im running dual boot vista/ubuntu with WM e17

---

### Post by Intrepid Ibex on 2009-10-21
Same problem here, increases Gparted launching time with something like 13 s, you found a fix/workaround yet?

---

### Post by drs305 on 2009-10-21
> **Intrepid Ibex said:**
> Same problem here, increases Gparted launching time with something like 13 s, you found a fix/workaround yet?

Depending on what you want to work on in Gparted, you can start it from the command line and only specify the partition. It speeds loading a lot.

Examples:
```
gksu gparted /dev/sda
gksu gparted /dev/sda /dev/sdc
gksu gparted /dev/sdb1

```

Of course, normally when using Gparted I work with many partitions, but I use the first one often.


@ akromm,

You might see if there is anything special that has been added to this partition's instructions in gconf-editor:
```

gksu gconf-editor /system/storage/default_options/

```
Run it as root since it's probably a system issue.

---

