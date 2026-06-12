---
title: "Weird external hard disk error &quot;I/O Error Writing File&quot;"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by gh0st on 2007-01-11
Hi, I have a problem with an external USB hard disk. It's formated to NTFS and I have been using NTFS-3G to read and write to it for months with absolutely no problems, until today ](*,) 

Here's the story. My motherboard seems to have a fault and keeps causing my machine to freeze and lock up, I finally got round to getting a new motherboard and case sorted and I was backing up some of my data to the external drive before I move to the new machine. 

While I was in the middle of a transfer the machine froze and I tried everything to revive it, In the end I had to do a hard reset on it by pressing the power button. Not ideal but it was a last resort.

When I rebooted I tried to do the transfer again and now my external drive won't let me write to it at all. I've tried everything, I even tried manually mounting it but it didn't make a difference. I just get a msg box with the following error "Error: I/O Error, file could not be written". I can see the files on the disk fine but now can't write or make any changes to the disk. This problem must have occurred because the machine crashed while transferring files.

Does anyone know what I can do to get this writing again? I was thinking of removing and then reinstalling NTFS-3G but I'm pretty sure it's a hardware fault and not a software one. Is there anyway I can reset the drive without reformatting and losing vital data? Whatever the machine was doing to the drive at the time of the crash it seems to be stuck in that state. Please help I need to rescue this data.

Thanks in advance and sorry about the long winded explanation :)

---

### Post by logos34 on 2007-01-12
The first thing I would do is try to run chkdsk from windows...the drive could have developed bad sectors, corrupt index, etc as a result of what you did (even though it has its own ac adapter and should have been unaffected when you cycled the power).   AFAIK there's no linux equivalent to check disk for scanning ntfs filesystem.

---

### Post by gh0st on 2007-01-12
Thanks for the advice I'll definitely try this. I was wondering if there was some way to check the disk in Linux but now I know there isn't, I'll stick in a Windows PC and see what I can do with it.

Just as a quick update, I tried reading stuff off the external disk and that still works so at least I can get my data back, that was a relief I can tell you 8)

---

### Post by gh0st on 2007-01-12
I ran chkdsk on my Windows machine with the external drive and it fixed the problem, I can read and write to it in Ubuntu again, Thanks for the tip. It cleaned out loads of rubbish from the disk which must have been left over when the transfer crashed. Happy days :D

---

### Post by logos34 on 2007-01-12
Glad to hear you fixed it.  Enjoy.

---

