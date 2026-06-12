---
title: "Problem with preseed and partman recipe"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by yaznar on 2009-04-08
Hi,

I try to install Ubuntu Server with PXE boot. And I have one problem with the partman recipe.

In my preseed.cfg I have this :
```
...
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/expert_recipe string root :: 8192 8200 8300 reiserfs $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ / } device{ /dev/sda } . 1024 1000 1024 linux-swap $primary{ } method{ swap } format{ } device{ /dev/sdb } .
d-i partman-lvm/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select
d-i partman/confirm boolean true
...
```

But, in fact I have the swap on sda2 and not on sdb1.

I think my partman recipe is good. And I do not understand why the swap partition are not on the good hard disk.

Do you have any idea or mistak i have made ?

---

