---
title: "Cannot mount secondary HDD data drive"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by MeanStreak on 2007-11-20
Hi

I've recently set up a dual-boot configuration with XP and Ubuntu 7.10. Installation went perfectly - I allocated 60GB free space on my C drive to Ubuntu. I have two HDDs - my E drive (160GB) contains my documents - data - music, video etc. Ideally I want to share the E drive between Windows and Ubuntu.

Upon first booting up Ubuntu, I could navigate to E and load up video files, and configured the audio player to import music files from the E drive, etc. No problems. Last night however I found I can no longer mount the E drive. Why? How can I fix this so Ubuntu can mount the E drive once more?

---

### Post by taurus on 2007-11-20
Sounds to me like you didn't shut down windows cleanly the last time you use it.  As a result, Ubuntu can't mount it unless you "force" it.  So, boot back into windows and shut it down cleanly this time.  Now, see if Ubuntu will mount it from /etc/fstab.  

Otherwise, post the output of this command from a terminal when you are in Ubuntu.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by MeanStreak on 2007-11-21
Thanks for the prompt reply! I re-booted Windows and ensured that it was shut-it down correctly this time. In Ubuntu, I was then able to mount the data drive without any problems. This issue is now resolved. Much appreciated.

---

### Post by anthonylane13 on 2008-01-21
Hi
I have the same problem described here except I have just finished a fresh install on my system, but have completely wiped out windoze.
It works great except I can't access my secondary HDD.  I typed in sudo fdisk -l and this is what I got...
```
Disk /dev/hda: 27.3 GB, 27329101824 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3183    25567416   83  Linux
/dev/hda2            3184        3322     1116517+   5  Extended
/dev/hda5            3184        3322     1116486   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
15 heads, 23 sectors/track, 226449 cylinders
Units = cylinders of 345 * 512 = 176640 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      226450    39062496    b  W95 FAT32

```

Any help would be much appreciated as I am a real Noob still (I was using Ubuntu on my mac, but only had it on there for a few weeks before the machine died... on pc now)

Thanks

---

### Post by Yellow Pasque on 2008-01-21
Can you mount with:
```
sudo mount -t vfat /dev/hdb1 /media/<some directory>
```
in the /etc/fstab, you should have an entry like the following:
```
/dev/hdb1 /media/<directory you want> vfat auto,exec,user 0 0
```

---

### Post by anthonylane13 on 2008-01-22
Thanks for your reply - I'm not sure if I understand, but here goes...

I can't mount the disk using the command you suggested - it says 
```
mount point does not exist
```

which makes me think I must be doing it wrong...

I know the directory structure on this disk, and it's just folders called documents, music etc etc - nothing cryptic

I assume that in the command 
```
sudo mount -t vfat /dev/hdb1 /media/<some directory>
```

media - should be replaced with the name of the disk??
My disk label is 'storage'
should I be using whatever name my system uses to refer to this disk?  If so, how do I find out what it's called.

Thanks again for your help.

---

### Post by Daelyn on 2008-01-22
> **anthonylane13 said:**
> Thanks for your reply - I'm not sure if I understand, but here goes...

```
mount point does not exist
```



The issue is that you can't mount it on a mount point that does not exist.

```
 sudo mkdir /media/<name of your choise> 
```
After that, you can 
```
 sudo mount -t vfat /dev/hdb1 /media/<THE SAME name of your choise> 
```

When you got that working correctly, edit the fstab according to previous post.

Hope this helps.

---

### Post by anthonylane13 on 2008-01-22
Success - thank you!

I have one remaining problem, although of a much lesser magnitude - I only have read access to the drive and all files on it. 

How do I change permissions so I can write/ edit to it as well?

Thanks again.:)

---

### Post by Daelyn on 2008-01-22
If you check in your fstab for a line looking something like this

```
 /dev/hdb1 /media/<where you now try to mount it> vfat auto,exec,user 0 0 
```

and retype it with the following.

```
 /dev/hdb1 /media/<path to the mount point> vfat defaults 1 0 
```
also to change permissions

```
 sudo chmod 755 /media/<path to the mount point> 
```
Should change your permissions to the drive.

```
 sudo mount -a 
```
To remount everything in fstab.


If, of some wierd reason, that does not work, here's another one I managed to think of (try the above first!)

In Fstab, replace the above line with
```
 /dev/hdb1 /media/<path to the mount point> vfat noauto,users,umask=777 0 0 
```

---

### Post by anthonylane13 on 2008-01-22
Thanks for your post

I think I must be doing it wrong, cos I can't make it work!

I updated the fstab file as you suggested, but it didn't work - and then I thought that maybe the last 2 bits of code in your post looked like they might be commands for the terminal, so I typed them. No response there, which I thought there shouldn't be, but still a read only disk.

So then I tried your last suggestion, but it hasn't worked either...
Even restarted my system, but it hasn't helped.  Any more ideas?
Now the system will not even let me browse the volume - is that very bad news?

Thanks

---

### Post by anthonylane13 on 2008-01-22
ok - I can browse the disk again, but only if I change the line in fstab back to:
```
 /dev/hdb1 /media/<where you now try to mount it> vfat auto,exec,user 0 0
```

If I try any of the other suggestions and try to browse the disk, I get an error saying I don't have the necessary permissions to view the volume.

That's a bit wierd after 
```
sudo chmod 755 /media/<directory>
```
isn't it?

Any other thoughts would be greatly appreciated.

Thanks

---

### Post by Yellow Pasque on 2008-01-22
Please give me output from the following command:
```
cd /dev; ls -l | grep hd
```

Also, open your /etc/group file with sudo gedit and make sure your user is listed in the disk group:
```
...
tty::5:
disk::6:<put your username here, without the brackets>
lp::7:daemon
mem::8:
```

---

### Post by anthonylane13 on 2008-01-22
Hi Temujin
Thanks for your help :)

I've added my username to the group file, and here's the output of the command you asked for.
```
lrwxrwxrwx 1 root root           3 2008-01-22 21:07 cdrom -> hdd
lrwxrwxrwx 1 root root           3 2008-01-22 21:07 cdrw -> hdd
lrwxrwxrwx 1 root root           3 2008-01-22 21:07 dvd -> hdd
brw-rw---- 1 root disk      3,   0 2008-01-22 21:07 hda
brw-rw---- 1 root disk      3,   1 2008-01-22 21:07 hda1
brw-rw---- 1 root disk      3,   2 2008-01-22 21:07 hda2
brw-rw---- 1 root disk      3,   5 2008-01-22 21:07 hda5
brw-rw---- 1 root disk      3,  64 2008-01-22 21:07 hdb
brw-rw---- 1 root disk      3,  65 2008-01-22 21:07 hdb1
brw-rw---- 1 root cdrom    22,   0 2008-01-22 21:07 hdc
brw-rw---- 1 root cdrom    22,  64 2008-01-22 21:07 hdd

```
Does it make any sense to you?

Thanks

---

### Post by Yellow Pasque on 2008-01-22
OK, so after you reboot, can you read/write?

---

### Post by Daelyn on 2008-01-22
Sorry. I'm like a big question mark right now. 
Don't see any good reason for it not working.

Wierd! :(

---

### Post by anthonylane13 on 2008-01-22
After I reboot, I'm back to read only - but only if the etc/fstab file contains this line
```
 /dev/hdb1 /media/<where you now try to mount it> vfat auto,exec,user 0 0
```
strange, no?

If I try any of the other suggestions on this thread, I can't even browse the volume...

:???:

---

### Post by Yellow Pasque on 2008-01-22
OK. Try this one:
```

/dev/hdb1 /media/<that dir. you created>  vfat  rw,auto,exec,user,uid=1000  0   0

```

---

### Post by anthonylane13 on 2008-01-22
Temüjin - you're a genius!

Success!! Thank you so much.

This is a brilliant community - I hope one day I'll be able to give something back, but for now I still feel like a helpless noob!

Great to have it working now.

---

### Post by Daelyn on 2008-01-25
> **Temüjin said:**
> OK. Try this one:
```

/dev/hdb1 /media/<that dir. you created>  vfat  rw,auto,exec,user,uid=1000  0   0

```

I should have thought about that one.
Argh.. )(*&^%$%

:lolflag:

---

