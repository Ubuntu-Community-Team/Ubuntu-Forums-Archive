---
title: "Changing Permissions on HD"
date: 2008-11-06
forum: General Help
---

### Post by LenWynne on 2008-11-06
Hi.

I am having a problem with permissions on one of my two hard drives.  I have ubuntu installed on the first HD (sda1) and no problems here. 

I have a second drive I set up (sdb1) just for files. I partioned it as primary partition with ext3. It shows up fine in the device list in the GUI and when opens I want to mount it, but beyond this I cannot do anything with it in terms of read/write. When I checked details in Dolphin is shows as belonging to root.

Any suggestions please?

Thanks

---

### Post by tiberiup on 2008-11-06
open terminal :
sudo chmod -R 777 mountedfolder

---

### Post by ubnewbie2 on 2008-11-06
change the permissions at the mount point to allow your normal user read,write, and execute. e.g. if it's mounted at /mnt/disk  then something like

sudo chmod 777 /mnt/disk

will probably help.  If it's already mounted with files on it, maybe add a -R option to change all the files in subdirectories as well.

You might also

sudo chown -R <username> /mnt/disk

substituting your username, to take ownership of the files, then

sudo chmod -R 744 /mnt/disk 

 (gives full control to you, and read only to everyone else)

---

### Post by Dave54 on 2008-11-06
The method I have always used is as follows:
First, mount the drive. Then run:```
sudo chown -R Owner:Group /media/mountpoint
sudo chmod -R 755 /media/mountpoint
```Replace Owner:Group with your user name and group (mine is dave:dave) and replace /media/mountpoint with the actual mount point.

If you're wondering why we're giving you different numbers (777, 744,755), [here's a good guide]("http://www.tuxfiles.org/linuxhelp/filepermissions.html").
Always remember to read the man pages ("man chown" and "man chmod")

---

### Post by LenWynne on 2008-11-07
I have tried these commands with the HD both mounted and unmounted but I seem to keep coming up against permission denied messages.  I am thinking the problem may be that the HD I need to path to is within the /dev directory in the filesystem and this whole structure is also owned by root, so I am not sure how to get around this.

---

