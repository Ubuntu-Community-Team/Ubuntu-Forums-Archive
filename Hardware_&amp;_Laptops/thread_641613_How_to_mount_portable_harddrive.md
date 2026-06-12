---
title: "How to mount portable harddrive?"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by BennieBlount on 2007-12-15
I have a Maxtor external hard drive that I can read from but when I try to write to it I get a message that tells me I do not have permission to write to it.

It is formated with Linux ext2.

How do I get permission to write to this drive?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Thanks,

Bennie

---

### Post by taurus on 2007-12-15
Do you mount where that external harddrive is being mounted to, the mount point?  _Assuming_ it's /media/disk, you just change the ownership of that mount point from root to your login name.

```
sudo chown -R **username**:**username** /media/disk
```
Replace **username** name with the actual name that you log in.

If you are not sure what the mount point is, just post the output of this command here.

```
df -h
```

---

### Post by BennieBlount on 2007-12-15
Thank you! That did it.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

Bennie

---

