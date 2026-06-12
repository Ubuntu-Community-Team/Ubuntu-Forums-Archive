---
title: "Unable to mount drive"
date: 2008-04-23
forum: Hardware
---

### Post by antz90 on 2008-04-23
I currently dual boot windows XP/Ubuntu 7.10

while i was updating my iPod(cant seem to find a program that'll import videos to the iPod on Ubuntu) windows freaked out, like always, so i restarted, and logged into Ubuntu, and i look around, and my main hard drive is gone)(sda1)..
i tried to mount it, and it wouldn't. i know its there, its in my laptop...

---

### Post by ikki_72 on 2008-04-23
try > sudo fdisk -l then find NTFS partion, mount it, say the partition /dev/sda1 to a directory
> mount /dev/sda1 anydirectory/

---

### Post by Yellow Pasque on 2008-04-23
If windows freaked out, I guess that means it didn't shut down properly? If so, you either need to force mount it or have Windows mount/unmount it properly.
Boot back into Windows and shut down properly. That should solve your problem. If not, we'll work on manually mounting it.

---

### Post by antz90 on 2008-04-23
Well, thanks to windows infamous blue screen of doom,
it didnt shut down right.
now windows cant even load up, right after the
"windows XP" loading screen, Boom! phys mem dump.

---

### Post by Yellow Pasque on 2008-04-23
Ideally, you'll want to connect the disk to a Windows box and stop/unmount it cleanly.
If that's not possible, then use the command below. There's a (small) possibility of data loss with force mounting, so don't say I didn't warn you. :P

```
sudo mount -t ntfs-3g /dev/sda1 */mount/point* -o ro,force,gid=100
``` 
(/mount/point = the directory you want to mount to)

Note: We are mounting it read-only on the first mount as a precaution. When you want to mount the disk in the future, use 'rw' instead of 'ro' (and obviously, no 'force').

---

### Post by antz90 on 2008-04-23
after running the
>  sudo fdisk -l
(see bottom)

the drive sda1 was my main drive with windows, and all my stuff (ie: music, movies, games, ect) and after updating my ipod, _windows_ crashed and now windows wont even get past the "windows loading" screen b4 a phys mem dump. 

i tried
> mount /dev/sda1 anydirectory/
and it says only root.

so to make this simple,
pretend i know nothing, and explain how to get my drive back -.-
:lolflag:

i had a force mount work b4, idk what i did, but my drive came back, and i restarted, and pop, its gone.

the 30GB drive is just the ipod, ignore it, :D

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         121        9855    78196387+   7  HPFS/NTFS
/dev/sda2           10770       12030    10128982+   c  W95 FAT32 (LBA)
/dev/sda3           12031       12161     1052257+  d7  Unknown
/dev/sda4            9856       10769     7341705    5  Extended
/dev/sda5            9856       10644     6337611   83  Linux
/dev/sda6           10645       10769     1004031   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders
Units = cylinders of 15810 * 2048 = 32378880 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 12, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb2               4         927    29206168    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(3, 12, 22)
Partition 2 has different physical/logical endings:
     phys=(911, 254, 62) logical=(926, 180, 59)

Disk /dev/mmcblk0: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              21      167680     1005958+   6  FAT16


---

### Post by antz90 on 2008-04-24
Any ideas?

---

### Post by Yellow Pasque on 2008-04-24
Now you need an entry in your /etc/fstab (gksudo gedit /etc/fstab)
```
/dev/sda1 /a/directory  ntfs-3g  rw,auto,exec,user,gid=100  0  0
```

---

### Post by antz90 on 2008-04-24
> gksudo gedit /etc/fstab

add that to it?
where?

---

### Post by Baje on 2008-04-24
After doing that it says fuse: failed to access mountpoint /media/external: No such file or directory

---

### Post by antz90 on 2008-04-24
I ran a force mount, and it worked this time.
but it didnt work last night.

i dont want to keep having to force it, eventually itll get ruined.

how can i fix it enough to run windows so it can solve its own damn problem?

i read on another post about fsck with a live cd. but then another said fsck wont work on NTFS drives (mine)

---

### Post by Yellow Pasque on 2008-04-24
Sounds like it's time to jump ship. You're due for a reformat and Windows reinstall. That's my suggestion to you. Get your data off while you can and get out. I just wrestled with this on my sister's computer and that ended up being the solution.

---

### Post by antz90 on 2008-04-24
Eh, i backed up my music, all i care about really.
The rest can burn with windows!:twisted:

Im probably just going to off windows completely.

---

### Post by Yellow Pasque on 2008-04-24
> **antz90 said:**
> Eh, i backed up my music, all i care about really.
The rest can burn with windows!:twisted:

Im probably just going to off windows completely.
Awesome! A functional Windows install isn't a bad thing to have around though. Some things (BIOS updates, DVD drive firmware updates) are just easier with Billy's OS.

---

### Post by antz90 on 2008-04-25
Yeah, maybe. when i wipe this computer to start anew, i might give windows a 5gig block. :P
other then that, its all Ubuntu. theres only a few things i dont like about Ubuntu, but all can be fixed. :D 

As for the drive mounting,
i just force mounted it, and it seems to mount, atleast until i restart, but as for this thread, its done, for now.
Thanks Temüjin

---

### Post by ulster_con on 2008-08-20
hey all, 

i have a similar issue, windows failed to load, so had to force shutdown, now i cannot get into windows at all, but thats ok, as i dont really use it. 

but... my partitioned 90GB wont mount, when i managed to force mount it, i (as u can see) mounted it a little incorrectly, and pointed it to the desktop. 

so now my desktop icons have dissappeared, and my mounted drives contents are on the desktop, but nothing else, i cannot unmount it via right click now either as it says it was not mounted by HAL

so... how can i undo that mount, then mount it correctly in command line to point to "where ever it should correctly mount", thus recovering and leaving my desktop intact?

thanks in advance,

Con

---

### Post by ulster_con on 2008-08-20
> **ulster_con said:**
> hey all, 

i have a similar issue, windows failed to load, so had to force shutdown, now i cannot get into windows at all, but thats ok, as i dont really use it. 

but... my partitioned 90GB wont mount, when i managed to force mount it, i (as u can see) mounted it a little incorrectly, and pointed it to the desktop. 

so now my desktop icons have dissappeared, and my mounted drives contents are on the desktop, but nothing else, i cannot unmount it via right click now either as it says it was not mounted by HAL

so... how can i undo that mount, then mount it correctly in command line to point to "where ever it should correctly mount", thus recovering and leaving my desktop intact?

thanks in advance,

Con

ive since managed to unmount via Partition Editor. 
but all the files remain on the desktop (but unable to open them ofcourse as they are unmounted), but i cannot delete them as the directory does not exist(unmounted)

so, just need to know where to point it correctly to mount it next time, 
and ideas?

i get this error when i try 
fuse: failed to access mountpoint /media/disk: No such file or directory

---

### Post by ulster_con on 2008-08-21
ahh, a reboot solved it all...
the force mount i see is only a temporary mount :D

desktop restored, and proper mount method restored :D

---

