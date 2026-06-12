---
title: "Browsing remote folders"
date: 2008-08-19
forum: General Help
---

### Post by Nonno Bassotto on 2008-08-19
With Ubuntu up to Gutsy Gibbon I was able to have links on my desktop to remote folders via ssh or ftp. This was a major feature of linux over windows for me: I could just forget the difference between local and remote folders and upload files seamlessly to, for instance, my website.

With Hardy there has been a transition from Gnome-VFS to GVFS and I'm not able to do this anymore. I can have the links under the places menu but:
1) I cannot keep the resource mounted on my desktop
2) I cannot decide the name of the remote folder when it is mounted
3) The mounted folder always points to the root of the remote filesystem.

I could not appreciate the advantages of GVFS ovr Gnome-VFS, but this has been a regression for me. Is there a way to restore the old beahviour?

---

### Post by Vivaldi Gloria on 2008-08-19
I use sshfs to mount a remote directory as a local one. I use the command

```
sudo sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
```

Now the remote directory becomes no different than a regular local directory. 

Actually I have a sshfs line in fstab which mounts it automatically but that's another story.

---

### Post by Nonno Bassotto on 2008-08-19
This seems to be what I'm looking for, thank you :)

I just have a couple more questions. How do you add it to /etc/fstab, so you don't have to manually mount it each time? If I do so, can I specify the password just when I open it?

---

### Post by Vivaldi Gloria on 2008-08-19
Adding sshfs to fstab works if you have passwordless key based ssh login.

In the client (desktop) machine create a key as follows:

```
ssh-keygen -t dsa
```

Enter empty password during the creation of the key. I believe that the key is secure enough. 

Now copy the key to the server machine using the following command in the client computer:

```
ssh-copy-id -i ~/.ssh/id_dsa.pub "-p <port_number> <user_name>@server_ip"
```

Note that if you use the default pot 22 then this copy command becomes simpler:

```
ssh-copy-id -i ~/.ssh/id_dsa.pub <user_name>@server_ip
```

After this you should be able to ssh the server from the client without a password.

For more info see:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Once you have key based ssh you can add it to fstab. I'll write howto in the below post.

Edit: See also [http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856)

---

### Post by Vivaldi Gloria on 2008-08-19
There is already a guide to automatically mount sshfs here:

[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

First read it then read my method below which is a bit simpler. 

Before you start make sure that key based ssh login works and you can mount remote sshfs folders using the commandline.


**Part 1**

Add the following line to fstab:

```
sshfs#username@server:/home/username    /mnt/mountpoint    fuse    noauto,users,exec,uid=1000,gid=1000,port=portnumber,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0
```

Change the following parts of the above code according to your system:

username
server
/mnt/mountpoint
portnumber (delete "port=portnumber" if you use the default port)
learn your uid & gid by giving the command "id" 

Now add the line

```
user_allow_other
```

to /etc/fuse.conf. Create this file if it doesn't exist.

This ends part 1. Restart system. Test that you can mount the sshfs volume using the command

```
mount /mnt/mountpoint
```

You can unmount it using the command

```
fusermount -u /mnt/mountpoint
```


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

Of course you can symlink /mnt/mountpoint to anywhere you want and you can add it to my places.

---

### Post by HermanAB on 2008-08-19
I use Konqueror and make bookmarks to whatever I frequently connect to, for example "sftp://whoever@server/wherever". The Gnome Nautilus file browser can do the same, but in practice it is more difficult to use than Konq.

Cheers,

Herman

---

### Post by itpaul on 2008-09-12
As far as I'm concerned, this is all besides the point. I've tried SSHFS and I don't like it. It's too slow.

Nautilus should be working but it isn't anymore thanks to "upgrades".


```
Couldn't display "ssh://root@mydomain.com".
Nautilus cannot handle ssh: locations.
```

I did downgrade GVFS and held it which was working until today when my system decided to do a rather large upgrade which destroyed my fix, despite the version being held.

I for one am extremely pissed off about this. It pretty much destroys my workflow. I've got better things to do than test Ubuntu's software for them. 

Sorry for ranting here but I'm not sure where I should.

Can anybody shed any light on this problem? Is there a proper fix - NOT an alternative like SSHFS? Should I report a bug or something?

In the mean time I shall be reviewing other distributions looking for this functionality.

Yours sincerley

A pissed user

---

