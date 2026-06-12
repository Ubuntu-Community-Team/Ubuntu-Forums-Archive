---
title: "moving /var and /tmp to a separate partition."
date: 2008-08-16
forum: General Help
---

### Post by sefs on 2008-08-16
Hi all I currently have this installation here with two partitions.

"/" and "/home"

I want to shrink the "/home" partition and create a third partition and put "/tmp" and "/var" on it.

Is this possible.  Is it ok to do this and finally how exactly would i do it and transfer what is currently in /tmp and /var to their new location.

Thanks.

---

### Post by cdtech on 2008-08-16
> **sefs said:**
> Hi all I currently have this installation here with two partitions.

"/" and "/home"

I want to shrink the "/home" partition and create a third partition and put "/tmp" and "/var" on it.

Is this possible.  Is it ok to do this and finally how exactly would i do it and transfer what is currently in /tmp and /var to their new location.

Thanks.

Yes, it is very much suggested to do it in this manor, especially if your running a server.

I would suggest using the "gparted live cd" since your working with your "/" root partition. The "/var" caches packages in "/var/apt" so if you install a lot of packages without cleaning it up, it could take a lot of spaces (just something to keep in mind). Also if you run a web server "/var/www" will fill up as well.

As far as transferring the data, I would use the "dd" command (you can check out the link in my signature for information on using the dd command).

Hope this helps........

---

### Post by sefs on 2008-08-16
so let me be certain...

1) reboot into knoppix for instance...

2) create / resize or whatever have you ....

3) mount /

4) use dd to copy /var /tmp to new partition

5) remove /var /tmp from  / and replace them with simlinks t the new locations.

Do i have to do any other special thing....

I ask because in the /home partition move tutorial here I see the guy using some strange looking commands....for instance 

```

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

```

... and i am wondering if i have to do any strange commands like this.

---

### Post by az on 2008-08-16
Since you want to copy files from one partition to another, you should just copy the files.  dd is useful for dumping the contents of an entire partition and that's not what you want to do here.  So don't use dd.

So, create the partitions, mount them as something else temporarily, move the data there, (delete it from the / partition once it is copied or else you will not recover the disk space) and then mount the /var and /temp partitions.

But honestly, you are shooting yourself in the foot.  You may have to repartition again and again as your needs for space change.  Why not just get rid of your home partition and let everything share the same partition?  You will not short-change yourself out of space that way.  

Backing up your home is not any less complicated by putting it on a different partition.

---

### Post by bingoUV on 2008-08-16
First of all, if you don't know how to do this, probably you do not need to do this. It does not matter for most users. By the time it matters to you, you generally know how to do this. So please let us know why you want to move /tmp and /var to different partition.

> **sefs said:**
> so let me be certain...

1) reboot into knoppix for instance...

2) create / resize or whatever have you ....

3) mount /

4) use dd to copy /var /tmp to new partition

5) remove /var /tmp from  / and replace them with simlinks t the new locations.

Do i have to do any other special thing....

I ask because in the /home partition move tutorial here I see the guy using some strange looking commands....for instance 

```

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

```

... and i am wondering if i have to do any strange commands like this.


4. Not use dd. dd is useless for you. Use cp, or just drag and drop files. You will not have much to preserve from tmp anyway. 

5. After you have copied contents of erstwhile /var and /tmp to their new partitions, remove these directories from erstwhile /. No symlink, no nothing. Make fstab entries for /tmp and /var. You will find fstab in your erstwhile /etc. Make entries like
```

/dev/sdXn /tmp ext3 defaults  0 0

```

replace sdXn to the correct partition for /tmp. Similarly for /var.

Now when you boot into Ubuntu, you will get /tmp and /var.

---

### Post by sefs on 2008-08-16
I'm out of disk space on the root partition and /var is taking up a lot of space so i wanted to move it to another place and do /tmp at the same time.

I am in knoppix doing all this moving around and have run into a snag.

when knoppix boots it does some weird thing with fstab by changing it to the knoppix way of things.

So if i sudo nano fstab..i get the knoppix fstab

if i nano fstab i get the correct fstab, but then I can't edit it because its read only.



Another question is I see them using the UUID format in fstab.  How do I get the UUID for new partitions?

---

### Post by az on 2008-08-16
> **sefs said:**
> I'm out of disk space on the root partition and /var is taking up a lot of space so i wanted to move it to another place and do /tmp at the same time.

I am in knoppix doing all this moving around and have run into a snag.

when knoppix boots it does some weird thing with fstab by changing it to the knoppix way of things.

So if i sudo nano fstab..i get the knoppix fstab

if i nano fstab i get the correct fstab, but then I can't edit it because its read only.



Another question is I see them using the UUID format in fstab.  How do I get the UUID for new partitions?


Are you mounting the target partition and editing the fstab there or are you trying to edit the /etc/fstab from the knoppix ramdisk?

To get the volume id for sda1, run

vol_id -u /dev/sda1

---

### Post by bingoUV on 2008-08-16
I assume you are using knoppix as only a live environment, and you have not installed knoppix.

In knoppix live environment, you need to mount the partition that was / in Ubuntu. If you don't know this, check the output of the following in Ubuntu
```

mount

```

There will be a partition, somewhat like /dev/sda2, corresponding to /. Use this. e.g. if it was /dev/sda2, do the following in knoppix
```

mkdir slash
sudo mount /dev/sda2 slash

```

After this, examine the directory slash to make sure it is indeed your / partition. The fstab you have to edit is slash/etc/fstab.

---

### Post by sefs on 2008-08-16
Ok, I'm a little lost at this point

So I have the partition hda6 with /tmp and /var on it....

so I go ...

```

/dev/sda6 /var ext3 defaults  0 0
/dev/sda6 /tmp ext3 defaults  0 0

```

?

What has me confused about this is that in the ubuntu partitioner when preparing partitions, it can allow me to mount /var or /tmp to hda6 but not both...and then that seems to me that it would place the contents of either in the root of hda6.  But what i want is them both to be on hda6 somewhat like hda6/var and hda6/tmp

Possible?


> 
5. After you have copied contents of erstwhile /var and /tmp to their new partitions, remove these directories from erstwhile /. No symlink, no nothing. Make fstab entries for /tmp and /var. You will find fstab in your erstwhile /etc. Make entries like
```

/dev/sdXn /tmp ext3 defaults  0 0

```

replace sdXn to the correct partition for /tmp. Similarly for /var.

Now when you boot into Ubuntu, you will get /tmp and /var.

---

### Post by az on 2008-08-16
One partition, one mountpoint.  You need to create a partition for /var and another one for /tmp.

To do it any other way would require you mount the partition as something else (/media/extra) and symlink /var and /tmp to /media/extra/var and /media/extra/tmp.  Messy.

---

### Post by sefs on 2008-08-16
Thank you to all muchly.

And I have added "erstwhile" to my vocab!

---

