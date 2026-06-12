---
title: "convert resier to ext3"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by tomski on 2006-08-03
hi there

here is the situation:

I use resier fs as my file system of choice, but i have a winxp install & i use mp3 files in both ubuntu & winxp.
 so i thought i could convert the reiser partition with these on to ext3 so i could use the win ext3fs driver to access it!!

would there be any corrpution to the files if i went ahead & can i use parted to do this ??

---

### Post by kaffelars on 2006-08-04
As far as I know (please correct me if I'm wrong!), you can't convert from ReiserFS to Ext3.
This means you'd have to completely reformat the drive (and loose everything on it).

If you do this, just make sure you get a Ext**3**-driver for Windows (i once used an Ext2-driver to write to an Ext3 filesystem, which resulted in an broken journal;) )

---

### Post by phitoo on 2006-08-04
> **tomski said:**
> 
would there be any corrpution to the files if i went ahead & can i use parted to do this ??


That's a good way to loose all the files on that partition. If you must share a partition between XP and Ubuntu, create a FAT partition. XP will see it as a drive and you can mount it on Ubuntu.

So, first, backup the files from the reiserfs partition.

Use fdisk to change the partition type to something appropriate.

Create your DOS partition. You'll need dosfstools, I think.

Last, restore the files you backed up from the reiserfs filesystem.

Enjoy!

---

### Post by tomski on 2006-08-04
thanks for the reply's 

this is exactly what i thought i would have to do but i was a bit unsure, hence the question.
:)

thanks again

---

