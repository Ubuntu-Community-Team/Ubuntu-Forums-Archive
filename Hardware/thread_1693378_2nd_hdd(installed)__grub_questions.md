---
title: "2nd hdd(installed)  grub questions"
date: 2011-02-22
forum: Hardware
---

### Post by Dutch70 on 2011-02-22
Hello everyone, 
 I dual boot Ubuntu & vista in a 360GiB sata hdd. I just installed a secondary 500GiB sata hdd. So far I just put it in & plugged it in. Deleted the old vista partition & left the recovery partition for now.

I choose which disk to boot by hitting "esc" to load boot options, then arrow keys to select the disk. Is there a better way? 

 Also, a bigger problem is, when I choose my 360GiB dual boot hdd, and select Ubuntu from the grub menu. It used to say this for about 5-10 sec...```
resume libgcrypt version: 1.4.5
``` and then boot up, but now it follows to...
```
resume could not stat the resume device file '/dev/sda6' 
Please type in the full path name to to try again 
or press ENTER to boot the system
```

When I hit enter it continues to...
```
>*some numbers I didn't catch*< Ext4 fs sdb5 mounted file system with ordered data mode. Opts: (null)
```

It loads after that :) but that is a loooong process & I'd really like to find out how to get rid of the libgcrypt 1.4.5 anyway. It mysteriously started about 2 weeks ago. How can I fix this? 

Sorry for the long post. 
Can anyone help me figure this out?

---

### Post by Dutch70 on 2011-02-23
Does anyone have any idea how to get rid of that libgcrypt 1.4.5?
 
 I have googled til I'm blue in the face and the only thing I can find is other libgcrypt11, something to do with hibernation.

---

