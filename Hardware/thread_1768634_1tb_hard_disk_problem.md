---
title: "1tb hard disk problem"
date: 2011-05-27
forum: Hardware
---

### Post by shini-kire on 2011-05-27
hello ...

my problem is this, buy a 1tb hard drive(7200 rpm s-ata) formatted with ntfs, and I formatio with ext4 and I eat my 80gb 1tb of space as with ext3 and ntfs fat32 but I do not eat 80 gb.

could be a hard error? to collect the warranty? or is it common for me to take those 80 gb? ntfs being than I eat them? and why is that?

I await your response, thank you very much

---

### Post by Grenage on 2011-05-27
> **shini-kire said:**
> hello ...

my problem is this, buy a 1tb hard drive(7200 rpm s-ata) formatted with ntfs, and I formatio with ext4 and I eat my 80gb 1tb of space as with ext3 and ntfs fat32 but I do not eat 80 gb.

could be a hard error? to collect the warranty? or is it common for me to take those 80 gb? ntfs being than I eat them? and why is that?

I await your response, thank you very much

From a 1TB drive you will only get about 917GB of space.

Manufacturers sell the drive based on 1GB=1000MB,Hard drives are formatted like this: 1GB=1024MB

---

### Post by shini-kire on 2011-05-27
> **Grenage said:**
> From a 1TB drive you will only get about 917GB of space.

Manufacturers sell the drive based on 1GB=1000MB,Hard drives are formatted like this: 1GB=1024MB

still do not understand that "ntfs" consume no more space in the case of ext4, fat32 ext3 and that if they consume a large amount of space in the formatting ... ext3 and ext4 still better than ntfs :confused:

---

### Post by Grenage on 2011-05-27
> **shini-kire said:**
> still do not understand that "ntfs" consume no more space in the case of ext4, fat32 ext3 and that if they consume a large amount of space in the formatting ... ext3 and ext4 still better than ntfs :confused:

I see; I should also mention that ext3/4 reserve 5% of the drive for emergency maintenance. This can be changed:

```
tune2fs -m 1 /dev/sda1
```

That would reduce the reserve to 1%, on partition *1* of *sda*.

---

