---
title: "Cannot Delete Files on External Drive"
date: 2008-10-15
forum: Hardware
---

### Post by spawn. on 2008-10-15
Awhile ago I made a backup of important files in a previous configuration of Ubuntu 8.04. I saved my Home directory onto an external hard drive. Well I did a clean install of Ubuntu; but when I connect my external hard drive to the computer, the files I copied into my new install could not be deleted on the external hard drive. When I tried to delete them, they went into my trash bin. When I emptied my trash bin, they remained. However, when I disconnect the external hard drive from the computer, my trash bin is empty and all is well.

Is it possible to reformat my external hard drive disk using my GParted Live CD?

Added: Permissions aren't recognized on the external.

---

### Post by serian on 2008-10-15
> **spawn. said:**
> Awhile ago I made a backup of important files in a previous configuration of Ubuntu 8.04. I saved my Home directory onto an external hard drive. Well I did a clean install of Ubuntu; but when I connect my external hard drive to the computer, the files I copied into my new install could not be deleted on the external hard drive. When I tried to delete them, they went into my trash bin. When I emptied my trash bin, they remained. However, when I disconnect the external hard drive from the computer, my trash bin is empty and all is well.

Is it possible to reformat my external hard drive disk using my GParted Live CD?

Added: Permissions aren't recognized on the external.

Show me output from command:
```
sudo ls -l /media/<external drive>
```

---

### Post by spawn. on 2008-10-15
```

Home@computer:~$ sudo ls -l /media/
total 36
lrwxrwxrwx 1 root       root     6 2008-10-13 12:12 cdrom -> cdrom0
drwxr-xr-x 2 root       root  4096 2008-10-13 12:12 cdrom0
drwx------ 3 Home       root 32768 1969-12-31 19:00 WD 250GB

```

---

### Post by spawn. on 2008-10-15
I noticed something else. I decided to plug-in a 2GB SD Device. When I opened the device, there was a file in it. I deleted the file and it was sent to my Trash bin. However, the same thing happens as with the external hard drive.

Added: Unlike the external hard drive, where deleted files remain in the Trash bin (while the device is still connected), when the files of the SD Device are deleted from the Trash bin, they no longer appear.

The symbols appearing on the "deleted" file folders are:  $RECYCLE.BIN (External hard drive) and .Trash (SD Device)

Let me guess, those have recycling bins of their own...The only way around it is to click Ctrl + H to hide the files. Also, according to my GParted Editor, both media devices have 0% Used space.

---

### Post by spawn. on 2008-10-15
**SOLVED**: Sometimes the simplest answer is the best solution.

Go to Computer,
Right Click on the <mounted media drive>
Select 'Open as administrator'
Then delete away...

---

