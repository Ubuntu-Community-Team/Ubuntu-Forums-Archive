---
title: "Multiple kernel entries in boot menu - how to get rid of"
date: 2008-11-12
forum: General Help
---

### Post by Harry Muscle on 2008-11-12
What's the best way to get rid of the multiple kernel entries in the boot menu?  I know I can just edit the menu.conf file, but I'm assuming there's a reason why a new entry is created whenever a new kernel is installed ... instead of just replacing the existing entries.  So would the best approach be to uninstall the pervious kernel package (is that even possible, or recommended)?  What do other people do to keep things clean and tidy on that menu.

Thanks,
Harry

---

### Post by Idefix82 on 2008-11-12
If the newest kernel works fine then you can uninstall all the older ones. Simply locate the relevant entries in Synaptic by searching for the kernel version number and uninstall from there.

---

### Post by philinux on 2008-11-12
If you install startupmanager, it's in synaptic. You can choose how many kernels to keep. I always keep 2 since updates have been known to break stuff and the kernels dont take up much space. Startupmanager end up in System>admin.

---

### Post by geirha on 2008-11-12
> **philinux said:**
> If you install startupmanager, it's in synaptic. You can choose how many kernels to keep. I always keep 2 since updates have been known to break stuff and the kernels dont take up much space. Startupmanager end up in System>admin.

Actually, they do take up a bit of space, so I would recommend removing the oldest ones once in a while, but do keep at least two kernels around to be safe. The latest kernel-version in Hardy:
```

$ aptitude -F '%I %p' search linux-image-2.6.24-21
60,0MB linux-image-2.6.24-21-386                                                
61,9MB linux-image-2.6.24-21-generic                                            
68,8MB linux-image-2.6.24-21-openvz                                             
62,0MB linux-image-2.6.24-21-rt                                                 
62,1MB linux-image-2.6.24-21-server                                             
26,1MB linux-image-2.6.24-21-virtual                                            
63,7MB linux-image-2.6.24-21-xen                                                                                   

```

---

### Post by Harry Muscle on 2008-11-13
Thanks everybody.

Harry

---

