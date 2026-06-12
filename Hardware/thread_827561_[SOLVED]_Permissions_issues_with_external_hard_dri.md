---
title: "[SOLVED] Permissions issues with external hard drive"
date: 2008-06-12
forum: Hardware
---

### Post by marmaladeskies on 2008-06-12
I have a Seagate FreeAgent 320gb external hard drive.  I loaded files onto it from my xubuntu computer as well as from a windows computer, and was able to move files around, make folders, etc, in it until loading from the windows computer.  I just tried to add more files to it on xubuntu again, and I can't because it has read-only permissions.  When I right click and go to properties and permissions, it says owner: root, access read and write; group:  root, access read and write; others:  read and write.  If I try to get into it with sudo thunar& and sudo thunar and change the permission, it says I can't change it because it's set for read-only.  Please help me!  Also, I would like to fix this without losing the files on the external hard drive because there isn't room for them to be copied onto my computer.  Thanks a million in advance!

---

### Post by cdtech on 2008-06-12
You'll need to remount it to read/write:
sudo mount /dev/yourdev -o remount,rw

Hope that helps...

---

### Post by marmaladeskies on 2008-06-12
This is very stupid, but how do I find out what mydev's name is?

---

### Post by cdtech on 2008-06-12
just type sudo fdisk -l to list your devices.

---

### Post by marmaladeskies on 2008-06-13
That didn't work.  If I try to add files to the FreeAgent, it still says 

Failed to copy "/home/jr/Music/3" to "/media/FreeAgent Drive/3".  Failed to create directory "/media/FreeAgent Drive/3" (Read-only file system).  

Also, I don't know if this is related, but if I try to unmount it from the desktop, I get this:  

Unable to eject "FreeAgent Drive":  An unknown error occured.

 Any more ideas?  I'd appreciate any help I can get.

---

### Post by marmaladeskies on 2008-06-13
I would appreciate any help anyone could lend.  If the problem can't be fixed, I'll have to return the drive to the store soon.  Thanks in advance

---

### Post by cdtech on 2008-06-13
Ok marmaladeskies, while your on your Ubuntu desktop, type sudo fdisk -l (with the external drive attached) and lets see the output.

You should get a listing of all the drives that Ubuntu see's.

Also, I'm thinking that if you removed the drive from Window's without safely removing via Window's, you may need to run 'ntfsfix' on your Ubuntu box which will reset the NTFS journal.

Just a couple of suggestions.....

---

### Post by Odrodzona-Sarmacja on 2008-06-15
open terminal
-sudo blkid
(gives you list of your partitions)
-mount
(gives you list of your mounted partitions)

open second terminal
-sudo nano /etc/fstab
(to save ctrl-o, to exit ctrl-x)

Fix entry in fstab for you harddrive to something like
/dev/<device is in "-sudo blkid">  /media/<name of your choice>
vfat  rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000  0  0
(partition can be like ntfs,ext3,vfat)

-sudo mkdir /media/<name of your choice>
(-sudo umount <former mount point, you have that in "-mount">)
-sudo mount -a

ENJOY!

---

### Post by marmaladeskies on 2008-06-15
> Fix entry in fstab for you harddrive to something like
/dev/<device is in "-sudo blkid"> /media/<name of your choice>
vfat rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,u id=1000 0 0
(partition can be like ntfs,ext3,vfat)

When you say "harddrive" do you mean my regular hard drive or my external FreeAgent one?  Because I don't think the FreeAgent one (sdb1) is even there, just my regular harddrive, swap, and scd0.  What should I do?  Should I add something via sudo mousepad /etc/fstab?  Thanks

---

### Post by Odrodzona-Sarmacja on 2008-06-16
> **marmaladeskies said:**
> When you say "harddrive" do you mean my regular hard drive or my external FreeAgent one?  Because I don't think the FreeAgent one (sdb1) is even there, just my regular harddrive, swap, and scd0.  What should I do?  Should I add something via sudo mousepad /etc/fstab?  Thanks

I mean all your harddrives with freeagent included.
Make sure your freeagent drive is disconnected.
Then go to terminal and create directory "sudo mkdir /media/FreeAgentDrive"
In terminal run "gksudo mousepad /etc/fstab" (gives you mousepad with root access)
In fstab set new single line with
"/dev/sdb1 /media/FreeAgentDrive vfat
rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,u id=1000  0  0"
If your free agent is ntfs then change vfat to ntfs.

Reconect Freeagent and let it mount. Then go to terminal and type "sudo mount -a", which mounts all hds (freeagent including) in fstab according to your own specifications. Now you can read and write to it on your user account too. If you start up computer with Freeagent connected, then you don't have to run "sudo mount -a". It is automounted correctly to your wishes during bootup.

:)

---

### Post by marmaladeskies on 2008-06-16
I fixed the stuff in fstab but now for some reason my drive refuses to mount 
"Unable to mount "FreeAgent Drive":
mount: only root can mount /dev/sdc1 on /media/FreeAgent/mydrive"

So doing sudo mount -a results in:

mount: mount point /media/FreeAgent/mydrive does not exist
mount: mount point id=1000 does not exist

(I made the drive mydrive by the way)

So, where do I go from here?  Thanks a million by the way - I feel like I'm really, really close, but this drive won't mount..  I'm pretty new to xubuntu by the way which may explain my confusion

---

### Post by Odrodzona-Sarmacja on 2008-06-17
> **marmaladeskies said:**
> 
So doing sudo mount -a results in:

mount: mount point /media/FreeAgent/mydrive does not exist
mount: mount point id=1000 does not exist

(I made the drive mydrive by the way)


You must make sure this directory exists before mounting hard drive to it.
"sudo mkdir /media/mydrive" and changing in fstab from "/media/FreeAgent/mydrive" to "/media/mydrive" should fix this issue. then run "sudo mount -a" and you should have your hd accessible without much problem.

---

### Post by marmaladeskies on 2008-06-17
> You must make sure this directory exists before mounting hard drive to it.
"sudo mkdir /media/mydrive" and changing in fstab from "/media/FreeAgent/mydrive" to "/media/mydrive" should fix this issue. then run "sudo mount -a" and you should have your hd accessible without much problem.

Ok, I did that.  The only problem that remains is the mount point.

jr@tosh:~$ sudo mount -a
mount: mount point id=1000 does not exist


Almost there!  Again, thanks so much

---

### Post by Odrodzona-Sarmacja on 2008-06-17
"/media/mydrive" is the mount point.
"sudo mkdir /media/mydrive" creates that mount point.
It should be there already.

---

### Post by marmaladeskies on 2008-06-17
AWESOME.  you are my savior.  it's working perfectly.  you saved me a huge amount of time, money, and files.  you're the best!  the best of luck to you skillfully helping out scrubs like me, haha!

---

