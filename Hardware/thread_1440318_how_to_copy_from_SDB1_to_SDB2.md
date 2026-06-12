---
title: "how to copy from SDB1 to SDB2"
date: 2010-03-27
forum: Hardware
---

### Post by tsalib on 2010-03-27
How do I make a complete back up copy from my primary HDD to my second one on ubuntu server I don't have any raid set up is there any way to copy all my data from one to another just so I have a back up 

thanks

---

### Post by Barriehie on 2010-03-28
> **tsalib said:**
> How do I make a complete back up copy from my primary HDD to my second one on ubuntu server I don't have any raid set up is there any way to copy all my data from one to another just so I have a back up 

thanks

Assuming you have sdb2 mounted at /mnt/drive2 and as root:
```

rsync -avr --delete --exclude "mnt/" / /mnt/drive2/
```

You might have to play around with the exclude; I've seen it presented different ways.

---

