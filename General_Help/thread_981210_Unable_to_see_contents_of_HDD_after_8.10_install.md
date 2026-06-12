---
title: "Unable to see contents of HDD after 8.10 install"
date: 2008-11-13
forum: General Help
---

### Post by pigboy on 2008-11-13
Hello.

Ever since I installed 8.10 I have been unable to see the contents of my other hard drive. Ubuntu is installed on Primary on IDE1 and my other drive is Primary on IDE2. 

Used to run WinXP PRO on IDE1 Primary, but ran into some problems with that a while back and was always wanting to just use this system as a Linux box anyway, so whipped it and installed Ibenex. 

The other drive, maybe it's locked by Windows or something? Maybe I have to reset it somehow to no longer be in use? I've read some stuff out their leading me to believe that is the problem. How do I do that though?

The drive is mountable, I tried recovering files from it, and got a lot of my photos back, but there's music on there to that I want and other stuff... Would prefer to just have the drive the way it was, with all files intact.

Was an NTFS file system, converted with gparted to ext3 to see if that would do it, nope. Drive did not always mount ok, converted it from NTFS and it now mounts but just doesn't show files on it at all.

Any help?

---

### Post by ohzopants on 2008-11-13
I don't think you can change the filesystem of a drive and keep data.
I'm pretty sure that using gparted to go from NTFS->ext3 was equivalent to formatting it.

---

### Post by ohzopants on 2008-11-13
Once you've mounted it run:
```

df -h

```

The output from that command might be helpful.

---

### Post by pigboy on 2008-11-13
> **ohzopants said:**
> I don't think you can change the filesystem of a drive and keep data.
I'm pretty sure that using gparted to go from NTFS->ext3 was equivalent to formatting it.

I supposed that's possible, however I know that changing the file system from Fat32 to NTFS for example will cause no data loss. I am not sure if going to ext file systems from NTFS would do so or not...

The files I was able to recover, were recovered post file system change.

I recovered them using magicrescue mind you.

---

### Post by pigboy on 2008-11-13
> **ohzopants said:**
> Once you've mounted it run:
```

df -h

```

The output from that command might be helpful.

Ran that command just now. Displays my file systems in terminal, but only a summary of them. Shows as pasted here:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              90G  8.9G   76G  11% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  208K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  476K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             113G  188M  107G   1% /media/120Gig


"/dev/sdb1" is the file system I am having issues with. 120Gig is the volume label I gave it a while back.

---

