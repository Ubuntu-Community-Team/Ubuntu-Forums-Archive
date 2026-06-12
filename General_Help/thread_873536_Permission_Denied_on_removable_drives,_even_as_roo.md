---
title: "Permission Denied on removable drives, even as root"
date: 2008-07-29
forum: General Help
---

### Post by Shampyon on 2008-07-29
I move files around between my Ubuntu PC at home, my relatives' WinXP PCs and my Win2K station at work. I've noticed that doing this seems to change the owner and file permissions on the drive contents all by itself. I tried changing them both as a user and as root through nautilus: nothing. I tried using *chown* and *chmod* from the terminal: nothing. No matter what user I attempt it as I'm told I'm not allowed to change the permissions.

This is especially frustrating as I do at least half of my work at home. I rely heavily on my portable drives.

---

### Post by dexter.deepak on 2008-07-29
remount your drive with r/w permissions :
sudo mount /dev/DeviceNode /mnt/MountPOint -o remount,rw,uid=UID

---

### Post by saravanan.2407 on 2008-07-29
I also faced a similar problem like this. But i could remember how it happened. I somehow rectified that problem. Sorry man, i could help, i didnt remember what i did for rectifying that

---

### Post by vanadium on 2008-07-29
Can you, with the drive connected to the Ubuntu system, post the output of following commands:

```

sudo blkid
ls -l /media

```

---

### Post by Shampyon on 2008-07-29
I used:
*sudo mount /dev/sdc /media/disk -o remount,rw,uid=4867-14A1*
but nothing happened. I also tried
*sudo mount /dev/sdc1 /media/disk -o remount,rw,uid=4867-14A1*
just in case the exact partition number was needed (it's a single partition drive). The command did nothing. I was sure I had all the right info, but I've never had to find a Device Node before.
[B]
EDIT: [/B]This was originally posted before I saw the above post. Results of those commands:

*sudo blkid*
/dev/sda1: UUID="ef823bf7-7c22-4a40-a32c-da3e628ad8d4" TYPE="reiserfs" 
/dev/sdb1: UUID="283aa65d-1ec8-41fb-8858-ab1a89001afb" TYPE="reiserfs" 
/dev/sdb5: UUID="8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3" LABEL="sdb5" TYPE="reiserfs" 
/dev/sdb6: UUID="9e3a4932-795c-41e4-b96a-4c33ba032c74" LABEL="sdb6" TYPE="reiserfs" 
/dev/sdb7: UUID="e35621df-059d-4288-b99c-8917ba917848" LABEL="sdb7" TYPE="reiserfs" 
/dev/sdb8: UUID="e6df3e16-1257-46a8-aa93-2718b84102a4" LABEL="sdb8" TYPE="reiserfs" 
/dev/sdb9: TYPE="swap" UUID="6180b5f7-152f-4942-b253-02631555ae18" 
/dev/sda2: UUID="90061adf-b9c3-4f97-ba7b-2efe8ffca164" TYPE="reiserfs" 
/dev/sda3: UUID="8c80e9ff-b985-4069-9c31-c6d7f7561832" TYPE="reiserfs" 
**/dev/sdc1: UUID="4867-14A1" TYPE="vfat" **
*(Removable drive in bold)*

*ls -l /media*
lrwxrwxrwx  1 root root      6 2008-04-27 05:13 cdrom -> cdrom0
drwxr-xr-x  2 root root     48 2008-04-27 05:13 cdrom0
drwxr-xr-x  2 root root     48 2008-04-27 05:13 cdrom1
**drwx------  4 shampyon  root  16384 1970-01-01 10:00 disk**
lrwxrwxrwx  1 root root      7 2008-04-27 05:13 floppy -> floppy0
drwxr-xr-x  2 root root     48 2008-04-27 05:13 floppy0
drwxr-xr-x  2 root root     48 2008-05-10 17:17 iso1
drwxr-xr-x  2 root root     48 2008-05-10 17:17 iso2
drwxrwxr-x  6 shampyon  users   136 2008-07-29 18:18 sda1
drwxrwxr-x 10 shampyon  users  1200 2008-07-29 18:17 sda2
drwxrwxr-x  6 shampyon  users   464 2008-07-27 12:31 sda3
drwxr-xr-x  2 root root     48 2008-06-14 18:42 sdb1
drwxrwxrwx 15 shampyon  users   472 2008-05-11 18:08 sdb5
drwxrwxr-x 13 shampyon  users   384 2008-05-02 18:38 sdb6
drwxrwxr-x 14 shampyon  users   600 2008-07-29 17:37 sdb7
drwxrwxrwx 21 shampyon  shampyon    1256 2008-07-29 16:22 sdb8
*(Removable drive in bold, username changed)*[B]

EDIT 2:[/B]Wait... does my removable drive say it was last used in *1970?!*

---

### Post by vanadium on 2008-07-29
This shows your drive is a fat32 drive, and that it is mounted with ownership to shampyon as a user. If you are logged in as shampyon, you should be able to write to that drive because all permissions are set.

This is how my USB stick shows itself:

```

/dev/sdd1: SEC_TYPE="msdos" LABEL="USB" UUID="3B69-1AFD" TYPE="vfat" 
f
drwx------ 8 vanadium root 16384 1970-01-01 01:00 USB
f

```

so this is perfectly comparable to your situation. To make sure all is ok with the mounting, you might also want to post the output of

```

mount

```
For my drive, the output says

```

/dev/sdd1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

which reveals that the drive is mounted for user 1000 (uid=1000) (which happens to be me, with full permissions for the owner, none for the group or others (umask=077).

Can you confirm you cannot write as user or as root issuing the commands (and posting output here)

```

touch /media/disk/file_as_normal_user
sudo touch /media/disk/file_as_root

```

If any error shows up here, we might need to look into checking the file system of the drive.

---

### Post by rated727 on 2008-07-29
While the following is only slightly connected to the main of this thread, I'll share it in hope that it helps if someone lands in the same spot I was.

I copied an unrestricted text file (no permissions required) from a floppy disk to hard drive.  The copy on the hard drive instantly and automatically became 'read-only'.  **WHAT??**  But, I planned to edit that file!!

**Surprise!** the file had inherited a 'read-only' attribute because it had originally been on a 'write-protected' floppy disk.

As superuser user, I removed the 'read-only' file, unprotected the floppy (pushed the tab back to cover the hole) and copied the file again to hard drive - this time it copied WITHOUT the 'read-only' restriction.

---

