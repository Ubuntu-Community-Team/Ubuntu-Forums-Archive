---
title: "[SOLVED] Application won't start - No access"
date: 2008-07-15
forum: General Help
---

### Post by sfilez on 2008-07-15
Hi! I need some help.
Some days ago, I installed ubuntu on my computer with the wubi.
It worked perfect, and i could also boot Win XP without any problems.
But, today, when i use ubuntu everything is so slow, and most applications
won't even start. Opera works, but when it starts I get the following error message:
> 
Store Init failed
Engine Init() failed


All other applications, shows only the window with no content. Just
a grey rectangle. If you know what i mean.
I can't even start Terminal. Or when i try to delete files from the
recycle bin, i get some error message saying I don't have premission
to delete files.

If you need more info about my system to help, please tell me.

Thanks for your time.:)

---

### Post by ago on 2008-07-15
I do not think it has much to do with wubi per se'.

[http://my.opera.com/community/forums/topic.dml?id=153467](http://my.opera.com/community/forums/topic.dml?id=153467)

---

### Post by sfilez on 2008-07-15
Thanks for the link ago. I think i found the reason.
[QUOTE="neeraj_deshmukh"]A store init error means Opera did not have the proper access permissions to your mail directory. You may have to change the permissions on the mail folder (to make it read-writable by your non-admin account) for it to work.[/QUOTE]

I looks like I dont have premissions to write to any folder when using ubuntu. I can't even open nautilus.
Is it possible i messed something by using the "Disk Cleanup Tool" in Windows XP?

Any advice?

---

### Post by ago on 2008-07-15
Well check whether / is mounted ro to begin with or if it is only a matter of individual files/folders. Can you write as administrator (sudo)? What filesystem are you using? Some filesystem will fall-back to read-only if there is any mount error

---

### Post by sfilez on 2008-07-15
Problem fixed. Thanks for your help ago. :)

I booted windows XP, restarted, and then Ubuntu.
Then i got this screen:
> 
...
fsck 1.40.8 ( 13-Mar-2008 )
/dev/shm/root: Contains a filesystem with errors, check forced.
/dev/shm/root: Deleted Inode 16069 has zero dtime. FIXED.
/dev/shm/root: Inodes that where a part of a corrupted orphan linked list found.
/dev/shm/root: Unexpected inconsistency; rund fsck manually. 
(i.e. Without -a or -p options)

fsck died with exit status 4
... fail!

*An automatic filesystem check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the file system restarted.
The fsck should be performed in maintenance mode with the root file system mounted
in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press control-D to terminate the maintenance
shell and restart the system.
bash:No job control in this shell
bash:groups: Command not found
bash:dircolors: Command not found


Runned fsck and restarted the system. Everything works perfect now.

---

