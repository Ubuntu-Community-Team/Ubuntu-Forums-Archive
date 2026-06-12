---
title: "Other Drive?"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by joshdudeha on 2008-02-08
I can't write to my other drive
Which has an ext3 partition.
It is apparently mounted, but only shows up in the "/" location.
It doesn't show as a drive, but as a folder.
The partition name is called "drive2".
When trying to write to this partition, it says I do not have the permissions.
Can somebody please help.
How can I mount it so that it is properly recognised as a hard drive and not as a folder.
Thanksx

---

### Post by jan quark on 2008-02-08
ok first some input to get into the situation

run the terminal commands and post the output

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

