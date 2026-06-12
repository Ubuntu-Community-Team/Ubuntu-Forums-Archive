---
title: "vfat not mounting"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by dodecaman on 2007-12-10
I've read through the various threads, and must be missing something important.

I'm new to Ubuntu - just coming back to Linux after a bad SuSE experience a couple of years ago.

I just set up my laptop to dual-boot winXP and Gutsy (7.10).  When I attempt to open my shared fat32 drive I'm required to enter my password - annoying, and probably the core of my problem.  The problem is that I can't seem to set it up to mount automatically at startup.  Here's what I have (fdisk -l):

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1622    13028683+   7  HPFS/NTFS 
/dev/sda2            1623        3887    18193612+   f  W95 Ext'd (LBA) 
/dev/sda3            3888        4864     7847752+  83  Linux 
/dev/sda5            1623        3837    17791956    b  W95 FAT32 
/dev/sda6            3838        3887      401593+  82  Linux swap / Solaris 

My fstab line  for the fat32 reads:

# /dev/sda5	/media/Shared	vfat	defaults,unmask=000	0	0

I have the "Shared" folder set up in the "media" directory, but am having no joy.  I don't seem to having any problem mounting externals (thumb drives, cds).  Any ideas what I'm doing wrong?

---

### Post by vanadium on 2007-12-10
The behaviour of having to type a password to access the drive is strange. Either you have access, read only or read-write, or you do not have access. Anyway, "unmask" in your /etc/fstab line should read "umask". Moreover, you may  need to add an option to mount it for you as a user, because currently, only root will have full privileges on the disk (see "man mount", look under "vfat options"). However, perhaps the umask option will be sufficient to give root user, root group and all others (including regular users) to fully access the drive.

---

### Post by dodecaman on 2007-12-10
I've updated my fstab (thanks for that).  Still no luck on the mount.  I notice I'm in a user group of my very own - should I add my user to the "admin" or "root" group to improve this process?

Also - not sure about "man mount."  Any chance you could walk me through that?

I'm afraid the water's a tad deep ...

---

### Post by dodecaman on 2007-12-10
I've tried adding my user to the admin and root groups - it didn't improve things for me.

Any ideas how to set up the drive so that it doesn't require a password to access?  I'm pretty sure that's where my problem lies.

---

### Post by taurus on 2007-12-10
Check your /etc/fstab again because you have an extra n in umask.

```
/dev/sda5 /media/Shared vfat defaults,u**[COLOR="Blue"]n[/COLOR]**mask=000 0 0
```

It should look like this.

```
/dev/sda5   /media/Shared   vfat   defaults,umask=000   0   0
```

---

### Post by dodecaman on 2007-12-10
I fixed the fstab entry ... still no love from my fat32 drive.

I'm pretty sure it has something to do with permissions - whatever is requiring me to enter a password to open the drive is probably also preventing fstab from mounting it.

---

### Post by dodecaman on 2007-12-11
Found a solution that seems to fix my problem:

1) Download .iso for 7.04
2) Reformat sda3 and install Feisty

Everything works as I expect it to now.

Perhaps my laptop just isn't ready for the Gutsy Gibbon

---

