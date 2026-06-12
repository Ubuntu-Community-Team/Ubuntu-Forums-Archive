---
title: "2nd hard-drive"
date: 2009-01-17
forum: Hardware
---

### Post by shrekfx on 2009-01-17
I just installed Ubuntu and also formatted my 2nd hard drive with ext3. I see in GParted that the partition is /dev/sdb1 but when i go to places, I dont see the hard drive. How do i get it so i can use it.?

---

### Post by ac7ss on 2009-01-17
You will have to mount it.

```
man fstab
man mount
```

and I am sure there is a GUI method of doing this.

You will have to make a mount point directory for it and create an entry in /etc/fstab so that it will mount on startup. I use a second drive for my /home and the /etc/fstab entry is
```
UUID=f3853865-6ebb-447c-9d3c-9ff8aac48da9 /home               ext3    defaults,errors=remount-ro 0       1

```

---

### Post by shrekfx on 2009-01-17
wow.. totaly confused me.. 

hehe

I'm very new to linux, like 4 days new. :)

---

### Post by ac7ss on 2009-01-17
You will have to wait till I get home to find the GUI way to do it. I am limited to an SSH from work.

---

### Post by shrekfx on 2009-01-17
That works... :) i'll search, might be able to find it.

---

### Post by fsierra3 on 2009-01-17
First create a directory where you want the second hard disk to be available: Type in a terminal
```
sudo mkdir /media/newdisk
```
Then mount it:
```
sudo mount /dev/hdb1 /media/newdisk
```

---

### Post by shrekfx on 2009-01-17
Hey, if you have time now.. dont know if you do, but you can give me step by step on mounting in terminal.. Since i'm using linux, should learn how to do it.

---

### Post by shrekfx on 2009-01-17
O.k. sweet. now will this load everytime i log in and stuff, or do i need to do this everytime i start?

sorry for all the noob questions.

---

### Post by fsierra3 on 2009-01-17
Go to Applications -> Accessories ->Terminal

And type:
```
sudo mkdir /media/newdisk
```

Then type:

```
sudo mount -t ext3 /dev/hdb1 /media/newdisk
```

The new disk will be available as a desktop icon from now on

---

### Post by shrekfx on 2009-01-17
o.k. i did it the first way you posted? was that o.k.?

also, when i go in there i see lost+found?  i just formatted it.. what would this be?

---

### Post by fsierra3 on 2009-01-17
lost+found: "Folder where salvaged scraps of files are saved in the event of a problematic shutdown and subsequent file system check"

And yes, in my first post I omitted the -t ext3 :( let me know if something goes wrong

---

### Post by Rhubarb on 2009-01-17
It's also possible to open up the other drive by going to:
Places --> Computer
Then double clicking on the hard drive you wish to open.

---

### Post by shrekfx on 2009-01-17
> **fsierra3 said:**
> lost+found: "Folder where salvaged scraps of files are saved in the event of a problematic shutdown and subsequent file system check"

And yes, in my first post I omitted the -t ext3 :( let me know if something goes wrong


Well right now i cant move anything to that drive, says i dont have autherization to do so.  Would i need to unmount it and then remount it.. and if so. how do i unmount it.

---

### Post by fsierra3 on 2009-01-18
Fortunately the omission of the file system type is not a fatal error, because if it is not specified the mount command guesses it.
To be able to copy files in the hard drive you have to change the ownership and permissions of the mount point:
```
chown yourusername /media/newdisk 
```
```
chmod u+rwx /media/newdisk
```

---

### Post by shrekfx on 2009-01-18
This is what i get..

tim@Ubuntu:~$ chown tim /media/backup
chown: changing ownership of `/media/backup': Operation not permitted

---

### Post by fsierra3 on 2009-01-18
preface it with sudo:
```
sudo chown tim /media/backup 
```

---

### Post by shrekfx on 2009-01-18
o.k. i must be doing something wrong for its still not working..

still says i dont have permition

---

### Post by fsierra3 on 2009-01-18
Try this
```
sudo chmod -R a+rwx /media/backup 
```
This will give permissions to read write and access the contents of the hard drive to everyone

---

### Post by ac7ss on 2009-01-18
Now, to make the drive auto mount, you will need to update the /etc/fstab file.

To do this: 
assume the drive to mount is /dev/sda1
and the mount point is /media/mounted (and already is chmod 777)

get the uuid of the drive (preferred method for identifying a drive)
```
$ ls -l /dev/disk/by-uuidtotal 0
lrwxrwxrwx 1 root root 10 2009-01-15 17:29 074f53af-2c61-4a80-b0d4-63a1b8440a6e -> ../../sdb5
lrwxrwxrwx 1 root root 10 2009-01-15 17:29 9497eac2-ce4f-49f2-87b3-0b0c8de487aa -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-01-15 17:29 f3853865-6ebb-447c-9d3c-9ff8aac48da9 -> ../../sda1
```
in this case the uuid for sda1 is ```
f3853865-6ebb-447c-9d3c-9ff8aac48da9
```
Edit the fstab file (from sudo) with a line like the following at the end.
```
# /dev/sda1
UUID=f3853865-6ebb-447c-9d3c-9ff8aac48da9 /media/mounted               ext3    defaults,errors=remount-ro 0       1

```The line starting with UUID ending with the 1 must be on one row, separated with tabs. I leave an empty line at the end of the file because some scripts require this. Be sure to substitute your value for UUID=.
This should make your drive mount each time you boot the computer.

---

