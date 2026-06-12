---
title: "Mount ext3 subdirectory in Ubuntu root directory"
date: 2008-05-31
forum: Hardware
---

### Post by Dan++ on 2008-05-31
Right, the title is slightly ambiguous but I don't know how else to explain it. Basically, I have a big 500GB ext3 disk which is to be shared by Windows and Linux. In Windows I'll have the "My Documents" thing pointing at Z:\Dan's Documents, and in Linux, my fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3e0b0cf8-2625-42d9-ad15-333d59cb9a31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=818e840f-9757-4c3e-a195-e29dcc0186bc none            swap    sw              0       0
/dev/scd0       				/media/cdrom0   	udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        				/media/floppy0  	auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 					/mnt/zdrive 		ext3 	defaults 		0 	2
```

Sp that all works fine, and I go to /mnt/zdrive/Dan\'s\ Documents to get to the directory for my documents.

But what if I want to mount the firectory /dev/sdc1/Dan's Documents to the /home/dan/Documents directory, and similar for My Music and My Videos?

Is there a way of doing this? I tried making fstab look like below but it didn't work (I've commented out the bits I tried to make it work this):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3e0b0cf8-2625-42d9-ad15-333d59cb9a31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=818e840f-9757-4c3e-a195-e29dcc0186bc none            swap    sw              0       0
/dev/scd0       				/media/cdrom0   	udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        				/media/floppy0  	auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 					/mnt/zdrive 		ext3 	defaults 		0 	2
# /mnt/zdrive/Dan\'s\ Documents 		/home/dan/Documents 	ext3 	defaults 		0 	2
# /mnt/zdrive/Dan\'s\ Documents/My\ Music 	/home/dan/Music 	ext3 	defaults 		0 	2
# /mnt/zdrive/Dan\'s\ Documents/My\ Videos 	/home/dan/Videos 	ext3 	defaults 		0 	2
# /mnt/zdrive/Dan\'s\ Documents/Website\ Stuff 	/home/dan/public_html 	ext3 	defaults 		0 	2
```

Any ideas?

Thanks:)

---

### Post by 505 on 2008-05-31
Change the last lines to
```

/mnt/zdrive/Dan\'s\ Documents /home/dan/Documents none defaults,bind 0 0

```
and it should work, as long as the (empty) directory Documents exists in /home/dan

---

### Post by sisco311 on 2008-05-31
First create an fstab entry for the partition:
1.) get the uuid of the partition(assuming /dev/sdc1 is the device):
```
sudo blkid /dev/sdc1
```2.) edit the fstab:
```
gksu gedit /etc/fstab
```and add this lines:
> # /dev/sdc1
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /mnt/zdrive  ext3    relatime,defaults        0       2where xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is the uuid you get from the blkid command.
3.) make sure the mount point exist:
```
sudo mkdir /mnt/zdrive
```4.) to mount the directories in your home add this lines to the fstab:

> /mnt/zdrive/Dan's\040Documents            /home/dan/Documents    auto    bind            0    0
/mnt/zdrive/Dan's\040Documents/My\040Music     /home/dan/Music auto bind         0 0[FONT=monospace]
[/FONT]/mnt/zdrive/Dan's\040Documents/My\040Videos     /home/dan/Videos auto     bind         0 0[FONT=monospace]
[/FONT]/mnt/zdrive/Dan's\040Documents/Website\040Stuff     /home/dan/public_html auto bind         0 0\040 = ascii code of space
5.)remount the partition:
```
sudo umount /mnt/zdrive
sudo mount -a
```

---

### Post by molotov00 on 2008-05-31
I wouldn't have thought to use mount to do this. I'd have used a symbolic link.

Symlinks are almost like shortcuts, except that they are transparent to applications because they exist on the file system level.

I'd do:
```
ln -s /mnt/zdrive/Dan\'s\ Documents /home/dan/Documents
```

With this, any changes made to /home/dan/Documents will actually be made in /mnt/zdrive...

I'd also recommend mounting Dan's Documents with a unix-compatible filename, such as dans_documents. This will probably save you grief in the future.

Even if you don't go with this solution you should know it does exist.

M

---

### Post by Dan++ on 2008-06-01
> **sisco311 said:**
> First create an fstab entry for the partition...

Excellent, it worked! Thank you :)

> **molotov00 said:**
> I wouldn't have thought to use mount to do this. I'd have used a symbolic link.

Symlinks are almost like shortcuts, except that they are transparent to applications because they exist on the file system level.

I'd do:
```
ln -s /mnt/zdrive/Dan\'s\ Documents /home/dan/Documents
```

With this, any changes made to /home/dan/Documents will actually be made in /mnt/zdrive...

I'd also recommend mounting Dan's Documents with a unix-compatible filename, such as dans_documents. This will probably save you grief in the future.

Even if you don't go with this solution you should know it does exist.

M

Thanks to you too, I'll change its name. Regarding symbolic links though... is that permanent?

---

### Post by sisco311 on 2008-06-01
> **Dan++ said:**
> Excellent, it worked! Thank you :)



Thanks to you too, I'll change its name. Regarding symbolic links though... is that permanent?

Yes the symbolic link permanent(until the target exist).

---

