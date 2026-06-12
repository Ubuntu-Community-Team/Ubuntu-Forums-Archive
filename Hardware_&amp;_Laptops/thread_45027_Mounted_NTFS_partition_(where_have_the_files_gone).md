---
title: "Mounted NTFS partition (where have the files gone?)"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by Beej on 2005-06-28
Hi I'm a completely new Linux user and I have so far relied entirely on ubuntuguide.org to get me set up and going, and I haven't used Windows in iver a week now(it feels good)

I set up my NTFS partition wich has XP on it following the instructions here :

[http://ubuntuguide.org/#mountntfs](http://ubuntuguide.org/#mountntfs)

All went well and I had rhythmbox set to read my mp3s from the partion. 

On rebooting rhytmbox didn't show any files. Then i read the next set of instructions in the guide showing how to set the partition to mount on boot. When i paste the instructions into the terminal I get the following message.

cannot create directory `/media/windows': File exists

When I go through the file system to the folder titled windows, it is empty.

Can anyone help?

---

### Post by apollo2011 on 2005-06-28
Welcome to the forum Beej! :)

I believe you followed the directions for the manual mount of an NTFS partition.  But then you mentioned using the boot-up directions.  Were the directions you were referring to these? [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

It sounds like the first time you set it up to mount in /media/windows.  When you went back to set it up again following the other directions, you tried to create a directory that already existed (so you got an error message).  When you browsed to the folder, you browsed to /windows, instead of /media/windows.

The directions you were following used /media/windows as the point at which they were going to have the partition mounted.  You can have that mounted to anywhere on your system.  So if you want, you could have it mounted to /windows, which is probably a better place for the drive to reside.

Below are my directions adapted to your situation:
1. Find which drive your NTFS partition is. (type "[COLOR=Red]sudo fdisk -l[/COLOR]") We will assume it is /dev/hda1

2. (We will assume you are going to have it mount in /windows) type "[COLOR=Red]sudo mkdir[/COLOR][COLOR=Green] /windows/C[/COLOR]".  This makes a C directory in the /windows folder.  You can substitute the part in green with any location you want.  If the directory already exists, skip this step.

3. type "[COLOR=Red]sudo cp /etc/fstab /etc/fstab_backup[/COLOR]".  This backs up the File System Table (fstab)

4. type "[COLOR=Red]sudo gedit /etc/fstab[/COLOR]" This opens fstab for editing.  If gedit is not installed, install it from Synaptic.

5. Append this line to the end of the file:
[COLOR=Blue]/dev/hda1[/COLOR] [COLOR=Green]/media/windows[/COLOR] [COLOR=Red]ntfs umask=0222 0 0[/COLOR]
Red stays, Green is the path to the directory you chose/created, Blue is the partition.

6. Save the file

7. type "[COLOR=Red]sudo mount -a[/COLOR]"  This remounts all the partitions including the new one you just added.

---

### Post by Beej on 2005-06-29
I managed to sort it so that when I boot it mounts the windows partition, by unmounting, and then following the instructios here: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

as discussed.

Will following your instructions mount the partition as a drive in my computer (as filesystem and my external hdd)? Also do I have to remove the mount point I created previously?(/media/windows)

---

### Post by apollo2011 on 2005-06-29
[QUOTE=Beej]I managed to sort it so that when I boot it mounts the windows partition, by unmounting, and then following the instructios here: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

as discussed.

Will following your instructions mount the partition as a drive in my computer (as filesystem and my external hdd)? Also do I have to remove the mount point I created previously?(/media/windows)[/QUOTE]

OK, Your first question, I assume you mean like in Windows where it would be the D: drive or some other letter.  If that is what you meant, then the answer is no, Linux doesn't mount seperate drives like that.  Instead, you mount them in a directory under the root (/).  Your second question, Remove any lines that are in fstab and start over.  You can leave the folder there if you are going to use it as the mount point, but then skip the mkdir step and if you aren't going to use that as the mount point, type "sudo rm -rfi /media/windows"  Hope that answeres your questions :)

---

### Post by Breepee on 2005-06-30
[QUOTE=apollo2011]OK, Your first question, I assume you mean like in Windows where it would be the D: drive or some other letter.  If that is what you meant, then the answer is no, Linux doesn't mount seperate drives like that.  Instead, you mount them in a directory under the root (/).  Your second question, Remove any lines that are in fstab and start over.  You can leave the folder there if you are going to use it as the mount point, but then skip the mkdir step and if you aren't going to use that as the mount point, type "sudo rm -rfi /media/windows"  Hope that answeres your questions :)[/QUOTE]
 I've noticed too that when rebooting Ubuntu appears to mount before it detects the drive or something, because the NTFS drives I've added to fstab, are on bootup also in error (couldn't find hda1 etc). Performing sudo mount -a myself on startup fixes it, but shouldn't be necesary.

---

### Post by Breepee on 2005-07-06
[QUOTE=Breepee]I've noticed too that when rebooting Ubuntu appears to mount before it detects the drive or something, because the NTFS drives I've added to fstab, are on bootup also in error (couldn't find hda1 etc). Performing sudo mount -a myself on startup fixes it, but shouldn't be necesary.[/QUOTE]
 Can anyone help me? And perhaps tell me how I can run that command automatically on startup?

---

### Post by apollo2011 on 2005-07-06
[QUOTE=Breepee]I've noticed too that when rebooting Ubuntu appears to mount before it detects the drive or something, because the NTFS drives I've added to fstab, are on bootup also in error (couldn't find hda1 etc). Performing sudo mount -a myself on startup fixes it, but shouldn't be necesary.[/QUOTE]

Are the NTFS partitions listed last in fstab? I am not sure this could affect it but it might...

---

### Post by Breepee on 2005-07-06
[QUOTE=apollo2011]Are the NTFS partitions listed last in fstab? I am not sure this could affect it but it might...[/QUOTE]
 Of course, read exaclty one reply up :)

---

### Post by apollo2011 on 2005-07-15
[QUOTE=Breepee]Of course, read exaclty one reply up :)[/QUOTE]

One post up doesn't answer that question....

---

### Post by geeves on 2005-07-20
I think I have exactly the same problem as Breepee.

My NTFS windows XP partition is in my fstab file but on boot it says **/dev/sda2 doesn't exist** but when I run **mount -a** it mounts no problem.

I have tried any number of different combinations of   ntfs    nls=utf8,umask=0222 0       0 after the original bit (any idea what all these things mean? pretty clear on the ntfs bit and I'm guessing the umask is the permissions but I've been told by different people to put different stuff in there... none of which works correctly of course but none of which stops mount -a working either)

I am somewhat at my wit's end at this stage!

Thanks in advance for any help

PS I have even tried adding mount -a to my startup routines... but alas no joy.  ](*,)

---

