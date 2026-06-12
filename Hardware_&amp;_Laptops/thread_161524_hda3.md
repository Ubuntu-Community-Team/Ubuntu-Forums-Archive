---
title: "hda3?"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-04-17
I created a hda3, 4.5GB FAT32 filesystem meant for sharing files between ubuntu and windows, but somehow, I cannot set permissions, even with gksudo nautilus. Can anybody help?

---

### Post by mpvano on 2006-04-17
FAT file systems do not HAVE most of the permissions that linux file systems support. You can only set or clear the ones that do exist in the design of that file system because they have to be stored in the file system somewhere and honored by all programs that use them, not just Linux.

I'm not sure which ones are actually available, but I can tell you that I don't believe FAT has the concept of 3 sets of permissions, so group, world and owner permissions can't be different from each other. There's also definitely no "execute" attribute, which also controls directory operations. There are no suid or guid bits either.

In most cases you can control the overall behavior of a volume at the time it's mounted by setting the mount options to force ALL the files on the volume to have a specific behavior, but even this has restrictions - refer to the mount documentation for the file system in question.

By the way, the problem is not restricted to FAT file systems, many other kinds of file systems have incompatible attribute systems that don't map perfectly into linux....

hope this helps you understand the problem better....

Mario

---

### Post by nolongerlivecd on 2006-04-17
In that case, what can I do to create a partition for file storage shared between windows and ubuntu?

---

### Post by mpvano on 2006-04-18
Why can't you live with the restrictions I described, just like the rest of us do?

Computers don't just "Do What You Mean" them to do. You need to design a solution by studying the problem, understanding all the limitations and figuring out a way to use the tools you've got that satisfies enough of your requirements to do the job. That's how all engineering works.

The bottom line is you can't upgrade windows FAT file systems behavior to magically give it the properties of Unix type file systems - Windows program's won't update the attributes they don't know about correctly, and vice-versa - nor can you store Unix-style files on FAT file systems - they don't have anywhere to put the extra directory information.

Different file systems have different goals and implement them in completely different ways. All you can hope for in shared access is the lowest common denominator. Normally, however, that's usually good enough.

You use the attributes that are there and lose the ones that don't get stored.

What exactly are you trying to do? The type of files and manner of sharing them will determine what you need to do to store them.

If some file's attributes are REALLY important, you can embed volumes using loopback file systems into single files on foreign file systems, but that means that the local file system can't access them since it may or may not know how to read what's in the file container you used. You might use this kind of technique to store Unix applications on a DOS volume (There are whole releases that store ALL their files on a FAT volume this way!). Of course, windows can't read the contents of that container, but it rarely needs to if you've only stored unix programs there.

If you think you need to set linux file attributes on a Windows file, you need to ask yourself what will a windows program do with them? It certainly won't honor them.

If you are trying to preserve file attributes on linux files when they are stored on a Windows file system, you will need to archive the files in a container that does that (like Tar).  If you are trying to preserve windows file attributes when they are stored on a unix file system, you are in a little better shape, but there are still some subtleties that only allow perfect restoration from an archive format like .ZIP).

There's usually a way to achieve what you are trying to do using the means I listed in detail in my earlier message. Did you look them up?

Pay special attention to all the options to the mount command that let you force attributes to certain values when the files are mounted.

For example, you can usually control simulation most of the behavior of the executable file attribute for unix this way by always clearing it on your FAT file system - there's no good reason to be storing unix binaries on a windows file system.

There will be some things you can't reconcile, like the differences in the way FAT and EXT file systems timestamp files (and especially directories - the semantics are completely different), but you'll just have to avoid storing files that rely on these behaviors on shared volumes, or find smarter programs!

Personally, on dual boot machines I just use an extra FAT partition of a few Gigabytes that I keep around just for moving things around. I don't recommend storing things while working ont them there unless they're too big to copy (like Video or Audio work files). Read-only access to other partitions is usually adequate  to just copy things from Windows.

For things that this isn't adequate for, you need to use a networked file server that can translate operations and hide extra file information as needed to fool different operating systems into each seeing what it needs. Solutions like this usually require a separate CPU, but it's cheap to set up an old junker to solve this kind of problem using Samba, Netatalk, NFS, and other free servers. You can even buy such solutions, ready to plug and play, quite cheaply from dozens of vendors like Linksys, Maxtor, WD, etc.

Sorry I can't be more specific. You'll need to work this out yourself depending on your needs.

I DO suggest, however avoiding simple minded solutions like trying to just throw all your files of both types into a single big volume and using it as your only disk volume.

Mario

---

### Post by nolongerlivecd on 2006-04-19
Thanks. I needed that :). Now, my MAIN problem is my wireless, re the networking forum second page currently (what? no internet?)

---

