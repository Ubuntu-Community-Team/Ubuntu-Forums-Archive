---
title: "Slight problems mounting hfs+ drive"
date: 2008-08-07
forum: General Help
---

### Post by DrQuincy on 2008-08-07
Bear with me here as I'm not very experienced in mounting drives . . .

I got an external drive (USB) for my Mac and formatted it as HFS+ with no journaling. I wanted to read/write with my Ubuntu machine to so I installed the hfsplusutil package.

When I plug the drive into Linux it doesn't appear in /media/

If I list all the drives in the shell it's there but the file format is 'Unknown'

I found this on another thread and adapted it (like I say this is all new to me):

```
sudo mount -rw /dev/sda1 /home/tim/Danny -t hfsplus
```

After that if I go to /home/tim/Danny in nautilus I can see all the file but can't write to it. I can as root though. Weirdly, I get an unmount volume option if I'm not running as root then it complains about it not being in the fstab file. But if I'm root I don't get the option to unmount.

So I guess my questions are:

1. How to I get the drive to appear automatically when I plug it in?

2. How do I get it so that I have permission to write and unmount the drive as me rather than root?

Thanks.

---

