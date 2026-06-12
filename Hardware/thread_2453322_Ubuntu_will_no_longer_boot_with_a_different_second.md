---
title: "Ubuntu will no longer boot with a different secondary hard drive attached"
date: 2020-11-07
forum: Hardware
---

### Post by freqflyer on 2020-11-07
Some time ago I installed Ubuntu to 18.04 to an HP I7 computer. This was a dual boot Windows 10 installation. The primary hard drive was 500GB and contained windows and Ubuntu.  The second hard drive was a 4 terabyte hard drive that was formatted in NTFS.  Everything worked fine.

Then I decided I needed a larger secondary hard drive and I bought a 10 TB hard drive and formatted it in ext4 with one partition.

Now Ubuntu will not boot. Windows 10 boots just fine and I can see the 10tb hard drive and access it.  Also I can boot it from my Ubuntu USB installation stick and it sees both hard drives and lets me access them.

What is preventing me from being able to boot from the 500gb hard drive when the 10tb drive is attached?

Thank you.

---

### Post by QIII on 2020-11-07
Hello.

Did you modify your fstab to remove the old drive and add the new one?

---

### Post by freqflyer on 2020-11-07
I did not.  Is there a guide to modifying fstab

---

### Post by oldfred on 2020-11-07
Internal drive partitions are normally mounted with UUID or labels.
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL, uuid | egrep -v "^loop"
sudo blkid -c /dev/null -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

Your Windows will not see ext4 partition, so did you format it as NTFS?
And only one very large 10GB partition is harder to manage for backup. You do have another 10GB drive for backup?

If ext4 formatted, you also have to give yourself ownership & permissions to use it.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

