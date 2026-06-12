---
title: "Hard Drive worked fine before, now will not mount"
date: 2008-08-25
forum: General Help
---

### Post by FoxTheCave on 2008-08-25
Hi, my 700gb FreeAgent External HardDrive worked perfectly a few days ago. Today however, I took it to a friends to get some movies off of him. He uses Windows Vista - now however, the hard drive will not mount on my Ubuntu Operating System. When I plug it in it simply says:

[[IMG]http://img137.imageshack.us/img137/6619/cannotmountam7.th.png[/IMG]](http://img137.imageshack.us/my.php?image=cannotmountam7.png)

Anyway, I tried both of the suggestions for Linux users there and neither worked. I typed that into the command line letter for letter, and it simply told me that 'only root could mount' (what does this mean?) and that for the second one, the directory didn't exist.

When I added sumo to the original as someone else told me to, the command line simply spat all this back out at me:


[[IMG]http://img528.imageshack.us/img528/3238/mountingprintscreenty0.th.png[/IMG]](http://img528.imageshack.us/my.php?image=mountingprintscreenty0.png)

Can someone translate that or direct me further?

Can someone please help me? This thing cost me a hundred sterling!

Many, many thanks in advance!

---

### Post by mssever on 2008-08-25
You have to connect the drive to a Windows machine, let it mount, then use the safe remove function in Windows. You might need to do  this twice.

---

### Post by FoxTheCave on 2008-08-25
I was afraid of that.

Is there no workaround? Connecting it to a Windows machine isn't too practical right now, for reasons to long to go into.

---

### Post by mssever on 2008-08-25
> **FoxTheCave said:**
> I was afraid of that.

Is there no workaround? Connecting it to a Windows machine isn't too practical right now, for reasons to long to go into.
I don't think that the Linux NTFS driver is able to safely cope with unclean NTFS partitions. So, as a safety precaution, it refuses to mount unclean partitions.

---

### Post by FoxTheCave on 2008-08-25
Okay, thanks.

---

