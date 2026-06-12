---
title: "backup permissions problem"
date: 2008-09-25
forum: General Help
---

### Post by Dwood108 on 2008-09-25
hello 
I have just added a second hard drive to backup my music and photos.
It is formatted as ext3 and I created a folder called .Backup in my home directory to mount it in.

However when I cannot copy anything to this drive.

If I drap and drop it just won't allow the file to copy over.
If I cut and paste the paste option isn't available.
I cannot create any new folders on this drive either.

I suspect it is a permissions problem.

here is the fstab entry for this drive:
#Backup partition
/dev/sdb1 /home/david/.Backup  ext3 auto,users,rw,relatime 0 0

Any ideas
thanks

---

### Post by tonybaqain on 2008-09-25
actually it seems like only root on your side can read/write on the drive, test it by :

```
sudo touch /home/david/.Backup/test.txt
```

if it succeeded, then try creating directories to your backup, changing the ownership to your user, as for example:

i have the directory mp3 to backup it, so 

[LIST]
[*]sudo -i or su - , and then enter your root password
[*]mkdir /home/david/.Backup/mp3
[*]chown david.david /home/david/.Backup/mp3
[*]quit
[/LIST]

now try copy pasting your mp3's into /home/david/.Backup/mp3/ directory.

and have fun :)

---

### Post by WWSmith36 on 2008-09-25
Try changing ownership and permission

```
sudo chown -R david:david /home/david/.Backup
sudo chmod 755 -R /home/david/.Backup

```
Hope that helps

---

### Post by Dwood108 on 2008-09-25
@tonybaquin I just got the following  message:
touch: cannot touch `/home/david/.Backup/test.txt': No such file or directory


@wwsmith36 - changing ownership and permission worked, thanks.

I have a shared data partition (shared with windows) formatted as ntfs and mounted at /home/david/MyFiles and have never had this problem with that partition. Do you know why this is so?

---

### Post by WWSmith36 on 2008-09-25
I don´t believe ntfs partitions have same ownership issues.  They do have permissions issues though ex. read-only.

---

### Post by vanadium on 2008-09-25
> have never had this problem with that partition.
You did not have a problem. It is how linux works (safety). The root user always has to grant normal users permission to do something. I prefer the approach of tonybaqain, where you create directories which you grant to the different users. Alternatively, with the approach of WWSmith36, you grant the whole disk to one user. A more neat way to do this, however, is to control that with the options for the drive in /etc/fstab.

---

### Post by Dwood108 on 2008-09-28
@vanadium - I would like to control the options for the drive with fstab as you suggest.
Current settings are:
here is the fstab entry for this drive:
#Backup partition
/dev/sdb1 /home/david/.Backup ext3 auto,users,rw,relatime 0 0

What settings would I need to change.
Generally I am the only person using this computer.

---

### Post by vanadium on 2008-09-28
The advice of WWSmith36 is actually perfect for an ext3 disk, so you are all set. It is only for "foreign" filesystems like ntfs that ownership and permissions are given in /etc/fstab.

Probably, you can just replace the options (auto,users,rw,relatime) in your fstab by "defaults". It is advised to replace the last "0" by "2" to make sure the disk is checked during startup.

---

### Post by tonybaqain on 2008-09-28
Dwood108

NTFS-3G is read/write file system on linux systems, though you were able to access it, with no permission problems, but since this drive is ext3, it goes down the ACL permissions of linux.

---

### Post by Dwood108 on 2008-09-28
Ok - I think I have that sorted.

One more question:

when organising files on the ntfs partition dragging and dropping a file from one folder to another, even on the same partition, copies it rather than just moving. To move instead of copy I need to use the right click options.

On the ext3 partition dragging and dropping file into folders works as you would expect, with them being moved by default and only copied if it is to a different disc or partition.

Why is this???  ... and is there a way to change it?

---

