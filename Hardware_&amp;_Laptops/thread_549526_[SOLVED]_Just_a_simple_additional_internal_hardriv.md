---
title: "[SOLVED] Just a simple additional internal hardrive."
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by anyoneseenmypenguin on 2007-09-12
Just looking for a simple procedure to set up a internal hard drive  to use with Ubuntu 6.10. Nothing fancy no Windows just a backup hard drive to have more space for pictures or music or backups or whatever. I set the drive in the bios and it's detected I tried g parted to format and and when I fdisk -l the drive shows up but I cannot mount it . It does not show up in the etc/fstab either? I created a directory first one call "My backup" did not mount I thought maybe it was my choice of name so I created another directory call harddrive2 and it did not mount. I tried sudo mount -t ext3 /dev/hdb1/media/"My backup" and comes up with an explanation on how to use mount. I would like to delete the harddrive2 directory and use and mount the "My backup" directory. I think I have a problem with the syntax? Or do I have to manually add the new drive to the etc/fstab ????:confused:

---

### Post by meierfra on 2007-09-12
> sudo mount -t ext3  /dev/hdb1 /media/"My backup"  

This should work. Please note the  "space" between hdb1 and /media.
If  it does not work please  post the output of "sudo fdisk -l"

You need to edit your fstab,  if you  want hdb1  to mount  automatically at boot up.

---

### Post by anyoneseenmypenguin on 2007-09-12
Thanks for the reply I most probably missed the space. I do want the drive mounted automatically on boot up how do I manually configure the etc/fstab do I have to use the uuid #'s? if so how should the table look? Also don't you have to reboot after mounting the drive for it  to show up under the computer tab for browsing? :confused:

---

### Post by meierfra on 2007-09-12
Using the UUID is the recommended method.. You can find your UUID via

```
blkid 
```

Open the fstab via

```
gksudo gedit /etc/fstab
```

Add the line

UUID=your_UUID  /media/"My backup"   ext3        defaults     0      2

Save the file.

Then

```
sudo mount -a
```


You shouldn't have to reboot. But  if you can't access the partition, try rebooting  before you asked for more help.

---

### Post by anyoneseenmypenguin on 2007-09-12
Something is wrong when I try blkid the /dev/hdb1 does not show up here is my fdisk -l output

 sudo fdisk -l

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2405    19318131   83  Linux
/dev/hda2            2406        2498      747022+   5  Extended
/dev/hda5            2406        2498      746991   82  Linux swap / Solaris

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         784     6297448+  83  Linux
:(
Maybe I should start over again from the beginning with a blank hard drive and take it from there.

---

### Post by MobiusNZ on 2007-09-13
What's the output of ```
blkid
```?

---

### Post by meierfra on 2007-09-13
Did you try mounting  /dev/hdb1 in terminal?
and post any error message you get.

Instead of using the UUID,  you can use 

/dev/hdb1 /media/"My backup" ext3 defaults 0 2

in the fstab. For internal drives, that should not cause any problems.

And you might try sudo  in front of blkid

```
sudo blkid
```
and post the output ( even if hdb1 does not appear)

---

### Post by anyoneseenmypenguin on 2007-09-13
Yes sudo works here is the output for blkid

sudo blkid
Password:
/dev/hda1: UUID="65cd94f8-4143-4071-85fd-aa7da41bbf70" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="61ad3a19-1a29-4575-987b-ae980bf8920c" TYPE="swap" 
/dev/hdb1: UUID="754d602d-1df2-4dc6-b236-cb181d951712" SEC_TYPE="ext2" TYPE="ext3" 
:)

---

### Post by anyoneseenmypenguin on 2007-09-13
OK I got the hdb1 to mount using the storage device manager which was exstreamly easy. Now I see the drive but can't get access to it. Cannot create a folder or see the folder My Backup anywhere. I don't have permission? I would like to use this drive like my usb key to drag and drop files etc.:confused:

---

### Post by meierfra on 2007-09-14
Post the output of

```
cat /etc/fstab
```

and 

```
 ls -l /media 
```

---

### Post by anyoneseenmypenguin on 2007-09-14
Hey thanks for all the help all I did was change ownership  sudo chown -R username:username /media/hdb1 and everything works now. By the way the storage device manager tool is a great way for new users like myself to mount and configure new drives and get the job done. It was listed in the add remove programs list and easy too install.

---

