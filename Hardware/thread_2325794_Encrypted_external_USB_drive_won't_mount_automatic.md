---
title: "Encrypted external USB drive won't mount automatically"
date: 2016-05-25
forum: Hardware
---

### Post by bradhaack on 2016-05-25
I have an encryped external USB drive that I use for rsnapshot backups, so I'd like to mount it automatically.   
My fstab entry did look like this, but it would hang at boot, saying that the disk drive is not ready...  press s to skip..., even though the drive was plugged in and turned on.
/dev/mapper/luks-3bddbc2d-6432-46df-9851-c86e15478ded /media/Maxtor1  ext4  defaults 0   2
mount -a would mount it. 

I changed it to this, so it doesn't hang the boot
/dev/mapper/luks-3bddbc2d-6432-46df-9851-c86e15478ded /media/Maxtor1  ext4  nobootwait 0   2

mount -a still works, but I would like to get it to boot automatically.

Edit:
I just added to fstab
/dev/mapper/luks-3bddbc2d-6432-46df-9851-c86e15478ded /media/Maxtor1  ext4  nobootwait,rw,suid,dev,exec,auto,user,async 0   2

Now mount -a failed,
mount: special device /dev/mapper/luks-3bddbc2d-6432-46df-9851-c86e15478ded does not exist

But, it still mounted, when I clicked the file system in the GUI is was there.

---

### Post by TheFu on 2016-05-26
Is the cryptab correct?  How is the disk encrypted?  encfs, encryptfs, dm-crypt?  What exact command was created to make the encrypted partition?  Is LVM involved?

Don't trust what the GUI shows when it comes to mounts.  Use the 
* mount
* df
commands.

---

### Post by bradhaack on 2016-05-26
> **TheFu said:**
> Is the cryptab correct?  How is the disk encrypted?  encfs, encryptfs, dm-crypt?  What exact command was created to make the encrypted partition?  Is LVM involved?

Don't trust what the GUI shows when it comes to mounts.  Use the 
* mount
* df
commands.

If my notes are correct, I encrypted it this way:
```
sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4
sudo chmod 0400 /root/keyfile
cryptsetup luksAddKey /dev/sdb1 /root/keyfile
```
I don't think LVM is involved.   It mounts manually, verified with df, and writing to the disk.

---

### Post by TheFu on 2016-05-26
Those aren't the correct or enough steps to get an encrypted file system working.

[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage) says you needed to use luksFormat to initialize the storage and set the initial passphrase/keyfile. 

Then a file system must be created inside the encrypted storage - sudo mkfs -t ext4 .... 

luksAddKey is how to add more passwords/keys for any Luks encrypted device - think there are 8 slots.  There is a changeKey option too.

To mount portable devices, I manually use 
```
sudo cryptsetup luksOpen
``` to open the partition and because I use LVM, I have to do some other steps to mount each LV which don't matter to you.  Always have to look up the device after each reboot. Don't think there is a UUID way, but I could be mistaken.

Did a little searching and found this: [https://askubuntu.com/questions/450895/mount-luks-encrypted-hard-drive-at-boot](https://askubuntu.com/questions/450895/mount-luks-encrypted-hard-drive-at-boot) - don't know whether that works correctly or not. There are a few tidbits about the order for mounting things and specific mount options. Also don't forget the initiramfs parts.

Hope this provides some leads that are useful.

---

### Post by bradhaack on 2016-05-27
Thanks.   Yea, I used the GUI  disk utility (disks).  It must have done that stuff for me.   Maybe I shouldn't have it mounted at boot, but when I login.  I can live with it as is for now.

---

### Post by TheFu on 2016-05-27
I have never used "disks" and don't know anything about it.

---

