---
title: "Seagate External Drive refuses to allow write access"
date: 2008-05-12
forum: Hardware
---

### Post by rokkphace48 on 2008-05-12
I can mount the thing and access files okay, but under no circumstances will it allow me to gain write access outside of root. I've tried the following commands -

```

sudo chown n0xsled:n0xsled -R /media/seagate
sudo chmod 777 /media/seagate

```


 - the former of which goes through every file on the drive and follows it with "Operation not permitted". I always mount it manually with this command -

```

sudo mount -t vfat /dev/sdc1 /media/seagate

```

Using sudo and terminal programs like nano and touch are the only way to write anything to the drive. How can I give myself global write access?

---

