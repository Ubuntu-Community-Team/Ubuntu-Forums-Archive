---
title: "Installing an internal ext3 hard drive"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by SaveMeFromXP on 2007-05-26
I have a Ubuntu only machine. I just added a second IDE hard drive and formatted it with GParted to ext3. After a reset, the disk appeared automatically in 'Computer' but I cannot write to the disk. When I go into the disk properties, it does not let me change them to 'read/write.' 

I searched around the forums and found many post on similar subjects (internal Hard Drives), but could follow them. They seemed to focus on mounting, which doesn't seem to be my problem. Is their an straightforward way to give me write permission on my HD?

---

### Post by taurus on 2007-05-26
Where do you mount the second harddrive, mount point?  You just need to change the ownership of that mount point from root to your login name.

```
sudo chown -R **username**:**username **/media/sdb1
```
Replace **username** with your login name and assume /media/sdb1 is your mount point.

---

