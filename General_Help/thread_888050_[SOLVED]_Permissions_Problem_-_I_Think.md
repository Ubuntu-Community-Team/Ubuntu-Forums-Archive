---
title: "[SOLVED] Permissions Problem - I Think"
date: 2008-08-12
forum: General Help
---

### Post by psuliin on 2008-08-12
Hi, folks!  This got started from a failed upgrade (Gutsy to Hardy).  I wrote about it [here]("http://ubuntuforums.org/showthread.php?t=884196"),  beginning with post #5 on that thread.  However it's turning into less of an upgrade problem and more - I think - of a permissions problem. So I decided to bring my last post on this thread over here.

Here's the capsule summary, for those who don't want to wade through the other thread.  It's still a bit long though - my apologies, but I don't know what's critical and what isn't.

I tried to upgrade from Gutsy to Hardy.  The upgrade froze during the process of building locales, and I ended up having to reboot.  When I tried to log in again though I got a system message saying that my home directory did not exist.  

I went in on a live CD, and found that my directory and associated files were still there, but I couldn't access them.  I'm still not quite sure what happened to cause this - possibly a glitch in the file system when I interrupted the upgrade that both prevented the system from recognizing my home directory and prevented me from getting in.

I used **chmod** and **chown** to return the permissions to my account, but I misunderstood the helpful fellow who told me how to do that, and ran those commands from within the live CD.  This of course didn't help me much.  I even added myself as a user on the system (using the same username and password I'd been using), but again this was done in the live CD session.

To make a long story short, none of this solved my problem.  As a last resort I backed up the files I could get to and reinstalled Gutsy from the live CD.  Fortunately I had most of my data on a separate storage partition, so I was able to leave that partition alone when I reinstalled.  UNfortunately that's the directory that I couldn't get into.  And I still can't, after reinstallation.

This is what I see when I look at the volumes on my media directory: 

```
lrwxrwxrwx  1 root root        6 2008-08-09 16:06 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-08-09 16:06 cdrom0
drwx------ 13 paul root     4096 1969-12-31 16:00 CORSAIR
drwxrwx---  1 root plugdev 12288 2008-08-09 09:21 sda1
drw-r--r--  5 paul root     4096 2008-04-13 04:25 sda4
```

CORSAIR is my USB flash drive.  /media/sda1 is my Windows partition (I'm dual-booting).  /media/sda4 is my data directory.  I can access every one of those except for the last one: /media/sda4.  A poster on the other thread suggested that the problem might be inconsistent user/group assignments, but I'm not sure that's the issue.  The user/group assignments are:

cdrom0: root/root
CORSAIR: paul/root
sda1: root/plugdev 
sda4: paul/root

I can access /media/CORSAIR, and it has the same user/group assignment as /media/sda4, which I can't access.  

The main difference seems to be in the access permissions.  /media/sda4 doesn't have e(**x**)ecute permission for either the user or the group.  All the others have (x) for at least the user, and usually both.  I just noticed this after digging around in Sobell's *Practical Guide to Ubuntu Linux* to learn how to decode the output from **ls -l**.

If I understand directory access permissions, that would prevent me from using **cd** to get into the directory, which is the problem I'm having.  If that's correct, then **chmod** should be able to help.  Something like this:

```
$ sudo chmod u+x /media/sda4
```

Before I go poking any more sticks into this, though, I'd like to confirm with someone more knowledgeable than I that this is the right command to fix this problem.

There is one other possible problem that occurred to me while I was trying to figure this out.  Is it possible for two different user accounts to have the same ID and password on a single system?  I wouldn't think it would be, but I wonder if, when I added "paul" as a user through the live CD, I might have created a second user named "paul" on my machine.  In that case the "paul" listed as user on /media/sda4 might not be the same as the "paul" on /media/CORSAIR.

That seems like an awfully slipshod way to design a system, so it seems pretty unlikely, but I figured I ought to ask before I go in and tinker with my access permissions any more than I already have.

Any advice?

---

### Post by kpatz on 2008-08-12
Is sda4 mounted when you're in the live session?

Type 'mount' and see what you get.  If it's mounted to say, /mnt, go to /mnt/home and check the permissions on your home directory there.

If it isn't mounted, try 'mount /dev/sda4 /mnt' (or use a different mount point if /mnt is already used).

---

### Post by psuliin on 2008-08-12
kpatz, I did reinstall Gutsy.  When I did that, I saw sda4 mounted, as one of the partitions that I might have turned into my new root.  I didn't see a pathname for it though.  

The permissions information that I posted in my OP was from a session on my new, reinstalled system.  Is there a reason why I'd need to go in on the live CD and look at this now?

---

### Post by kpatz on 2008-08-13
I thought you were working from a live CD session.

When you type 'mount' from your new install, what is the output, particularly for /dev/sda4?  There should be a mount point shown.

For example:

/dev/sda4 on /home type ext3 (rw,relatime)

---

### Post by psuliin on 2008-08-14
> **kpatz said:**
> I thought you were working from a live CD session.

When you type 'mount' from your new install, what is the output, particularly for /dev/sda4?  There should be a mount point shown.
OK, here's what I get.  I'm bolding the output for sda4

```
paul@machine:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
[B]/dev/sda4 on /media/sda4 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)[/B]
/dev/sdb1 on /media/CORSAIR type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
paul@machine:~$ 

```

---

### Post by psuliin on 2008-08-15
So, any clues there?

---

### Post by psuliin on 2008-08-16
Well, didn't hear anything back on this thread, so I went ahead and tried the **chmod** command.  It seems to have worked.  Now I just need to upgrade to Hardy.

---

