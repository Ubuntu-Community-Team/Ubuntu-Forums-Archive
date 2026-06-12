---
title: "Cannot format corrupted raspberry SD card on Ubuntu"
date: 2016-11-15
forum: Hardware
---

### Post by bunyaminsg on 2016-11-15
I was trying to install Raspbian NOOBS image on my SD card. I copied the files and plugged it to raspberry. While installing, there was a problem and I had to eject the card. Then, I tried to format it on my computer with Ubuntu. At first, it was recognizing the card and showing the partitions. Then, I tried to delete all partitions and create new one. But gparted could not delete all partitions. Now when I plug it to the computer and open gparted, it gives this error:

    > Error opening /dev/sdb: No such device or address

And gnome-disks shows the partitions at the beginning, but then it shows only one partition and when trying to format it gives: 

    > Error formatting volume
    Error wiping device: Command-line `wipefs -a "/dev/sdb2"' exited with non-zero exit status 1: wipefs: error: /dev/sdb2: probing initialization failed
     (udisks-error-quark, 0)

I also tried to delete and install Ubuntu on it with Ubuntu installation disk  but it gave 'input/output error'.Does anyone have an idea how to fix it?

---

