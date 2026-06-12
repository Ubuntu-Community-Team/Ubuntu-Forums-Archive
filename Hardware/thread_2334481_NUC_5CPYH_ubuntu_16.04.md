---
title: "NUC 5CPYH ubuntu 16.04"
date: 2016-08-19
forum: Hardware
---

### Post by mune on 2016-08-19
I have successfully installed ubuntu 16.04 on NUC (4GB, Celeron, 150GB SSD). It worked for 15 days; yesterday I did a normal upgrade (also the kernel), now ubuntu stops while starting.

As the live distribution (with a bootable USB stick) boots, it is NOT a nuc problem, so I guess something new makes it fail when in conjction with nuc.

The starting process takes a long time and finish complaing that journal says that /dev/sda2 is not clean.

Anyone experience a similar issue?

Thanks.

---

### Post by mune on 2016-08-19
I booted the NUC with the live distro, then I mounted /dev/sda2 (browsing it with nautilus), finally I unmounted it, rebooted and started from the SSD: but I got the same error :(

PS Hoping that the mount/unmount cycle force a cleaning.

---

### Post by mune on 2016-08-19
I launched gparted in the live USB an says
[IMG]http://i.stack.imgur.com/lsXSi.png[/IMG]
(as in [page]("http://askubuntu.com/questions/781223/physical-block-size-is-2048-bytes-but-linux-says-it-is-512-when-formatting-a") (but the main disk and not for USB pen).)

---

### Post by sudodus on 2016-08-20
I suggest that you boot from an external drive (USB pendrive). Check that the partition(s) of your installed system is/are unmounted and run the following command the fix the partition(s) of your installed system:

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number, for example **/dev/sda1** and/or **/dev/sda6** (only one partition in a standard system where 'everything is in the root partition except swap'). Check the manual ```
man e2fsck
``` if you want more details.

After that you can run ***tune2fs*** to check and change the settings for checking the drive. See the manual ```
man tune2fs
```

Check the settings with ```
sudo tune2fs -l /dev/sdxy
```

---

