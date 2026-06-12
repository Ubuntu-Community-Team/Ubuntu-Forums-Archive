---
title: "Why is my hard drive always mounted under a different name?"
date: 2013-12-07
forum: Hardware
---

### Post by Cleveland Rock on 2013-12-07
Whenever I start up Ubuntu, my secondary hard drive is always mounted as something different. Sometimes it's "sdb1". Other times, it's something like what it currently is: "39004318-fe35-494c-9452-e06b4fb22975".

Its model number is ATA ST31000528AS, the device name is apparently /dev/sda1, and it's formatted as ext4.

The "media" folder has three folders: "39004318-fe35-494c-9452-e06b4fb22975", and two blank ones named "apt" and "sdb1". I can only access "apt" as root.

Can anyone help? Thanks.

---

### Post by Bashing-om on 2013-12-07
Cleveland Rock; Hi !

How are your mounting the secondary hard drive ? Is this drive an external drive ?
If you are not explicitly mounting that secondary hard drive from "/etc/fstab" with UUID, then depending on when the system recognizes the drive may get identified in different ways.
See:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
For full details.
If you require additional assistance, please post the output - between code tags - of terminal commands:
```

cat /etc/fstab
mount

```
And we will see what can be done to mount that drive as you desire.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-12-07
Partitions are mounted, not drives, and in my opinion the best way to always mount a partition automatically in the same place is to give it a label which you can do with gparted on a live CD/DVD.

I am assuming this is an external drive, and if so the partition on it will always mount at **/media/LABEL** or in newer ubuntu versions **/media/username/LABEL**.

---

### Post by Cleveland Rock on 2013-12-08
Sorry. I should have mentioned that this is an **internal** drive. Should I go ahead and give it a label in Gnome Partition Editor anyway?

Here's this:

```
clevelandrock@Centurion2:~$ cat /etc/fstab
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
UUID=dad66471-5aec-4a42-ae06-18d4d003626a  /            ext4  defaults             0  1  
UUID=89d7c37c-fd73-494c-a550-b25449456a67  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext4  defaults             0  0  
clevelandrock@Centurion2:~$ mount
/dev/sda1 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/sdb1 type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/clevelandrock/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=clevelandrock)
clevelandrock@Centurion2:~$ 


```

---

### Post by Bashing-om on 2013-12-08
Cleveland Rock; Hey,

The conventional manner to mount a "partition" is to use the devices UUID, That identifier does not change.
I am not going to assume the mount point for sdb1 exist, post back the output of terminal code:
```

ls -la /media

```
What I suggest is to change this line in the file /etc/fstab :
> 
/dev/sdb1                                  /media/sdb1  ext4  defaults             0  0 

"/dev/sdb1" to the UUID as provided by the terminal command:
Post this output also;
```

sudo blkid

``` for the partition sdb1. Use your favorite text editor to make the change ( hey make a backup prior to editing the file, SOP)
```

sudo cp /etc/fstab /etc/fstab-orig
gksudo gedit /etc/fstab

```
Substituting "/dev/sdb1" with the appropriate UUID.
Save the file, exit back to terminal and execute terminal command:
```

mount -a

``` to insure that there are no format errors in the fstab file.
No output ( a good thing, system accepted), should be good to go; 
Reboot and see what results now.

[INDENT]just the way 
[INDENT][INDENT]I would do this
[/INDENT][/INDENT][/INDENT]

---

### Post by Cleveland Rock on 2013-12-09
```
clevelandrock@Centurion2:~$ ls -la /media
total 16
drwxr-xr-x  4 root root 4096 Dec  8 14:48 .
drwxr-xr-x 25 root root 4096 Dec  7 02:46 ..
drwxr-x---  2 root root 4096 Dec  4 00:08 apt
drwxrwxrwx 14 root root 4096 Dec  6 13:08 sdb1
clevelandrock@Centurion2:~$ sudo blkid
[sudo] password for clevelandrock: 
/dev/sda1: UUID="dad66471-5aec-4a42-ae06-18d4d003626a" TYPE="ext4" 
/dev/sda5: UUID="89d7c37c-fd73-494c-a550-b25449456a67" TYPE="swap" 
/dev/sdb1: UUID="39004318-fe35-494c-9452-e06b4fb22975" TYPE="ext4" 
clevelandrock@Centurion2:~$ sudo cp /etc/fstab /etc/fstab-orig
clevelandrock@Centurion2:~$ gksudo gedit /etc/fstab
clevelandrock@Centurion2:~$ mount -a
mount: only root can do that
clevelandrock@Centurion2:~$ sudo mount -a
mount: special device 39004318-fe35-494c-9452-e06b4fb22975 does not exist
clevelandrock@Centurion2:~$ gksudo gedit /etc/fstab
clevelandrock@Centurion2:~$ sudo mount -a
clevelandrock@Centurion2:~$ 


```

As you can see, I screwed up the first time editing the file. I forgot to add "UUID=". I shall restart my computer and see how it goes.

---

### Post by Bashing-om on 2013-12-09
Cleveland Rock; Hi ! 

We can get through this. Sorry as my instruction is not too clear:
Activate the text editor loading the file "fstab" on the path of "/etc" with admin privileges:
```

gksudo gedit /etc/fstab

```
make this line:
```

/dev/sdb1                                  /media/sdb1  ext4  defaults             0  0

```
to this: (you may copy and paste)
```

UUID=39004318-fe35-494c-9452-e06b4fb22975   /media/sdb1  ext4  defaults             0  0

```
Make sure that the format is correct and no errors by terminal command:
```

sudo mount -a

```
As no errors are reported, now reboot and see that sdb1 is always mounted with the UUID as sdb1.

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by Cleveland Rock on 2013-12-09
Sorry, I completely forgot what I was doing! Everything looks good so far. I'll give it a little while before I mark this thread as solved, however.

---

