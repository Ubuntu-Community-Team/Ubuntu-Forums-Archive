---
title: "[SOLVED] dv9000 &amp;amp; HD-DVD"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by DillyP on 2008-01-25
I have a HP dv9000 that came with an HD-DVD drive, I'm running 7.10.  When I put an HD-DVD disc into the drive, it will not mount. It says there in an invalid mount option when attempting to mount the volume.

It does just fine with regular DVDs and CDs though... not sure if it Ubuntu just doesn't recognize the drive as being HD-DVD, if there is just a problem mounting those discs, or something else.

The /etc/fstab entry for the drive:

UUID=124aaabe-8182-4541-a053-a8d189ae7bca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Anyone have any idea or a way to find the root cause?

---

### Post by DillyP on 2008-01-28
Found this link: [http://www.strapp.co.uk/#hddrive](http://www.strapp.co.uk/#hddrive)

This was all I needed to do:

 wget http://www.strapp.co.uk/files/udf-$( uname -r ).ko
sudo mv udf-$( uname -r ).ko /lib/modules/$( uname -r )/kernel/fs/udf/udf.ko

---

