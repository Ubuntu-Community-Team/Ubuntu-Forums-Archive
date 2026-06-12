---
title: "READ ONLY!! Problems with External Seagate HD"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by rharriso on 2007-08-23
My external hard drive is behaving like a read only memory source, is there any way I can change this?

---

### Post by merlinus on 2007-08-23
Post results of:

```

sudo fdisk -l
cat /etc/fstab

```

How is the drive formatted?

-merlin

---

### Post by rharriso on 2007-08-23
</code>Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
</code>


its listed ast NTFS. It didn't come up with the second command.
I was wondering how i could reformat it.

---

### Post by rharriso on 2007-08-23
also how do you post code correctly

---

### Post by merlinus on 2007-08-23
You do not need to format.  Instead, install the drivers so you can write to it from ubuntu.

```

sudo apt-get install ntfs-config

```then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

If you want to reformat the drive as ext3, then use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

To get code to display properly, lose the forward slash in the opening code tag.  It only goes in the closing one.

-merlin

---

### Post by rharriso on 2007-08-24
thanks a lot

<code>

code

</code>

---

