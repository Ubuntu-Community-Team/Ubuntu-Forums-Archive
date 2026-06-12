---
title: "Partition suddenly read-only"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by soupface on 2005-05-13
I have a FAT partition that I will be using as a go-between Ubuntu and Windows XP: a space for music, videos, and PDFs accessible by both operating systems. The partition, mounted at /gobe, was working well until a general system crash a few hours ago. The partition is now read-only, not allowing any user (including root, through sudo) to remove or add files, both on the machine itself or over Samba.

What can I do to return my ability to write/delete from the /gobe partition?

The partion was mounted as per [Ubuntu Guide's instructions](http://ubuntuguide.org/#automountfat). I have another FAT partition mounted at /windows to which I can still read from and write to. A copy of my fstab follows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    noatime         0       2
/dev/sda8       /gobe           vfat    umask=000	0       0
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda6       /windows        vfat    umask=000        0       0
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` 
The crash that seems to have caused the problem occurred while copying files to the /gobe partition from a disc through Nautilus. The entire system froze and wouldn't respond for several minutes; I had to hard reset.

I found the following lines in the syslog around the time of the crash:
[list]
[*]Date : 13 May 02:14:13 PM
Process : kernel
Message : FAT: Filesystem panic (dev sda8)
[*]Date : 13 May 02:14:13 PM
Process : kernel
Message : fat_get_cluster: invalid cluster chain (i_pos 0)
[*]Date : 13 May 02:14:13 PM
Process : kernel
Message : File system has been set read-only
[/list]

*edit: clarification

---

### Post by harryc on 2005-05-13
Just a thought here. Boot into windows and see if you can get to this disk. If you can, try running (from a command prompt) "chkdsk c: /f" without the quotes. Since this is your C: drive?? and probably has Windows installed on it, you should receive a report that files are locked and it will ask you if you wish a check performed when you next boot the system. Answer "Y", again, without the quotes and exit the prompt. Then reboot and see if it works. You can't check a disk in Windows NT, 2000, XP that has open files such as the Windows files or the swap file. If it's the D or E drive it should run for you.

---

### Post by soupface on 2005-05-13
That's not a bad idea harryc, except that I have not yet installed Windows on either of the two FAT partitions (and my Windows XP disc isn't with me). Surely, there must be some way of checking the file-system's integrity and permitting writing within Ubuntu.

---

### Post by harryc on 2005-05-13
Ah I see, so this is not really accurate yet - "I have been using a FAT partition as a go-between Ubuntu and Windows XP".  Well, I think what you need to look into is fsck.vfat. A google search should get you going. I've never had to use fsck for vfat. It should be similar to any other file system though.

---

### Post by soupface on 2005-05-13
Sure enough, excecuting dosfsck -a /dev/sda8 a few times and resetting the system has solved the problem: /gobe once again allows writing and deleting. Thanks, harryc.

---

### Post by harryc on 2005-05-13
[QUOTE=soupface]Sure enough, excecuting dosfsck -a /dev/sda8 a few times and resetting the system has solved the problem: /gobe once again allows writing and deleting. Thanks, harryc.[/QUOTE]Excellent!. You're welcome.

---

### Post by Franko30 on 2005-06-11
I had the same problems, encountered them after my laptop crashed because of empty battery (battery panel doesn't work). But I was lost until my brother pointed me to the /var/log directory and then, using less, I found the problem and then here in the forum (not via Google) the solution. :smile: 

So, a BIG THANKS from me, too! dosfsck - r solved my problems and I even had a chance to look at the problem before anything was repaired.  ;-) 

Cheers

Franko30

---

### Post by the.tsr on 2005-08-04
Same problem here, solution worked for me as well, another satisfied customer. :wink:

---

### Post by sumanjay on 2005-11-05
Ditto here... worked beautifully. Now all I need to do is figure out why I have FAT32 partitions anyway?!

---

