---
title: "Partition Help Please"
date: 2008-11-01
forum: General Help
---

### Post by invalidusername on 2008-11-01
Hi everyone, I'm very new to Ubuntu and could really use some help. I've been using it for about 1 day now and just can't figure out how to setup a data only drive.

I have two hard drives. HDD 0 is 250 gigs and consists of my os install. Everything is fine with that drive.

HDD 1 is a 500 gig drive that I want to be used for data storage only. So I create the partition in ext3 format and then restart the computer but when I try to copy my data files back to the drive it tells me I "don't have permissions to create it in the destination". Why? Did I do something wrong? I've never had a problem creating a data only drive under Windows so I'm just not understanding what's going on.

EDITED: Added exact error message.

---

### Post by Earl_Maroon on 2008-11-01
I think you might be able to use this code in a terminal:
```
sudo chown [your user name] [path to drive]
```
This will change the ownership of the partition to your user account. Once you do this you should be able to change permissions from within Nautilus by right clicking and going to properties (or whatever it is - I'm not on my Ubuntu box right now). I can't check at the moment, but that might not even be necessary.

---

### Post by invalidusername on 2008-11-01
Sorry, but like I said this is my first day using Ubuntu. What is a terminal?

---

### Post by daniel of sarnia on 2008-11-01
Under Applications in accessories you will see a program called "Terminal" all it is, is a way to interact with your operating system via entering text commands

---

### Post by fornix on 2008-11-01
How have you mounted your drive. Can you paste the output of 
```
$ cat /etc/fstab
```

---

### Post by invalidusername on 2008-11-01
> **fornix said:**
> How have you mounted your drive. Can you paste the output of 
```
$ cat /etc/fstab
```

The partition editor says it is mounted. But this is the response when I type the command into the terminal.

> bash: $: command not found
danderson@Windtamer:~$ 

---

### Post by invalidusername on 2008-11-01
> **Earl_Maroon said:**
> I think you might be able to use this code in a terminal:
```
sudo chown [your user name] [path to drive]
```
This will change the ownership of the partition to your user account. Once you do this you should be able to change permissions from within Nautilus by right clicking and going to properties (or whatever it is - I'm not on my Ubuntu box right now). I can't check at the moment, but that might not even be necessary.

I get no response when I try this command.

---

### Post by fornix on 2008-11-01
You can familiarize yourself with ubuntu with this
[https://help.ubuntu.com/]("https://help.ubuntu.com/")
Read the desktop documentation. Currently its for 8.04 but it's almost the same for 8.10.

---

### Post by thestig_992 on 2008-11-01
> **invalidusername said:**
> The partition editor says it is mounted. But this is the response when I type the command into the terminal.

Maybe you made a mistake in spelling cat, or put the $ sign in?
What you should write is
```
cat /etc/fstab
```
cat is a program to read the file, and /etc/fstab is the locatio of a file with you mounted hard drives among other things.

I think it might be better type another command, ```
df
```, and paste the results here.

---

### Post by invalidusername on 2008-11-01
> **thestig_992 said:**
> Maybe you made a mistake in spelling cat, or put the $ sign in?
What you should write is
```
cat /etc/fstab
```
cat is a program to read the file, and /etc/fstab is the locatio of a file with you mounted hard drives among other things.

I think it might be better type another command, ```
df
```, and paste the results here.

These are the results of those commands.

> danderson@Windtamer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3590831e-7ba8-463b-9985-d1213c278fea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=62101522-9efa-4e29-8e69-48e2d7073136 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

> danderson@Windtamer:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            234394748 200425212  22062964  91% /
tmpfs                  1036428         0   1036428   0% /lib/init/rw
varrun                 1036428       208   1036220   1% /var/run
varlock                1036428         0   1036428   0% /var/lock
udev                   1036428      2796   1033632   1% /dev
tmpfs                  1036428       428   1036000   1% /dev/shm
lrm                    1036428      2000   1034428   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdc1              7880508   1023760   6856748  13% /media/disk
danderson@Windtamer:~$ 

---

### Post by invalidusername on 2008-11-01
> **fornix said:**
> You can familiarize yourself with ubuntu with this
[https://help.ubuntu.com/]("https://help.ubuntu.com/")
Read the desktop documentation. Currently its for 8.04 but it's almost the same for 8.10.

Thank you, I've been looking at that and it has helped a lot. :)

---

### Post by invalidusername on 2008-11-01
> **Earl_Maroon said:**
> I think you might be able to use this code in a terminal:
```
sudo chown [your user name] [path to drive]
```
This will change the ownership of the partition to your user account. Once you do this you should be able to change permissions from within Nautilus by right clicking and going to properties (or whatever it is - I'm not on my Ubuntu box right now). I can't check at the moment, but that might not even be necessary.

Hah, this worked! I think I entered it wrong the first time. Thank you so much for the help.

---

