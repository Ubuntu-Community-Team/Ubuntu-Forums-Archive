---
title: "problem with blank space in mount point"
date: 2009-06-23
forum: Hardware
---

### Post by pagheca on 2009-06-23
Hi everyone,

when I installed Ubuntu 9.04 (gnome) on my laptop I created a partition to be shared with XP. This partition, by default, was mounted as "/media/New Volume", with a blank space. I tried to get rid of this blank space by editing fstab, but something went wrong and now there is something wrong in the access to this disk.

So, I reversed the sitation and I put everything back, by writing "/media/New\ Volume" in the /etc/fstab file but I found a blank and a "\ " are NOT the same thing.  Now I'm stuck in this situation. Something is wrong but I can't understand what. If I try, for example:

$sudo umount /media/New\ Volume/
umount: /media/New Volume: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

while:

$df
Filesystem           1K-blocks      Used Available Use% Mounted on
[...]
/dev/sda5            184321744  50356544 133965200  28% /media/New Volume
[...]

If I edit again /etc/fstab and change the partition point to 

/dev/sda5 /media/DataDisk ntfs umask=222,utf8 0 0

while if:

$sudo mount /media/DataDisk 
fuse: failed to access mountpoint /media/DataDisk: No such file or directory

Also in gparted I found something strange: 

"umount: /media/New Volume: device is busy. "

also if is not.

What's wrong? How to change the partition name (or just go back to the original one) without risking the data?

I also tried to put back another name editing fstab. Now the disk is DataDisk, but:

$ sudo mount -a
fuse: failed to access mountpoint /media/DataDisk: No such file or directory

the disk is correctly seen by the WinXP boot.

thanks for any help!

pagheca

---

### Post by Odemia on 2009-06-23
"device busy" almost always means that you have nautilus or terminal window working in the directory or sub directory.

[LIST]
[*]Close any nautilus (dolphin if you are using kde) windows you have open
[*]Change the current working directory ("cd ~") or close any terminals currently in /media/New\ Device (or it's sub directories).  Also if you have used alt-f1, alt-f2 etc.  make sure those terminals are not in /media/New\ Device.
[/LIST]
Then try running umount again.

As for mounting it to a new location.  You need to umount succesfully first.  Then you need to create the directory that you want to mount to ("sudo mkdir /media/NewMountPoint").  You can mount using "mount /dev/sda5 /media/NewMountPoint".

Finally as a bit of a side note, if this is an internal drive you may want to mount it to /mnt/New\ Device and then create links to it.  The difference between /media and /mnt being things in /mnt don't showup on your desktop.  That's just incase you are worried about cluttering your desktop.

---

### Post by pagheca on 2009-06-23
thanks very much for your prompt reply. 

Unfortunately I do not have any terminal or dolphin or nautilus open on that disk. 

Let me try to summarize the current situation after a reboot.

1.
$ less /etc/fstab
[...]
/dev/sda5 /media/DataDisk ntfs umask=222,utf8 0 0
[...]

2. 
gparted show nothing under Mount Point for this partition

3. 
$ sudo mount -a
fuse: failed to access mountpoint /media/DataDisk: No such file or directory

4. 
$ sudo umount /media/DataDisk
umount: /media/DataDisk: not found

???

So, I can't mount anymore this disk.

pagheca

---

### Post by pagheca on 2009-06-23
**** sorry - sorry - sorry ***

I got your point... I missed to create the directory where to mount this partition. It looks working now.

Thanks very much!!!
pagheca

---

### Post by Odemia on 2009-06-23
np, just happy to have been able to help.  It's a little validation after hundreds of hours fiddling with linux.

---

### Post by pagheca on 2009-06-24
Actually, I felt happy too early...I discovered the problem is not solved as I can't modify any of those files or write in the partiiton. Now, the mount point is \Data. 

$ mount
/dev/sda5 on /Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

I changed ownership and permissions with the following commands:

sudo chown -R <login>:<login> /Data          (<login> is my login name)
sudo chmod -R 755 /Data

I got no error and the disk has been busy for a while while attending to these commands. However:

$ ls -l
total 165
...
lr-xr-xr-x 1 root root    24 2009-06-17 17:55 datadisk -> datadisk (this is an example)
...

So, the owner of all the files is still root. What's wrong? How can I change things? 

this is the relevant line in /etc/fstab:
/dev/sda5 /Data ntfs umask=222,utf8 0 0

Remember this is a shared partition in a XP/Ubuntu 9.04 dual boot system. I would like to understand why it was working fine until yesterday and how to go back to the original situation.

Any hint very welcome.  Thank you.

Regards,
pagheca

---

### Post by raheel Pasha on 2009-06-24
> **pagheca said:**
> Hi everyone,

when I installed Ubuntu 9.04 (gnome) on my laptop I created a partition to be shared with XP. This partition, by default, was mounted as "/media/New Volume", with a blank space. I tried to get rid of this blank space by editing fstab, but something went wrong and now there is something wrong in the access to this disk.

So, I reversed the sitation and I put everything back, by writing "/media/New\ Volume" in the /etc/fstab file but I found a blank and a "\ " are NOT the same thing.  Now I'm stuck in this situation. Something is wrong but I can't understand what. If I try, for example:

$sudo umount /media/New\ Volume/
umount: /media/New Volume: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

while:

$df
Filesystem           1K-blocks      Used Available Use% Mounted on
[...]
/dev/sda5            184321744  50356544 133965200  28% /media/New Volume
[...]

If I edit again /etc/fstab and change the partition point to 

/dev/sda5 /media/DataDisk ntfs umask=222,utf8 0 0

while if:

$sudo mount /media/DataDisk 
fuse: failed to access mountpoint /media/DataDisk: No such file or directory

Also in gparted I found something strange: 

"umount: /media/New Volume: device is busy. "

also if is not.

What's wrong? How to change the partition name (or just go back to the original one) without risking the data?

I also tried to put back another name editing fstab. Now the disk is DataDisk, but:

$ sudo mount -a
fuse: failed to access mountpoint /media/DataDisk: No such file or directory

the disk is correctly seen by the WinXP boot.

thanks for any help!

pagheca



Nice

---

### Post by pagheca on 2009-06-24
what is nice?

---

### Post by pagheca on 2009-06-24
Hi again,

please note my latest message (2 before this). The situation is becoming more and more confusing for me. Now, I noticed that when I run Dolphin there is a directory called "datadisk", remembering of an old attempt. 

Moreover:

$ ls -l /media/
total 16
lrwxrwxrwx 1 root root    6 2009-06-03 18:28 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-06-03 18:28 cdrom0
drwxr-xr-x 2 root root 4096 2009-06-23 18:04 DataDisk
drwxr--r-- 2 root root 4096 2009-06-04 22:29 New Volume
dr-xr-xr-x 1 root root 4096 2009-06-23 21:23 WinXP

Again, the "New Volume" and Datadisk attempts are still there. They were earlier attempts. So, in some way the system has maintained all the disks mounted. The point is that if I cd to them:

$ cd /media/New\ Volume/
bash: cd: /media/New Volume/: Permission denied

There is no trace of them in mtab and fstab.

I think I'm missing a focal point here. Any help welcome again - thanks

pagheca

---

### Post by Odemia on 2009-06-24
> **pagheca said:**
> 
...
drwxr--r-- 2 root root 4096 2009-06-04 22:29 New Volume
...
$ cd /media/New\ Volume/
bash: cd: /media/New Volume/: Permission denied

The permissions on "New Volume" do not give execute permissions to anyone other than root.  Execute permissions are needed on directories in order to access items within them.  Therefore you would have to:

[LIST=1]
[*]"sudo su; cd /media/New\ Volume;"  (become root, then access), or
[*]"sudo chmod a+x /media/New\ Volume; cd /media/New\ Volume;" (a=all users, +=add, x=execute permission.  "chmod a+x"=add execute for all users.  Then enter the directory)
[/LIST]
If you are no longer mounting to these locations you can get rid of the directories.

Not sure I understand the previous post regarding:
[quote=pagheca]
sudo chown -R <login>:<login> /Data          (<login> is my login name)
sudo chmod -R 755 /Data
...
lr-xr-xr-x 1 root root    24 2009-06-17 17:55 datadisk -> datadisk (this is an example)
[/quote]

I am unclear where you ran "ls -l".  What is the output of "ls -l /Data", do regular files and directories have the same ownership and permissions as "datadisk" or is it just links that aren't changing permissions? What is the current state of fstab and mtab?

---

