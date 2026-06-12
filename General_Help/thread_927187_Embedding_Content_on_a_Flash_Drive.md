---
title: "Embedding Content on a Flash Drive"
date: 2008-09-22
forum: General Help
---

### Post by johntelthorst on 2008-09-22
Is is possible to "embed" data on a flash drive so that it can't be deleted (at least not very easily)?

---

### Post by lisati on 2008-09-22
Making it "hidden" and/or "read-only" might be a start.....

---

### Post by stickmangumby on 2008-09-22
Not really. If you're sending the flash drive to somebody else, and computer they put it in doesn't have to respect the file permissions that are 'protecting' it.

However, if it's attached to your computer, and you're worried about somebody else using your computer and deleting stuff from it, you can set permissions on it. I'd use a Linux based filesystem on it though, such as ext3.

Hit me with specific details and I'll be more able to help you.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
You could also create two partitions, one fat32 and one ext3.

That way, if a windows user put the flash drive in his box, windows will only show him the fat32 partition.

Whereas you will see both partitions if you put the flash drive in a linux box.

---

### Post by mb_webguy on 2008-09-22
Some Flash drives, like the fancy ones that self-destruct if someone tries to tamper with them, have programs embedded on them, but those programs are hard-coded on the chip, and not contained in the flash memory.

If the Flash drive is formatted as ntfs (although most are formatted as FAT32), you can set the ntfs permissions to make it hidden and read-only in Windows.  If you then make the filename start with a dot ("."), then it will also be hidden (but not read-only) on Linux.  However, in every case, all a user would have to do is set their file manager to view hidden files and then change the permissions in order to delete the file.

---

### Post by johntelthorst on 2008-09-22
Well I'd like to be able to have someone I give the drive look at the files, and execute them, but not be able to delete them.  I'd like for it to be compatible with Linux, OS X, and Windows XP/Vista.  It sounds like I don't really have any options though.

---

