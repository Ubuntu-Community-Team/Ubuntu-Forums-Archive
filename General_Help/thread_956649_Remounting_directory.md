---
title: "Remounting directory"
date: 2008-10-23
forum: General Help
---

### Post by mohitkakkar on 2008-10-23
Hello,

I have a directory on a hard drive that is taking up a lot of space. I would to unmount it from the hard drive and remount it on another hard drive that is less full.

Can someone show me how to do this?

Mohit

---

### Post by Elfy on 2008-10-23
Assuming that you have both drives available, copy the directory from one to the other - use nautilus if you prefer the gui way.

Or I'm not understanding what you want to do or the problem you have.

---

### Post by mohitkakkar on 2008-10-23
Basically what I want to do is to mount the directory onto a new physical drive such that any programs using the directory do not have to be modified to go to the new physical location. I might need a pointer of sorts so I am not sure how to go about accomplishing this task.

---

### Post by Elfy on 2008-10-23
Is it a system directory or some data? I would just move the folder to the new drive. Is the drive installed and formatted - we can look at mounting it in fstab which will ensure it mounts at boot.

I am not at all sure what you mean by mount a directory on a new drive. Can you perhaps give a bit more information about what you're trying accomplish.

---

### Post by prshah on 2008-10-23
> **mohitkakkar said:**
> 
I have a directory on a hard drive that is taking up a lot of space. I would to unmount it from the hard drive and remount it on another hard drive that is less full.


> Since Linux 2.5.1 it is possible to atomically move a mounted  tree  to
       another place. The call is
              mount --move olddir newdir
 from ```
man mount
```-- worth a read!

---

### Post by snova on 2008-10-23
I think the OP is confused as to what "mount" means. To "mount" is the process of binding a partition or disk drive to a directory on the filesystem. For example, on my system two partitions are automatically mounted at boot- /dev/sda1 is put on / and /dev/sda3 is mounted in /home. This is the default configuration for my installation.

If you want to move a large directory to another drive without breaking compatibility, simple move it and create a link. But this won't work for certain folders. It depends on where it is. What directory in question is taking up too much space?

---

### Post by mohitkakkar on 2008-10-23
> **snova said:**
>  What directory in question is taking up too much space?

A user created directory. How would we go about it moving it and creating the link. Moving is easy--I can use Nautilus. How do I create the link?

---

### Post by snova on 2008-10-23
Well, Nautilus probably has some way of doing that. But as I don't use it, I don't know how, and there's also the risk that it will create the wrong kind of link. So from the command line:

```
ln -s /new/location/of/directory /location/of/link
```

---

### Post by mohitkakkar on 2008-10-23
> **snova said:**
> 

```
ln -s /new/location/of/directory /location/of/link
```

So the /location/of/link should be the original location of the directory right? That way when programs go check that directory they can be directed the new location.

---

### Post by snova on 2008-10-23
Yes. Unfortunately my example assumes that you always mount the drive at the same place. It also assumes the device is always mounted (the link will still work, it'll just point to a nonexistent directory on an unmounted partition).

An alternative method would be, if the partition you're moving it to only contains this folder, you could mount the entire partition on the folder in question. It would involve changing /etc/fstab to add an entry something like this:

```
/dev/DEVICE /place/to/mount <FSTYPE> defaults 0 0
```

Be careful...

---

### Post by mohitkakkar on 2008-10-23
> **snova said:**
> Yes. Unfortunately my example assumes that you always mount the drive at the same place. It also assumes the device is always mounted (the link will still work, it'll just point to a nonexistent directory on an unmounted partition).

An alternative method would be, if the partition you're moving it to only contains this folder, you could mount the entire partition on the folder in question. It would involve changing /etc/fstab to add an entry something like this:

```
/dev/DEVICE /place/to/mount <FSTYPE> defaults 0 0
```

Be careful...

One thing I might not clear about...in your example where you used your ln -s command, would the command look like the following assuming I have a sdb1 parition on the new drive, a home/mohit/backup on sdb1 and have a /home/mohit/databases directory on my original machine. (I will be running the ln command from the sdba drive)

ln -s /sdbl/home/mohit/backup /home/mohit/databases

---

### Post by mohitkakkar on 2008-10-23
I reposted the above post in this one by accident...so I just deleted it to avoid confusion.

---

### Post by snova on 2008-10-23
Yes. That should work.

---

### Post by mohitkakkar on 2008-10-24
Thanks...

---

