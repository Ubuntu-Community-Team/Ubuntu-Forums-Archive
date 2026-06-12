---
title: "'Moving /home dir to new partition' ended up in disaster"
date: 2008-09-03
forum: General Help
---

### Post by abcuser on 2008-09-03
Hi,
on Ubuntu 8.04 with Gparted I have created (resized and created) new partition /dev/sda3 and /dev/sda4. By default Ubuntu is installed on /dev/sda1 partition. (see picture bellow but ignore the /dev/**h**da1 it is /dev/sda1 - Gparted does not recognizes disk type correctly).
[img]http://shrani.si/f/2c/L6/3YwfmT9E/1.jpg[/img]

Then I followed the following how-to (just changed /dev/hda5 to /dev/sda4):
[http://microwavebiscuit.wordpress.com/2007/11/12/move-home-to-it%E2%80%99s-own-partition/](http://microwavebiscuit.wordpress.com/2007/11/12/move-home-to-it%E2%80%99s-own-partition/)

Every step went OK - I have double checked it!
But after reboot error appeared:
[img]http://shrani.si/f/2C/eC/1K62wCbf/2.jpg[/img]
I pressed Ok. And another error:
[img]http://shrani.si/f/1H/13K/3TiuRmqp/3.jpg[/img]

It looks like Ubuntu can't recognize /home directory and files inside. Or it looks like some permissions are not correctly set.

So I booted into recovery mode and checked disk partition by 'df' command:
[img]http://shrani.si/f/7/10w/2r29GHSh/5.jpg[/img]

Then list / dir: "ls /"
[img]http://shrani.si/f/30/iZ/3QyedBJp/6.jpg[/img]

Then list /home dir: "ls /home"
[img]http://shrani.si/f/6/6T/3yzycTxE/7.jpg[/img]

Then opened /etc/fstab file:
[img]http://shrani.si/f/z/66/4puiAFiL/4.jpg[/img]

and it looks like in instructions above.

Any idea what is wrong and how to fix the problem?
Thanks,
Abcuser

---

### Post by kpatz on 2008-09-03
Your home directories need to be owned by the users that they belong to.  Since you copied them into a new partition (and presumably didn't use the -p option on the cp command), the directories are now owned by root.  

Do you still have the original /home intact (renamed directory)?  If you do, you can recopy using **sudo cp -pR /oldhome/* /home**  to copy everything again and retain ownership, permissions, etc.  (replace oldhome with whatever you renamed the original home directory to).

If you don't have the original /home directory still, you'll have to chown the new directories. I can't make out the home directory names in your screenshot, but for example, let's say you have /home/harold and /home/nancy.  To fix the ownerships, you would issue these commands:

```

sudo chown -R harold:harold /home/harold
sudo chown -R nancy:nancy /home/nancy

```

Substitute the names of your directories and users for "harold" and "nancy" in my example, of course.

---

### Post by abcuser on 2008-09-03
Hi,
I still have /old_home and I enter run level 1:
```
sudo init 1
```
```
sudo cp -pR /oldhome/* /home 
```(this command put some errors but almost all was ok)
Then I reboot Ubuntu and I can log in and my home dir doesn't have any errors.

But user db2inst1 has settings to run IBM DB2 database and in his home dir start up are programs and trying to start db2 database I get error:
```

myuser@myuser-ubuntu804:/home/db2inst1$ db2start
SQL1042C  An unexpected system error occurred.  SQLSTATE=58004
myuser@myuser-ubuntu804:/home/db2inst1$ db2 ? SQL1042C


SQL1042C  An unexpected system error occurred.

Explanation: 

A system error occurred. Some possible reasons for this error are: 
*  The database manager is not installed correctly or the environment is
   not set up correctly.

```

So it looks like cp command didn't copy all the thinks. By the way tutorial suggested that I shouldn't use 'cp' command but the following command:
```

sudo find . -depth -print0 | sudo cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome/ 
```

Is there any way I could restore my /old_home to /home without errors?

Thanks,
Abcuser

---

### Post by kpatz on 2008-09-03
What were the errors you got when you did the cp -pR?

Another option for your db2 directory is tar:

```

cd /old_home
tar cvf db2inst1.tar db2inst1
cd /home
tar xvf /old_home/db2inst1.tar

```
This will tar up the db2inst1 directory and then restore it to its new location, including special files, etc.

Also, check the db2 documentation, there may be a procedure for moving/backing up/restoring a db2 installation.

If all else fails and you want to go back to your old /home, in single user mode just unmount the new /home partition (and remove it from fstab, or change its mount point if you want to mess with it more), and then rename the /home_old back to /home.

---

### Post by abcuser on 2008-09-03
Hi,
Tar reported an error to, but... I have checked the /old_home dir and I see original files are corruped!!! The database should not be running when I was moving the /home dir to new partition. So data are already corrupted... OK, not a big problem, because I have a backup of whole system.

But I would like to repeat whole process one more time. What is the safest way to 'copy' files from /home dir to new dir /new_home?

Is it "sudo init 1" safe enough? I would just like no database and no other program that is using files from /home directory is started.

Thanks,
Abcuser

---

### Post by kpatz on 2008-09-03
It would be better to reboot in recovery mode than to use sudo init 1, because there's no absolute guarantee that all running processes will be shut down when you go into init 1.  The shutting down occurs via scripts in the rc*.d directories, so if there's no DB2 shutdown script for going to runlevel 1, it's not going to be shut down when you thought it was.

Better yet, boot from a live CD, then you're guaranteed not to be running anything that isn't on the CD.

But, for a database application like that (db2, mysql, or what have you), it's a good idea to back everything up and then manually shut down the database server before doing anything with the partition the database files are on.

---

### Post by abcuser on 2008-09-03
Hi,
thanks a lot for you info. I will try boot from CD variant. I didn't know I could access disk with CD-Live.

By the way, I have restored the system from my backup and now it works fine again.

But as you know Linux users like to get to the bottom... so I will try CD-Live variant.
Thanks,
Abcuser

---

### Post by abcuser on 2008-09-05
Hi,
I have restored my system back to original and after restore system is working fine.

I rebooted computer and from grub menu I have entered recovery console and then I have followed: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) tutorial and completely!!! the same problem appeared as described in my first post.

Has someone successfully moved /home directory to new partition?

P.S. It looks like I will have to restore the system from backup again.
Regards,
Abcuser

---

### Post by abcuser on 2008-09-05
Hi,
instead of copying files with command:
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
as described in tutorial I used (from recovery console):
```
mv /old/home/ /new/
```

No errors were returned so I edit /etc/fstab file and add last line:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=956da7ca-df14-4312-82aa-22fab7cda0f9 /               ext3   noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# /dev/sda5
UUID=bac77762-e7e5-40c9-8e09-bfe39fde57ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

```

I rebooted computer and no!!! more errors starting Gnome was found.
But when trying to start DB2 database from /home/db2inst1... dir the error returned:
```

SQL1220N  The database manager shared memory set cannot be allocated.
db2inst1@igor-ubuntu804:~$ db2 ? sql1220n


SQL1220N  The database manager shared memory set cannot be allocated.

Explanation: 

The database manager could not allocate its shared memory set. The cause
of this error may be insufficient memory resources either for the
database manager or the environment in which its operation is being
attempted. Memory resources that can cause this error include: 
*  The number of shared memory identifiers allocated in the system
*  The size of the shared memory segment
*  The amount of paging or swapping space available in the system
*  The amount of physical memory available in the system

User response: 

One or more of the following: 
*  Validate that sufficient memory resources are available to satisfy
   the database manager's requirements, and those of the other programs
   running on the system.
*  On Linux 32-bit, increase the kernel parameter shmmax to 256 MB. On
   Linux 64-bit, increase the kernel parameter shmmax to 1GB.
*  Reduce database manager's memory requirement for this memory set by
   reducing the database manager configuration parameters which affect
   it. These are: fenced_pool and, numdb.
*  Where appropriate, stop other programs using the system.

```

So IBM DB2 relation database can't be started. I can't figured out why DB2 has lack of memory if no memory parameter have been changed? And what is this: "On Linux 32-bit, increase the kernel parameter shmmax to 256 MB."?



Just to try out I 'reverse' moved /home files from third partition to first one (like before moving at all):
```
mv /new/ /old/home/
```
Then commented out last line from /etc/fstab to disable third partition and reboot.

DB2 is up and running without errors of any kind. So it looks like mv command is working as it should. But why there becomes memory problems in DB2 if no memory has been changed? I haven't changed Linux swap partition either.

Any idea why DB2 has a lack of memory when moving /home directory to new partition (db2 is installed in /home/db2inst1 by default).
Regards,
Abcuser

---

### Post by abcuser on 2008-09-10
Hi,
as I see moving /home directory to new partition also changes "ipcs settings" which is minimum memory limits.

Before moving /home directory (command: ipcs -l):
```

------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 262144
max total shared memory (kbytes) = 8388608
min seg size (bytes) = 1

------ Semaphore Limits --------
max number of arrays = 1024
max semaphores per array = 250
max semaphores system wide = 32000
max ops per semop call = 32
semaphore max value = 32767

------ Messages: Limits --------
max queues system wide = 1024
max size of message (bytes) = 65535
default max size of queue (bytes) = 65536

```

After moving /home directory to new partition:
```

------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 32768
max total shared memory (kbytes) = 8388608
min seg size (bytes) = 1

------ Semaphore Limits --------
max number of arrays = 128
max semaphores per array = 250
max semaphores system wide = 32000
max ops per semop call = 32
semaphore max value = 32767

------ Messages: Limits --------
max queues system wide = 16
max size of message (bytes) = 8192
default max size of queue (bytes) = 16384

```

You see "max seg size" from "Shared Memory Limits" section is after move of /home dir set to 32768 kB, before moving it was set to 262144 kB. The minimum for starting DB2 database is 262144 kB.

Why this parameters were changed automatically! when I have moved /home dir to another partition?

Regards,
Abcuser

---

