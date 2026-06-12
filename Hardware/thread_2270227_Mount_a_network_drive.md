---
title: "Mount a network drive"
date: 2015-03-21
forum: Hardware
---

### Post by bill-lancaster on 2015-03-21
I always struggle mounting devices and have done much googling.
I have a device (Arduino Yun) logging temperature to an on board sd card.
I can access the log file through ssh like this:-
#:ssh -l root 192.168.1.11
pw = xxxxx
#:cd /mnt/sda1
#:cat datalog.txt        (dumps file contents to terminal)

How can I mount this folder?

Kubuntu 14.04

---

### Post by SeijiSensei on 2015-03-21
Is this device on a different machine from yours?  If so, you'll have to configure that machine to export the directory with NFS or CIFS.  If both machines run Linux, NFS is the best choice: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo).  On the client, you need to install the **nfs-common** package.  Then you can mount the device in /etc/fstab with an entry like this:
```
192.168.1.11:/mnt/sda1 /media/arduino nfs defaults 0 0
```
after creating the "mount point" directory, /media/arduino.  Make sure that /mnt/sda1 has 755 permissions on the Arduino device so you can browse it and read the file as a non-root user.

---

### Post by bill-lancaster on 2015-03-23
Thanks for the help.
Despite the information and links provided I'm finding it quite a challenge.
Using scp I can easily download the file to my local drive without too much trouble and since the file is needed only once or twice a day, it's no problem.
Thanks again

---

### Post by SeijiSensei on 2015-03-23
Since you can use SCP, try mounting the share with **sshfs** instead.
```

sudo apt-get install sshfs
sshfs server:/home/bill /mount/point
ls /mount/point

```
The ls command should now list the contents of /home/bill.

I mount some shares with sshfs via an entry in /etc/rc.local like this:
```
sshfs -o uid=505,gid=500,allow_other,nonempty user@server:/some/share  /mount/point
```
Because this command runs as root, I use the uid and gid options to set the ownership of the mounted directory to the user that owns the files on the remote system.  "Allow_other" lets other users besides the one mounting the directory to access the files with the usual permission checks.

You can mount sshfs filesystems via /etc/fstab, but I find it simpler to use the sshfs command in rc.local.

To make this work seamlessly, you'll need to set up "[keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)."

---

### Post by bill-lancaster on 2015-04-14
Have got around to trying your sugestion to use sshfs.
1) Installed sshfs ok
2) Created directory /mnt/remote
3) Changed permissions: $ sudo chown bill /mnt/remote/
4) Ran $ sshfs server:/home/bill /mnt/remote
    result: "read: Connection reset by peer"
5) Tried $ sshfs -o -p alex2304 uid=505,gid=500,allow_other,nonempty root@192.168.1.12:/mnt/sda1  /mnt/remote
     but got "fuse: bad mount point `uid=505,gid=500,allow_other,nonempty': No such file or directory"
     The remote device (an Arduino Yun microprocessor with SD card) requires a password for access so I tried
6) $ sshfs -o -p password  root@192.168.1.12:/mnt/sda1  /mnt/remote
    and got "read: Connection reset by peer"

Didn't really knowing what I was doing and now don't really know what I've done!

Any ideas?

Also thanks for the help so far

Bill

---

