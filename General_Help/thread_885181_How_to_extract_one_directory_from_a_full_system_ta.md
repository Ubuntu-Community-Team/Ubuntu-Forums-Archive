---
title: "How to extract one directory from a full system tar backup"
date: 2008-08-09
forum: General Help
---

### Post by sofasurfer on 2008-08-09
I backed up my system using...

 "tar cvpzf backup.tgz.07.01.08 --exclude=/proc/* --exclude=/lost+found/* --exclude=/sys/* --exclude=/mnt/* --exclude=/media/* /"

Now, since the restore function left me with a none bootable system, I want to extract a particular directory from this file to put into my newly installed system.

How do I do this?

---

### Post by jerome1232 on 2008-08-09
```
tar xzf [archive] [directory to be extracted]
```

ie if I wanted /home and the archive was backup.tgz and I wanted it extraced to /
```
tar xzf backup.tgz /home -C /
```

---

### Post by sofasurfer on 2008-08-10
When running the command that you suggested I end up with this command...

tar: /home: Not found in archive
tar: Error exit delayed from previous errors

I understand that the "error" message is to be expected and has no ill effect. But the "not found" error is perplexing because it most certainly does exist.

This is the command I ran...

 "sudo tar vxzf /media/disk/backup.tgz.07.31.08 /home -C /"

---

### Post by jerome1232 on 2008-08-10
edit: I think use home instead of /home will do it

try listing out the contents of the archive btw you can check the man page for tar for most of this but I know they can be confusing sometimes.  This command will create a listing of the contents of your archive, then view it with gedit, of course you can replace gedit with your favorite text editor
```
tar tvvzf /media/disk/backup.tgz.07.31.08 >backup.tgz.07.31.08.list
gedit backup.tgz.07.31.08.list
```

then you can view the contents in a text file (maybe it's as simple as typing home instead of /home)

---

### Post by sofasurfer on 2008-08-11
It works.
To restore a particular directory I used this command...

root@daryl-desktop:/# tar xzf /media/disk/backup.tgz.07.13.08 home/daryl/Videos -C /home/daryl 

You must be root. Then you may or may not need to cd /, But you might as well.
After specifying the archive, you specify the particular directory or file WITHOUT PROCEEDING IT WITH "/". 
The last part (after -C) tells what directory you want it to go into.



To create a listing of a particular archive directory you use nearly the same format with just a couple of changes...

root@daryl-desktop:/# tar tvvzf /media/disk/backup.tgz.07.13.08 home/daryl/Videos >video.list 

The options (tvvzf) are differant. "t" means to make a list. I do not understand what "vv" does. I thought it would print out the progress on the screen but it does not. And I don't understand why there are 2 v's.

The last part (>video.list) says to send the list to a file called "video.list". This will go into whatever directory you are cd'd into.

Thanks for your help and I hope my clarification helps someone else.

EDIT:: 
I have just verified that you MUST 'cd /' in order to get you directory restored to the proper location.

---

### Post by jerome1232 on 2008-08-11
You know what I thought the second v made it more verbose, but on investigation I don't think it does, the output looks the same to me. So the second v can be eliminated it's not doing anything.

```
jeremy@destkop:~$ tar tvvf tar.tar
drwxr-xr-x jeremy/jeremy     0 2008-08-10 17:09 torrent-files/
-rw-r--r-- jeremy/jeremy 22545 2008-08-10 17:09 torrent-files/ubuntu-8.04.1-server-i386.iso.torrent
jeremy@desktop:~$ tar tvf tar.tar
drwxr-xr-x jeremy/jeremy     0 2008-08-10 17:09 torrent-files/
-rw-r--r-- jeremy/jeremy 22545 2008-08-10 17:09 torrent-files/ubuntu-8.04.1-server-i386.iso.torrent

```

---

