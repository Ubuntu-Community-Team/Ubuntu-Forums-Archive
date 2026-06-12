---
title: "to reformat or not?"
date: 2009-09-19
forum: Hardware
---

### Post by Bunny Boy on 2009-09-19
I recently purchased a Western Digital My Book Essential Edition 1 TB USB 2.0 external hard drive.  I got it to do back-ups and was pleased to see that it worked right out of the box.  Problem:  many of my files have names that contain unacceptable characters.  I'm supposing that this is because of the file system used.  I suspect it is some sort of FAT, but when I check in my disk utility, it tells me "unknown."  

I'm wondering if it would be prudent or even feasible to reformat this hd as ext3, thereby allowing my files to be copied.  I want to be careful because this runs the risk of rendering the drive inoperable. Western Digital offers absolutely no support for linux. 

Barring that, I guess I could try to rename all of the files.  Is anyone aware of a script that will do this?  There are hundreds of them, so changing them manually is not really possible.

Ubuntu 6.06 LTS Dapper Drake

---

### Post by quixote on 2009-09-20
which disk utility are you using?  Anything *nix-based ought to be able to do better than "unknown."  Linux recognizes about a 100 different filesystems, and I'd be surprised if even Western Digital could come up with something totally unknown.  Try```
sudo fdisk -l
``` when the WD drive is mounted and see what it reports.  ("-l" is for list.  Careful with the options on this command, since it can also be used to format your drive.)

When you say "unacceptable characters" are these ones you used, eg spaces in filenames, or some strange stuff the WD drive is putting in?  If it's ASCII characters, like spaces, you can use krename (installable via synaptic) to find and substitute them all with something else.  It will operate on subdirectories recursively, but that's an option you have to select.

---

