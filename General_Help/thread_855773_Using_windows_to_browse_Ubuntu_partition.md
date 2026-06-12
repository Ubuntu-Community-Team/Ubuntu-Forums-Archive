---
title: "Using windows to browse Ubuntu partition"
date: 2008-07-10
forum: General Help
---

### Post by itsjareds on 2008-07-10
I downloaded some software for Windows that let me browse my Ubuntu files as a separate drive (L:) in Windows Explorer. 

It works fine, but I don't know where my /home/ directory is at. Does anyone else have experience with this and know where to find it?

These are my directories:

> 
/DOS
/MFGSTAT
/minint
/preboot
/RECOVERY
/swwork
/TPTOOLS


I did a search for "home", and it returned no results.

---

### Post by iaculallad on 2008-07-10
I don't know what utility you're using. I had once used [Explore2FS]("http://www.chrysocome.net/explore2fs") and I can directly browse Ubuntu's filesystem hierarchy (/home directory included) using that application.

---

### Post by bodhi.zazen on 2008-07-10
E:\home

You may need to use the correct letter here.

---

### Post by un_dave on 2008-07-10
The root directory for a Ubuntu install should look something like this:

```
dave@hades:~$ ls /
bin    data  **home        **initrd.img.old  media  proc  src  tmp  vmlinuz
boot   dev   initrd      lib             mnt    root  srv  usr  vmlinuz.old
cdrom  etc   initrd.img  lost+found      opt    sbin  sys  var
```

Note the home directory in plain site!

Is it possible you've mounted the wrong drive or partition in Windows?

---

### Post by itsjareds on 2008-07-10
It let me give it any drive letter.

This is the program I am using: [Ext2 IFS For Windows]("http://www.fs-driver.org/index.html")

I think I'll just use the link you gave.

---

### Post by itsjareds on 2008-07-10
> Is it possible you've mounted the wrong drive or partition in Windows?

It definitely is possible because I am an idiot. 

Which drive should I mount? (and what does mount mean..?)


iaculallad, I used the program you gave me, and no files or folders came up. It was completely blank..

---

### Post by un_dave on 2008-07-10
What options does it give you for drives/partitions to mount?

Take a screenshot if you like, and post it here.

---

### Post by itsjareds on 2008-07-10
> **un_dave said:**
> What options does it give you for drives/partitions to mount?

It gives what I think is all the drives from E: through Z:

---

### Post by un_dave on 2008-07-10
If it's quick to select and browse a drive, I'd just quickly flick through each of the drive letters, and try them all until you see a directory structure similar to the one I posted earlier. 

If you still can't find it, I'd try a different application, maybe the one iaculallad recommends, Explore2FS. With any luck it should narrow down the drives available to just a handful.

---

### Post by itsjareds on 2008-07-10
The files and directories are all the same no matter what drive letter I give it.

Explore2FS didn't show any folders or files when I ran it :\


Edit: I have a feeling that it is just showing some random Windows files, because I see a bunch of folders/files with names like "x86 Microsoft.Windows.Common-Controls"

---

### Post by un_dave on 2008-07-10
Weird. I'm not sure where your Ubuntu partition is hiding then... 

Does Ubuntu still boot on the pc? Is the partition definitely still there?

---

### Post by itsjareds on 2008-07-10
I've tried 3 different programs, and all of them aren't showing my linux partition. So it's probably something wrong with my computer, but i don't know what.

---

### Post by itsjareds on 2008-07-10
> **un_dave said:**
> Does Ubuntu still boot on the pc? Is the partition definitely still there?

Yes

---

### Post by shp on 2008-07-10
The /home directory could be on a different drive?

---

### Post by itsjareds on 2008-07-10
I think it's on the C drive, which is the same one Windows uses. Is that even possible?

The applications only let me do drives E-Z

---

### Post by shp on 2008-07-10
C: is the drive letter windows assigns to the partition. You could have a separate drive or partition that is mounted at /home/.

what does df output in ubuntu?

---

### Post by itsjareds on 2008-07-10
u mean if i type > df in a terminal?

---

### Post by shp on 2008-07-10
yeah

---

### Post by itsjareds on 2008-07-10
df:
> 
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13563852   2171684  10708576  17% /
varrun                  512860       108    512752   1% /var/run
varlock                 512860         0    512860   0% /var/lock
udev                    512860        40    512820   1% /dev
devshm                  512860        12    512848   1% /dev/shm
lrm                     512860     38684    474176   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      13563852   2171684  10708576  17% /home/jared/.gvfs


Hehe, I noticed that for some reason it mounted my /media folder, which I didn't do.. how can I change the location it mounts?

---

### Post by un_dave on 2008-07-10
```
Filesystem 1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
```

Ah, have you installed Ubuntu using one of those new-fangled methods where it installs within the current windows partitions, so that it doesn't have to create a new one?

---

### Post by shp on 2008-07-10
yeah u dont have separate partition but i think i misunderstood ur question you dont appear to be mounting the right partition or drive and i dont mean changing the drive letter. 

Try this go into control panel > administration tools > data sources > storage > disk management

It should show u a list of the partitions you have mounted in windows.

Check the one the matches up with the drive letter u assigned the linux drive in windows and check that it is a ext2/3 format and that u have not accidentally mounted a windows drive.

---

### Post by shp on 2008-07-10
> **un_dave said:**
> ```
Filesystem 1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
```

Ah, have you installed Ubuntu using one of those new-fangled methods where it installs within the current windows partitions, so that it doesn't have to create a new one?

lol i was wondering what that was

---

### Post by itsjareds on 2008-07-10
> **un_dave said:**
> ```
Filesystem 1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
```

Ah, have you installed Ubuntu using one of those new-fangled methods where it installs within the current windows partitions, so that it doesn't have to create a new one?

Yeah. I thought I had to completely remove Windows to use Ubuntu, I didn't know I could dual-boot instead. Works for me.. so it's fine.

---

### Post by itsjareds on 2008-07-10
> **shp said:**
> 
Check the one the matches up with the drive letter u assigned the linux drive in windows and check that it is a ext2/3 format and that u have not accidentally mounted a windows drive.

I didn't mount it, I used a program that mounted it for me. It mounted the /media file on my Linux partition instead of the root directory

---

### Post by shp on 2008-07-10
do u mean it mounted just the stuff inside /media/? 

and read what itsjareds is saying you ubuntu drive is a file on the windows drive. You would need some program that can read the file as a virtual hard drive. I don't think that program would do that.

---

### Post by un_dave on 2008-07-10
I assume you installed Ubuntu on windows, using Wubi. 
[http://wubi-installer.org/](http://wubi-installer.org/)

From [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> How can I access the Wubi files from Windows?

There are a few Windows applications that can mount ext2-based file systems. See for instance:

    *

      [WWW] [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    *

      [WWW] [http://www.fs-driver.org/](http://www.fs-driver.org/)

The relevant Wubi files you need to access are located under C:\ubuntu\disks\ 

---

### Post by itsjareds on 2008-07-10
Ext2FS doesn't work for me, and FS-Driver for some reason just mounts /media.

I just remembered, I can save stuff from linux into my windows partition. If i really needed to read stuff on windows from linux.

---

### Post by un_dave on 2008-07-11
I think this should help you:
[http://ubuntuforums.org/showthread.php?t=436923](http://ubuntuforums.org/showthread.php?t=436923)

---

