---
title: "New Folder in Flash Drive"
date: 2024-05-02
forum: Hardware
---

### Post by daniell59 on 2024-05-02
I just formatted my flash drive to Ext 4. I am now unable to make a new folder in the flash drive. Any insight into this problem will be appreciated.

---

### Post by yancek on 2024-05-02
Exactly how did you try to do this?  Did you do it using a GUI file manager?  Using a terminal?  External drives including flash drives are generally shown as owned by root when using a Linux filesystem so you need to ascertain the device name and mount point using  lsblk  then running the command:  ls -l on the mount point to determine the owner:group and permissions.  If you want to access/write to the partition you will need to give your user or group write permission.

---

### Post by daniell59 on 2024-05-02
First I formatted the flash drive in G Parted. As I have always done, I right clicked the mouse. it did not allow me to make the new folder. Of course my knowledge is limited. I am anxious to learn however.

---

### Post by daniell59 on 2024-05-02
If somebody could walk me through the process, it would be very helpful.

Thanks in advance

---

### Post by daniell59 on 2024-05-02
In Windows 10 I formatted the flash drive to ex FAT. I booted back into Ubuntu. I am now able to open a new folder.
I really wish I knew what I was doing.
I would appreciate it if somebody could explain it to me.
Thanks in advance.

---

### Post by oldfred on 2024-05-02
Part of the advantage of Linux partitions is ownership & permissions. This help restrict unknown users from running apps from the system directly if ownership & permissions are set correctly.

Windows formats like NTFS, FAT32 & exFAT do not support Linux ownership & permissions. You end up setting a default when mounting those types of partitions. And cannot change them. Often owned by / (root) but wide open permissions so not as restrictive as they should be.
Also FAT32 & exFAT not recommended for larger partitions. 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Default mounts are normally in /media. But I have a data partition mounted in /mnt.
So sometimes I download a file or execute a command using sudo when I should not and a file or two do not have correct ownership & permissions. I just reset everything. Note that -R is recursive & modifies everything below the path specified. Never to be run on / (root) or root folders as that destroys system and reinstall is about the only way to restore. 

sudo chown -R $USER:$USER /mnt/data
sudo chmod -R a+rwX /mnt/data

---

### Post by #&amp;thj^% on 2024-05-02
Mine is formatted as fat32, now I need to move to that Drive first ie:

```
cd /media/me/MINE/
```

Now I'll make a Folder called "folder"
```
mkdir folder

```

Lets look now with:
```
/media/me/MINE 
&#9492;&#9472;> ls
folder

``` 
And there it is my new folder, but if I want to Name it something meaningful to me:
```
mkdir folder My-New-Folder

```
Always check to verify:
```
ls 
folder  My-New-Folder

```

Drive Details:
```
sudo blkid /dev/sdh
[sudo] password for me: 
/dev/sdh: LABEL_FATBOOT="MINE" LABEL="MINE" UUID="90F3-D60A" BLOCK_SIZE="512" TYPE="vfat"

```

There is plenty of documentation on the web for this.
One here for basic info: [https://www.cyberciti.biz/faq/how-to-make-a-folder-in-linux-or-unix/](https://www.cyberciti.biz/faq/how-to-make-a-folder-in-linux-or-unix/)

---

### Post by tea for one on 2024-05-03
> **daniell59 said:**
> First I formatted the flash drive in G Parted. As I have always done, I right clicked the mouse. it did not allow me to make the new folder. Of course my knowledge is limited. I am anxious to learn however.
> **daniell59 said:**
> If somebody could walk me through the process, it would be very helpful.
Two items of information:-

(a) When a new user is created (even during the installation process), a new group with the same name is created and the user is added to it. This group is called the primary group of the user.
e.g. Your user name is daniell59 and there will also be a group called daniell59
(b) Using gparted to format a partition with ext4, the owner will be root.

Now, in order to use the partition as a regular user, the permissions have to be edited.

You will need to know where the external drive is mounted.
Attach your flash drive and open Disks (gnome-disk-utility)
Select the disk and you should see the mountpoint.
e.g. /media/daniell59/0dcedd13-7a42-458c-a2a6-b722cf8ab67d

This information is then used to create a command to change the ownership of a flash drive from root to daniell59. 
Open a terminal and enter:-
```
sudo chown -R  daniell59:daniell59 /media/daniell59/0dcedd13-7a42-458c-a2a6-b722cf8ab67d/
[COLOR="#0000FF"]           #Change user, group and mountpoint to match your data[/COLOR]
```
Alternatively, you can use Disks to take ownership of a device.
Attach your flash drive.
Open Disks (gnome-disk-utility)
Select the disk/flash drive
Click the gear wheel to reveal Additional partition options > Take ownership and Enable recursive mode > OK > Enter user password

N.B. Terminal command above with option –R = Recursive mode

---

### Post by vanadium on 2024-05-03
To claim ownership on the newly formatted disk (with a file system that supports Linux permissions), open Disks, select the partition you just formatted, click the cog wheel and select "Take ownership".

---

### Post by daniell59 on 2024-05-03
This time I formatted the flash drive to ext 4 using Disks instead of Gparted. There were no problems. I was able to write to the flash drive.
Thanks to all for your helpful input.

---

