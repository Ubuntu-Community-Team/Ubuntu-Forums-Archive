---
title: "Need help mounting new HD, cannot write"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by elev on 2007-06-25
OK, so I have a 200GB IDE drive installed at hdb and a ext3 partition taking up the whole drive.  My entry in fstab looks like like this:
```
/dev/hdb1	/media/shared_media	ext3	defaults 0	0
```

but after I "sudo mount -a" I cannot write anything to it unless I do some thing like "sudo mkdir..."

Does anyone know where I am going wrong?

---

### Post by jimrz on 2007-06-25
> **elev said:**
> OK, so I have a 200GB IDE drive installed at hdb and a ext3 partition taking up the whole drive.  My entry in fstab looks like like this:
```
/dev/hdb1	/media/shared_media	ext3	defaults 0	0
```

but after I "sudo mount -a" I cannot write anything to it unless I do some thing like "sudo mkdir..."

Does anyone know where I am going wrong?

try this 
```
sudo chmod -R 777 /media/shared_media
```

or
```
sudo chmod -R a+rwx /media/shared_media
```

---

### Post by elev on 2007-06-26
I think that did it. Thanks,

---

