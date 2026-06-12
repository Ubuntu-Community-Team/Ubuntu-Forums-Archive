---
title: "Ubuntu NEWB: Mounting Hard Drive?"
date: 2008-09-22
forum: Hardware
---

### Post by Menissalt on 2008-09-22
OK, I AM a newb first off, but I am not stupid so I will understand stuff. My problem is that I have a dual boot and would like to have access to my other partition. I know I need to mount but I don't know what to do, I know where to start and that yall need more info, but I'm not sure what. Tell me what to type into Terminal and anything else that is necessary and I will get it quickly.

I would normally just look it up and work on it until I finally got it right, but I'm am currently too busy for trial and error.... could I get some help?

---

### Post by Crafty Kisses on 2008-09-22
I'm not sure, but for me it would be:
```
sudo mount -t ext3 /dev/sda1 /mnt/sda1
```

---

### Post by Menissalt on 2008-09-22
> **Codename said:**
> I'm not sure, but for me it would be:
```
sudo mount -t ext3 /dev/sda1 /mnt/sda1
```



So mine should have my hard drives formatting (in place of ext3) and sda2 because of it being an hp

---

