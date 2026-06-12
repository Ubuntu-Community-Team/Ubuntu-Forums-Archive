---
title: "fstab settings for new partition"
date: 2008-08-22
forum: General Help
---

### Post by jadhav333 on 2008-08-22
I have recently re-installed ubuntu 8.04 using the following partition configuration.

sda1 /           ext3 15Gb
sda2 /home       ext3 15Gb
**sda3 not mounted ext3 465GB **
sda4             swap 5Gb

It was understood that the purpose of **sda3 465Gb **was to serve as a common shareable partition between different users.

when ubuntu starts it mounts the sda3 automatically.. but does not allow me to write to the same.

I intend to add the mount details of the same by editing the **fstab**.

Pls help me write the correct settings. Pls note it has an ext3 file system. I need to provide read/write/execute access to all users on that partition. 

Thanks.

Pls reply asap as I am waiting to 'enable' the sda3 to copy my stuff/ and its 2am in the morning :)

---

### Post by LateNiteTV on 2008-08-22
what label did you give sda3?

---

### Post by clueless on 2008-08-22
```

/dev/sda3 /path_to_mount_point    ext3    relatime 0       2

```

Make sure you create a blank directory first where you want the partition to appear (I usually put all my disks under /media/) and change the permissions with the chown command.

---

### Post by jadhav333 on 2008-08-22
currently the partition sda3 gets mounted in /media/disk automatically. I mean there is no such entry in fstab.

I und the following:

1) umount the sda3 partition

2) make a folder in /media
       [COLOR="Blue"]sudo mkdir /media/sda3[/COLOR]

3) change the owner of the folder using chown. 
       [COLOR="Blue"]**can u pls advise on the code to type?**[/COLOR]

4) back up the fstab file.
       [COLOR="Blue"]cp /etc/fstab /etc/fstab.bak[/COLOR]

5) edit the fstab file
       [COLOR="Blue"]sudo gedit /etc/fstab[/COLOR]

6) add the following line in fstab
       [COLOR="Blue"]/dev/sda3 /media/sda3    ext3    relatime 0       2[/COLOR]

7) re-login ubuntu

Is this procedure and code correct. pls advise as i understand editing fstab is very critical..

---

### Post by clueless on 2008-08-23
1) umount the sda3 partition

sudo umount /dev/sda3



2) make a folder in /media
sudo mkdir /media/sda3

correct


3) change the owner of the folder using chown.
can u pls advise on the code to type?

sudo chown your_username:your_username /media/sda3


4) back up the fstab file.
cp /etc/fstab /etc/fstab.bak

correct


5) edit the fstab file
sudo gedit /etc/fstab

correct


6) add the following line in fstab
/dev/sda3 /media/sda3 ext3 relatime 0 2

correct


7) re-login ubuntu

reboot the computer


And that should be it!

---

### Post by mb_webguy on 2008-08-23
It's not absolutely necessary to change ownership and permissions for the new mount point.  In some instances, it would be better not to do so.

Everything else, though, looks good.

---

### Post by vanadium on 2008-08-23
I agree: looks very good except for the change user part.

Because that partition should be a "a common shareable partition between different users", there is no reason to change the user to any other than root.

There are a couple of ways to allow different users of the system to do anything on that partition:

1) set all permissions open (not any restrictions)
2) change the group of the partition to a group to which all users belong, and set all group permissions open (only users that are member of that group can do anything).

---

