---
title: "How to put a program into boot process if program required password?"
date: 2008-08-21
forum: General Help
---

### Post by abcuser on 2008-08-21
Hi,
in Ubuntu 8.04 I would like to mount remote directory as local one. This is according to [Vivaldi Gloria suggestion](http://ubuntuforums.org/showpost.php?p=5619260&postcount=2) done the following way:
```
sudo sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
```

The above command works fine from command line. Command asks for sudo password on local computer and password on remote computer.

When adding above command to System | Preferences | Session to start up command at boot time - the command doesn't have effect. It is most probably because passwords are required.

How to automatically execute command/program at boot time?
Thanks,
Abcuser

---

### Post by Vivaldi Gloria on 2008-08-21
Hello again. :-)

First you have to enable passwordless key based ssh login.

In the client (desktop) machine create a key as follows:

```
ssh-keygen -t dsa
```

Enter empty password during the creation of the key. I believe that using only a key is secure enough. 

Now copy the key to the server machine using the following command in the client computer:

```
ssh-copy-id -i ~/.ssh/id_dsa.pub "-p <port_number> <user_name>@server_ip"
```

Note that if you use the default port 22 then this copy command becomes simpler:

```
ssh-copy-id -i ~/.ssh/id_dsa.pub <user_name>@server_ip
```

After this you should be able to ssh the server from the client without a password.

Once you have passwordless key based ssh you can add it to /etc/rc.local to start it automatically:

```
sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
exit 0

```

Actually, I prefer another way to automatically mount sshfs. I use two scripts. The first one mounts the sshfs volume when a network connection is available. The second one unmounts it when there is no connection. Hence you don't get errors when the connection is down. This is a better way then using /etc/rc.local. I'll write it below. Note that the below method also requires passwordless key based ssh login. So do the above steps first.

---

### Post by Vivaldi Gloria on 2008-08-21
There is already a guide to automatically mount sshfs here:

[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

The method below is adapted from that but it is a bit simpler. Read that thread anyway.

Before you start make sure that key based ssh login works and you can mount remote sshfs folders using the commandline.


**Part 1**

Add the following line to /etc/fstab:

```
sshfs#username@server:/home/username    /mnt/mountpoint    fuse    noauto,users,exec,uid=1000,gid=1000,port=portnumber,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0
```

Change the following parts of the above code according to your system:

username
server
/mnt/mountpoint
portnumber (delete "port=portnumber" if you use the default port)
learn your uid & gid by giving the command "id" - if you're the only user than they're 1000.

Now add the line

```
user_allow_other
```

to /etc/fuse.conf. Create this file if it doesn't exist.

**This ends part 1.** Restart system. Test that you can mount the sshfs volume using the command

```
mount /mnt/mountpoint
```

Note that there is no "sudo" before "mount". You can unmount it using the command

```
fusermount -u /mnt/mountpoint
```

If these work ok then proceed with part 2.

**Part 2**

Now we will create two scripts. The first one will mount the sshfs volume when a network connection is available. The second one will unmount it when there is no connection.

Create a file /etc/network/if-up.d/sshfs_mount containing the script

```
#!/bin/bash
sudo -u <username_client> sh -c "mount /mnt/mountpoint"
```

here <username_client> is your username in the client (desktop) system.

Create a file /etc/network/if-down.d/sshfs_unmount containing the script

```
#!/bin/bash
fusermount -u /mnt/mountpoint
```

Now make sure that these new files have the right owner & permissions:

```
sudo chmod 755 /etc/network/if-up.d/sshfs_mount
sudo chmod 755 /etc/network/if-down.d/sshfs_unmount
sudo chown root:root /etc/network/if-up.d/sshfs_mount
sudo chown root:root /etc/network/if-down.d/sshfs_unmount
```

Done. Restart. The sshfs volume should mount automatically when there is a connection.

---

