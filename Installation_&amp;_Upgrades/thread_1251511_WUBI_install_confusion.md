---
title: "WUBI install confusion"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by Nibblers on 2009-08-27
Hi everyone

I used WUBI to install ubuntu 9.04 within the Windows environment, mainly because I wanted a dual boot option and my notebook CDROM is not working right now.

As this is my first time with ubuntu so I assumed the install went ok. I had 2 partitions (C:/D) I configured WUBI to install on D: (35Gb free) with a default install. Re-booted into ubuntu from the dual boot option and the auto install went through the configuration steps but then stops with a "partition too small" error message.

The free space on the partition is obviously more than is required so how do I solve the partition size problem? Or should I be starting ubuntu within the Windows environment rather than using the dual boot option - if this is the case how do you start ubuntu within Windows?

Thanks in advance for any help with this.

footnote
- I can start the demo version via the dual boot and everything works fine however I can't save any session changes

---

### Post by raymondh on 2009-08-27
> **Nibblers said:**
> 

footnote
- I can start the demo version via the dual boot and everything works fine however I can't save any session changes

In demo mode, can you access a terminal (applications > accessories) and type
```

df -h
```

kindly post back its' output.

---

### Post by garvinrick4 on 2009-08-27
Install's in folder in windows like an app.  install in same partition as boot.
C:    Just pick the size at least 8 or so  I use 25. 

It uses the DOS  GRUB    cannot make mistake with WUBI  it will configure everything
for you,  you just pick  the size  a  password  and install.

---

### Post by Nibblers on 2009-08-28
raymondhenson - I'll do that 

garvinrick4 thanks, could a clue here! I installed on the D: partition rather than C:

If this is the answer then how do you move the ubuntu install to C: - can it be done? I realise you can move the install folders easily but I suspect an edit of the boot.ini would be required as well. Is this all or would it be just as simple do a re-install?

Thanks for your help

---

### Post by ottosykora on 2009-08-28
I made the experience that the wubi 9.04 for ubuntu 9.04 must have some big bugs in it.
Tried about 15 times and did not manage to make an installation.

Sometimes I had similar error like you, then I discovered that instead crating disk files, the wubi did produce a log file of the same size either in TEMP folder or under documents and settings. The rest of the disk it created in the correct position was then too small.

On next occassion it produced correct disk files, but then stopped in the middle of the installation saying it creates swap space in drive 1 (??)

On other occassions mostly the grub4dos installation was foulty, either it remained fixed set to drive C: and was unable to find kernel even I tried to enter the command manually.

I doubt that this works as supposed, spent 3 nights on it without any substantial results.

---

### Post by garvinrick4 on 2009-08-28
WUBI is just a folder like any other folder inside Windows. I have never had a problem
loading or uninstalling. Just put in same partition as Your Windows download Wubi 9.04
select size, give password and install. Will give dual boot option on booting process and boot from the original Dos GRUB. It works fine, it is just another app to Windows. 
I believe I selected to download a 1.2 meg file of WUBI to my desktop and it takes about
12 minutes to finish 9.04 installation. Have done it multiple times to upgrade to 9.10.

---

### Post by Nibblers on 2009-09-03
Hi

Fearful of breaking my XP install (even for a short time) I would love to find a simplistic method of solving the problem. I am sure there must be one! Here is the result from df -h 

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 565M  2.4M  562M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 565M  2.4M  562M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 565M     0  565M   0% /lib/init/rw
varrun                565M  104K  565M   1% /var/run
varlock               565M  4.0K  565M   1% /var/lock
udev                  565M  148K  565M   1% /dev
tmpfs                 565M   76K  565M   1% /dev/shm
rootfs                565M  197M  368M  35% /
/dev/sda5              43G   12G   32G  27% /isodevice
/dev/loop0            699M  699M     0 100% /cdrom
/dev/loop1            676M  676M     0 100% /rofs
tmpfs                 565M   14M  552M   3% /tmp
ubuntu@ubuntu:~$ 

```

---

### Post by ottosykora on 2009-09-03
> **garvinrick4 said:**
> WUBI is just a folder like any other folder inside Windows. I have never had a problem
loading or uninstalling. Just put in same partition as Your Windows download Wubi 9.04
select size, give password and install. Will give dual boot option on booting process and boot from the original Dos GRUB. It works fine, it is just another app to Windows. 
I believe I selected to download a 1.2 meg file of WUBI to my desktop and it takes about
12 minutes to finish 9.04 installation. Have done it multiple times to upgrade to 9.10.

and here the problem: the grub4dos seems to be not able to properly point to a place on second physical drive. Just matter of luck if it finds the place,paritcularly if there are many logocal drives on the system.

and ubuntu 9x , I have after about 15 attempts on different machines not be able to install, since it is trying to create swap file and this seems to go for ever...

---

