---
title: "Hard drive label"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by kwylez on 2007-04-30
I have a second internal IDE hard drive that is formatted FAT32.  My Fiest Fawn installation sees the drive perfectly.  I have an entry in fstab that puts the drive's mount point to /mnt/data.

When I boot the machine up I see the drive on my desktop as /mnt/data.  How do I change the label for the drive to just display "Data"?

Thanks,
Cory

---

### Post by jimbob on 2007-04-30
Try making a directory named /Data, giving it rwx privileges and changing your /etc/fstab to mount it there instead.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

