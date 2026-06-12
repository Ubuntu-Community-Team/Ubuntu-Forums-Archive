---
title: "[SOLVED] Convert an NTFS partition to ext3"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by hunter_te on 2008-04-02
[IMG]http://img232.imageshack.us/img232/2237/31639318mp1.jpg[/IMG]

Do u see that 30GB empty partition formatted with NTFS..

Yah right, that one.

I want to format it to ext3 and want ubuntu to install all new programs into it. How?? :confused:

Thanks in advance... :popcorn:

---

### Post by wieman01 on 2008-04-02
You need to format it using GParted, the partition editor. But you cannot just install programs on it. Simplest way to achieve this would be merging it with the root partition. 

But this could turn out to be tricky because your HD's aren't in sequence. Is merging an option?

---

### Post by Gen2ly on 2008-04-02
Forget me noobishness, but couldn't this partition be formatted and then specified in the fstab???  For instance:

```
/dev/sda4   /usr/bin            ext3        noatime,errors=remount-ro   0 1
```

Current "/usr/bin" files would have to be copied onto "/dev/sda4" after sed act and before rebooting machine.

I'd consider a bit before doing this though hunter as 30GB is a fair amount for "/usr/bin".  However, many users eventually put "/home" on a seperate partition (there's some tutorials around) that would alleviate some space on "/" (root).

---

### Post by hunter_te on 2008-04-02
Thanks for replying wieman and Dirk.

It would be more nice if i could merge the 9GB ext3 with 30GB....but as u said, they are not in sequence.

I am still using XP for couple of things, so dont want to format other drives...

I was thinking if its possible to move my /home directory to that 30 gig partition after formatting it with ext3....

@ dirk, 

That code went above my head. And ya, as u said, most people put /home in seperate partitions, thats what i want to do. Actually i would be updating to hardy once it comes out and i dont want to download all the tit-bits again. So......

---

### Post by wieman01 on 2008-04-02
> **Dirk.R.Gently said:**
> Forget me noobishness, but couldn't this partition be formatted and then specified in the fstab???  For instance:

```
/dev/sda4   /usr/bin            ext3        noatime,errors=remount-ro   0 1
```

Current "/usr/bin" files would have to be copied onto "/dev/sda4" after sed act and before rebooting machine.

I'd consider a bit before doing this though hunter as 30GB is a fair amount for "/usr/bin".  However, many users eventually put "/home" on a seperate partition (there's some tutorials around) that would alleviate some space on "/" (root).
Yes, you could do that as well. I generally don't like to do such thing, but under the circumstances this is the best advice.

In fact you could also move the **root **partition there.

---

### Post by Gen2ly on 2008-04-02
hunter, if you do decided to move the "/home" directory here are a couple tutorials:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.ibm.com/developerworks/library/l-partplan.html](http://www.ibm.com/developerworks/library/l-partplan.html)

I personally have used the first one and it worked without any problems.  The second  although is more thorough.  If using the second I'd recommend formatting using the journaled ext3 rather than it's unjournaled couterpart (ext2).

```
mkfs.ext3 /dev/partition
```

or use was wieman suggested and use Gparted for formatting.

The device/partition will then need to be specified in the "/etc/fstab" file (like the line above) and then the system will need to be rebooted so it can recognize the new partition.

---

### Post by prshah on 2008-04-02
> **hunter_te said:**
> 
I want to format it to ext3 and want ubuntu to install all new programs into it. How?? :confused:

Thanks in advance... :popcorn:

My suggestion: 

You cannot "format" a partion from NTFS to ext3. Delete it in GParted or somesuch; then creat a ext3 partition with the mount point "/media/extra" or whatever name you like.

It will automatically show up in your "/" filesystem at whatever mount point you have specified.

It's better you do not specify an EXISTING mount point such as "/home" "/usr/bin" etc, since then you will have to manually move the directory into your new partition while still on the live CD.

---

### Post by Gen2ly on 2008-04-02
nice tip about NTFS partitions prshah, I wasn't aware of that.  He will need to specify a partition though as he's trying to free up space in / (root).  Though I agree parshah that it is easier to create another partition and store extra files in there.

---

### Post by hunter_te on 2008-04-03
prshah, i was doing what u said........ 

And now ran into this

[http://ubuntuforums.org/showthread.php?p=4642577#post4642577](http://ubuntuforums.org/showthread.php?p=4642577#post4642577)

This is some other problem, but please help..

---

### Post by prshah on 2008-04-03
> **hunter_te said:**
> prshah, i was doing what u said........ 

And now ran into this

[http://ubuntuforums.org/showthread.php?p=4642577#post4642577](http://ubuntuforums.org/showthread.php?p=4642577#post4642577)

This is some other problem, but please help..

Post #2 in that thread (by Weiman01) gives you the solution

---

