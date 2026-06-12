---
title: "Missing hard disk"
date: 2014-10-09
forum: Hardware
---

### Post by parcdulas on 2014-10-09
Hello,
I have just installed 14.04 on a new clean system with a 256Gb solid state disk as the primary device and a 1Tb hard disk for data storage. Every thing seemed fine until I tried to access the 1Tb hard disk - It wasnt there! Only the 256Gb one shows up. At Bios level it is seen so what should I do to get it recognised by Ubuntu. I'm fairly new to Linux so sorry if I've missed something trivial.

Thanks,

Martin

---

### Post by Vladlenin5000 on 2014-10-09
What is the file system of the aforementioned 1TB HDD?

Please post the results of: ```
sudo parted -l
```

---

