---
title: "Out of Memory?"
date: 2008-11-25
forum: General Help
---

### Post by DManX04 on 2008-11-25
I installed Ubuntu using Wubi, upgraded to Intrepid, and have since installed Google Earth and whatever updates were made available to the OS itself. I have a year old Inspiron 1720, and I allocated to Ubuntu 15 GB of about 35 left on the hard drive.

Suddenly, after about a week, I am getting error messages saying I have no available memory. Firefox can't restore sessions. Open Office won't autosave and crashes when it tries to. I get an error saying that there is no memory in "home/donald/.openoffice/user/backup" and asks me to allocate more memory to that directory. It also freezes when I try and do a regular save as well. The thing is, that file doesn't exist, or at least it doesn't show up in any file viewer or search. Even if it did, how could I add more space to it? At startup it also says that another user is trying to access a session of Office. I don't even know what that means. At first I thought it was just Open Office so I tried to download 3.0, hoping it would fix it, but I got an error saying that there wasn't enough available memory to save the download. Then the firefox restore issue came up after I had to restart the computer when Office crashed.

I have absolutely no idea what to do, but I really need this fixed. Any help is much appreciated.

---

### Post by teddks on 2008-11-25
Run the command ```
df -h
``` and post the results. You probably have too much stuff on your hard drive, and it's full. You can add more space by deleting some of it.

---

### Post by DManX04 on 2008-11-25
I'm not in Ubuntu right now, so I can't run that command yet, but I really don't think it's a disk space issue. I installed Hardy in July/August and have only installed Google Earth. This problem came up just this week after installing Intrepid about a week ago. As I said before, there were about 35 GBs left on the hard drive before I installed Ubuntu, and I allocated 15 GB to the partition when Wubi installed the OS. Unless Ubuntu+Google Earth > 15 GBs then this is not a disk space problem. It also happened in a Kubuntu 8.10 install last week that I just completely removed and replaced with Ubuntu Intrepid.

When I reach a stopping point in my work I'll reboot to Ubuntu and try that command, but that it seems like a different problem, especially since it happened without me having installed anything in a few days.

---

### Post by Toet on 2008-11-25
Remember GoogleEarth uses diskspace to cache.

---

### Post by kanikilu on 2008-11-25
Can you use *gnome-system-monitor*, *top* or *free* to see what your memory usage is? If it's not memory, then I would check the disk space, as suggested earlier...

---

### Post by DManX04 on 2008-12-16
Ok, now that finals are over, I can try and fix this one. Any help would be appreciated since I have no idea what I'm doing

Here's the output of df -h

```
donald@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  112K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.9M 1002M   1% /dev
tmpfs                1004M  104K 1004M   1% /dev/shm
/dev/sda3             137G  117G   20G  86% /host
lrm                  1004M  2.4M 1002M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   40K  984K   4% /tmp
```

---

### Post by teddks on 2008-12-16
> **DManX04 said:**
> Ok, now that finals are over, I can try and fix this one. Any help would be appreciated since I have no idea what I'm doing

Here's the output of df -h

```
donald@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  112K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.9M 1002M   1% /dev
tmpfs                1004M  104K 1004M   1% /dev/shm
/dev/sda3             137G  117G   20G  86% /host
lrm                  1004M  2.4M 1002M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   40K  984K   4% /tmp
```

Your root filesystem is full (as youc an see from the 100%). Just delete some big stuff (or expand root.disk) and free up some disk space, and you'll be fine.

---

### Post by DManX04 on 2008-12-16
Ok. here's my question. All I've installed is Google Earth, Amarok, and maybe Quanta. How is the 15GBs I allocated in the Wubi install already taken up by those? The Ubuntu website says it only requires 4GBs of disk space. Also, why would my bookmarks be gone and the back button not work in FireFox. FF also won't restore the previous session either. I'm not doubting your response, and I appreciate the help, but it just doesn't make a lot of sense that 11GBs would be gone based on what little I've installed.

---

### Post by teddks on 2008-12-16
> **DManX04 said:**
> Ok. here's my question. All I've installed is Google Earth, Amarok, and maybe Quanta. How is the 15GBs I allocated in the Wubi install already taken up by those? The Ubuntu website says it only requires 4GBs of disk space. Also, why would my bookmarks be gone and the back button not work in FireFox. FF also won't restore the previous session either. I'm not doubting your response, and I appreciate the help, but it just doesn't make a lot of sense that 11GBs would be gone based on what little I've installed.

Check out where the biggest files are with Disk Usage Analyzer (baobab), which you can find under Applications>Accessories>Disk Usage Analyzer.

Your entire hierarchy seems to be on that one filesystem, so anything on the system will fill it up. Backups are a common culprit, in my experience, but it's definitely something, and you can find out easily.

---

### Post by DManX04 on 2008-12-16
I doubt this is related, but now I can't even boot Ubuntu. I select it at the boot loader, it goes to the splash screen, and then I get this:

```
Gave up waiting for root device. Common Problems:
-Boot args (cat/proc/cmdline)
   -check rootdelay = (did the system wait long enough?)
   -check root = (did the system wait for the right device?)
- missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/E2A407FDA407D2C9 does not exist. Dropping to shell!
```

It then goes to the shell and just say to type help for a list of commands. All that's on the screen is this:

```
(initramnfs)_
```

Not really sure what to do about this.

---

### Post by teddks on 2008-12-17
> **DManX04 said:**
> I doubt this is related, but now I can't even boot Ubuntu. I select it at the boot loader, it goes to the splash screen, and then I get this:

```
Gave up waiting for root device. Common Problems:
-Boot args (cat/proc/cmdline)
   -check rootdelay = (did the system wait long enough?)
   -check root = (did the system wait for the right device?)
- missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/E2A407FDA407D2C9 does not exist. Dropping to shell!
```

It then goes to the shell and just say to type help for a list of commands. All that's on the screen is this:

```
(initramnfs)_
```

Not really sure what to do about this.

It's dropping to the **init**ial **ram**disk shell, because your root filesystem is full and **bad things happen when that does.**

Boot off of a liveCD and expand the size of the image, and it'll likely fix your problem.

---

### Post by jerome1232 on 2008-12-17
Can you get to a recovery console at least? (Select a recovery option from grub)

Using this command (as root) should at least tell you where all your space is hiding at. Then you can go about deleting files to free some space up.

```
# du -hx --max-depth=1 /
```

---

