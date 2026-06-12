---
title: "[SOLVED] thumb drive permissions"
date: 2008-08-24
forum: Hardware
---

### Post by Ghliofris on 2008-08-24
I have an 8 gig thumb drive. It has only been used in Ubuntu systems. It is filesystem type msdos vfat (fat32). I have been able to write to it no problem. Now Permissions can't be determined. Gone in terminal and tried chmod 766 but comes back "Read Only" It has me as owner root as group, with 700 on permissions.

drwx------  8 digital root 4096 1969-12-31 19:00 disk
digital@volvo:/media$ chmod 766 disk
chmod: changing permissions of `disk': Read-only file system

The date on it is 12/31/1969, ummm huh?:confused: 

Could that be the culprit? Can I change the date and how?

---

### Post by forger on 2008-08-24
I would do the following:
1) check if there is a "read-only" switch on the drive ;)

2) "I have been able to write to it no problem. Now Permissions can't be determined."
Did you change computers? I mean is this on some other computer or a fresh install of Ubuntu?

3) check on your permissions, System > Administration > Users and Groups > select your username, click "Properties" > User Privileges.
I'm not sure which ones you have, but I'd check all the options there that related to drives and removable media :)
(You have to log out and log back in for it to take effect, or even reboot sometimes if you have other users logged in)

4) You have try his:
```
sudo chown -R $USER:$USER /media/disk
```
This will make the current user as owner of the folder and its contents


5) back up your valuable data to a folder on the Desktop, install **gparted** (Gnome partition editor) and head to System > Administration > Partition editor, select your device from menu Gparted > Devices, then right-click and format your thumb drive again.
Unmount it and mount it back in. Copy back all your data it, unmount it and mount it back in.

---

### Post by Ghliofris on 2008-08-24
> **forger said:**
> I would do the following:
1) check if there is a "read-only" switch on the drive ;)

2) "I have been able to write to it no problem. Now Permissions can't be determined."
Did you change computers? I mean is this on some other computer or a fresh install of Ubuntu?

3) check on your permissions, System > Administration > Users and Groups > select your username, click "Properties" > User Privileges.
I'm not sure which ones you have, but I'd check all the options there that related to drives and removable media :)
(You have to log out and log back in for it to take effect, or even reboot sometimes if you have other users logged in)

4) You have try his:
```
sudo chown -R $USER:$USER /media/disk
```
This will make the current user as owner of the folder and its contents


5) back up your valuable data to a folder on the Desktop, install **gparted** (Gnome partition editor) and head to System > Administration > Partition editor, select your device from menu Gparted > Devices, then right-click and format your thumb drive again.
Unmount it and mount it back in. Copy back all your data it, unmount it and mount it back in.

1. no read only switch on drive.

2. same install on mainframe, new install on laptop and fresh install on wife's computer, all same results.

3. I have permission for all but send & receive faxes. access external storage devices automatically is checked. That is the only one I see that would relate to a thumb drive.

4. yes, here is the abridged result:
chown: changing ownership of `/media/disk/My eBooks/The Linux Kernel Primer A Top-Down Approach for x86 and PowerPC Architectures.chm': Read-only file system
chown: changing ownership of `/media/disk/My eBooks/Thomson Linux+ 2005 In.Depth -2005.pdf': Read-only file system
chown: changing ownership of `/media/disk/My eBooks/ubuntu-8.04-dvd-i386.iso': Read-only file system
chown: changing ownership of `/media/disk/My eBooks': Read-only file system
chown: changing ownership of `/media/disk': Read-only file system

5. Yeah, was thinking about that, got everything backed up on main and laptop. Will give this a try.

---

### Post by Ghliofris on 2008-08-24
Reformatted it, still permissions can not be determined on the drive itself; however, I can read and write to it. I formatted it to vfat (32fat).

Thanks

---

### Post by forger on 2008-08-24
fat32 doesn't have actually file/folder permissions
If you really want permissions you'll have to use ext2 or ext3, but bear in mind that if you use it on a different computer, the UID/GID (userid and groupid) numbers will be a problem :)

to find out your userid/groupid:
```
cat /etc/passwd | grep $USER
cat /etc/group | grep $USER
```

to find out userid/groupid of files/folders:
```
dir -n
```
(it will show numbers instead of the owner and group name)

So, if you want ext2/3, make sure the user you are using on the current computer matches the **UID number** (not name) of the owner of the files in your thumb drive.

---

