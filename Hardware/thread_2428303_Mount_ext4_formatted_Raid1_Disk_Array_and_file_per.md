---
title: "Mount ext4 formatted Raid1 Disk Array and file permissions questions"
date: 2019-10-02
forum: Hardware
---

### Post by ozkan on 2019-10-02
Hi,

In /etc/fstab I have one line which is mounting an ext4 formatted Raid1Array in boot time:

*/dev/md35 /depo35 ext4 defaults,nofail,discard,grpid*

it mounts successfully no problem.

what I want to achieve is that: every newly created new file shall have *myname : plugdev* with file permissions wrxwrx.r.

in fstab grpid option is allowing me to give myname : plugdev ownership of every new file created because the parent folder is always myname : plugdev 
but somehow ... system does  not give proper permissions for newly created files, they are always rwxr..r.. although parent folder permission is wrxwrx.r. 

what is the proper option to achieve it in fstab ? (I am looking for an option like umask as I do  for ntfs partitions)

ps:myname is also belonging to plugdev

---

### Post by TheFu on 2019-10-02
```
/dev/md35 /depo35 ext4 defaults,nofail,discard,grpid
```
seems to be missing 2 columns. There need to be 6 columns for each mount. Always 6. Always.

Also, no need to say "defaults", then change settings.  I have never seen the grpid option used before. Looking it up.  Eh ... fine. Seems a little odd, but whatever. I'm comfortable using setgid.

```
/dev/md35      /depo35      ext4      nofail,discard   0    0  
```
The number of spaces between columns isn't important. 1 or 15 doesn't matter, but there needs to be 6 columns.  The manpage for fstab explains what each column means.

wrxwrx.r. is an odd order for permissions.

rwx is the normal order, in 3 groups. The permissions and group for any new object in a directory are controlled by the setgid and the umask for the userid creating the object (file or directory).  The parent directory can only control the group.  The permissions are controlled by your umask.

To handle newly created objects being in th plugdev group, do:
```
chgrp plugdev  /depo35
chmod g+s /depo35
```

To force 775 permissions for directories and 664 for files, set your umask to 0002.  Do that in your ~/.bashrc file, if you like or you can do it in any terminal where you want that.  If you want all processes under your userid to honor it, then logout and login again after the .bashrc change.  BTW, the default for Ubuntu is umask 0002, so it would only be different if someone screwed with it.

Just to be extremely clear - the umask command looks like this:
```
umask 0002
```
To see it, run 
```
$ umask 
0002 
```

There is no need for grpid in the fstab.   I didn't look too closely at the other mount options. I use this:```

/dev/mapper/ubuntu--vg-home--lv       /home     ext4      errors=remount-ro,noatime     0       2
``` for my /home mount.

---

### Post by ozkan on 2019-10-03
hi TheFu, thanks for the support 

yes it is 6 columns and sorry for my mistake it is in rwx rwx rwx  order  :) 

grpid is listed inside the mount manual I found it from there and it really works I don't need to do 

> chgrp plugdev  /depo35
chmod g+s /depo35

for the file permissions you say bashrc solution but actually this is a server and there are some applications where their users(same name with APP such as samba plex ... trasnmssions daemon etc ) are in plugdev group must create and access  files and edit them even it is created by another. so bashrc is just for the user who start a session through a terminal right? and it is not systemwide permanant solution . 

Normally I choose this for ntfs partitions 
> UUID=1CF867DFF867B624 /depo10         ntfs    defaults,nls=utf8,uid=1000,umask=002,gid=46 0       0

 it is perfectly works but umask option does not exist for ext4 in mount

---

### Post by TheFu on 2019-10-03
I wouldn't use plugdev for plex data.  I use plex (the group) for plex data and add my userid to the plex group.  plugdev group is for specific reasons and plex files is NOT one of those reasons.  For my use, which is mostly remote from other systems, plugdev would never work for plex.  I'm seldom actually logged into our plex server.

~/.bashrc isn't the same as "bashrc".  We need to be exactly correct with file names so lurkers don't get lost. Every login loads the initialization files specified by the passwd data base.  Most of the time, the user's shell would be bash and bash has startup rules which include processing the ~/.bashrc is part of that, before any GUI session is started. The bash manpage explains all the different files used.

Settings like umask are setup for each user. The system has a default and every process inherits that, until it is overridden. Tools/scripts are setup based on the system defaults for umask and system security is based on that default, so changing that system-wide umask wouldn't be something I did.  Every program/script that keeps the system running might be impacted.  But changing your personal umask is definitely safe, provided the desired permissions result and you can fix it when they don't.

For NTFS, there are a few other things I'd use as options, assuming NTFS can't be purged completely. Some options prevent names being created that Windows doesn't like, others will improve performance and others are for security to prevent NTFS based data storage from being used to launch attacks.  I usually set a specific dmask and fmask for NTFS, since I want files NOT to have the eXecute bits set where only data should be.

Update:  You seem to think that using mount options is the way to solve this.  It isn't.  The solution I'd use it what I've already said.   Mount options are for non-native file systems, like ntfs/vfat/exfat - foreign file systems.  For native file systems, learn and use the normal permissions.   Or ignore advice, if you prefer.

---

### Post by ozkan on 2019-10-04
Hi TheFu 
thanks for your support,  
finally I learned  a couple of things I wan to share: 

1) umask does not behave in ntfs as it behaves in ext4. when you mount ntfs partition if you want to assign different permissions for files and directories you can not use umask you have to use dmask and fmask
2) yes "defaults" are not necessary
3) grpid is necessary for my case for ext4
4) it is pity that I can not give fmask and dmask for ext4 in etc fstab. Finally I changed create mask and  directory mask for applications such as samba in their config file. 

now it does exactly want I want.

---

