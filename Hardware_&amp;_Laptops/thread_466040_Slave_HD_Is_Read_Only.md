---
title: "Slave HD Is Read Only"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by Incarnadine on 2007-06-06
I just recently added a slave HD to my computer (Ubuntu 7.04) that was previously the slave HD to another WIndows XP computer. Ubuntu can read the HD just fine and there are no problems there. It's just that the HD is locked. It says I'm not the owner and I can't delete or add anything to it. Is there anyway of taking over the ownership of the HD so that I can use it?

Ever since I got Ubuntu I have had a lot of bumps in the road, but whatever it was you guys have always helped me out. Thanks:popcorn:

---

### Post by BatsotO on 2007-06-06
Depends on where you mount your HD. I usually mount my slave on /media/disk , and set the permission for this folder sudo chmod -R 777 /media/disk 
This solve the permission issue, you don't have to own it, let root mount it, as long as you  have all access that should be enough.

---

### Post by taurus on 2007-06-06
What filesystem is on that second harddrive?

```
sudo fdisk -l
```

---

### Post by pbw on 2007-06-06
> **BatsotO said:**
> Depends on where you mount your HD. I usualy mount my slave on /media/disk , and set the permission for this folder sudo chmod -R 777 /media/disk 
This solve the permission issue.

Don't change the permissions of everything on the hdd. 

Firstly, if the drive is ntfs you have to install ntfs-3g to aquire write permisisons. (do a quick search, it's simple).

Secondly, if it's not ntfs and you simply are not owner of the files. then use chown to change ownership. Don't change permissions on everything though, that's just dumb.

following the above example you would do.. sudo chown -R yourname.users /media/disk

I'm going to assume it's the first scenario, since it came from an XP computer.

-- pbw

---

### Post by BatsotO on 2007-06-06
I think changing permission on the folder where he mount the hd is enough (works for me). I forget that the slave maybe still ntfs, my mistake, sorry.  What I mean is you gain permission to write to folder where you mount the drive (assume the drive was non-ntfs). Changing permission will be effective if you have multiple account, so you can access the drive when you login under different account.

---

### Post by samsonson on 2007-06-06
Thanks batsotO. that solved my no permission to write prob. as well
Cheers.

---

### Post by Incarnadine on 2007-06-07
Sorry for not getting back to you guys sooner. The slave drive is indeed NTFS. So I guess the best route is to go with installing 3G. Hahahaha.....I have no idea what that is, but I will do some searching around the forums and find out. Thanks for the advice:)

---

### Post by taurus on 2007-06-07
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
gksudo ntfs-config
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Incarnadine on 2007-06-07
I checked under the Add/Remove files to see if the pack was available there and it was! I just installed it and checked the box that allows me to write files on my NTFS drive and that was it. Closed case problem solved. Thanks for the help. That wouldn't have been possible without pbw giving me the name of the program. Thanks:popcorn:

---

### Post by wkdown on 2007-06-10
Unfortunately, it didn't go so easy for me.  I ran through the steps mentioned here.  I ran

```
 sudo chmod -R 777 /media/disk 
```

But it didn't seem to affect it.  Do I chmod /dev/sdb1, instead of the mount point?

I also installed NTFS-3G, got the aforementioned option box to enable writing to an external device, and still no change.  So I unmounted the external HD and brought it back up, still no change.

---

### Post by wkdown on 2007-06-13
Anyone have any ideas?  And yes, I did try chmod on /dev/sdb1

---

### Post by sochbat on 2007-06-14
i haven't tried chmod, but i did the other three commands.  it went well, but when i try to transfer anything, it prompts me again.  Shoud i really run the chmod command?

---

