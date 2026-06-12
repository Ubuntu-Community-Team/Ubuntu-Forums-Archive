---
title: "Partition automatically formatted"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by ameya_joshi on 2009-10-23
Hi people,

I recently started using Ubuntu 9.04 .

I installed it on a seperate slave HDD.

Next i decided to mount my windows partition permanently , so i followed the guide 

i.e created a mount point in /media and mounted the partition .

Suddenly my mind decided why not attach it direcly to root i.e /

So i created the mount point there edited the fstab and mounted it.

So it was mounted twice .

In order to delete the mount point in /media directory i unmounted the volume and

executed rm -rf command to delete the mount point location in /media.

After the i mounted the volume on new mount point i.e /

Guess what the entire partition was blank my data was gone.

Now anybody can explain how come the data gor wiped off??

Any chances of me recovering it??

Regards,
Ameya

---

### Post by presence1960 on 2009-10-23
you just learned a lesson the hard way. When use the rm command it deletes whatever file/directory you specify in that command. Even though the directory was  mount point it contained your windows directory. Unless some miracle happened for you your windows is gone!

to be sure boot into ubuntu and run this command ```
sudo fdisk -l
```post the results back here

---

### Post by oldfred on 2009-10-23
I thought it was umount to unmount and rmdir to remove directory.

I try to avoid any rm command as a wrong space  or / makes a huge difference.

---

### Post by az on 2009-10-23
> **ameya_joshi said:**
> Hi people,

I recently started using Ubuntu 9.04 .

I installed it on a seperate slave HDD.

Next i decided to mount my windows partition permanently , so i followed the guide 

i.e created a mount point in /media and mounted the partition .

Suddenly my mind decided why not attach it direcly to root i.e /

So i created the mount point there edited the fstab and mounted it.

So it was mounted twice .

In order to delete the mount point in /media directory i unmounted the volume and

executed rm -rf command to delete the mount point location in /media.

After the i mounted the volume on new mount point i.e /

Guess what the entire partition was blank my data was gone.

Now anybody can explain how come the data gor wiped off??

Any chances of me recovering it??

Regards,
Ameya

You mounted it twice and it didn't unmount.  Usually it will refuse to unmount and throw out an error.  Did you see that?

Also, why did you recursively try to remove the (presumed) empty folder?  You would have saved yourself a lot of problems by avoiding the habit of using -rf when you don't need to.  It it is empty, you get rid of the directory.  It it's not empty, it throws an error and saves your data from being deleted.

You can use file carving software like Photorec to recover most of your important files.  But you will not be able to restore the partition to what it was.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Also, don't try to fsck or chdisk the empty drive.  If it moves anything around, you are likely to corrupt deleted files and you will not be able to recover them.

At any rate, your filesystem is gone and you will need to reinstall Windows.

---

### Post by ameya_joshi on 2009-10-24
Nothing has happened to windows...........my windows partiton is safe and sound!!!! i dint even thought of mounting it permanently

Thank you from now on i wont use rm -rf command

2nd thing i did the same thing with 2 drives E:/ and F:/

Well the E: lost all its data 

but the data in F: is intact

Now why such different behavior ???

Plz any body can explain this?

@ AZ photorec s/w huh....i will try it and hope i recover them!!!

---

### Post by ajgreeny on 2009-10-24
This whole saga points up one of the ambiguities of the ```
man rm
``` which says:-
```
By  default,  rm  does  not  remove directories.  Use the --recursive (-r or -R) option to
       remove each listed directory, too, along with all of its contents.
```
Perhaps an extra warning could be added someway, though I realise this is not ubuntu specific.

---

