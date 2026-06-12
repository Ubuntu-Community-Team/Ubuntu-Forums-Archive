---
title: "I want to write in my HDD"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by seiferkai on 2006-08-12
first it was the drive..i formatted it to linux and now its functional with 1 folder "lost+found" but there's 1 problem

the Root neither can I could write on the drive. I cant create folders, I cant save on it, nothing...nada

when i do go to root to change permission to the folder which is /media/hdb1
i get this error message

Error message #1

The permissions could not be changed.
Couldn't change the permissions of "hdb1" because it is on a read-only disk

Error message #2 - when trying to change users

The owner could not be changed.
Couldn't change the owner of "hdb1" because it is on a read-only disk


my plea is ..can anyone help me get this drive off read-only....i dont want read-only

here is my fstab file....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     ext3    users,ro        0       1


please help me....i been on this problem for hours and hours..im tired there has to be a simple solution....im logging now
im pretty sure i put all the info so it should be smooth sailing from here..


[B]
before i go[/B]

MY FDISK DATA - just in case anyone need it

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4866     1614532+   5  Extended
/dev/hda5            4666        4866     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601   83  Linux

---

### Post by Hg80 on 2006-08-12
if there ntfs drives your need [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/) which is still in testing and therefore could cause some corruption when writing to these drives.

If there fat32 then try this
```
sudo chmod 777 /media/hdb1
```

---

### Post by RRS on 2006-08-12
To make yourself the owner of hdb1 change the line in fstab to:
/dev/hdb1 /media/hdb1 ext3 defaults 0 0

---

### Post by mpvano on 2006-08-12
The fstab entries show that this is not an ntfs disk - that can't have anything to do with the problem.

I hope you take this the right way, but you can't write to that disk because your fstab shows that YOU have TOLD the system to mount the disk read only and not allow writing!

I have no idea how you created that entry, but it's only one of several things causing your problem.

Once you fix it, you will then also need to use administrative rights to create one or more shared folders and then set their ownership and rights correctly (and safely) for what you intend to do with them.

Once you figure out EXACTLY what kind of access rights you need to allow and to whom they should apply, you can find the details of how to use administrative commands to set up the disk and folders from the help menu or the terminal window as man commands. Look up the topics "fstab", "mount", "mkdir", "chown", "chmod" and "gksudo" and "sudo".

You can also do what's needed from the nautilus graphic interface by using "sudo" or "gksudo" to start a nautilus window with administrative privileges, but that's usually a bad idea since everything you touch or disturb from that window or any program it starts will be permanently changed, even if the  results will destroy your system or break things in subtle ways.

You need to understand what you are doing before you make this kind of changes. Done incorrectly, you will expose yourself to remote break-ins or other very hard to correct  system damage. That's the whole point of the design of the system. You're not supposed to be able to modify things you don't understand.

For example - certain other typos or incorrect commands (similar to the one you already made) in the fstab file will prevent your system from booting and can only be repaired by booting from a recovery disk and editing the file to correct them. Others will result in trashing all your files in such a way that they cannot be recovered.

I hope this message points you toward an eventual solution, but don't forget that these are not simple issues and this may not be a good place to expect folks to write you a personalized system administration tutorial.

You shouldn't have any trouble finding a brief overview of how the file protection system works and how to safely use it by searching for a beginner's guide to linux here or via a search engine. There are plenty of them out there.

good luck getting it all sorted out,

Mario

---

### Post by wpshooter on 2006-08-12
Seiferkai:

If you are saying what I think you are, then you are NOT supposed to be able to write to these directories/folders as a normal Ubuntu user.  You have to be logged in as administrator/root user to write to these areas of Ubuntu.

---

### Post by seiferkai on 2006-08-12
so what your trying to say is...as long as im trying to learn this system i could never get to write in this drive?

i know there's a way i just need help

---

### Post by RRS on 2006-08-12
The fstab line I posted earlier will remove the write only restriction and make the user (you) owner of the partition and it's files so you won't have to log in as root to write to them.

The similar restrictions in your fstab for hda1 are to help protect the sytem as that's your root partition according to it's mount point. As I'm guessing hdb1 is for data, music files, or similar there's no practical reason for it to have the same  degree of protection.

You might also want to visit [this site]("http://www.psychocats.net/ubuntu/index.php") by Aysiu. It contains a great deal of usefull information and some good tutorials to help you learn your way around Ubuntu.

I hope this helps wirh your questions. If you need more clarification be sure to post back.

---

### Post by seiferkai on 2006-08-12
thanks for the site...i dont wanna use my primary drive for music and videos
i wannna use my 300gig hdd to do that

and i set the fstab to default 0 0 just like you pointed out
and i still dont have write acess to the drive

and my resolution in windows i had it at 1280x1024
now its at 1024x768....how can i return it to my orignal size


but thats a whole new problem ...lets get my drive functional first

---

### Post by seiferkai on 2006-08-12
OMG after reading reading and more reading i have finally found the solution...

to acess write capabilities to a drive...to abolish the read-only function from a drive you have to go into the terminal and add these codes...


sudo chown -R username:username /storage
sudo chmod -R 755 /storage


where you see "username" replace with your username you login to Ubuntu
and thats that...now on to my resolution..but i will make a new thread for that...this thread is ova lol

---

### Post by futz on 2006-08-12
> **seiferkai said:**
> OMG after reading reading and more reading i have finally found the solution...

to acess write capabilities to a drive...to abolish the read-only function from a drive you have to go into the terminal and add these codes...


sudo chown -R username:username /storage
sudo chmod -R 755 /storage


where you see "username" replace with your username you login to Ubuntu
and thats that...now on to my resolution..but i will make a new thread for that...this thread is ova lol
You know what? Those two lines (the chown and chmod lines above) are **EXACTLY** what I was telling you to do last night, only my directions described doing it without using the terminal. So *now* it works, but last night it didn't? How strange... :???:

---

### Post by mpvano on 2006-08-13
If you're the only user that needs access to the new drive, the following should fix your problem safely, as well as providing a simple way to extend access to other users in the future. If you're trying to SHARE the drive in any way (i.e. with other user's accounts, you'll need to give us more details about who needs access to the drive and for what purposes.

All the following commands must be executed with root authority, in this example they are preceded by the "sudo" prefix in a terminal window. You will need to enter your password when you give the first one to be allowed to use these commands.

They will create a top level folder on the disk named "myfolder" that you can read or write to and from and that members of the group with the same name as that of your account can read from. Everyone else is denied access. I'm assuming that your account name is "myaccount".

sudo mkdir /media/hdb1/myfolder
sudo chown myaccount:myaccount /media/hdb1/myfolder
sudo chmod 750 /media/hdb1/myfolder

This should be quite safe except for one caution. The way you have the drive mounted and with the 750 permissions I suggested, you can run programs that are installed on this disk.

You should be careful because this means that it is possible for you to unknowingly download trojan programs to this disk and accidentally execute them by double clicking on them with nautilus. Since this is the same risk as occurs in your home folder, it's usually relatively safe. If you want to share this folder the situation can become more complicated.

If you are doing something more complicated, I still suggest learning what you are doing. If you MUST try to get help here to do it, the only safe way to do so is to explain EXACTLY  what you are trying to do. Disabling all security on the drive is definitely not a solution.

One of the complications about what you are doing is that the drive appears to be presently mounted by a root owned process in the automount folder. This folder doesn't belong to you and tampering with the way it works can be dangerous or confusing.

FYI If you REALLY wanted to mount a disk yourself and have the ability to do whatever you want with it, you need to have fstab configured properly to allow non-root mounting, but you probably also want to mount the disk to a folder that belongs to you (i.e. in your home directory), and mount it yourself instead of letting the automounter or boot process do it. That way, the whole drive will belong to you, not just the part (inside the folder) that the real owner (root) gives you permission to use. The references I referred you to explain all this in detail. Eventually you'll probably want to read them.

I'm sorry if it appeared I was giving you a hard time, I really am only trying to make sure you don't disable all the security on your machine. Improperly configured machines with internet access are really quite a threat to everyone else using the net. Most servers (like the ones I run) are the target of hundreds of attack attempts a day, many of them presently coming from linux installations done by new linux users who decide that they don't need to keep their machine secured, since they didn't have to do that under windows...

good luck and if the above isn't what you need, try telling us more about what you are trying to do.

Mario

---

