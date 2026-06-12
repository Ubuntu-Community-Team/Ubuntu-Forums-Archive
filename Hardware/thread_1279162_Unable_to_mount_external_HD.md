---
title: "Unable to mount external HD"
date: 2009-09-30
forum: Hardware
---

### Post by opower95 on 2009-09-30
I've been using this particular external hard-drive for over a year with no problems. I switch between a Windows computer and an Ubuntu laptop but it works fine doing so.
[INDENT]      I should give a little bit of back story here. My laptop is breaking physically and freezes from time to time. When it freezes I can do nothing but move the mouse and I have to shut it down manually.
[/INDENT]     Last night I ran out of space on my 40GB (I know :( ) laptop *again* so I do what I normally do: go get the external hard-drive and began transferring. 
      
Well last night it froze while I was transferring files and I had no choice but to shut it down without unmounting the EHD. When I went to plug it in this morning I'm getting this message when I go to my computer folder:
"Unable to mount location
Can't mount file"

How can this be fixed? I'm assuming it's because I didn't unmount it but I could be wrong. 

Please and thank you.

---

### Post by mikewhatever on 2009-09-30
You need to run a file system check on the external hdd's partition. Connect the hdd and run **sudo fdisk -l** to get the device name. Don't bother mounting, it's not needed. Then, run sudo fsck -a /dev/sdXY, where X and Y are the identifies corresponding to the external hdd's partition. If the file system in question is ntfs, you need to use ntfsprogs instead.
If you need some more help, post the output of fdisk -l here, along with any other questions.

---

### Post by opower95 on 2009-09-30
I apologize for not being too savvy with terminal (I guess Ubuntu for that matter) but can you tell me what this means:
[INDENT] *****@*****-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe9cbe9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
*****@******-laptop:~$ sudo fsck -a /dev/sda2
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

[/INDENT]

---

### Post by mikewhatever on 2009-09-30
This simply shows your partitions (sda1,sda2,sda3), but I don't think the external hdd is there. Is it connected? Usually, the external hdds show as sdb or sdc. You can also install Gparted to do the same system check graphically.

---

### Post by opower95 on 2009-09-30
Yes, it's connected but it doesn't show up on my desktop or in the places menu. If I go to the computer folder I can see where it should be it says "USB drive" but when I try to open it, it gives me the "Unable to mount location...". 

It's not showing up on the system check. 

[Here]("http://imgur.com/KvRyU.png") is the computer folder when the hard-drive is plugged in, and [here]("http://imgur.com/QHofO.png") it is when it's not plugged in. Sorry about that update notification in the corner.

And the system check listed the same things as Terminal. 

I'd like to add that I really appreciate your help on this, thank you very much.

---

### Post by mikewhatever on 2009-09-30
Very odd. I'd expect the drive to be seen by fdisk if it shows in the file browser. You might need to wait up to 5-10 seconds before running the command though. Anyway, it should be safe to assume that the partition on that drive is sdb something. Try the following and see what happens:

sudo fsck -a /dev/sdb1

---

### Post by opower95 on 2009-09-30
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by mikewhatever on 2009-10-01
Hmm, not sure what to say, I am no expert in file system repairs. Have you tried Gparted yet? I doubt it would work, but there is no harm in trying. Once installed, open it from System->Admin->Partition Manager. You get to select hdds in the top right corner, if the external hdd is there, right click on a partition and select Check.

---

### Post by community nerd on 2009-10-01
If all you are trying to do is get your files before you re-install ubuntu, just boot from the ubuntu cd on a live session.

---

### Post by mikewhatever on 2009-10-01
> **community nerd said:**
> If all you are trying to do is get your files before you re-install ubuntu, just boot from the ubuntu cd on a live session.

And how would that help, might I ask?

---

### Post by opower95 on 2009-10-01
No, it doesn't show up in Gparted, but thank you both for trying to help. I just can't interact with the HDD in any way, that's the overall problem. I guess I'll just keep trying as many things as I can think of. :)

---

### Post by cmcanulty on 2009-10-02
Same problem here and ext HD is fine with windows but I need to backup my files before I can reinstall. This is a huge Ubuntu problem for many people.

---

