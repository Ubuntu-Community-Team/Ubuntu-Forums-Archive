---
title: "Simple Problem"
date: 2008-11-06
forum: General Help
---

### Post by jollygamer321 on 2008-11-06
Alright, I've set up multiple new partitions in fstab without any trouble, but for some reason I can't figure this one out. I'm had a fat32 partition set up and working and mounted in /data.  I could copy, paste, and do whatever.  I reformatted the partition to ext3 because I needed to support files larger that 1 GiB.  Now, I can't figure out how to get the permissions set right again to let me have control over that partition.  Whenever I try to paste files or create a folder it tells me permission denied.  Here's my current fstab line for it:

# /dev/sdb5
UUID=9c1d55ed-c475-4d28-b7ca-854d45bc8bd9  /home/luke/Data          ext3         auto,exec,user,rw,async  0      0  

What am I doing wrong? (I wanted it mounted were it is ever though originally I had it in /data).

---

### Post by kubug on 2008-11-06
Eventhough you may have it mounted in your home directory you still need to set owner and write/read permissions.

Once you boot up and the partition is mounted through fstab, put this in your terminal:

```

sudo chown luke /home/luke/Data

```

Enter your password, and you should be good to go. Please correct me if I am wrong. I am still learning too.

---

### Post by taurus on 2008-11-06
Personally, I would change the /etc/fstab to make /dev/sda5 to look like this.

```

UUID=9c1d55ed-c475-4d28-b7ca-854d45bc8bd9 /home/luke/Data ext3 defaults 0 0

```
Then, just change the ownership of that partition as

```
sudo chown -R luke:luke /home/luke/Data
ls -la ~/Data
```

---

### Post by jollygamer321 on 2008-11-07
Alright, the chown thing got the permissions fixed, but now I have a different problem.  When I use the default settings, it doesn't mount automatically.  Even if I put auto in there, it doesn't.

---

### Post by kubug on 2008-11-08
> **jollygamer321 said:**
> Alright, the chown thing got the permissions fixed, but now I have a different problem.  When I use the default settings, it doesn't mount automatically.  Even if I put auto in there, it doesn't.

Allright, after a bit of google-ing (is there such a word now?) it seems the general consensus is to add partition with ext3 like this:

> 
*UUID* /the/folder ext3 defaults,errors=remount-ro 0 1


So in your instance it would be:

> 
UUID=9c1d55ed-c475-4d28-b7ca-854d45bc8bd9 /home/luke/Data ext3 defaults,errors=remount-ro 0 1


If that doesn't work, check your UUID with this command:

> 
blkid


---

