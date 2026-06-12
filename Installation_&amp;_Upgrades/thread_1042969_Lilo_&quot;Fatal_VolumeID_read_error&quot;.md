---
title: "Lilo &quot;Fatal: VolumeID read error&quot;"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by snowbug on 2009-01-18
Got this error when trying to upgrade to server 8.10. Now whenever I run "lilo -v, I got:
```
Cannot proceed. Maybe you need to add this to your lilo.conf:
        disk=/dev/sdb inaccessible
(real error shown below)
Fatal: VolumeID read error: sector 0 of /dev/sdb not readable

```

The /dev/sdb is just a regular hard drive that I mounted recently to access some old files stored on it. It should be readable. But since it's not used during the boot process, it's okay to skip it by lilo. So I added the "disk=/dev/sdb inaccessible" line to the lilo.conf, but still the same error. 

Here is my lilo.conf (removed comments):
```
boot=/dev/sda
map=/boot/map
delay=20

lba32

disk=/dev/sdb inaccessible

default=Linux

image=/vmlinuz
        label=Linux
        read-only
#       restricted
#       alias=1
        append="root=/dev/sda1  "
        initrd=/initrd.img
        disk=/dev/sdb inaccessible

```

As you can see, I added the "disk" line at two places. I also tried to use only one of these two lines and the result is the same. The lilo never actually skip scanning that /dev/sdb disk.

Does anyone know how to solve it? I need to avoid rebooting as this error happened during the upgrading to 8.1, so rebooting may preventing me to get into the system. 

Thanks,

---

### Post by nealstep on 2010-09-20
Did anyone fix this I have this problem too.

---

### Post by JPS77 on 2010-09-20
Hiiii

I had a problem, i'm new to ubuntu... thought it was something similar so i've posted it here


[PHP]ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/PHP]

---

