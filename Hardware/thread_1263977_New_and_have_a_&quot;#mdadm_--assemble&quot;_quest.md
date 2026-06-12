---
title: "New and have a &quot;#mdadm --assemble&quot; question"
date: 2009-09-11
forum: Hardware
---

### Post by sunpyo on 2009-09-11
I had a pre-existing raid that seems to have the right partitions and stuff, one of the drives failed. Regardless, I know that RAID5s can function with only 3 disks available, so I was wondering if I could assemble them by using:
 
#mdadm - Av /dev/md0 (the UUID) /dev/sd*
 
I believe this might assemble them, however will assembling or attempt to assemble in this manner result in data corruption or lost? Or will this just attempt to assemble and not play with the data. Thanks.

---

### Post by sunpyo on 2009-09-11
And also found that the 3 remaining "good" drives all have the same UUID.

---

### Post by tgrimley on 2009-09-11
mdadm should assemble just fine.  When the drive died did you stop the array?  Upon boot it should assemble degraded on its own.  When you add a replacement disk it will resync on its own too.

---

### Post by sunpyo on 2009-09-14
it should've remade the array, however since it was a NAS box that created the array, it made it didnt remake the array like i thought it would.
 
So by remaking the raid there shouldn't be any damage or corruption to the HDs right? Normally I would back it up, however it's 4 x 2.0 TB HDs and I don't got the money to get another set right now.

---

### Post by tgrimley on 2009-09-14
"remaking" (--create) will destroy data, "reassembling" (--assemble) will not.

not sure what you mean by a NAS box made the array.. but keep in mind you might (under some circumstances I can't think of right now) have to reassemble in the exact order that you originally issued the create command (luckily you only have 24 permutations)

---

### Post by sunpyo on 2009-09-15
I was able to assemble the partitions in my Raid5. Turns out there were a couple of them. However when I try to mount the main Raid5 partition which is:
 
[COLOR=red]/dev/md2[/COLOR] to the filesystem that the Raid 5 was in, which was [COLOR=red]/media/disk/shares, [/COLOR][COLOR=black]I get the error:[/COLOR]
 
[COLOR=red]mount: you must specify the filesystem type[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]I used this command:[/COLOR]
 
[COLOR=red]#mount /dev/md2 /media/disk/shares[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]I heard I can make the drive be recognized as an EXT3 filesystem by using:[/COLOR]
[COLOR=black][/COLOR] 
[COLOR=red]#mkfs.ext3 /dev/md2[/COLOR]
[COLOR=black][/COLOR] 
then mounting by doing:
 
[COLOR=red]#mount -t ext3 /dev/md2 /media/disk/shares[/COLOR]
 
[COLOR=black]But I'm afraid of is writing onto the drive and not being able to recover the neccessary files on the HD. Any clarity or information will be much appreciated. Thanks![/COLOR]

---

### Post by tgrimley on 2009-09-15
```
mkfs.ext3 /dev/md2
```
will format your drives, don't do this.

Try specifying the filesystem with the -t ext3 flag when you mount.

---

### Post by sunpyo on 2009-09-15
Yep figured that out as well. I tried every combination that I know of filesystems when trying to mount. Nothing has worked. Is there a way to find out what filesystems are in my partition? I looked around and couldn't really find a command for it.

---

### Post by tgrimley on 2009-09-15
Sorry I missed where you said you mounted by
#mount -t ext3 /dev/md2 /media/disk/shares

did it work?

if you're worried about writing to the disk you can mount with the -r readonly flag?

---

### Post by tgrimley on 2009-09-15
There's also a good chance the NAS uses its own filesystem you won't be able to mount.  What's the make/ model

---

### Post by sunpyo on 2009-09-15
WD ShareSpace. Thanks man you've really helped me through this.

---

### Post by tgrimley on 2009-09-15
Was going to post a link I found on linuxquestions.org ([http://www.linuxquestions.org/questions/linux-server-73/help-with-wd-nas-recovery-4-x-2.0-tb-raid-5-755401/](http://www.linuxquestions.org/questions/linux-server-73/help-with-wd-nas-recovery-4-x-2.0-tb-raid-5-755401/)) regarding this until I realized it was you! ha.

So I found that supposedly that NAS uses unmodified EXT3 file system, but were you I would confirm with WD.

You've certainly streamlined your question, hope someone can help you more than me.. curious about the solution.

---

### Post by sunpyo on 2009-09-16
so i spoke with the people over at WD and he told me that all partitions use ext3 filesystems. I'm quite confident that doing mdadm --create will restore that.
 
Will fsck.ext3 do anyone for this system? Thanks!

---

