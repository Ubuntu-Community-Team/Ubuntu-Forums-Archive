---
title: "unable to mount volume-ntfs"
date: 2008-08-06
forum: General Help
---

### Post by yenson on 2008-08-06
hello i havin this prob,i wanted to access the file inside but i couldnt,i tried ntfs config tool,any1 know how to solve it,appreciated
[IMG]http://img504.imageshack.us/img504/7530/screenshotgnomemountca0.png[/IMG]

---

### Post by sklyer on 2008-08-06
Did you try sudo?

If you want all users to have read-write access, try this:

sudo mkdir /media/windows (or whatever you want the drive to be called)
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,unmask=000

Where /dev/hda1 is the location of the ntfs drive

Hope this helps.

---

### Post by yenson on 2008-08-07
hi thx 4 help,but the problem is,i dont even know the location of the drive,how can i locate the drive?:(

---

### Post by cdtech on 2008-08-07
Open a terminal and type "sudo fdisk -l"

---

### Post by yenson on 2008-08-07
i am very appreciate for all the help,my problem solved:guitar:

---

