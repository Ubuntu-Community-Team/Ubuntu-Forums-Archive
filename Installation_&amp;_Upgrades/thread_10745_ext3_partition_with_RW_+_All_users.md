---
title: "ext3 partition with RW + All users"
date: 2005-01-10
forum: Installation &amp; Upgrades
---

### Post by Benn on 2005-01-10
Hi, recently i bought a new 80Gb harddrive  :mrgreen: . I properly installed under *ubuntu linux*, format it to **ext3** filesystem, and now i'm able to mount it. I wanted to be auto-mount on **startup**, and ***readeable-writable*** for all users. So i add the following line to my /etc/fstab file:

> /dev/hdb1          /mnt/hdb1          auto          rw,users,exec          0          0 

Now it mounts itself on startup and ALL the users are able to mount/umount that hd.

But the problem is that **normal users don't have write permissions**. How can I do this ? What should be added to fstab file ?

Thanks A Lot!!!!

---

### Post by twisted_steel on 2005-01-10
I believe you need to add  ```
umask=000
```

---

### Post by Benn on 2005-01-10
So, my new fstab line is:

>  /dev/hdb1 /mnt/hdb1 auto rw,users,exec,umask=000 0 0

Then, when mounting:

> $ mount /mnt/hdb1
mount: wrong fs type, bad option, bad superblock on
/dev/hdb1,       or too many mounted file systems

 :cry: 

Why ?

---

### Post by Benn on 2005-01-11
Which is the option I have to add in fstab file ?

---

### Post by twisted_steel on 2005-01-11
It looks like the option I suggested will not work for ext3 partitions, which is why it comes up with the errors wrong fs type, bad option.
   
   Looking at a [message]("https://www.redhat.com/archives/fedora-list/2004-December/msg03069.html") on the fedora mailing list gives one possible solution. You could create a directory on the filesystem as root and change ownership for your user. Another possibility is creating a new group and adding all users that need to write to this folder to that group.
   
   To change ownership, you can use the [chown]("http://www.die.net/doc/linux/man/man1/chown.1.html") command, which allows you to specify a user, and optionally a group.  To change the group only, use the [chgrp]("http://www.die.net/doc/linux/man/man1/chgrp.1.html") command.
   
 From what I've come across, you cannot mount the partition read-write for all users because it still uses the permissions of the files currently on it. Perhaps someone else has a more elegant solution.
  
   Hope this helps :D

---

### Post by Benn on 2005-01-11
Well, I've ereased 'umask=000' in fstab, then, I've changed /mnt/hdb1 permsissions and tried to make a dir but stills don't work!

[I]> root $ chown -R myuser /mnt/hdb1
root $ chgrp -R myuser /mnt/hdb1[/I]

[I]> myuser $ mkdir /mnt/hdb1/foo
mkdir: can't create '/mnt/hdb1/foo' directory. Permission denied.[/I]

My necesity to make /mnt/hdb1 _*Writable/Readable*_ for all users is to share that partition with **SAMBA**.

---

### Post by ragu on 2005-01-28
Hi,

You probably allready have found a solution to your problem, but i have a similar problem which i have solved as follows. I create a directory as root, then give that directory full rights. This works for several distros. 

I am also interested in the SAMBA solution. Though i have only one PC, sharing between local users. So it might be too much work, setting up a SAMBA server???

/rasmus

---

### Post by Xanthous on 2005-06-22
[QUOTE=Benn]
My necesity to make /mnt/hdb1 _*Writable/Readable*_ for all users is to share that partition with **SAMBA**.[/QUOTE]

I also need help in this.

To make a second HD read/write and shared on the LAN.

Thank you!

BTW, I'm on  Hoary 5

---

### Post by Crypto on 2005-06-25
I've the same problem but need a solution, too :(

---

### Post by hellmet on 2007-07-01
Same here guys !!

---

### Post by egcv on 2007-07-02
Hi guys,

If you already have this problem, all you need to do is change permissions on the folder where you  mount your partition.

The command is:

chmod -R 777 /folder

Where "/folder" is the folder where you mount your partition

This will overwrite your defaults permissions in all your files and folders.

I hope this be usefully, and I'm very sorry about my english---:D

---

