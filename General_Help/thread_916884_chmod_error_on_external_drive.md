---
title: "chmod error on external drive"
date: 2008-09-11
forum: General Help
---

### Post by gewitty on 2008-09-11
I've managed to do something that I thought was impossible (ignorance is bliss). I wanted to change the overall permissions for an external USB hard drive. I opened up a terminal and used chmod to set the drive as follows:

sudo chmod -R 766 /media/disk

This seemed to work OK and I got no error messages. However, I cannot access the disk at all now and when I check the Permissions tab in Properties, it says 'The permissions of 'disk' could not be determined'.

What stupid mistake have I made and how can I fix it?

---

### Post by HalPomeranz on 2008-09-11
I'm guessing you wanted to do "chmod -R 777 ..." instead of using mode 766.  "7" is "rwx" while "6" is "rw-".  Generally, the "x" bit on directories is extremely important-- without it you can't access the directory or any of the files and/or directories under it.

Still, making the whole drive world-writable is not generally good practice.  Better instead to change the ownership of the files on the drive so that they're owned by your user ID ("sudo chown -R ...").

---

### Post by gewitty on 2008-09-11
Thanks for the reply. I managed to get into the disk, so I can now see and access all of the contents. However, I still can't change the permissions, either with chmod or chown. 

I tried sudo chmod -R 777 /media/disk, which had no effect. So then I tried sudo chown dave /media/disk, which also had no effect. The owner is still shown as root and I am unable to create new directories or write to the disk.

---

### Post by HalPomeranz on 2008-09-11
Do you get an error message when you attempt to chown/chmod the disk?

What sort of file system is the disk formatted with?  If it's NTFS or FAT, then all your chown/chmod commands aren't going to make any difference.  You have to use options in your /etc/fstab file to set default ownerships and permissions, like so:

```

/dev/sda5  /media/shared   vfat    defaults,utf8,umask=007,uid=1000,gid=1000 0       1
/dev/sda1  /media/windows  ntfs    defaults,umask=007,uid=1000,gid=1000 0       1

```

---

### Post by gewitty on 2008-09-11
I get no error message. Just a return to the terminal prompt. The file system o the disk is ext3.

Odd, isn't it?

Perhaps it's worth adding that when I run chmod -R 777 /media/disk, the system runs through every file on the disk, but ends each line with an error saying that file permissions cannot be changed. When I run the same command, prefixed with sudo, I just get returned to the command prompt.

---

### Post by HalPomeranz on 2008-09-11
> **gewitty said:**
> 
Perhaps it's worth adding that when I run chmod -R 777 /media/disk, the system runs through every file on the disk, but ends each line with an error saying that file permissions cannot be changed. When I run the same command, prefixed with sudo, I just get returned to the command prompt.

Well chmod isn't going to print anything unless it encounters an error, so if you're getting no output it's theoretically working.  But when you do an "ls -l /media/disk" the perms on the files in that directory are not mode 777?

---

### Post by gewitty on 2008-09-12
The problem cleared after I shut down everything overnight and then re-started this morning. Obviously, it needed a reboot before the new permissions took effect, which is unusual.

Thanks for all the help anyway.

---

