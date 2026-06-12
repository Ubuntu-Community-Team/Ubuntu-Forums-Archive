---
title: "CD-ROM doesn't work"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by mrbaz on 2006-07-30
I'm using Dapper Drake, and I have an icon for the CDROM, but everytime I try to open it, it says "mount: special device /dev/hdc does not exist"

---

### Post by matko on 2006-07-30
try
```
sudo mkdir /media/cdrom
```
and than
```
sudo nano /etc/fstab
```

and comsult/add line for cdrom

```
/dev/hdc        /media/cdrom   udf,iso9660 user,noauto     0       0

```

---

### Post by polloz on 2006-07-30
same problem here. the above solution didn't worked for me. this is wierd, it worked properly yesterday. was it maybe an update that did this?

---

### Post by matko on 2006-07-30
> **polloz said:**
> same problem here. the above solution didn't worked for me. this is wierd, it worked properly yesterday. was it maybe an update that did this?

what was output from shell?
have you rebooted?
give here some rows from syslog please.

---

