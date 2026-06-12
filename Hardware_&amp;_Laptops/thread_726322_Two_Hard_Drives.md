---
title: "Two Hard Drives"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by rocky5051 on 2008-03-16
This is a problem I've been putting off for a while. I have two IDE Western Digital 20gb hard drives. In addition to the main drive, I wish to have the second one mount and work so I can use it purely for extra storage purposes. However, every time I try to do something with it, it doesn't work.

For example, I have created an ext3 primary partition across this drive, and created the mountpoint /media/linuxstore/ for it. I go into the drive, and when I try to create a folder, Dolphin tells me that it failed to do so. (For the record, I use Kubuntu 7.10).

I can go to System Settings, and enable the drive, do all I want with it, and still I get no further. I know that the drive is fine since I used it on a previous machine with no problems.

If I use fdisk to list my drives, this is what I get.

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10311030

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x106c106b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+  83  Linux
```

(Of course, I have only cut out the two internal hard drives from the top of the list.)

The main drive is obviously sda, while the one I want to get to work properly is sdb.

Once again, thanks for any help in advance. :)

---

### Post by logos34 on 2008-03-16
Try this procedure:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by rocky5051 on 2008-03-17
I feel so stupid now. I neglected to punch in one line when I was changing the permissions of the drive.

```
**sudo chown -R justin:justin /media/linuxstore**
sudo chmod -R 755 /media/linuxstore/
```
(The bolded line being the one I didn't put in)

Well, thanks; I won't be forgetting that again. :lolflag:

---

