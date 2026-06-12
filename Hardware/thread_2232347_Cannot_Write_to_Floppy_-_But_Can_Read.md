---
title: "Cannot Write to Floppy - But Can Read"
date: 2014-07-01
forum: Hardware
---

### Post by cedric9 on 2014-07-01
I recently installed Ubuntu 14.04 LTS on my old Pentium 4, and I've run into 
some trouble using my floppy drive. (I'm one small step above newbie.)

At first I could not use my floppy drive at all, and the indicator light would 
stay on constantly whenever I tried to mount.  Eventually I got it working well 
enough that the light no longer stays on, and I can now read the contents of my 
floppies, but I cannot write to them.  (Although I can format them in Ubuntu.)

Here is a quick recap of everything I've done to get to this point: 
=============================================================================
* Add the following line to /etc/modules
"floppy" (Without quotes)
=============================================================================
* Comment out the following lines within /etc/fstab
#/dev/fd0 /mnt/fd0 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
#/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
(I added the above lines while experimenting, but both commented out now.)
(All other lines left the same)
=============================================================================
* Added all users to Floppy group
==============================================================================
* Installed fdutils Version 5.5-20060227-6 - via Muon Package Manager
(Verified with "apt-cache show fdutils" command)
================================================================================
* Installed udisks Version 1.0.5-1
(I also have udisks2 Version 2.1.3-1 - Will this cause a problem?)
================================================================================
* Changed the "1" to "0" in the following lines within the floppy section of 
/lib/udev/rules.d/80-udisks.rules  (Example below)

KERNEL=="fd*", ENV{ID_DRIVE_FLOPPY}="0"
ATTRS{bInterfaceSubClass}=="04", ENV{ID_DRIVE_FLOPPY}="0"
ENV{ID_VENDOR}=="*IOMEGA*", ENV{ID_MODEL}=="*ZIP*", ENV{ID_DRIVE_FLOPPY_ZIP}="0"
(All other lines left the same.)
================================================================================
* Added the following command to /etc/rc.local  
"floppycontrol -C 2147483647" 
(without quotes)
================================================================================

I'm wondering if my problem could be due to the lines I commented out within 
/etc/fstab?  Also, I read somewhere that someone had solved a problem similar 
to mine by changing the line within /etc/fstab to read as below: 
"/dev/fd0u1440/media/floppy0 auto rw,noauto,user,exec 0 0"
However, I don't know if this will solve my problem?   

Also, is the package listed as "udisks2 Version 2.1.3-1" a duplicate of udisks 
Version 1.0.5-1, and is this causing a problem?

---

### Post by SeijiSensei on 2014-07-01
Insert the floppy in the drive, then run the "mount" command.  Is it marked read/write?

You didn't happen to flip the read-only switch on the physical floppy itself, did you?

---

### Post by Yellow Pasque on 2014-07-01
Is your user in the 'floppy' group?

Other tips here, though they are for Ubuntu 12.04 and Ubuntu 14.04 might have some different elements (like udisks2): [http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubuntu](http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubuntu)

---

### Post by cedric9 on 2014-07-01
> **SeijiSensei said:**
> Insert the floppy in the drive, then run the "mount" command.  Is it marked read/write?

You didn't happen to flip the read-only switch on the physical floppy itself, did you?

Hello SeijiSensei, When I enter the mount command, I do not receive any error messages stating that it is mounting in read only mode.  If my floppy was being mounted in read only mode, would I see an error message say it was read only? 

Is there another command I can use to determine if the floppy is being mounted in read only mode?  Sorry, I'm still a bit of a newbie.
(I can see the contents of my floppy within /media/floppy0) 

Also, the read only switch on the floppy is in closed position.

---

### Post by cedric9 on 2014-07-01
Hello Juan,  yes, I added all of my users to the floppy group.  Hmm...I will take a look at the above link when I get home.

---

### Post by SeijiSensei on 2014-07-02
> **cedric9 said:**
> Hello SeijiSensei, When I enter the mount command, I do not receive any error messages stating that it is mounting in read only mode.  If my floppy was being mounted in read only mode, would I see an error message say it was read only? 

No, but you should see an "rw" entry in the list of options being used.  Here, for instance, is the entry for a hard drive partition on this machine:
```
/dev/sda1 on /boot type ext2 (rw)
```
You should see "rw" at the end of the floppy entry.  If it reads "ro" it is read-only.

---

### Post by cedric9 on 2014-07-02
I got it to work!  I added the below line to my /etc/fstab and now I can read and write to my floppies.

/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,umask=0,utf8 0 0

Not sure how or why it is now working, but I found the above line in a similar thread to mine.

---

### Post by Marc_Hendry on 2014-08-18
(0) Make sure the floppy kernel module is loaded

[FONT=courier new]**lsmod | grep floppy**[/FONT]

If this is not the case, edit /etc/modules and add a line that contains

[FONT=courier new]**floppy**[/FONT]


(1) Create a folder to mount the floppy to:

[FONT=courier new]**mkdir /media/floppy**[/FONT]

You'll only have to do this, if the folder doesn't exist yet. Choose a name (and location) of your desire. The desktop environment will adapt to this automatically.


(2) Change ownership and permissions

[FONT=courier new][B]chgrp floppy /media/floppy
chmod 750 /media/floppy[/B][/FONT]

That way, only users in group "floppy" can access this directory. Also, if no floppy is mounted, there are no write permissions to this location, therefore nobody can accidentally drop data in here. Users that are not members of the floppy group can't read or write here at all.


(3) Add the following line to /etc/fstab

[FONT=courier new]**/dev/fd0 /media/floppy auto rw,user,noauto,exec,_gid=floppy_,_umask=007_ 0 0**[/FONT]

Now *every* user can mount a floppy to /media/floppy. After mounting the floppy, the group of /media/floppy will still be "floppy" (it would be "root" if the _gid_ option was omitted). Also, members of group "floppy" will now be able to write to this directory, while everyone else still has no read or write permissions (if everyone else should have read permissions, _umask_ must be set to 002).


This is basically cedric9's soloution, just featuring more detailed read and write permissions. Using this configuration, only members of the floppy group can read or write floppy disks, while still being able to enforce restrictions to all others. You may want to consider this if your PC is a multi unser environment.

---

