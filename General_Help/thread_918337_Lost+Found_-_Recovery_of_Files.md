---
title: "Lost+Found - Recovery of Files"
date: 2008-09-12
forum: General Help
---

### Post by xefialtis on 2008-09-12
Ok, so I had some major troubles with my raid array, and it dumped everything. I ran the fsck thing, and it went on for 2 and a half days. Then to my great horror, but not a surprise, all my data is GONE...
But wait, it isn't really gone, it is in the Lost+Found folder...only, I don't recognize any of the files...

So, to make this task simple (ha-ha) I need a little information...
in the properties of the file, we see things like :
cr--r-Sr-t 
brwxrwxrwx 
srwx-wsr-t 
pr--rwSrw-
drws--s---

and so on...

CAN ANYONE TELL ME WHAT THIS ALL MEANS?  I have lots of files I would like to see if I can recover...but I just don't get how...

For instance, how do I tell if this file is a document, or a program?

Is there any data stored in the file itself that might tell me the original name...because I know the name of the file isn't #9988070, or #9887289, or even #98.

Thanks for any help, insight, information, or chastisement... ;-}

---

### Post by HalPomeranz on 2008-09-12
> **xefialtis said:**
> 
cr--r-Sr-t 
brwxrwxrwx 
srwx-wsr-t 
pr--rwSrw-
drws--s---


The first letter indicates what kind of object you're dealing with.  For example, the last entry above starts with a "d", meaning it's a directory.  "c" and "b" are device files, which you probably don't care about.  "s" and "p" are sockets and named pipes, which you also probably don't care about.  Things beginning with "-" are regular files and those are probably what you want to start looking through first.

The other nine letters are the permissions on the file-- "read" ("r"), "write" ("w"), "execute" ("x"), and special bits like "set-UID" and "set-GID" ("s") and the "sticky" bit ("t").  These are probably not that interesting to you in terms of trying to recover your data.

> **xefialtis said:**
> 
For instance, how do I tell if this file is a document, or a program?


The "file" command can help with this.  For example:

```

$ **file /bin/bash /etc/passwd /var/log/messages.1.gz**
/bin/bash:              ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
/etc/passwd:            ASCII text
/var/log/messages.1.gz: gzip compressed data, was "messages.0", from Unix, last modified: Sun Sep  7 07:43:19 2008, max compression

```

You could use the file command to at least give you a clue about what kinds of files you're dealing with.

> **xefialtis said:**
> 
Is there any data stored in the file itself that might tell me the original name...because I know the name of the file isn't #9988070, or #9887289, or even #98.


There's nothing in the files themselves that's going to help you.

The numbers being used for the file names are the internal file system index node (aka inode) numbers that the OS uses to keep track of files.  In a functioning file system, directories are a special kind of file that associates a human-readable file name with an inode number.  Unfortunately, since your file system got trashed, it's going to be really difficult for you to reconnect the file names with their inodes.  There may be some sort of file system forensic tool out there that could help with this, but I don't know of any.

---

### Post by Herman on 2008-09-12
Another Ubuntu user, confused57, told me that he had all of the files in one partition sent to the /lost+found.
He said he just did 'sudo nautilus', and recovered all his files this way,
> Opened the partition and the only folder present was  "Lost+Found"(owned by root), which contained all the folders that I previously had on the partition, except the folders were renamed to the inode on which they were found.  I just did a "gksudo nautilus", right-clicked on the "Lost+Found" folder, changed the ownership and permissions.  Although the folder names were changed the file contents inside the folders had the original filenames and were intact.  It was no problem to drag & drop the folders to a spare partition, even a couple of small FAT32 truecrypt volumes I was playing around with were completely recovered.  I believe I was able to recover nearly 100% of the data on the partition, Will that help? :)

---

