---
title: "my vfat external usb 2.0 drive detected as ext3"
date: 2009-05-03
forum: Hardware
---

### Post by Nicezia on 2009-05-03
I haev an external usb harddrive, which is working fine in windows, but i'm trying to make the move to linux PERMANENT(not wanting to reformat my partitions though) however this drive which i keep all my data files is somehow being detected as a ext3 drive and blkid returns:
:(
```

/dev/sde1: LABEL="Media5" UUID="fc180b86-5708-474a-819f-99553520a1fb" SEC_TYPE="ext2" TYPE="ext3"

```

Its not listed at all in /dev/disk/by-label

```

ghost@Saturn:/dev/disk/by-label$ ls -l
total 0
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 MEDIA1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 Media2 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 Media3 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 MEDIA4 -> ../../sdc7
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 RESOURCES -> ../../sdc5
lrwxrwxrwx 1 root root  9 2009-05-03 09:55 Ubuntu\x209.04\x20i386 -> ../../sr1
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 WINDOWS -> ../../sda1

```

or by-uuid

```

ghost@Saturn:/dev/disk/by-uuid$ ls -l
total 0
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 01B5-01B7 -> ../../sdc7
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 1C81-D661 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 4b3726f3-2219-4565-87d7-6a5691ab81bf -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 66200EAB200E81F3 -> ../../sdc6
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 A1C6-704B -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 B604425004421431 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-05-03 14:55 C042-FED9 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2009-05-03 09:54 d6544008-079d-4902-9017-6f84840ecfb6 -> ../../sda6

```

this drive has never before been mounted or used on linux .. (until today)... I can mount it using the /dev/sde1 but that changes everytime i boot (since i use several external harddrives..) 

I need access to at least the label to have it mount in the same directory each time  i plug it in. 

I need a little help here.
I'm pretty decently involved in linux but this one has me stumped, and after spending 7 hours on google looking for a solution i figured this is the best place to turn:(

Edit: looking back at it Media 2 is also being detected as ext3 when its actually  vfat
I wasn't having this problem before i switched to 9.04 could it possibly be a bug in 9.04?

---

