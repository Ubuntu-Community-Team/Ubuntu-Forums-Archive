---
title: "SMBFS not mounted at system start"
date: 2008-11-07
forum: General Help
---

### Post by danduq on 2008-11-07
I've upgraded to Intrepid, and suddenly my SMBFS mounts aren't being mounted when I boot up. Running a "mount -a" successfully mounts the shares though.

Hunting through syslog I found umask errors (no longer supported) so have removed them from my fstab. Now when I run a "mount -a" I get a message in syslog that I'm struggling to find any info on (although it still mounts successfully);

```
kernel: [ 4061.676243]  CIFS VFS: Send error in SETFSUnixInfo = -5
kernel: [ 4061.676260]  CIFS VFS: Negotiating Unix capabilities with the server failed.  Consider mounting with the Unix Extensions
kernel: [ 4061.676264] disabled, if problems are found, by specifying the nounix mount option.
```

Here's an example of my fstab;
```
//server/share /mnt/dir smbfs auto,credentials=/root/.credentials,uid=9931,gid=8987,rw,user 0 0

```

Any help greatly appreciated!

---

### Post by pholden on 2008-11-07
Can't really help, but myself and others are having the same problem since upgrading: [After Ibex upgrade external drives not mounting]("http://ubuntuforums.org/showthread.php?t=966824") :neutral:

---

### Post by mccartyj on 2008-11-19
Ditto here...

---

### Post by Iowan on 2008-11-19
A couple of things - SMBFS has been replaced by CIFS. Much, much info on mounting CIFS [here]("http://ubuntuforums.org/showthread.php?t=288534").  There is info on the **nounix** option for fstab mounts in the link.  I've seen **nounix** mentioned in other threads, but my search only turned up the one.

---

### Post by danduq on 2008-12-22
As mentioned by Geirha in [http://ubuntuforums.org/showthread.php?t=966824](http://ubuntuforums.org/showthread.php?t=966824)...

Known bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828)

---

### Post by danduq on 2009-01-14
Resolved by setting up CIFS properly.

---

### Post by Roasted on 2009-01-14
> **Iowan said:**
> A couple of things - SMBFS has been replaced by CIFS. Much, much info on mounting CIFS [here]("http://ubuntuforums.org/showthread.php?t=288534").  There is info on the **nounix** option for fstab mounts in the link.  I've seen **nounix** mentioned in other threads, but my search only turned up the one.

Uh, what?

Isn't SMBFS the same as "Samba" basically?

I have a Samba server set up with 4 hard drives in my computer. They mount automatically every time I boot up. I used "blkid" to find the full name of each drive and added that to my fstab file, though. But other than that I've had zero problems with Samba in Intrepid. I did a fresh install. I never upgrade OS's.

---

### Post by uvdevnull on 2009-01-15
> **danduq said:**
> Resolved by setting up CIFS properly.

Perhaps you could post what you did wrong originally and how you corrected it?  For the benefit of those who will surely make the same mistake in the future... :)

---

### Post by HermanAB on 2009-01-15
The trouble is that smbfs is deprecated and unmaintained.  You have to use cifs.  Smbfs will gradually become worse and will eventually be completely unusable.  As found above, cifs works.

Cheers,

Herman

---

### Post by Iowan on 2009-01-15
> **Roasted said:**
> Uh, what?
Isn't SMBFS the same as "Samba" basically?
I'm not exactly sure how to answer...Samba  is not a file system - Samba *used* SMBFS , now *uses* CIFS. Linux  *used* EXT, now *uses* EXT2 or EXT3, and may soon use EXT4.  **man mount** lists several other file systems that may be mounted.

---

### Post by Roasted on 2009-01-15
> **Iowan said:**
> I'm not exactly sure how to answer...Samba  is not a file system - Samba *used* SMBFS , now *uses* CIFS. Linux  *used* EXT, now *uses* EXT2 or EXT3, and may soon use EXT4.  **man mount** lists several other file systems that may be mounted.

Oh, I think I was confused. I thought that Samba required SMBFS in order to mount shares, but could also use CIFS. My question was, with the way I was mounting the drives, which was I using... SMBFS or CIFS? But I guess either way I wasn't using either one because... the mount command is a linux command. That's how I mounted the drives before. Now, I mount them automatically in fstab... 

So I guess the moral of the story is, SMBFS and CIFS have nothing to do with the linux "mount" command or "fstab" with how I mount the drives... but they're actual file systems that are used on the designated shares in question.

That's interesting, because on my samba drive it's formatted with ext3, yet I guess it still uses a file system (CIFS, perhaps?)

---

