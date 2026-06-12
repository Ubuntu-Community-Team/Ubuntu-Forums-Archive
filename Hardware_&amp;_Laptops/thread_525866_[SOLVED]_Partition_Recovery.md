---
title: "[SOLVED] Partition Recovery"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by gali98 on 2007-08-14
I have a serious problem. I have an old computer, with a 6 gig hard drive. It is split into two partitions, the main file system and the swap. Somehow, (I have no idea) the file system (ext3) became corrupted. I was able to boot a live cd and used gparted to find this. It showed the partition as being corrupted, or unrecognizable. I'm not the most advanced in linux, so I'm a little scared to do anything yet, because I do want to recover a few files off of it. I'm okay with reinstalling, after that, but I want to able to bypass that if able. basically what I need is a way to tell linux that this partition is ext3. Any help would be much appreciated. Ask and I will try and answer any questions. I can probably follow most advanced instructions. Thanks....
Kory

---

### Post by merlinus on 2007-08-14
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

-merlin

---

### Post by gali98 on 2007-08-15
Thanks I did find that, but it didn't work so well, so I tried a fresh install... and that didn't work so well either. For some strange reason, it erased it all, but it cannot for the life of me repartition it. I tied Gparted and Gparted Live, but on both when I try to partition the only option it gives me is "new" and when I do that it pops up for me to create a disk label, and when I go through that and say yes a few times, it just scans the disks again, and then goes back to the way it was, and all I can pick is new again...... and on and on. Any suggestions? Tomorrow I'm going to put it in My Windows Xp box, and see if it can do anything to it. Again, any help would be appreciated. Thanks,
Kory.

---

### Post by gali98 on 2007-08-15
Okay I found out what is wrong, though not what I can do about it... I put it in windows and it formated it to fat32. So I put it back in my other linux box and opened the gparted live cd, and told it to delete that and partition it as ext3. It goes on and deletes it and then comes up and says it cannot read the "disk label." Then it puts me where I was in the beginning. It lets me pick new and lets me set the disk label, but when I say okay it just brings me back to the part where I can pick new again. So I guess the disk label is damaged, and gparted can't fix it. Does anyone know what can? I'm really not even sure what a disk label is, but I guess it's important. Any help would be appreciated...
Kory

---

### Post by gali98 on 2007-08-15
Okay I fixed it. I'm posting this in case anybody ever has this problem. First of all I'm pretty sure I could have recovered everything with that link above. (thanks merlinus), but i wasn't quite sure what I was doing, so yeah.... But you should try testdisk first to see if you can recover any lost or corrupted partitions... moving on.... In my case the partition table (partition map, disk label, all the same...) got messed up somehow, probably when I was messing around with it trying to fix it.... the irony.....
Anyway so I used testdisk (the same program above) to delete the MBR (master boot Record) and then write the testdisk MBR. I did it a couple of times, and when I went in to install Ubuntu again, it worked like a charm. I hope this helps someone, and that you read this before you destroy anything.... Thanks everyone. Problem solved.
Kory

---

### Post by gali98 on 2007-09-15
Hey everyone. This is an update....obviously...
Well after I reinstalled and made everything perfect (which took many hours) I rebooted and it did the same thing....(some things make you want to take a shotgun to the thing).... after reinstalling  again it did the same thing, so I guess the hard drive went bad. If you hard drive does the same as mine, consider getting another hard drive... it could save you some tears...
So all in all I had like four systems crash... not fun. Good bye all.

---

