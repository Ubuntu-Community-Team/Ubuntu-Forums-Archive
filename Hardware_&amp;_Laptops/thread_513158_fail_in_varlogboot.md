---
title: "fail in /var/log/boot"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by tomcheng76 on 2007-07-30
i found there is one entry showing failed
that was  Assembling RAID arrays.... failed

i searched on the forum, it said related to udev
so i did "sudo apt-get install --reinstall udev"
here was the warning msg i got
> 
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.


anyone have a idea on how to fix it ?
i have no RAID arrays but a LVM partition, is it related?
any help would be appreciated

---

### Post by tomcheng76 on 2007-07-30
oops, i found that the log date is Apr 21
how to get the latest boot log ?

---

### Post by tturrisi on 2007-07-30
Well, in Debian, boot logging is set OFF by default.  Not sure about Ubuntu.  Go to /etc/default/bootlogd & if boot logging is enabled it should look like this:
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

The default is:
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

A reboot creates a new /var/log/boot.

---

### Post by tomcheng76 on 2007-07-30
Thanks tturrisi, just changed the setting
i will read the boot log again if i have to reboot

---

