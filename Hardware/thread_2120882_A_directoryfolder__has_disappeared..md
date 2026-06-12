---
title: "A directory/folder  has disappeared."
date: 2013-02-27
forum: Hardware
---

### Post by Silvernail on 2013-02-27
Ubuntu 12.04
Gnome3


A very large and very important 'directory' has disappeared from my hard drive. This directory had between 50 or 60 sub-directories and at least a 1000 files, pdfs, and images. I became aware of this very shortly after using file manager to transfer some images from a sans disc in my card reader to a subdirectory in the directory that disappeared.

I went immediately to these forums to read about recovery. Saw lots of post on recovering file but very little on recovering directories. 

I took this image about 5 minutes after this happened.
```

dave@Dafydd:~$ cat /var/log/syslog | grep sda1
Feb 27 15:51:30 Dafydd kernel: [    1.367947]  sda: sda1 sda2 < sda5 >
Feb 27 15:51:30 Dafydd kernel: [    2.062512] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Feb 27 15:51:30 Dafydd kernel: [   19.349960] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
dave@Dafydd:~$ 

```

I took this after an hour and a reboot. Probably means neither is relevant.
```

dave@Dafydd:/var/log$  dmesg | grep sda1
[    1.367947]  sda: sda1 sda2 < sda5 >
[    2.062512] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.349960] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
dave@Dafydd:/var/log$ 

```

Back in the 8 bit era, (Motorola 6809 and Microware OS-9), we had a raw disk editor that would let us open a disk in raw mode and edit/search the data of the file allocation table to find the location of files or directories.  DOES SUCH AN ANIMAL EXITS FOR LINUX?

If someone can put me on some recovery applications, I will really appreciate it. This directory was the location of all the code/images/stuff for the club website I administer.

Thanks
Dave

---

### Post by Silvernail on 2013-03-02
Found. 
Something had moved the entire directory to another directory.

---

### Post by papibe on 2013-03-02
Hi Silvernail.

Glad you figured it out.

Just in case, here you can find several data recovery tools options: [Data Recovery]("https://help.ubuntu.com/community/DataRecovery").

Regards.

---

### Post by Silvernail on 2013-03-04
Thank you for posting the 'data recovery' link. > This guides applies to Ubuntu 7.04, 7.10 and 8.04." How effective/useful is it for 12.04 and above when it comes to specifics. I know data recovery is pretty much the same across all flavors of OS's.

---

