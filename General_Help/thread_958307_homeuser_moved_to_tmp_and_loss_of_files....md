---
title: "/home/user moved to /tmp and loss of files..."
date: 2008-10-25
forum: General Help
---

### Post by jokoon on 2008-10-25
Hello :)

I'm in a big trouble, I lost all my home user files... :( :confused:
Here is the story :
I asked my computer teacher to connect my laptop to the nis network (all machines uses ubuntu) and mount my server files, so I can use my laptop at the school and copy everything directly on my laptop, when I finish something.
We did the steps like changing the server password encryption back to DES from blowfish so other distro can connect (I wasn't able to configure pam to use blowfish correctly...), then we needed to change my UID in /etc/passwd because the server's passwd already had a 1000nth user...

And for some reason my teacher moved my /home/moli (my local username being moli) to /tmp... he moved it there because usually (he thought that) /tmp has the sticky bit (t) so the files can't be deleted by somebody else than the user who created it (at the moment, the root), he also changed my UID in /etc/passwd to 8888 and put the profile dir to /tmp/moli

I did what I need to do on the network, needless to say that I had a xfce on my local profile, and the remote profile was all misconfigured, 

Then I went home, started my machine to switch things back, went to /tmp/moli, and all I could find were default folders (on a new installed ubuntu). Apparently ubuntu *emptied* everything that were in /tmp before shutting down, thus my folder and and all its data (got documents, notes, source files, music, download, etc...)

I'm quite disappointed, does anybody know some nice tool to restore deleted files (from the different ones that exist), and of course tell me why ubuntu deletes all that is in /tmp... :cry:

---

### Post by geirha on 2008-10-25
/tmp is only meant for temporary files and will be cleaned on boot. Your files are most likely gone for ever. You could try booting up a liveCD, install foremost on it, then see if foremost can find any deleted files on it. The probability of recovering deleted files on ext3 filesystems is very slim though. At any rate, if you want to recover files, you want to immidiately stop using the filesystem. Any write operation may overwrite your files.

---

### Post by louieb on 2008-10-25
> **jokoon said:**
> ... and of course tell me why ubuntu deletes all that is in /tmp... :cry:
Thats the way Ubuntu Linux works. /tmp gets emptied when Ubuntu reboots. 

Might be able to recover using photorec available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") it can recover a lot more file types not just photos.

---

### Post by jocko on 2008-10-25
> **jokoon said:**
>  and of course tell me why ubuntu deletes all that is in /tmp... :cry:

That's just the way it is. /tmp is only for temporary storage and is cleared when you reboot.
I don't know much about recovery of deleted files, but I think [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") may recover files for you.

---

### Post by jokoon on 2008-10-26
Thanks for answers !
I put SystemRescueCd on a usb key, I can use either foremost or photorec, didn't try them yet, but isn't there some generic tool to recover lost files other than photos ?
What about ext3grep ?
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)
Its quite a recent tool...
:popcorn:
(no, in fact I'm doing a coconut cake, not popcorn)

---

### Post by jokoon on 2008-10-31
Well I read the tutorial, compiled and used ext3grep, I narrowed the time of deletion of my files, did a -restore-all of another partition, it copies all my partition but my deleted files, I don't really know what to do...
photorec restores a lot of stuff, but mostly random deleted files with generic directory names, so all I got are pieces of text music and so on, in many directories...
Anyone in this forum already used ext3grep ?

---

