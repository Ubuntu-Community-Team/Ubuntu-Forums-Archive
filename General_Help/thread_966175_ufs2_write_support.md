---
title: "ufs2 write support"
date: 2008-11-01
forum: General Help
---

### Post by tom.clements on 2008-11-01
Hi,

Can anyone confirm if Intrepid Ibex includes read *and* write support for ufs2 formatted disks? I gathered from this post [http://ubuntuforums.org/showthread.php?t=867168&page=1]("http://ubuntuforums.org/showthread.php?t=867168&page=1") that support has been included from the 2.6.26 so given 8.10 has the 2.6.27 kernel it should be?! If so how do I go about mounting my drive? 

I have successfully mounted the drive read only but when I change the ro to rw in my fstab it gives a mount fail error.

Many thanks for any help,

Tom.

---

### Post by kidders on 2008-11-02
Hi there,

> **tom.clements said:**
> Can anyone confirm if Intrepid Ibex includes read *and* write support for ufs2 formatted disks?Technically yes, but ...```
$ grep CONFIG_UFS_FS /boot/config-`uname -r`
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
```That indicates my kernel (a generic 2.6.27) *can* support writing to UFS2 filesystems, but doesn't. The Ubuntu gods probably thought UFS2 write support was either too unstable or just not of practical benefit to most users, and didn't enable it.

To mount a UFS2 filesystem in read/write mode, you'll need to recompile your kernel with CONFIG_UFS_FS_WRITE set to 'y'.

If you like, you could submit a request to have the option enabled by default in future.

---

### Post by tom.clements on 2008-11-10
Many thanks kidders.. that's the conclusion I had come to. Recompiling the kernel is not something I have done before.. is it easy to accomplish? My only other thought which I will probably go for is to take all the data off the ufs drive and reformat it using ext3.

Cheers,

Tom.

---

### Post by kidders on 2008-11-11
Building & running your own kernel is quite straightforward, but you do have to spend a little time making sure you fully understand each step, so that if/when something goes wrong, you can fix it.

I would recommend making no configuration changes except the one I mentioned in my last post.

Switching away from UFS to JFS/Ext3/etc. is another good option. If you don't *need* to use UFS, then you might as well switch. Then again, there are plenty of good reasons for holding on to it ...[LIST]
[*]You might like UFS's features (eg fragmentation resistance).
[*]You might be using it to share files between multiple OSs.
[*]Your UFS filesystem might be too big to reformat easily.
[/LIST]

I hope that helps.

---

### Post by Buntumatic on 2011-12-09
I know this is an old thread, but it showed up first in Google.
I have slight correction to above.
Kernel recompile in cases like this is not required. All you need is correct sources (the ones your kernel was built with). Run ```
make menuconfig
``` enable desired feature as module, run ```
make modules && make modules_install
```Enjoy, no reboot needed.

---

