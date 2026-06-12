---
title: "Problem writing to hard drive"
date: 2012-02-06
forum: Hardware
---

### Post by rmcellig on 2012-02-06
This has never happened to me before. I just formatted my external USB drive after booting from the Puppy Linux 5.2.8 CD using Gparted to format. The formatting went fine but for some reason I can't write to the drive, Access not allowed. I gather this is a permissions issue? If so I never had a problem like this after formatting a drive. What should I do?

The same thing happened when I was logged into my Ubuntu sda4 desktop and went to format the same drive.

---

### Post by Morbius1 on 2012-02-06
A freshly formatted linux partition regardless of where it's located will have owner as root and permissions for root to read and write and for everyone else to only read.

One way to rectify this is to take possession of the mounted partition:
```
sudo chown your-user-name /media/mount-point
```

---

### Post by rmcellig on 2012-02-06
Thanks I will try that. One question. When I create a partition table, should I select the msdos default option or do I need to select something else?

---

