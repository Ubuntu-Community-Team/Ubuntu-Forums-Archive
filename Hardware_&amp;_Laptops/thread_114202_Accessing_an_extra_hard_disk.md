---
title: "Accessing an extra hard disk"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by casperlingus on 2006-01-08
Okay, I'm not a newb to linux or Ubuntu, but for some reason I just cannot find the answer I'm looking for.  I am hoping someone can just clear this up simply for me.  I apologize if this has been answered somewhere else.  

I have 3 HDDs in my computer.  Only the partition with Ubuntu on it is mounted at boot, along with some Windows partitions.

What I am looking for is to use one of my other hard drives as storage.  In otherwords, I want user casper to have unrestricted read/write access to a one of the ext3 partitions and one of the vfat partitions.  

Specifically, I have Ubuntu on one harddrive, and Gentoo on another harddrive, and I want to be able to share a VMware virtual machine (common Windows emulation) between the two of them.  

Additionally, I want to transfer files back and forth from Ubuntu-Gentoo without have to su/sudo every time.  I've tried all sorts of fstab options and attempting to change folder permissions, but so far I have had no luck.  

Can someone give me some fstab/mount options and/or permissions operations which I can use to accomplish this during boot?

Casper...

---

### Post by casperlingus on 2006-01-11
bump...?

---

### Post by darrenc on 2006-01-12
[QUOTE=casperlingus]
What I am looking for is to use one of my other hard drives as storage.  In otherwords, I want user casper to have unrestricted read/write access to a one of the ext3 partitions and one of the vfat partitions.  

Can someone give me some fstab/mount options and/or permissions operations which I can use to accomplish this during boot?
[/QUOTE]

Don't know if it will fix it for you, but I mount a separate vfat partition on my primary drive and a second harddrive (ext3) with gentoo at Ubuntu boot with fstab.

For the windows partition, this is the line from my fstab file:

/dev/hda8   /mnt/win_f   vfat   umask=0,iocharset=iso8859-15,codepage=850   0   0


And for the second harddrive with gentoo, I mount it with this line:

/dev/hdd3   /mnt/gentoo   ext3   rw   0   0


This gives me unrestricted read/write and file and folder ownership.

---

### Post by fredfredfred on 2008-02-08
I was having similar difficulties and had played with fstab and file permissions throught root.  I finally got around to finding sda1, sda2, sdb1 etc type stuff in the /dev directory.  Once I changed the permissions here I was in!!

---

### Post by casperlingus on 2008-02-29
It's funny finding posts I wrote two years ago, and realizing how much I've learned since then.  I can now answer my own question.

> I was having similar difficulties and had played with fstab and file permissions throught root. I finally got around to finding sda1, sda2, sdb1 etc type stuff in the /dev directory. Once I changed the permissions here I was in!!

Your solution of changing permissions in the /dev dir is a security issue.  You should never change the permissions directly on the devices.

Although I don't have the exact fstab entries, I can explain what is so confusing about this.  It has to do with the fact that vfat and ext3 both have different "styles" for mounting. 

**EXT3**:  I don't have an ext3 system to test this on, but I seem to remember that the key to mounting ext3 was to change the owner and the permissions of the mount point folder BEFORE mounting, and it will preserve these permissions after mounting (replacing 755 with your desired permissions, casper:casper with username:group):

```

sudo chmod 755 /media/ext3MountPoint
sudo chown casper:casper /media/ext3MountPoint
sudo mount -t ext3 /dev/sda1 /media/ext3MountPoint

```



**VFAT**:  if you try to do a standard mount of a vfat drive (mount -t vfat /dev/sda1 /media/vfatMountPoint), the mount point is automatically owned by root (regardless of what it was before) and a standard user will not have write access to it.  Therefore, you need to make a specification in the mount command as to it's permissions/owners.  Two ways to do this:  specify uid/gid:

```
sudo mount -t vfat /dev/sdb1 /media/externalHDD/ -o uid=1000,gid=1000
```

Where 1000 refers to my user ID number and gid refers to my group ID number which can be observed with the following command:

```
casper@casper:~$ **grep casper /etc/passwd**
casper:x:1000:1000:Joe Schmoe,,,:/home/casper:/bin/bash

```
The third item is your uid, the fourth one is your primary group, gid.  If you're the only that uses your computer, you uid/gid is probably 1000/1000 (replace casper with your usename).  But uid/gid doesn't work if you have multiple users that want to access the drive.  The alternative is to set the permissions of the drive using the umask option:

```
sudo mount -t vfat /dev/sdb1 /media/externalHDD/ -o umask=000
```

Where the 000 is the compliment mask for the normal permissions string, so this example mounts the drive with rwxrwxrwx (same as "chmod 777" -- learn more about _[file permissions]("http://http://snap.nlc.dcccd.edu/learn/madden/intro/perms.html")_).   I know, it's weird.  As another example, the following two commands both produce the same permsions, rwxr-xr-x:

```
chmod 755 aRandomFileOrDirectory
sudo mount -t vfat /dev/sdb1 /media/vfatMountPoint -o umask=022
```

So we can combine the two concepts to offer fine-tuned control over this particular vfat drive for a variety of users.  Simply put all the users into a particular group, and then mount the drive as 
```
sudo mount -t vfat /dev/sdb1 /media/externalHDD/ -o gid=1002,umask=007
```

Which will give all users in the group with gid=1002 read-write access to everything on the drive, and anyone not in the group, no access whatsoever  (umask=003 to give others the ability to read the drive, but not write to it).

---

