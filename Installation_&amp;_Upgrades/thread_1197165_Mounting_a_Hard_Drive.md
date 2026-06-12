---
title: "Mounting a Hard Drive"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by MidsummerDawn on 2009-06-25
Ok, this is my second thread I need help with. My Dell Mini (installed with Ubuntu) has an 8 gigabyte hard drive. But here is the issue, I have a 320 gigabyte Iomega external hard drive that I want to mount. Is there a way I can do this? I keep getting a message that says it won't mount. Any help would be very much appreciated.

~MidsummerDawn

---

### Post by fugaki on 2009-06-25
Can you post the error?

---

### Post by merlinus on 2009-06-25
How is it formatted?  You can first try mounting it manually, and if that works, make it automatic on startup.

Also mounting commands need to be prefaced with sudo, e.g.

```

sudo mount -t ext 3 dev/sdb1 mnt/data 

```

Another thing that may be causing the problem is that ubunu mounts partitions, not drives, so you would have to create a partition on the iomega.

---

### Post by MidsummerDawn on 2009-06-25
This should be it.

---

### Post by merlinus on 2009-06-25
Do you have windows?  If so, mount the drive there, and shut it down correctly.

---

### Post by MidsummerDawn on 2009-06-25
I run Ubuntu on my Mini.

---

### Post by merlinus on 2009-06-25
Yes, you said that in your first post.  What I am suggesting is that you take it someone who has a windows machine, because although the -force mounting option may work, it also may cause data loss.

---

### Post by MidsummerDawn on 2009-06-25
Data loss on how big s proportion? I just got the external hard drive in the mail and haven't used it. And there is really nothing on my Mini that can't be replaced.

---

### Post by raymondh on 2009-06-25
If you say there is nothing in the external, I would go ahead and try -force mounting.  

Also, consider what merlin said about Ubuntu mounts partitions, not drives,

---

### Post by merlinus on 2009-06-25
If it is brand new, then I wonder why it is showing an unclean shutdown error message....

Looks like it is formatted ntfs, from the error message.  You could try these commands in a terminal whilst booted into ubuntu:

```

sudo apt-get install ntfs-config

```You problably will need to restart.

Then:

```

sudo mkdir /mnt/data
sudo mount -t ntfs-3g dev/sb2 mnt/data -o force

```

---

### Post by MidsummerDawn on 2009-06-25
This is what I got when typing in the command error it gave me.

---

### Post by merlinus on 2009-06-25
Did you run the first two commands?  What happened with them?

---

### Post by MidsummerDawn on 2009-06-25
I'm a first time Ubuntu user..when it comes to commands, that's where you lose me. You mean the commands on the previous page? I didn't see those until I posted the screen shot.

---

### Post by merlinus on 2009-06-25
Do you know how to access a terminal?  Type in the commands, one at a time.  Better yet, you can copy-and-paste, but in ther terminal you cannot use a mouse so use Shift-Insert.

The first will install ntfs-3g drivers, which will require a restart.  Thes second creates a mountpoint for your iomega.  The third attempts to mount it to that directory.

Each one will prompt you for your password.

---

### Post by MidsummerDawn on 2009-06-25
I did the commands. But when I looked at the mount error message again. It was sdb1 that showed an unclean shut down. sdb2 was the file that was trying to be created.

---

### Post by merlinus on 2009-06-25
My bad.  Change sb2 to sdb1 in the third command.

Should be:

```

sudo mount -t ntfs-3g dev/sdb1 mnt/data -o force

```

---

### Post by MidsummerDawn on 2009-06-25
Did it, won't work. I'm going to grandparents house and use their laptop to see what we can do about shutting it down or something. Then I'm going to my uncles to download 337 updates I missed. If anything changes, I'll come right back here. Would that be okay?

---

### Post by merlinus on 2009-06-25
Of course.  Good luck.  I'm off to watch a film for the next two hours anyway, but will check back afterwards.

---

