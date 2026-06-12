---
title: "can I get this file back?"
date: 2008-08-02
forum: General Help
---

### Post by tbunix on 2008-08-02
I installed [_SweetHome3d_](http://sweethome3d.sourceforge.net/) on both my Linux and XP partitions. Mapped my house on the Windows side, booted into Ubuntu 8.0.4 and wanted to work on it. During a momentary brain lapse I dragged file from Nautilus and dropped in on the SweetHome3d desktop icon. 

The program gave an error and ... no file.

I tried sudo find / -name '*sh3d'
and sudo find /home -name 'sh3d' to no avail.

I assume it's gone and that lesson cost me a couple of hours work but thought I'd ask and see if any of the bright ones here know where else I might look.

---

### Post by pytheas22 on 2008-08-02
First of all, try not to do anything else to your file system (don't install or move anything), because it will decrease the chance that you can get the file back.

The file, or most of it, should still exist on the disk and *may* be recoverable that way.  What does this command tell you:
```

lsof | grep sh3d
```

Also, keep in mind that 'locate' doesn't always find files if they're really new.  Trying it again in a few hours may help.

And which file system are you using (ext3, reiserfs...)?

Finally, this [guide]("http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html") may be useful.

---

### Post by tbunix on 2008-08-03
Thanks for the lesson in recovering files! 
But since I had already rebooted lsof did not work. That link is interesting. I'll mark it for use if (when) I lose a file again.

I am using ext3

---

### Post by dexter.deepak on 2008-08-03
may this link help you :
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by tbunix on 2008-08-04
very interesting link!- a quantum leap in my understanding of ext3

since I dragged the file from an ntfs partition and dropped it on an icon on my Ubuntu desktop. I started looking for the file on the ntfs side - no luck.

I am recreating the file
and learning more and more about file systems

in that sense it is a happy accident

---

### Post by pytheas22 on 2008-08-04
Also keep in mind that [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") is a nice tool for recovering lost files by searching for remnants of file headers, on any kind of normal file system.  It can be installed in Ubuntu with:
```

sudo apt-get install testdisk
```

(it's part of the testdisk suite).

Unfortunately it can only recover a limited list of file types.  If you knew what the file header for sh3d files looked like, you could maybe get photorec to search for it.  But it's probably not worth the work it would take to write that, and anyway I assume that the program is proprietary and its file streams are not documented.  There may be NTFS recovery tools that could help you, but I don't know much about that side.

photorec is nice for recovering stuff like music, pictures and documents, though, so I thought I would mention it in case anyone else finds this thread looking for disaster-recovery help.

---

