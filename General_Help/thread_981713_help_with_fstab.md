---
title: "help with fstab"
date: 2008-11-14
forum: General Help
---

### Post by jonny.milano on 2008-11-14
k, please don't flame me here. i've tried 20 times and i'm really into learning the command line but could someone please help me write a line for my fstab file? whenever i start my computer, it gives me an error (different ones depending on how i edit the fstab file) and the drive doesn't mount. i want a line that will mount /dev/sda1 on /media/disk2. it's an ext3 file system on a ide drive. i want to mount it so that all users can read, write, and delete files. 

can someone please help!?

thank you in advance.

---

### Post by Zack McCool on 2008-11-14
Sure...

In /etc/fstab (sudo nano /etc/fstab): ```

/dev/sda1  /media/disk2  ext3  relatime  0  0 
```

Then, make sure that /media/disk2 exists...

Once you know it is there, mount the filesystem: ```

sudo mount /media/disk2 
```
Of course, enter your password...

Once the drive is mounted, you can set permissions on any directories in there with chmod and chown, depending on your needs.  For instance, you could do the following to give owner, group and everyone else read write and execute for all the subdirectories currently present on the drive: ```

sudo chmod -R 777 /media/disk2 
```

Hope that helps!

---

### Post by jonny.milano on 2008-11-14
thanks you SO much!!! this helps me immensely. i think that i was looking at older versions of how to edit fstab. i never saw relatime. thanks!!!!!!!

---

### Post by bigbrovar on 2008-11-14
@Zack McCool  beat me to it :lolflag:

---

