---
title: "[SOLVED] Ubuntu Backup System"
date: 2008-08-27
forum: General Help
---

### Post by CrusaderAD on 2008-08-27
Hello. We want to implement a Ubuntu System that runs regular backups for folders on our network. How would we do this? Thanks!

---

### Post by mellowd on 2008-08-27
What kind of folders? How are they shared?

---

### Post by CrusaderAD on 2008-08-27
They are windows share folders. I've got samba up and running. I can map the drives just fine.

---

### Post by mellowd on 2008-08-27
You could use a combination of scp and tar. You could set up a cron job too so once it's working you can leave it alone.


well not exactly, you should always test your backups at least once a month (it surprises me how many people never do this)

---

### Post by CrusaderAD on 2008-08-27
What about sbackup? Any good?

---

### Post by mellowd on 2008-08-27
Never used it myself, you could give it a try

---

### Post by CrusaderAD on 2008-08-27
Going to give it a try since it seems to be a user friendly GUI. I will post my results here. Thanks!

---

### Post by CrusaderAD on 2008-08-27
Does anyone know if sbackup can backup network drives? When choosing a directory to backup, it doesn't list the mounted network drives.

---

### Post by Zill on 2008-08-27
raptormanad: I would guess that SBackup will backup networked drives if you select the appropriate mount point in the "Include" tab of the SBackup Config Backup Properties screen.

This screen has an "Add Directory" button which shows the full filesystem.

Just select the include/exclude options you require.

Caveat:  I use SBackup to backup each of our three PCs automatically but do not include networked drives.

---

### Post by CrusaderAD on 2008-08-27
Where would the mount point be from within the file system? It doesn't show any of the links I make.

---

### Post by mssever on 2008-08-27
> **raptormanad said:**
> Where would the mount point be from within the file system? It doesn't show any of the links I make.
The mount point is whatever you specified in /etc/fstab. If you didn't use fstab and instead use Nautilus, then your shares will only be available from programs that support the GnomeVFS.

---

### Post by CrusaderAD on 2008-08-29
I have a mount point specified in my fstab file, but when I navigate to it, it's empty.

---

### Post by CrusaderAD on 2008-08-29
Ok I got it. I removed the extra mount point in my fstab (not sure how it got there) and rebooted. I am now able to mount this drive just fine now and view it in other programs. Thanks!

---

### Post by CrusaderAD on 2008-09-03
Here's some instructions for anyone who needs them.

After you have Ubuntu installed and your desktop is set do the following:

Download these programs:

sudo apt-get install samba smbfs sbackup

Change your samba settings to match your network:
*Do not play with this file unless you know what you're doing*

sudo vi /etc/samba/smb.conf

Next we need to mount the drives:
*Again, Do not play with this file unless you know what you're doing*

sudo vi /etc/fstab

Add this line so it fits your settings:

//192.168.5.1/folder1/  /home/username/folder2/  cifs  username=username,password=password  0  0

Save and mount the drives:

sudo mount -a

Launch sbackup from System > Administration > Simple Backup Config

Edit the settings to backup what you wish. You should now be able to view and backup networked drives from this tool.

---

### Post by silverglade00 on 2008-09-03
Thanked for coming back and posting a walkthrough after solving it.

---

### Post by CrusaderAD on 2008-09-07
Keep is also another good program. In fact it maybe better because you can schedule multiple backups rather than just one.

---

### Post by CrusaderAD on 2008-09-19
Here's an update. If you're backing up to some external hard drives, format them first with gparted to NTFS, the default FAT32 has a file size cap of 4 gig.

---

### Post by colau on 2009-05-07
A question.
Only backing up the /home directory will do the job?

---

### Post by theozzlives on 2009-05-07
Simple backup

---

### Post by colau on 2009-05-07
So if the system crashes,I have to install the ubuntu 9.04 every time and restore the backed up file ??

Is there any way to avoid reinstalling the system every time?

---

### Post by colau on 2009-05-07
So if the system crashes,I have to install the ubuntu 9.04 every time and restore the backed up file ??

Is there any way to avoid reinstalling the system every time?

---

### Post by CrusaderAD on 2009-08-04
> **colau said:**
> So if the system crashes,I have to install the ubuntu 9.04 every time and restore the backed up file ??

Is there any way to avoid reinstalling the system every time?

It depends on what caused the crash. Usually a fresh install is the best way to go, then restore your data.

---

