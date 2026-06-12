---
title: "help: sata drivers loaded after init mounts fstab"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by wazoo42 on 2004-11-01
I have my linux partitions on an ide drive (hda), and I have two ntfs windows drives (sda and sdb).  BTW I am running the 64bit version, and I haven't run into this on suse 9.1 64bit or mandrake 10.0 64bit.  I can mount them just fine, but when I try to add them to fstab I get an error during init saying that the device /dev/sda1 does not exist (likewise for the other sata partitions).  I wrote a simple script to mount them after I get in, and I put a line in /etc/init.d/bootmisc.sh to run it.  This seems kludgy, and I was wondering if there is an easy way to tweak init's order to get the Silicon Image driver loaded before the fstab entries are mounted?

---

### Post by wazoo42 on 2004-11-01
bump for a new day

---

### Post by diebels on 2004-11-02
I guess running /etc/rcS.d/S35mountall.sh is failing becase some module that's loaded by /etc/rcS.d/S40hotplug is needed by the sata-drive. You could link an extra mountall.sh
```
chdir /etc/rcS.d && ln -s ../init.d/mountall.sh S40mountall.sh
```This would mount everything after hotplug has loaded the needed modules.
Don't think it hurts to remount, things that are mounted gets ignored.

---

### Post by wazoo42 on 2004-11-04
[QUOTE=diebels]I guess running /etc/rcS.d/S35mountall.sh is failing becase some module that's loaded by /etc/rcS.d/S40hotplug is needed by the sata-drive. You could link an extra mountall.sh
```
chdir /etc/rcS.d && ln -s ../init.d/mountall.sh S40mountall.sh
```This would mount everything after hotplug has loaded the needed modules.
Don't think it hurts to remount, things that are mounted gets ignored.[/QUOTE]

Thanks, all things considered though I don't know if this is any better than my hack.  I will give it a shot anyways.

---

### Post by spp on 2004-11-05
I am not sure if hotplug is your problem. But if it is and you need to load it earlier, run the following command:

```
mv /etc/rcS.d/S40hotplug /etc/rc5.d/S34hotplug
``` 

This will execute hotplug before mountall. Not tested so I can't be sure.

SP

---

### Post by ekravche on 2005-08-28
good advice. This seems to partially work for me. I get the fat32 drive connected to a raid controller to load at least. still having problems with the ext3 raid drive though.

---

