---
title: "Write Caching in Ubuntu"
date: 2008-09-02
forum: General Help
---

### Post by EmanresuusernamE on 2008-09-02
I know that's the term used in Windows, but it's the best way for me to describe my issue.  What is the best way to remove automatic write caching in Ubuntu?  Whenever I want to copy stuff over from my hard drive to my USB drive(s), I want to be able to just pull the drive out of the machine.  I don't want to have to unmount it every time as I'm used to windows just writing the data to the drive.  What's the best way out there right now?

---

### Post by jpkotta on 2008-09-04
I think you can disable write caching with the sync mount option.  But then it's really slow.  Unmounting is a good idea...

foo is a 32 MB file of random data.

```

[20:05:59][jpkotta@gauss][~][0]
$ mount /media/removable
[20:05:59][jpkotta@gauss][~][0]
$ rm /media/removable/foo
[20:05:59][jpkotta@gauss][~][0]
$ time cp foo  /media/removable/ && time umount /media/removable/

real	0m0.162s
user	0m0.000s
sys	0m0.088s

real	0m3.607s
user	0m0.000s
sys	0m0.052s

```
```

[20:07:46][jpkotta@gauss][~][0]
$ sudo mount -o sync /media/removable/
[20:07:46][jpkotta@gauss][~][0]
$ sudo rm /media/removable/foo
[20:08:22][jpkotta@gauss][~][0]
$ time sudo cp foo /media/removable/ && time sudo umount /media/removable/

real	1m37.437s
user	0m0.008s
sys	0m0.572s

real	0m0.040s
user	0m0.000s
sys	0m0.040s
```

If you do a sync before removing, it should be as good as unmounting, but it's just as easy to unmount as to issue a sync  (sync is a command than writes all pending data to all disks).

---

### Post by EmanresuusernamE on 2008-09-11
#-o Forgot about this thread.

Hmmm, that seems like it will work somewhat, but then again as you said at the end, it's just as easy to umount the drive first.  What I'm looking for, is a way to have it always write the data to the jump drive without having to do anything to it at all.  The speed of the drive writing is not an issue for me as I tend to forget to remove the drive and have to go back and redo what I had did again.  I'll wait for the little light to stop flashing before I remove the device.

---

### Post by jpkotta on 2008-09-11
> **EmanresuusernamE said:**
> #-o Forgot about this thread.

Hmmm, that seems like it will work somewhat, but then again as you said at the end, it's just as easy to umount the drive first.  What I'm looking for, is a way to have it always write the data to the jump drive without having to do anything to it at all.  The speed of the drive writing is not an issue for me as I tend to forget to remove the drive and have to go back and redo what I had did again.  I'll wait for the little light to stop flashing before I remove the device.

If you're OK with the speed when sync is on, then you can add an entry in /etc/fstab.  This is what mine looks like, as an example:
```
/dev/sdb1       /media/removable        vfat    rw,user,noauto,dmask=077,fmask=177      0 0

```
The options are explained in the mount man page.

---

