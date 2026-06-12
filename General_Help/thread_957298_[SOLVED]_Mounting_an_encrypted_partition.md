---
title: "[SOLVED] Mounting an encrypted partition"
date: 2008-10-24
forum: General Help
---

### Post by jameskinds on 2008-10-24
Hi all,

When I setup Ubuntu on my machine I used the alternate install CD and setup an encrypted partition.

I have made an image of this partition using DD.

Ok so far so good. Now I boot into Ubuntu and want to try and mount this backup image.

I have tried "mount /media/disk/dd_image_file /mnt/mountpoint" but received an error message that said "unknown filesystem type 'crypto_LUKS'"

So I did a bit of digging on the forums and then tried the following:

 sudo cryptsetup luksOpen /media/disk/dd_image_file /mnt/mountpoint

but then I received the following error message "Command failed: Can't get device information.".

At this stage I am out of ideas. I know the image file was created correctly with DD. Oh, and I imaged the encrypted partition only into the file.

Can anyone help me and tell me what I need to do to mount the DD_Image_File so that I can obtain some files that are in the backup.

Thanks in advance.

Regards,

James.

---

### Post by Bucky Ball on 2008-10-24
[http://swik.net/mount+ntfs](http://swik.net/mount+ntfs)

[http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/](http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/)

[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

They should give you a few clues. You could tell me ... what is DD?

---

### Post by hyper_ch on 2008-10-24
you're using cryptsetup wrongly:

```

sudo cryptsetup luksOpen /media/disk/dd_image_file dd_image_file
sudo mount /dev/mapper/dd_image_file /mnt/mountpoint

```
And when you write down commands or error output or config files, use [noparse]```

```[/noparse brackets around it.

---

### Post by jameskinds on 2008-10-24
Bucky Ball,

Thanks for the pointers.

The links you provided were excellent tutorials in how to mount standard images.

However the image that I want to mount contains an encrypted filesystem (and that is what is causing the problems).

As for 'DD'; well it is a low level copy program that you find in pretty much any *nix (Linux, BSD, etc.). Instead of copying files, DD copies the underlying data blocks. You can use DD to make image files from CDs, HDDs etc.

Thanks for your help.

Regards,

James




> **Bucky Ball said:**
> [http://swik.net/mount+ntfs](http://swik.net/mount+ntfs)

[http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/](http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/)

[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

They should give you a few clues. You could tell me ... what is DD?

---

### Post by jameskinds on 2008-10-24
Hyper CH,

Thank you for the help.

I tried what you noted but received the same problem as before.

When I entered:

```

sudo cryptsetup luksOpen /media/disk/4gb.mnt /dev/mapper/mapme/

```

I received the following error message: 

```

Command failed: Can't get device information.

```

As a consequence, I can not progress to the second step in your instructions. I have tried using different mountpoints for the "mapme" mountpoint, including the original filename, creating a random mountpoint, and creating a mountpoint in the /dev/mapper/ directory, but all to no avail. 

Do you have any other ideas?

Thanks again for your help.

James

> **hyper_ch said:**
> you're using cryptsetup wrongly:

```

sudo cryptsetup luksOpen /media/disk/dd_image_file dd_image_file
sudo mount /dev/mapper/dd_image_file /mnt/mountpoint

```
And when you write down commands or error output or config files, use [noparse]```

```[/noparse brackets around it.

---

### Post by hyper_ch on 2008-10-24
you don't use a full path for the mapper... just a mapper name.

---

### Post by jameskinds on 2008-10-24
Hi there,

Thanks again. I finally managed to do it with a bit of persistence.

The one step that seemed to be missing, and perhaps this is what you meant, was the "losetup" command.

I was finally successful in mounting the image by doing the following.

```

Enter:
losetup /dev/loop7 /media/disk/dd_image_file
cryptsetup luksOpen /dev/loop7 testfs
Enter LUKS passphrase: <enter your password>

You should see:

key slot 0 unlocked.
Command successful.

Then enter:
mount /dev/mapper/testfs /mnt/mount_point/

```

Note that the "loop7" device was an existing device on the system and as such it may be somewhat different on other systems.

Also note that "testfs" is not a variable. You must use this name to get the system to mount the encrypted partition.

Thanks again for your help.

Hopefully the "extra" step will make it a little clearer for newbies (such as me) to this stuff.

Kind regards,

James



> **hyper_ch said:**
> you don't use a full path for the mapper... just a mapper name.

---

### Post by Bucky Ball on 2008-10-24
Good news and good tip for anyone with this problem. Could you mark the thread as solved from 'Thread Tools', upper right so others can find your fix? :)

---

### Post by jameskinds on 2008-10-25
Have done.

Thank you for the forums etiquette tip.

Regards,

James

> **Bucky Ball said:**
> Good news and good tip for anyone with this problem. Could you mark the thread as solved from 'Thread Tools', upper right so others can find your fix? :)

---

### Post by jerome1232 on 2008-10-25
I would like to add one thing to your post. When I image I have a habit of imaging the entire drive not just the individual partitions. So I wanted to figure out how to handle that.

In this case when you do losetup you need to offset by x number of bytes, and only go x number of bytes into the image. For a simple example I did this on my little 512 stick. sdb. I always dump the output of fdisk -lu with my images for info.
```
Disk /dev/sdb: 503 MB, 503709696 bytes
255 heads, 63 sectors/track, 61 cylinders, total 983808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000199ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      979964      489951    7  HPFS/NTFS
```

As you can see 1 sector is 512 bytes on this drive, and the partition begins 63 sectors in, or 32256 bytes. It's the only partition so I don't worry about where it ends but if you DID, mine ends at 979964 sectors in, or 501741568 bytes in.

**32256** bytes is the begining of the partition
501741568 bytes is the end.
If you do the math (end - beginning) that makes this partition
**501709312** bytes long.


To setup the loop device I need to offset to where the partition starts. And set a size limit for how long that partition is.

```
sudo losetup /dev/loop0 -o 32256 --sizelimit 501709312 sdb.img
```

Then proceed with opening /dev/loop0 with cryptsetup. And then mounting the mapper device.

---

### Post by jameskinds on 2008-10-26
jerome1232,

Thank you for the update. I had not even considered the situation where the drive contained more than a single partition.

This is indeed a useful addition.

I think that all in all this post now offers a good solution summary for anyone who is seeking to mount an image of an encrypted drive.

Thanks again.

Regards,

James

> **jerome1232 said:**
> I would like to add one thing ...

---

### Post by Kolossos on 2009-08-14
Thank you Jerome!

I had encrypted my disks without partitioning them first. Your losetup walk-through was a life (=information) saver. :)

---

