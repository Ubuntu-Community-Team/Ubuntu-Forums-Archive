---
title: "External Hard Drive read-only"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by erasmo.da.rotterdam on 2007-03-22
Hi!!:KS 
I recently bought an external 500Gb Maxtor hard drive.
With the old Windows XP I saved on it some Gb.:popcorn: 
My always improving Ubuntu recognize it and I can even browse its content, unfortunately I cannot write on it. The device seems to be read only.:( 
I looked for hidden file and I discovered that there is some sort of system thing to help my Maxtor recovery or to function properly so I am not sure if it'd be a good thing to format everything with an ext3 partition.
Can somebody tell me how to let my hard drive be written/readed by Ubuntu and Windows without damaging those system files?
Every help would be really appreciated

---

### Post by taurus on 2007-03-22
What filesystem is that external harddrive?  If it's ntfs, then you need to install ntfs-3g first before you can write to it; but if it's vfat, then you just need to mount it with the right arguments so you can write to it.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by erasmo.da.rotterdam on 2007-03-22
Thanks
It was NTFS
I have found this interesting thread
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
I'll try this path
All the best:)

---

