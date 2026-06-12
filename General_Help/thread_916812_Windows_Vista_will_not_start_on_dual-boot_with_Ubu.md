---
title: "Windows Vista will not start on dual-boot with Ubuntu (Lenovo Thinkpad T61)"
date: 2008-09-11
forum: General Help
---

### Post by rjaguar3 on 2008-09-11
I recently installed Ubuntu over Vista on a Lenovo.  Unfortunately, after the install was complete, I found that my Windows partition was too small.  In any case, I shrank the Ubuntu partition and moved the Vista partition right 5 GiB to try to enlarge it with the free space.  Unfortunately, Vista will no longer load now (it displays the progress bar, then crashes into Lenovo's Rescue and Recovery).  Furthermore, Lenovo is too cheap to provide installation media, so I cannot reinstall Windows (without using their "tool" to restore the entire drive to the factory default).

I've tried ntfsfix to restore the partition.  I think the bootloader needs to be fixed, but I'm not sure how to do that.  Can anyone help me?

---

### Post by caljohnsmith on 2008-09-11
If you don't have any kind of Vista CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you have that, boot it, go to the command line, and do the following commands:
```

chkdsk /r
bootrec /fixboot
bootrec /rebuildbcd
```
Let me know how it goes, or what happens when you boot Vista after doing the above.

---

