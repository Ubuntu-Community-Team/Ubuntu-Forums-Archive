---
title: "Restoring system"
date: 2008-10-06
forum: General Help
---

### Post by lcruz007 on 2008-10-06
Hello!
Is there a way to restore the system to a previous date like windows?

I am having problems with Ubuntu, and I don't know why it got crazy...


Thanks in advance

---

### Post by presence1960 on 2008-10-06
> **lcruz007 said:**
> Hello!
Is there a way to restore the system to a previous date like windows?

I am having problems with Ubuntu, and I don't know why it got crazy...


Thanks in advance
This won't help you now, but for future reference install sysres from the repositories. You will then be able to create restore points and restore these if need be.

---

### Post by hyper_ch on 2008-10-06
no, there is no such thing (by default) - but what are your problems that you're experiencing?

---

### Post by lcruz007 on 2008-10-06
> **hyper_ch said:**
> no, there is no such thing (by default) - but what are your problems that you're experiencing?

Hmm well, there are several things not working properly...

1)I can't copy files because I don't have enough memory (But I have 20GB available)
2)Firefox is not working, and it doesn't let me download anything else to reinstall it.
3)I cannot install tar.gz files, I don't know if I'm doing something wrong but after extracting them I try installing them with make and make install but it prints some errors...
4)I cannot install some updates because I get some erros with dpkg.

I have other problems but don't remember right now, is there anything I can do to solve these issues I mentioned?

---

### Post by lcruz007 on 2008-10-06
> **presence1960 said:**
> This won't help you now, but for future reference install sysres from the repositories. You will then be able to create restore points and restore these if need be.

How can I do I restore point? 
Is it possible to re-install Ubuntu with the CD? Or I need to format the partition...?

---

### Post by lcruz007 on 2008-10-06
Sorry for the multiposts...

---

### Post by hyper_ch on 2008-10-06
> **lcruz007 said:**
> 1)I can't copy files because I don't have enough memory (But I have 20GB available)
what does 
[code]
df -l
[code]
return?

> **lcruz007 said:**
> 2)Firefox is not working, and it doesn't let me download anything else to reinstall it.
very likely related to (1)

> **lcruz007 said:**
> 3)I cannot install tar.gz files, I don't know if I'm doing something wrong but after extracting them I try installing them with make and make install but it prints some errors...
a new install won't help here... what are you trying to install?

> **lcruz007 said:**
> 4)I cannot install some updates because I get some erros with dpkg.
and those are?

> **lcruz007 said:**
> is there anything I can do to solve these issues I mentioned?
post them individually (except for 1 & 2 which are very likely related)

---

### Post by lcruz007 on 2008-10-06
Output:
```
luis@luis-laptop:~$ df -l
Filesystem           1K-blocks Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       3681640   3496204         0 100% /
varrun                 1033204       108   1033096   1% /var/run
varlock                1033204         0   1033204   0% /var/lock
udev                   1033204        52   1033152   1% /dev
devshm                 1033204        12   1033192   1% /dev/shm
lrm                    1033204     39760    993444   4% /lib/modules/2.6.24-19-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon       3681640   3496204         0 100% /home/luis/.gvfs
luis@luis-laptop:~$ 
```

OK these are the problems more detailed....

1) Well, the forward and back arrows of firefox aren't working, and I cannot download anything because the download manager of firefox won't appear. 
2) Ubuntu is asking me to update the system, but I get this problem when I try to do so:
[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
I think dpkg is a software that helps to manage .deb installations.


By the way, I was trying to install limewire, but for some reasons after extracting the tar.gz file the make command would not work...

---

### Post by hyper_ch on 2008-10-06
well, you see how you don't have any space levt on the root partition?

and for problem 2: did you read what it says there?

Why install limewire manually when you have frostwire in the repos?

---

### Post by lcruz007 on 2008-10-06
> **hyper_ch said:**
> well, you see how you don't have any space levt on the root partition?

and for problem 2: did you read what it says there?

Why install limewire manually when you have frostwire in the repos?

Hmm that's extrange, I have 20GB available in the partition I have installed Ubuntu. What can I do here...?

About the dpkg? I just get the output showing the files installed and the ones not installed correctly.


I see... Well, I remembered... I was installing limewire with the .deb files... The tar.gz that I tried to install were some OpenGL files to be able to play chess in 3D MODE. 

I should uninstall these files...

---

### Post by hyper_ch on 2008-10-06
what does it say in dpbk?

what does

```

sudo fdisk -l

```

return?

---

### Post by lcruz007 on 2008-10-06
> **hyper_ch said:**
> what does it say in dpbk?

what does

```

sudo fdisk -l

```

return?

Well, it seems that somehow I installed the missing .deb updates..
I still have to fix the firefox problem and the space problem... 

I have Ubuntu in a 25GB partition, which 20GB are free on the partiton... 

Outcome:
```

luis@luis-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc62bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       11407    90083324    7  HPFS/NTFS
/dev/sda3           11407       14594    25597952    7  HPFS/NTFS
luis@luis-laptop:~$ 
```

---

### Post by hyper_ch on 2008-10-06
you still don't read what the error message says and that partition is no 25 GB in size...

---

### Post by lcruz007 on 2008-10-06
> **hyper_ch said:**
> you still don't read what the error message says and that partition is no 25 GB in size...

I did the partition of 25GB on windows vista, and then  installed Ubuntu. I don't know why I can't see the partition I am using on Ubuntu, however, if I check on Windows, there are 20GB available of 25GB.

---

### Post by mssever on 2008-10-06
> **presence1960 said:**
> This won't help you now, but for future reference install sysres from the repositories. You will then be able to create restore points and restore these if need be.
As far as I know, sysres isn't yet in the repositories. You have to get it from [https://launchpad.net/sysres](https://launchpad.net/sysres) . Its forum is [http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php) . I'm one of the developers of sysres.

---

### Post by presence1960 on 2008-10-07
> **mssever said:**
> As far as I know, sysres isn't yet in the repositories. You have to get it from [https://launchpad.net/sysres](https://launchpad.net/sysres) . Its forum is [http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php) . I'm one of the developers of sysres.
Thanks msserver, I thought I got it from the repositories, but obviously I was mistaken. nevertheless it is available for the orignator of this thread, but it won't help with the current problem. Like the rest of us you live and learn.

---

### Post by Nasaki on 2008-10-07
This may not be that applicable to you,

But my favorite way of backing up my Ubuntu box is to Tar the entire drive (excluding some directories, Ex video). Then when Ubuntu starts acting funky, I can untar it on top of its self. 

This probably isn't the best way to do it, but I find it humerous to watch it overwrite the tar program as its running :).

---

### Post by jerome1232 on 2008-10-07
Well your space is definitly full, lets take a look at a few things. If you run the following command to see what is taking up all the space. Also df -h list it in a more readable format (I dont' want to convert bits/sectors to figure out how big that partition is.

```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by lcruz007 on 2008-10-11
Well. I re-installed Ubuntu with its own partition, didn't do it from windows this time. It seems it is working better now. :)
And made a restore point using sysres.

Thank you for your helpful replies!!

---

