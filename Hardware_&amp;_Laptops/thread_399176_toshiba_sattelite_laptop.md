---
title: "toshiba sattelite laptop"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by nwadams on 2007-04-02
i'm trying to install ubuntu on a toshiba sattelite laptop and the partition editor will not let me resize my windows partition...plz help because i cna't get rid of windows entirely and i'd like to be able to use ubuntu on it

---

### Post by teaker1s on 2007-04-02
defrag/scan disk  it and then you can use "gparted live iso" to resize it

note: you must let windows run scan disk after resize or you risk BSD

---

### Post by nwadams on 2007-04-02
i've ran chkdsk twice now, and it still won't work

what is gparted live iso? is that the gnome partitioner that is pre-installed on the live ubuntu cd's?

thanks for any help you can provide

---

### Post by stchman on 2007-04-02
> **nwadams said:**
> i'm trying to install ubuntu on a toshiba sattelite laptop and the partition editor will not let me resize my windows partition...plz help because i cna't get rid of windows entirely and i'd like to be able to use ubuntu on it

I had the same problem.  I assume you are using the LiveCD portion of Ubuntu using Gnome Partition Editor.  You must run chkdsk /f not just chkdsk.

You probably have some errors on the Windows drive.  You will have to go to the Windows installation and run a **chkdsk /f** on all Windows (NTFS/FAT32) partitions.  The C:\ drive can only be checked this way upon boot up, other drives can be checked while Windows is running.  Once you have done check disk I recommend you defrag all Windows drives.

This should allow you to resize your windows partitions.  Check out my webpage about resizing partitions and partition info at:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

I hope this helps.

---

### Post by todoporron on 2007-04-02
No, the gparted live iso CD is a  live cd which runs gparted booting from the CD rom. It worked perfectly for me when shrinking the windoze partition. You can obtain it from 

```
http://gparted.sourceforge.net/livecd.php
```

---

