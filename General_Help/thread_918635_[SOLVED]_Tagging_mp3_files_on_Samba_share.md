---
title: "[SOLVED] Tagging mp3 files on Samba share"
date: 2008-09-13
forum: General Help
---

### Post by graabein on 2008-09-13
Hi, I've got a file server running with no GUI. My main box is running Ubuntu 8.04 and Windows XP and can connect with ssh and Samba. I can connect through Nautilus and copy over music and everything, but how do I run mp3 tagging programs like **Ex Falso** locally and edit tags on the server? Anyone have an idea?

---

### Post by gvartser on 2008-09-13
mount the samba share and then edit the mp3 tags.

```
sudo mount -t smbfs -o username=<RemoteUserName>,password=<RemotePassword>,uid=<YourLoginNameUbuntu>,gid=<YourGroupNameUbuntu> //<server_name>/<share_name> /<path>/<to>/<local>/<mount>/point>
```


_Example: _
You want to mount "//server1/music" share onto your local ubuntu machine in the folder "/mnt/music" as the remote USER1 user, giving ownership to your ubuntu account "kalle":
```
sudo mount -t smbfs -o username=USER1,password=SomePass,uid=kalle,gid=kalle //server1/music /mnt/music
```

Best regz,
/g

---

### Post by graabein on 2008-09-15
Can I put the mount command in a script for each user? What scripts are run on login again? .bashrc? 

And can I do it in the background without having to input sudo password?



Update: Tried with the -t smbfs and got **smbfs: mount_data version 1919251317 is not supported**

---

### Post by graabein on 2008-09-16
I found some info on [this site]("http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html") saying I should use *-t cifs* instead of *smbfs*. Going to try it later tonight. 

```
# mount -t cifs //ntserver/download -o username=u,password=p /mnt/ntserver
```

---

### Post by graabein on 2008-09-16
No biscuit. 

```
**$ mount -t cifs ...** 
mount: wrong fs type, bad option, bad superblock on //ntserver/download,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
**$ dmesg | tail**
CIFS VFS: cifs_mount failed w/return code = -22
```

---

### Post by niteshifter on 2008-09-16
Hi,

Not Samba, smbfs and smbclient are needed. Available in the repos. 

Example mount:
```
sudo smbmount //nsu01/SomeShare /mnt/nas -o username=JoeBob,password=abcd,uid=joeb,gid=joeb
```

```
//nsu01/SomeShare  =  accesses the share SomeShare on machine nsu01
/mnt/nas           =  the mount point in the _local filesystem_
-o                 =  options:
username=JoeBob    =  JoeBob is the user of the above share
password=abcd      =  JoeBob's password for the share
uid=joeb,gid=joeb  =  JoeBob is joeb on the local machine, sets owner:group
                      on the local file system mount.

```

The one-liner shown above is a sanitized version of the script I use on my system(s). My music lib is on a NAS, I needed to do much the same as you, edit tags on mp3's (via EasyTag). Worked well.

---

### Post by graabein on 2008-09-21
Thanks! I tried it but got a permission error.

```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

Guess I have to log on to the server and set the proper user and group permissions on the share, right?

---

### Post by graabein on 2008-09-24
Allright, I got it to mount manually at least. I want it to automount on boot but this will do for now.

```
$ sudo /sbin/mount.cifs //ntserver/share /mnt/ntshare -o user=john,pass=johnspassword
```

---

