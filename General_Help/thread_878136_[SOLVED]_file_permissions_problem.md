---
title: "[SOLVED] file permissions problem"
date: 2008-08-02
forum: General Help
---

### Post by wolfen69 on 2008-08-02
thanks to the great help on here, i finally got my ext3 partitions up and running. now i have a new problem. i've added folders containing mp3's to my music partition. but now, after i copy over the folders, they have a lock symbol over them. i tried:  ```
sudo chown -R ed:ed /media/music/*
``` but the lock symbols are still there. is that the right command? do i have to reboot first?

---

### Post by rEbyTer on 2008-08-02
This problem is irritating me sometimes and with **chown** i couldn't solve it.
As i am reading the man pages, maybe **chmod** will solve this.

[Here](http://www.ss64.com/bash/chown.html) is the **chown MAN page**, and [here](http://www.ss64.com/bash/chmod.html), the **chmod MAN page**.

Maybe you'll get it to work with **chmod** by settings at least read permissions to **Others**.

Tell me if that works. Now i'm reading man pages to solve this.

---

### Post by silkstone on 2008-08-02
Yes, or just unmount and remount the drive/partition. 

sudo umount /media/music
sudo mount /media/music

That's assuming the mount point is correct!

EDIT/ You don't need the * in the chown command. The -R is recursive so it changes the ownership of everything on the partition.

sudo chown -R ed:ed /media/music

---

### Post by rEbyTer on 2008-08-02
Thank you, silkstone. It works!

---

### Post by Elfy on 2008-08-02
sudo chown user.users /mount/point
sudo chmod 770 /mount/point/

Is what I've used to get the permissions

---

### Post by linfidel on 2008-08-02
Wouldn't it have been better to mount this somewhere in the home directory?  I have a separate drive mounted as ~/media, and I don't think there were any problems at all, since I am the owner of my home directory.

---

### Post by linfidel on 2008-08-02
> **forestpixie said:**
> sudo chown user.users /mount/point
sudo chmod 770 /mount/point/

Is what I've used to get the permissionsThat makes all the files executable, though.  A more reasonable value would be 664, which makes it R/W for user and group, and read-only by everyone else.
R  W   X
4   2   1
\   /
  6 = R + W
  7 = R + W + X (execute)
  etc.

---

### Post by Elfy on 2008-08-02
thanks I get confused with the numbers - I still have 770 in my media folders though

---

### Post by silkstone on 2008-08-02
@ linfidel - The problem is that you normally use gparted as root - it's under System > Administration and you enter your password to start it.

That means that root is the owner of any new Ext3 (or Ext2) partitions you create, so you then have to change the ownership and permissions. I don't think that mounting in your home folder would help there.

---

### Post by Elfy on 2008-08-02
> @ linfidel - The problem is that you normally use gparted as root - it's under System > Administration and you enter your password to start it. I use partedmagic as a livecd ;)

---

### Post by rEbyTer on 2008-08-02
> The problem is that you normally use gparted as root - it's under System > Administration and you enter your password to start it.

with gksudo will work ? sometimes i have to run gparted from terminal because it's a fast way to start it...

also with cfdisk will be the same problem ?

---

### Post by wolfen69 on 2008-08-02
the folders containing the mp3's were on cd. why would it lock the folders? chown did not work.

---

### Post by rEbyTer on 2008-08-02
Maybe because you copied them on HDD with root permissions for example:

You open nautilus with **gksudo nautilus** and copy your music to HDD. and then when you use nautilus as normal user you may have problems with permissions.

I have the same problems sometimes.

---

### Post by wolfen69 on 2008-08-02
> **rEbyTer said:**
> Maybe because you copied them on HDD with root permissions for example:

You open nautilus with **gksudo nautilus** and copy your music to HDD. and then when you use nautilus as normal user you may have problems with permissions.

I have the same problems sometimes.

i did not do that. i believe most of the mp3's were done on a windows machine.

---

### Post by silkstone on 2008-08-02
@ linfidel: Aha! All is explained :)

---

### Post by silkstone on 2008-08-02
> **wolfen69 said:**
> the folders containing the mp3's were on cd. why would it lock the folders? chown did not work.

Windows filesystems (NTFS and FAT32) do not recognise permissions. If you look at the ownership of a FAT32 drive, it will probably say 'root' - but really that means 'no ownership'. You cannot change ownership and permissions on Windows filesystems (as far as I know!).

If you then copy those files to a Linux partition currently owned by root, I believe that they will take on the same ownership as that partition.

If you now own the new partition, files copied there should be yours.

---

### Post by linfidel on 2008-08-02
> **silkstone said:**
> @ linfidel - The problem is that you normally use gparted as root - it's under System > Administration and you enter your password to start it.

That means that root is the owner of any new Ext3 (or Ext2) partitions you create, so you then have to change the ownership and permissions. I don't think that mounting in your home folder would help there.
Normally?  Always is more like it.  It won't run as normal user.  It displays a dialog saying "Root privileges are required for running GParted".  :-)

I probably did the chown without thinking about it at the time.  But it still seems like the /home directory is a better place to mount something like that.

---

### Post by geirha on 2008-08-02
Files on CDs do not have the write-bit set (since you can't edit files on a CD). When you copy them, they inherit the same bits as they had on the CD, thus they all lack write-permission. ```
chmod -R ug+w /media/music
``` should give (u)ser and (g)roup owner of those files write access. You set yourself as the owner of the files with sudo chown earlier, so that means you will get the write access. (Also since you own the files, you don't need to have sudo infront of chmod)

---

### Post by wolfen69 on 2008-08-02
> **geirha said:**
> Files on CDs do not have the write-bit set (since you can't edit files on a CD). When you copy them, they inherit the same bits as they had on the CD, thus they all lack write-permission. ```
chmod -R ug+w /media/music
``` should give (u)ser and (g)roup owner of those files write access. You set yourself as the owner of the files with sudo chown earlier, so that means you will get the write access. (Also since you own the files, you don't need to have sudo infront of chmod)

that worked! thank you very much. these forums are the best. :guitar:

---

