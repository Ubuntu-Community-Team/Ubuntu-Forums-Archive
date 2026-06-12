---
title: "ubuntu installed twice"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by philippe75 on 2009-08-15
Hi,

Ok it sounds weird, but I first installed Ubuntu few days ago but without enough memory - so I tried to re-install it because nothing had been done on the first install so I thought this would be easier.
I also thought I had deleted the old ubuntu partition with the partition manager of the live CD, but actually I did not! so now I have two ubuntu OS at start up (and XP)

I am more than a newb (this explains the situation I guess) so if someone could explain me how to remove the 'old' ubuntu and give the space to the one?

Thanks a lot

Phil

Just in case if it helps, here is the result of df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              17G  2.5G   14G  16% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  132K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  168K  501M   1% /dev
tmpfs                 501M   76K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 501M  2.2M  499M   1% /lib/modules/2.6.28-14-generic/volatile

and fdisk -l shows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        6991    48829567+   7  HPFS/NTFS
/dev/sda3            6992       12161    41528025    f  W95 Ext'd (LBA)
/dev/sda5            6992        9552    20571201    7  HPFS/NTFS
/dev/sda6           11836       12139     2441848+  83  Linux
/dev/sda7           12140       12161      176683+  82  Linux swap / Solaris
/dev/sda8            9553       11734    17526883+  83  Linux
/dev/sda9           11735       11835      811251   82  Linux swap / Solaris

from my understanding, I should get rid of /sda6 and /sda7...

---

### Post by s3MA00RRNY on 2009-08-15
You may see something like this
```

Ubuntu 9.04, linux-2.6.28-14-generic
Ubuntu 9.04, linux-2.6.28-14-generic (recovery mode)
Ubuntu 9.04, linux-2.6.28-11-generic
Ubuntu 9.04, linux-2.6.28-11-generic
Other Operating Systems:
Windows Vista/Longhorn

```

If this is what you are getting, you do not have two Ubuntu OSes installed. You have two *kernels* installed. Ubuntu gets frequent kernel updates. The newest one is at the top. The idea is that if the new kernel backfires, you can still boot the old one. They are not very large, only over 100MB, so you don't really need to remove the old one.

---

### Post by philippe75 on 2009-08-15
thanks for the reply pcdude2143.

well, from my understanding, I have several partitions for ubuntu, of the exactly same version of the system (same install disk, two instal within 24 hours, just one has more memory than the other, the one I would like to remove).
there is nothing like a recovery kernel etc on my laptop (yet)

so how can I remove what is useless?

I agree, this is not a lot of memory, but still... I'd like to clean my mess!

thanks again

---

### Post by colau on 2009-08-15
> **philippe75 said:**
> thanks for the reply pcdude2143.

well, from my understanding, I have several partitions for ubuntu, of the exactly same version of the system (same install disk, two instal within 24 hours, just one has more memory than the other, the one I would like to remove).
there is nothing like a recovery kernel etc on my laptop (yet)

so how can I remove what is useless?

I agree, this is not a lot of memory, but still... I'd like to clean my mess!

thanks again
Does this help?
[http://ubuntuforums.org/showthread.php?t=1240788&highlight=linux](http://ubuntuforums.org/showthread.php?t=1240788&highlight=linux)
See post #17.

---

### Post by harry2006 on 2009-08-15
find the one that got installed later, modify the grub to remove the entry for others...done!!! get back those partitions and use them under the current ubuntu...

---

### Post by raymondh on 2009-08-15
I hope I understood your post.... which is to do partitioning work to delete partitions and enlarge some to take up the vacated space.

You can use gparted from the liveCD to work on partition (deleting, resizing, moving).

A live gparted ought to unmount the partitions.  Just to be sure, right click on the intended partition and if given the option to unmount, do so.  Also, rt. click on swap and select swap-off.  You'll know that it is mounted if it either has a key sign of you have greyed-out options to resize, etc.

Back up your files.  Know which partition to delete.  You may have to recover or reinstall grub but that is easy to do.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If I understood wrong, my apologies.

---

### Post by philippe75 on 2009-08-15
Thanks for all the replies!

I tried colau's commands, without sucess.
I did not really understand harry's solution, I will have to think about it.

I tried the gparted stuff, boot, from thier cd etc.
I saw the partition I wanted to deleted, I tried to delete them, but for reason there are still here!!

The thing is, I try to do that from a broken screen laptop and I use my TV if I can - with the boot CD of gparted, the vga mode failed, and I had to guess what was on the broken screen (depending on the angle, I may see something, but it is really really dark) so maybe I forgot an 'OK' or something...

Anyway, thanks again for the replies, I wil definitively retry later on!

Phil

---

### Post by stlsaint on 2009-08-15
hey i dont know what everyone else was saying becuz it looks like you just need to remove the kernel which is easy: SYSTEM>STARTUP MANAGER!!!
from there you will be able to set how many kernels you see at boot up and if you absolutely want to get rid of the kernels and you cant find how to do them from there than post here again and we will try via terminal!!

---

### Post by raymondh on 2009-08-15
kindly confirm ...

are you trying to remove kernels from your boot up screen or ... are you trying to delete a partitioned ubuntu installation?

If it is kernel ..... see what stlsaint says.  Install startupmanager and set defaults, etc. from there. See attached screenshots.  It will also write to the menu.lst.

If delete a partitioned install (because you installed it twice) ... then see the links provided on how to.

---

### Post by philippe75 on 2009-08-15
First of all, thanks a lot, I managed to do most of the changes I wanted. I think my problem was close to what raymondhenson suggested - delete a partition.

So I got gparted work in a safe graphics mode finally - then, I deleted the partitions that I did not want anymore, resize the others, got an error grub error 22 at the following reboot, but the last link given by raymondhensonsolve solved everything.

And now, fdisk -l return this:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf82bc96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        6991    48829567+   7  HPFS/NTFS
/dev/sda3            6992       12161    41528025    f  W95 Ext'd (LBA)
/dev/sda5            6992        9552    20571201    7  HPFS/NTFS
/dev/sda6            9553       12058    20129413+  83  Linux
/dev/sda7           12059       12161      827316   82  Linux swap / Solaris

which is fine for me.

But when I reboot, I still see 2 linux in the list of possible OS's to start with, and I don't want to try the old one for now - any idea on how edit this list and keep only OS's alive?

I hope this is clear.

Thanks again,

Philippe

---

### Post by raymondh on 2009-08-15
> **philippe75 said:**
> 

which is fine for me.

But when I reboot, I still see 2 linux in the list of possible OS's to start with, and I don't want to try the old one for now - any idea on how edit this list and keep only OS's alive?

I hope this is clear.

Thanks again,

Philippe

Congratulations.

On to your next issue.  Now .... I think you are referring to kernels (2.6.28-x, etc).  If so, install startupmanager *(go to system > administration > synaptic and search/mark/apply ... once installed, you'll find it in system > administration)* and edit/set from there.

You can limit the number of kernels to see on boot up as well as set which kernel to default-boot into. See first attached (in earlier post) titled screenshot-startup-manager.

I suggest you keep memtest and recovery mode.  See the attached .png titled 'advanced'

Good luck.

---

### Post by philippe75 on 2009-08-15
raymondhenson, I tried what you proposed... but with no luck unfortunately.

I still see when I boot the old Linux.
I see the first free lines that I want to keep, ubuntu 9.04 kernet 2.6.28-14 generic
and the recovery mode and mem test mode

Then, I have the line Others Installed OS, below I see windows XP, and then... 3 others linux OS - not the same numbers though, it is like ubuntu 9.04 kernet 2.6.28-11 (on sda 6)

sda 6 was the 'name' of the partition I have deleted, the new linux, the one I use currently, was on sda 8. Now after gparted, the new Linux is on sda 6, no more sda 8 etc.

Last thing: I did tried to boot on this other Linux and I had an error 'file not found' which is not surprising for me - I has been deleted with the partition right? maybe there is an entry in the bios or whatever of the computer - this is all very new for me, I will check that later.

Anyway, that's weird, but I can definitively live with that for now :)

Thanks a lot for your help!!

phil

---

### Post by philippe75 on 2009-08-16
ok just to conclude on this subject: I have edited the /boot/grub/menu.lst file, and at the end I have commented the last few lines, and that's it! no more dead lines in the boot menu!

thanks a lot for the help

philippe

---

### Post by raymondh on 2009-08-16
> **philippe75 said:**
> ok just to conclude on this subject: I have edited the /boot/grub/menu.lst file, and at the end I have commented the last few lines, and that's it! no more dead lines in the boot menu!

thanks a lot for the help

philippe

'forehead-slapping moment'.... my apologies ... I got focused on something else that I forgot editing the menu.lst.  

Congratulations.  Well done.

Again, sorry.

---

