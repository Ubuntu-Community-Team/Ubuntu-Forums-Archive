---
title: "USB hard drive disappears"
date: 2010-09-02
forum: Hardware
---

### Post by PatrikG on 2010-09-02
I have added a LaCie USB hard drive to my desktop running Karmic.

I can list it with ls -l /dev/disk/by-uuid, and then I mount it with the UUID, and shortly afterwards it disappears totally. After an unmount I can't see the drive for a while, and then it pops back in again, like below:

```
patrik@patrik-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 0f0afba9-e83a-47fe-a3ce-61afafa6dff3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 18953995-0744-4de4-a5c5-7fb88cb1e5da -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 27f4d688-43e5-41da-b26c-44e6bbe670d4 -> ../../sda1
patrik@patrik-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 0f0afba9-e83a-47fe-a3ce-61afafa6dff3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 18953995-0744-4de4-a5c5-7fb88cb1e5da -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-09-03 00:18 27f4d688-43e5-41da-b26c-44e6bbe670d4 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-09-02 22:31 3CC3-44E0 -> ../../sdc4
lrwxrwxrwx 1 root root 10 2010-09-02 22:31 DA14BBBD14BB9AC9 -> ../../sdc3

```

I have tried adding it to fstab, but then it doesn't show up at all.

It's formatted as NTFS it that would make a difference. And there are two partitions on it, hence both sdc4 and sdc3 in the list above.

---

