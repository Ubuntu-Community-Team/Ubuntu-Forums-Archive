---
title: "Cannot change permission on new Hitachi 3tb external drive"
date: 2011-01-04
forum: Hardware
---

### Post by sptrsn on 2011-01-04
3tb Hitachi external drive for $150! Amazing!

I'm running Ubuntu 10.04. 

Just bought the new drive. Took it to my friend who, using Win7, copied some files on the drive for me. Let's just call them large media files. 

I brought the drive home. It works flawlessly. Auto mounts. Files read fine. WD TV Live Plus reads it fine and I can copy and delete files from it. In short, great purchase.

However, I cannot change permission on anything. I'm trying to access it using AjaXplorer and it just refuses to cooperate. I'm pretty sure this is a permission issue since group and other have no permission, only me, the owner.

I've tried chmod as root. I acts like it's working fine, but alas there is no change made.
I've tried "gksu nautilus." The permission drop downs are there, but when you select them, they just dissapear and no change is made.
I plugged the drive into my Win7 machine. Added user "Everyone" and gave him "full control" then plugged it back into Ubuntu... no change. 

I'm stuck. Any ideas?

Thanks.

---

### Post by damphoud on 2011-01-04
Would sudo cp have any different permission handling? Although this probably wouldn't solve the original problem, even if it did work.

---

### Post by Fafler on 2011-01-04
It's acl related. I don't know what the exact solution is, but take a look at this: [http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)

---

### Post by sptrsn on 2011-01-04
Thanks Fafler. I'm guessing at this point...but you're probably right. 
The article you reference has a link to a tool called usermap that looks like it might be able to help me fix the problem, but it seems ultimately awkward. 

What do you think about this idea?? I'm using 2tb on a 3tb drive. If I could format that empty 1tb as linux, move 1tb over from the windows partition, then expand the linux partition, then move the 2nd tb over to linux, then finally expand the partition to use the whole drive. In theory, I could get rid of the windows partition and permissions altogether.

Now the problem I have is that gparted doesn't see the drive. Is that an easier fix from your perspective.

Is there another partition tool that might recognize the drive?

Thanks..

---

### Post by psusi on 2011-01-04
Windows filesystems do not support unix permissions.  You have access so why are you trying to change them anyhow?  No problem here, move on.

---

### Post by Fafler on 2011-01-04
It's possible to do it with the command line tools, but i don't really know how to do it without gparted. If we can't make gparted work, i can look into it.

Are you running gparted as root? Can you choose any other devices in the upper right corner?

Second, harddrives aren't necessarily partitioned, so the first thing you should check is that your drive is. With the drive connected:
```
cat /etc/mtab | grep media
```

It should return a devicename, like /dev/sdb or /dev/sdc1. If it ends with a number, the drive is partitioned and can be resized. If it doesn't there's probably no practical way in can be done.

---

### Post by sptrsn on 2011-01-04
Upon launching gparted from the command line as root, (good call on that), I got an additional error msg that did not manifest when launched from the pull down menu. 

"Ignoring device /sda/sdc with logical sector size of 4096 bytes because gparted only supports a size of 512."

So that answers that question. So I guess for now, I'll just have to live with it. Not the end of the world. 

Thanks Fafler. 

And Psusi, I was trying to allow a third party application to access the data. When it didn't work I assumed it was a lack of permission.

---

