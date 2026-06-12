---
title: "fsck failed :("
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by missing on 2005-12-30
hello everyone. i'm new in linux :( After reboot error (X server not start):

```

*Checking root file system...
/contains a file system with errors, check forced
/:
Duplicate or bad block in use!
/: Multiply-claimed block(s) in inode 8: 1024
/: Multiply-claimed block(s) in inode 81297: 1024
/: (There are 1 inodes containing multiply-claimed blocks.)
?: File <The journal inode> (inode #8, mod time Mon Dec 26 21:40:14 2005) has 1 multiply-claimed block(s), shared with 1 file(s):
/: /bin/zless (inode #81297, mod time Fri Jul 8 22:19:49 2005)
/:
/: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., witjout -a or -p options)
*fsck failed. Please repair manually and reboot


```

Please help me :( What should i do step by step :(

---

### Post by kaamos on 2005-12-30
This leaves you on a prompt, right? Type
```
fsck
```
Then if you get asked about performing operations to a mounted filesystem, answer that you don't wish to do so.

Default answers should probably be ok for other questions. When fsck has finished, type
```
shutdown -r now
```
And your system reboots, and hopefully boots to the gui.

This error was caused by errors on the disk. Perhaps the computer crashed, or for some reason the disk didn't unmount properly. I get this on and OLD (~10 years) hd from time to time.

---

### Post by missing on 2005-12-30
Thanx a lot :) All works fine :) Happy new year !

---

### Post by beameup on 2006-01-09
I just deleted a partition and resized another with the free space. I get that same error at bootup, but I just hit ctrl D and it boots OK. Going to try this tip on next reboot. Thanks

Well, not the same exact error. It's looking for hda3 which is gone. Says to repair manually. I'll search some more. Is there a log where I can capture the exact error?

---

### Post by Iesos on 2006-01-09
I've think i had the same type of problem a while ago. If I get it right fsck kraches when "Checking filesystems" runns during boot. Acctually, I dont think it kraches, it just takes a lite more time. All I had to do was to go "hit the head", and then it had started all by it self. When you experience the same problem again, try just to wait for 5-10 minutes.

---

### Post by beameup on 2006-01-09
It fails after checking filesystems, and sits at a root prompt.

"failed to open device /dev/hda3  no such file or directory"

"fsck failed  please repair manually"

Pressing Ctrl D will ignore it and continue the boot process, which goes fine.

dev/hda3 is still listed in fstab, it was also still listed in the /media folder. 

I had an 80GB hard drive I had divided in 2 - 39GB partitions and a swap so I could dual boot distros. (After screwing up Kubuntu and Mepis a few times I decided I better stick with one). Using Gparted on the LiveCD, I deleted /hda3, then resized /hda1 back to full size. When it finished, it said some of the changes were made to a busy device, and it was recommended to reboot, which I did.

So you are saying just let it sit a few minutes at that prompt? 
Googling showed me it's a common problem, but I never got any specific hits for my resizing issue. So I haven't done anything yet.

---

### Post by beameup on 2006-01-09
I removed the entry for /dev/hda3/ in my fstab file and the error went away. :cool:

---

