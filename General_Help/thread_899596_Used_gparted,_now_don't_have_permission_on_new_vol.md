---
title: "Used gparted, now don't have permission on new volume"
date: 2008-08-24
forum: General Help
---

### Post by terry123b99 on 2008-08-24
Just as title says, used gparted to shrink my 250gb hdd in half and have two partitions. Filesystem partition is fine, but I have tried creating a folder on my new partition and I get permission denied?

Any ideas?

---

### Post by drs305 on 2008-08-24
> **terry123b99 said:**
> Just as title says, used gparted to shrink my 250gb hdd in half and have two partitions. Filesystem partition is fine, but I have tried creating a folder on my new partition and I get permission denied?

Any ideas?

You probably haven't set the permissions on the folder yet so it is still owned by root. Run these to set ownership and permissions:
```

sudo chown -R yourusername /path/foldername
chmod -R 755 /path/foldername

```

Mode 755 lets you read/write/execute and groups/others read and execute but not write.

---

### Post by terry123b99 on 2008-08-24
Just tried that m8, no luck. Here is the error when moving the folder.

> 
The folder "Perl" cannot be copied because you do not have permissions to create it in the destination.

btw the destination is my newly created partition.

---

### Post by Too Late on 2008-08-24
Please post the command you actually wrote. I'm sure it should work. Here it is, again:
```
sudo chown -R terry: /mnt/stuff
```
Now I'm assuming that terry is your username and the mounting point of that partition is /mnt/stuff.

(A colon after your username changes the group.)

---

### Post by Elfy on 2008-08-24
Did you make a folder for it to mount in?

I assume you are going to want to use the partition all the time, why don't you add it to the fstab so that it mounts automatically.

Run these commands to get the necessary information -
```
sudo fdisk -l
sudo blkid
```

Make a directory for it to mount - I'll use name - change to suit in both the mkdir and fstab

```
sudo mkdir /mnt/name
gksudo gedit /etc/fstab
```

To edit the file you need the UUID for the new partition which blkid gave you, add this line to the end of the fstab file

> UUID=changetouuidfromblkid /mnt/name ext3 user 0 2

Save the file and then run
```
sudo mount -a
```

That should return with no output, if not there is an error

After that use the commands drs305 gave replacing /path/foldername with /mnt/name

---

### Post by drs305 on 2008-08-24
> **terry123b99 said:**
> Just tried that m8, no luck. Here is the error when moving the folder.


btw the destination is my newly created partition.

I may have put the cart before the horse. I usually make a distinction between mount points and other folders. To put something into the partition, you are going to have to own the mountpoint. The command is the same, but you don't use the folder name but the mountpoint name. So if you are trying to put a folder in /media/myfolder, you would run:
```
sudo chown -R username /media/myfolder
```

At that point you can put anything you want into myfolder, assuming you have made the mountpoint *myfolder*.

---

### Post by reatile on 2009-08-31
A quick heads up. 

the following command line did not work for me
 [code] sudo chown -R username /media/your-partition [code] 

but the following did 
  [code] sudo chown -R username: /media/your-partition [code]

Take note of the colon after the the username. 

Who knew take ownership you just have to type a colon.  :)

---

### Post by drs305 on 2009-08-31
The colon is a 'shortcut' for adding the group ownership. 

**chown -R *username*** would make *username* the owner. The group would remain assigned to whatever it was previously.

**chown -R *username:*** is the same as *username:username*, which changes the owner and group to *username*

---

