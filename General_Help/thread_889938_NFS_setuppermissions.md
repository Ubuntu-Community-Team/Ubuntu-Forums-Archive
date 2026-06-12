---
title: "NFS setup/permissions"
date: 2008-08-14
forum: General Help
---

### Post by MemoryDump on 2008-08-14
(I decided to move this post here as I'm not sure where it should go.. perhaps software)

hey all,

I have 2 linux boxes. 1 is my workstation (chaos) and my other is my fileserver (crash).

I have a drive on my fileserver (crash) mounted as /goodstuff owned by "root" and the group "goodstuff". 
The permissions on the /goodstuff folder are 775 (drwxrwxr-x). 
Now on this box I have a user named "memdmp" and belongs to the "goodstuff" group. 
I have an export for this folder setup as:
```
/goodstuff      192.168.30.1/255.255.255.0(async,anongid=1002,no_root_squash,rw)
```
now on my workstation (chaos) I have an fstab entry to mount this export:```

crash:/goodstuff  /goodstuff  nfs  user,dev,rsize=8192,timeo=14,wsize=8192,intr,suid,exec  0  0
```
I even made sure that the the group "goodstuff" has the same ID on both machines.
```
goodstuff:x:1002:memdmp
```

So now the problem.. which is odd.. I can mount the drive, however I can only read it's contents. I can't write/create/delete/etc even though it's owned by root:goodstuff and it's permissions are set to 775 (drwxrwxr-x) on both chaos and crash.

any ideas?
Thanks
-MD

---

### Post by MemoryDump on 2008-08-15
bump! anybody :(

---

### Post by MemoryDump on 2008-08-18
> **MemoryDump said:**
> bump! anybody :(

nobody here uses NFS?

---

### Post by ilrudie on 2008-08-18
Are you logged in as or su 'd to the memdmp user or is the user you are logged in as a member of the goodstuff group?

Also if you are a member of more than 16 groups on the client pc you may have issues (see security considerations in the man pages for nfs).  Maybe you should try chowning the directory to be owned by your primary group.  Also I'm not sure if it would make a difference but you could try adding the rw flag to your fstab entry.

try ```
grep -c <username> /etc/group
```to see if too many groups could be your problem.

---

### Post by fragos on 2008-08-18
Here's what works for me.

In this example I will setup my laptop as server and mount on my desktop. I've chosen to to manually mount for security reasons. Both systems have the same user name "user" and the desktop hostname is "Desk" and laptop with hostname "Laptop".

NFS server (laptop), create /etc/exports with following line with folder to be shared "/home/user" and host allowed access "Desk.local(rw)". When ever you boot the laptop this NFS connection is automatically setup. After editing /etc/exports you may run "sudo exportfs -rv" to make changes active without a reboot.

/home/user Desk.local(rw)

On the desktop client create directory "/home/user/Laptop". To mount run "sudo mount Laptop.local:/home/user Laptop" with folder on Laptop to be shared "Laptop.local:/home/user" and mount point "Laptop".

---

