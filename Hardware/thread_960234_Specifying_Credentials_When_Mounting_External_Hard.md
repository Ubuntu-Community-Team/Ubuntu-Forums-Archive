---
title: "Specifying Credentials When Mounting External Hard Drive"
date: 2008-10-27
forum: Hardware
---

### Post by simonfiction on 2008-10-27
Hi,
I have an external hard drive that was hanging of an NSLU2 Unslung NAS device. I need to access the files on it directly but when I plug it into my Ubuntu desktop machine I can simply list the files and directories but not read or write to them. I'm assuming I have to somehow provide my credentials to get that level of access but I'm unsure how I mount the drive with my NAS device credentials.

Any help would be much appreciated.

- Si

---

### Post by pelle.k on 2008-10-27
You need to supply more information. How are you connecting this drive now? Are you going to continue using it in the NAS? What file system?

---

### Post by simonfiction on 2008-10-27
I'm not using the NAS anymore (for now). I'm attempting to access it directly (plugging the hard drive in via USB to my desktop PC, letting Ubuntu do it's automatic detecting and mounting). I'm relatively certain it's an ext2 filesystem. Although I'm not home to double check that right now.

Let me know if there's anything else I can provide.

---

### Post by pelle.k on 2008-10-27
Then you probably need to "own" the filesystem. No need for mounting with parameters.
A new filesystem is owned by root, and in your case it's an old filesystem, and it's probably owned by the root (or another user) of the NAS.

Method 1.
This way you "own" the files on the drive. You cant really undo it. Well you can chown it to root again, but the action is recursive (it goes into subdirs) so it's not going to be exactly as it was.
**Please understand what you are doing, before you enter this command**
```
sudo chown -R <yourusername>:<yourusername> /media/<mountpoint>
```

Method 2.
You may mount it using fstab (if always connected), or if you right click the drive on the desktop > volume tab > settings, mount using the "acl" option. That way you can use acl to set up read/write even though the filesystem is owned by root.
```
sudo setfacl -R -d -m g:plugdev:rwx <mountpoint>
sudo setfacl -R -m g:plugdev:rwx <mountpoint>
```

Good Luck!

---

