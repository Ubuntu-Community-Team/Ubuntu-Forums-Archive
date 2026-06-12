---
title: "Need to clone a Ubuntu 12.04 boot drive"
date: 2013-02-06
forum: Hardware
---

### Post by coolecho on 2013-02-06
I need to clone a 600gb Ubuntu boot drive to an empty 600gb drive and have it bootable exactly like the original.  I started to use Norton ghost (2003) but it didnt recognize the file system and gave warning need to run chkdsk, and the option to continue anyway. I aborted it. I Downloaded clonezilla and may try that. If a image cloningtool needs initialization of a empty disk can it be initialized fat32 even though source is ext4?

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by oldfred on 2013-02-06
Are you planning on keeping both drives connected? If so you will have boot issues as a true clone has duplicate UUIDs and depending on timing by BIOS you may boot one or the other.
If just a clone to keep off line then it will work, but as ahallubuntu suggests it will get out of date quickly.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

       Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

    Files that may need update on image copy
 fstab, reinstall grub and grub's reinstall location. Or change UUIDs
If different computer:
/etc/hostname and /etc/hosts,

---

### Post by coolecho on 2013-02-06
We are trying Image for windows (terabyte). It is a drive that will be cloned for use in another identical system. I'm hoping image will work. Thanks for your help.

---

### Post by oldfred on 2013-02-06
You cannot legally copy Windows from one system to another.

And  generally should use Linux tools for Linux if copying a Linux system.

---

### Post by coolecho on 2013-02-07
I used image for windows (terabyte). Thanks.

---

