---
title: "Shred command issues."
date: 2010-12-10
forum: Hardware
---

### Post by Sobuntu88 on 2010-12-10
Hello,

I am having a shred issue. I hope you someone can help. I am using Ubuntu 10.10 and I am trying to shred a drive connected to a Thermaltake BlackX cradle. It is connected using USB. I have shred'ed multiple drives using the same method. With success. This is the only drive giving me problems. I started off using the command: [sudo shred -vfz -n 7 /dev/sdb1] which worked for 2 passes and the returned: [shred: /dev/sdb: fdatasync failed: Input/output error] I have umounted the drive and retried several times. The drive will now do zero passes and returns the same error. I also tried the [sudo shred -n1 /dev/sdb1] which seemed to start working for about 20-25 minutes and then it returns the same error.

---

### Post by physicsparadox on 2011-02-09
It's Feb 2011 and it happened to me too.

---

### Post by coffeecat on 2011-02-09
> **physicsparadox said:**
> It's Feb 2011 and it happened to me too.

What has happened to you? If you need some help, please post details.

Reading the OP's post, I would think that in their case the most likely explanation is it's not shred failing, but the drive.

---

