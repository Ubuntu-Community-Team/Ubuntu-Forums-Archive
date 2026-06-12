---
title: "gparted or partition table error?"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Diabolis on 2007-08-01
This morning I started firefox in my laptop as usual, but I noticed it was a bit slower than usual so I checked the system monitor, I though maybe some heavy process was running. What I found out was that my swap partition wasn't mounted, so I installed gparted from synaptic. I checked and all my paritions appeared as usual except my swap partition. gparted didn't recognize it, so i created a new swap partition with the free space.

I have 2 partitions hda3 (for media and stuff) and hda4 (dual boot), both appear on my desktop when I start my system. The problem appears when I open gparted, It will remount both partitions and now I would have hda3 hda4 hda3(2) hda4(2) over my desktop.

**It still intrigues me why my old swap partition ceased to work.

this is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda2 -- converted during upgrade to edgy
UUID=e0ad2ffd-903f-4f8f-a67a-8413ee7091f0 / ext3 defaults,errors=remount-ro 0 1

# /dev/hda3 -- converted during upgrade to edgy
UUID=340a1b7a-bd6d-4cf1-aa1c-7d7bf463b548 /media/hda3 ext3 defaults 0 2

# /dev/hda4 -- converted during upgrade to edgy
UUID=55415b7d-0404-45e9-b53a-79080d25e7d8 /media/hda4 ext3 defaults 0 2

# /dev/hda1 -- converted during upgrade to edgy
/dev/sda1 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by mathewb on 2007-08-01
Is the swap not working? It could be the different device name for the swap:
> 
# /dev/**hda1** -- converted during upgrade to edgy
/dev/**sda1** none swap sw 0 0

Try changing "sda1" to "hda1" and see if that fixes it.

My setup is similar, and my swap is working:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9c5dacd5-88b0-4256-9fcd-d83ea1bb6a17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=95b18262-6048-4459-afc1-f2417ba5892f /boot           ext3    defaults        0       2
# /dev/sda7
UUID=0a0b38ed-5a2f-4f01-93ac-73d91c0a8991 /home           ext3    defaults        0       2
# /dev/sda1
UUID=045CE63B5CE626E0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=946F-3A7C  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=6a190dcc-15dd-470a-8ef2-ec094faac92d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by Diabolis on 2007-08-01
Swap is already working. What I don't like is that everytime I run gparted all my partitions get mounted again.

---

