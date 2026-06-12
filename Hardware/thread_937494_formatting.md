---
title: "formatting"
date: 2008-10-03
forum: Hardware
---

### Post by jkale on 2008-10-03
alright i am trying to set up a fileshare server and i have 2 hard drives in it a 60gb and a 300gb i installed ubuntu on the 60gb and the i formated the 300gb with gpart to ext2 and then i cant write on it or anything what can i do to make the perrmission under my user?

---

### Post by nixscripter on 2008-10-04
If the first hard drive is **sda**, and the second hard drive is **sdb**, try this:

```

mkdir mydir
sudo mount /dev/**sdb**1 mydir
sudo chown **username**:**username** mydir
sudo umount mydir
rmdir mydir

```

The actual drive names may be different.

---

### Post by jkale on 2008-10-05
> **nixscripter said:**
> If the first hard drive is **sda**, and the second hard drive is **sdb**, try this:

```

mkdir mydir
sudo mount /dev/**sdb**1 mydir
sudo chown **username**:**username** mydir
sudo umount mydir
rmdir mydir

```

The actual drive names may be different.
this did nothing 

what my problem is i can't write on the hard drive and when i right click on the hd and hit the permissions tab it says 
"The permissions of "disk" could not be determined"

can someone plz help me been trying on and off to get this server up for sooo long

---

### Post by nixscripter on 2008-10-05
What I believe might be the problem is nothing with the drive itself.

It's that that the filesystem on the second drive is owned by root, mounted by root, and you don't have root permission. I'm trying to give your user permission.

In that case, what is the disk called in Gnome? If it were called **my disk**, there should be a directory called /media/**mydisk** where it's mounted. Try this: ```
 sudo chmod o+rwx "/media/**my disk**"
``` filling in the disk name.

---

