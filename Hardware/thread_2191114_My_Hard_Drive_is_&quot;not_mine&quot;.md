---
title: "My Hard Drive is &quot;not mine&quot;"
date: 2013-12-01
forum: Hardware
---

### Post by joebutton64 on 2013-12-01
I've recent added some old hard drives to my pc and one drive has some files left on it and I am not able to move them to the trash or format the drive. I went to the porperties of the drive and it said the onwer is root, how do I get root access to the hard drive?
Thanks for the help!

---

### Post by deadflowr on 2013-12-01
Why move the files?
Why not copy them?
Then if the permissions stay root-owned change them when the are in your user folder.

If you plan on reusing the drive, then after copying the files reformat it.
Make sure to unmount the drive when reformatting.

---

### Post by heir4c on 2013-12-02
Have yo format it via the Disk-Utility?
Or you can format it via gParted (Partition Manager. You have to install it)

For changing the permissions you can open Nautilus with root.
Type in terminal:

 ```
gksudo nautilus
```
In that window you can rightclick on the disk and choose for the properties and change there the right.

---

### Post by joebutton64 on 2013-12-03
Thank you for the help! The drive has been reformatted and I can once again use it normally!

---

