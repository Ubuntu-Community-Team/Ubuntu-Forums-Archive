---
title: "changing the uuid"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by renkinjutsu on 2009-07-03
I recently got a new harddrive, so i backed up my previous drive into a tarball.. I extracted the contents onto my new harddrive and everything works fine but..

every time i install a new linux image, it likes to add a new grub entry, and every time it adds an entry, the UUID in those entries are incorrect(it's possibly using the UUID from my previous drive), resulting in a GRUB "file not found" error, unless i remember to fix it.  This is very inconvenient and i don't want to keep having to fix my menu.lst

is there anyway for me to tell the system what the correct UUID is? Right now it's assuming one that is incorrect (possibly my old drive's UUID) How can i change that?

---

### Post by ad_267 on 2009-07-03
You'll probably want to change this section of your menu.lst:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6faaa026-e45f-4437-98b2-64a7f58d0eb9 ro vga=775

## default grub root device
## e.g. groot=(hd0,0)
# groot=6faaa026-e45f-4437-98b2-64a7f58d0eb9
```

Like it says, you don't uncomment the lines, just change them.

---

