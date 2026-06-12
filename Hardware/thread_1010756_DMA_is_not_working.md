---
title: "DMA is not working"
date: 2008-12-14
forum: Hardware
---

### Post by usamahashimi on 2008-12-14
edited

---

### Post by linux_tech on 2008-12-14
Check output of dmesg for 

scsi 2:0:0:0: Direct-Access ATA

and post these lines

---

### Post by linux_tech on 2008-12-14
If you are in doubt of disk performance then you can also run a test-

[http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html)

---

### Post by usamahashimi on 2008-12-14
edited

---

### Post by linux_tech on 2008-12-14
Please attach dmesg output

Please post output of 

```
sudo hdparm -tT /dev/sda
```

---

### Post by usamahashimi on 2008-12-14
edited

---

