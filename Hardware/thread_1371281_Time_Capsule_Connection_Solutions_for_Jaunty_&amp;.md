---
title: "Time Capsule Connection Solutions for Jaunty &amp; Karmic"
date: 2010-01-03
forum: Hardware
---

### Post by ytene on 2010-01-03
After some experimentation, I've managed to get a reasonably effective working solution that enables me to use my Time Capsule with a Jaunty workstation quite effectively.

Here are some key statements from my /etc/fstab file, with comments following:-
 
```
# /media/sdb1 was on /dev/sdb1 at instal
UUID=5AD9-9F01  		 	   /media/sdb1     vfat    utf8,umask=007,gid=46 		0       1
# /media/sdb4 was on /dev/sdb4 at instal
UUID=d72603a9-fbb0-4333-b8f7-0bcd91ef528f /media/sdb4     ext4    relatime        			0       2
# /media/sdb5 was on /dev/sdb5 at instal
UUID=ECB45C56B45C24FC  			   /media/sdb5	   ntfs	  defaults,nls=utf8,umask=007,gid=46	0	1

# Apple Time Capsule
//192.168.1.40/TimeCapsule/user 	   /media/capsule  cifs password=myP4ssw0rd,rw,iocharset=utf8,gid=46,file_mode=0770,dir_mode=0770
```

OK, some key points to note for you here:

1. You need to have the "smbclient" and "smbfs" packages installed.

2. The above statement will mount the Time Capsule as if it were a "Windows" [i.e. SMB-based] partition. This means that because Linux cannot apply individual file ACLs, it will set all files in the Capsule file system to inherit the permissions that you specify in the connection string. 

3. Because of the ACL inheritence described in 2., above, you might want to think about having at least one FAT32 or NTFS partition on your local machine. Why? Because those non-native file systems inherit permissions in exactly the same was as the capsule, it means that if you want to use something like the unison file synchronisation tool to keep 2 or more directories in sync, you will be able to without getting funny "unable to set permissions" errors. 

4. gid=46 sets the group ownership of the Capsule "mount" to the group "plugdev". At least, it does on my machine. 

5. The above is tested and validated for Jaunty [9.04]. There are some minor changes to be observed for Karmic [9.10]. If you are running Karmic, then you should use a variation of this string instead:

```
//192.168.1.40/TimeCapsule/user /media/capsule smbfs noserverino,nolinux,username=user,password=myP4ssw0rd,rw,iocharset=utf8,gid=46,file_mode=0770,dir_mode=0770 0 0
```

First, when performing my original ubuntu installation, I chose to manually partition my machine and used the opportunity to ask for some non-Linux partitions to be mounted into the /media tree. To make this example useful I've included samples of FAT32, NTFS and EXT4 partitions.

If you do this, you should see that the volumes are owned by a group called "plugdev". If you check the code, above, you will see that I've mounted all my non-native partitions with "gid=46", where 46 is the group id for "plugdev". I have also inserted the same parameter on the mount statement for the Time Capsule. **This is really important.**

If you set your Capsule to mount with the same "ownership" parameters as any non-Linux partitions (i.e. FAT32, NTFS) in your machine, it means that permissions of files and folders in any of these file systems will be applied in a single, consistent manner by the OS. This means that you can copy and move files between these files systems completely transparently. 

However, I have not yet been able to get the same level of consistency with native Linux partitions such as an ext4 environment. The challenge is that by default an ext3 or ext4 partition will inherit a different set of file permissions. I'm still working on that part, and I will post an amendment as/when I get that fixed.

---

### Post by peap on 2010-05-21
I'm using this fstab entry to successfully mount my TimeCapsule using Lucid server.

//10.0.1.1/TimeCapsule /media/timecapsule cifs password=password,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

