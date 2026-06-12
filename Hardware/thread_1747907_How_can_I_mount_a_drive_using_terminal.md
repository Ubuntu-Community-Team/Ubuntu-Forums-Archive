---
title: "How can I mount a drive using terminal?"
date: 2011-05-03
forum: Hardware
---

### Post by Uewd on 2011-05-03
I want to mount a drive using terminal or a run command, but how can I do this?

Please help.
Thanks.

---

### Post by IcarusR on 2011-05-03
Create directory to mount dive to. Mount point must exist & be read write by user. ie /home/user/external

In terminal run

```
sudo fdisk -l
```

enter password

Work out which is the drive you want to mount & it's filesystem. ie /dev/sdb & ntfs

Then in terminal

```
sudo mount /dev/sdb /home/user/external ntfs 
```

This will mount a drive /dev/sdb formatted to ntfs to /home/user/external

This needs to be adjusted to suit your needs.

There are loads of options to the mount command, for details see the manual page

```
man mount
```

When done with drive unmount with this

```
sudo umount /home/user/external
```

---

### Post by Uewd on 2011-05-04
> **IcarusR said:**
> Create directory to mount dive to. Mount point must exist & be read write by user. ie /home/user/external

In terminal run

```
sudo fdisk -l
```enter password

Work out which is the drive you want to mount & it's filesystem. ie /dev/sdb & ntfs

Then in terminal

```
sudo mount /dev/sdb /home/user/external ntfs 
```This will mount a drive /dev/sdb formatted to ntfs to /home/user/external

This needs to be adjusted to suit your needs.

There are loads of options to the mount command, for details see the manual page

```
man mount
```When done with drive unmount with this

```
sudo umount /home/user/external
```
I liked your Idea (but didn't try it). Sorry I forgot to tell you that I want a command to add it on startup so that the drive will be mounted automatically.
Thanks.

---

### Post by IcarusR on 2011-05-04
Thanks, you could have been more precise with your question.
Try using google, the following page comes high up.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

