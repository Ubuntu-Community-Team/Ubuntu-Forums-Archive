---
title: "Unable to mount sata drive"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by eggzenbeanz on 2006-10-21
hi,

I have recently decided to play with linux. I have been messing with freespire for a week or so with some success. But the samba side of things was a little flaky! - so i thought id give ubuntu ago.

My problem: I have 2 x sata drives which were formated to ext3 in freespire, and all my divx and mp3s loaded bak onto them. These drive were accessable in freespire. However, now that i have installed ubuntu (latest release) i cannot access the drives. When i go into "computer" to view drive contents i get error message when try to open

error: device /dev/sdb1 is not removable

error: could not execute pmount

How can i get the drive mounted? i want to then share folders within these drive over samba? any help would be great.

m

---

### Post by taurus on 2006-10-21
Did you remember to mount them first before you try to access them?  What does your /etc/fstab look like then?  Otherwise, try something like

```

sudo mkdir /media/first_drive /media/second_drive
sudo mount -t ext3 /dev/sda1 /media/first_drive
sudo mount -t ext3 /dev/sdb1 /media/second_drive
df -h

```

---

