---
title: "Unable to Mount Floppy A"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by nicehill on 2005-12-20
Hi, 

I'm new to Linux. Just installed Ubuntu. 
When I try to read a diskette, it show 
the below error message: 

" Unable to mount the selected volume, 
error: given UDI is not a mountable volume" 

Have chk the floppy connection, is Ok. 
Please help. 

thk you

---

### Post by paulmilliken on 2005-12-20
[QUOTE=nicehill]Hi, 

I'm new to Linux. Just installed Ubuntu. 
When I try to read a diskette, it show 
the below error message: 

" Unable to mount the selected volume, 
error: given UDI is not a mountable volume" 

Have chk the floppy connection, is Ok. 
Please help. 

thk you[/QUOTE]


Did you type "mount /media/floppy" after inserting the disk?

---

### Post by nicehill on 2005-12-20
It works when I type in "mount /media/floppy"

You everytime I need to read a floppy I need 
to do this. Is there anyway that can be detected 
automatically.

thanks again

---

### Post by canadianwriterman on 2005-12-20
This is not how floppy mounting is supposed to work in Breezy. Rather than all the terminal entries and creating an icon on your desktop, etc., I prefer to have the functionality working as it was really designed to.

Unfortunately, there were many people (myself included) for whom this function did not work. There was a bug in the pmount file that controls mounting. Developers fixed the file, but it was not sent out as an update. But, you can update it yourself.

To update pmount, go to:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

Download and install pmount_0.9.6-1_i386.deb

Now, just insert your floppy, open **Computer** and right click on the floppy drive. You'll have a menu option to **Mount** and then **Unmount** it. Hope that helps.

---

### Post by new2lnx on 2005-12-21
[QUOTE=canadianwriterman]
There was a bug in the pmount file that controls mounting. Developers fixed the file, but it was not sent out as an update. But, you can update it yourself.

To update pmount, go to:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

Download and install pmount_0.9.6-1_i386.deb

Now, just insert your floppy, open **Computer** and right click on the floppy drive. You'll have a menu option to **Mount** and then **Unmount** it. Hope that helps.[/QUOTE]

I installed pmount_0.9.6-1_i386.deb to solve the problem with my laptop's floppy.  Now I can mount and unmount floppy within nautilus.  Unfortunately the problem transferred to usb disk because with the new pmount, I can now mount my usb disk only as root.

I want to be able to mount my usb disk as regular user.  Please help

---

### Post by nicehill on 2005-12-21
By the way, how to install pmount_0.9.6-1_i386.deb.

Thanks

---

### Post by new2lnx on 2005-12-21
[QUOTE=nicehill]By the way, how to install pmount_0.9.6-1_i386.deb.

Thanks[/QUOTE]

sudo dpkg -i pmount_0.9.6-1_386.deb

---

### Post by new2lnx on 2005-12-21
[QUOTE=new2lnx]I installed pmount_0.9.6-1_i386.deb to solve the problem with my laptop's floppy.  Now I can mount and unmount floppy within nautilus.  Unfortunately the problem transferred to usb disk because with the new pmount, I can now mount my usb disk only as root.

I want to be able to mount my usb disk as regular user.  Please help[/QUOTE]

Ok, i found a solution from a post in this forum.  It said user hal should be included in groups cdrom, floppy, plugdev.  I followed the advice and mounting/umounting of floppy, cdrom, and usb disk just works as it did before!

Thanks everyone.

---

### Post by dfj on 2006-01-03
[QUOTE=new2lnx]Ok, i found a solution from a post in this forum.  It said user hal should be included in groups cdrom, floppy, plugdev.  I followed the advice and mounting/umounting of floppy, cdrom, and usb disk just works as it did before![/QUOTE]

I too an new to Linux and Ubuntu and, if you would, please explain, in detail, the process that you used to successfully auto mount a floppy and also the same for CD0 and CD1

Thank you very much,

Dave

---

### Post by new2lnx on 2006-01-11
[QUOTE=dfj]I too an new to Linux and Ubuntu and, if you would, please explain, in detail, the process that you used to successfully auto mount a floppy and also the same for CD0 and CD1
[/QUOTE]

1. Click *System, Administration, Users and Groups*
2. enter password of the first user you created during installation
3. Click *Groups* tab within the *Users and Groups* window that appears
4. Select *cdrom* under *Group then click **Properties*** button
Group members should show **hal**; if not, select it from the left tab then click **Add** button, then **OK** button
Repeat step 4 above for *floppy* and *plugdev* groups.

---

### Post by new2lnx on 2006-01-11
[QUOTE=dfj]I too an new to Linux and Ubuntu and, if you would, please explain, in detail, the process that you used to successfully auto mount a floppy and also the same for CD0 and CD1
[/QUOTE]

BTW you could also follow this [http://www.ubuntuforums.org/showthread.php?t=113947&highlight=floppy+mount+problem](http://www.ubuntuforums.org/showthread.php?t=113947&highlight=floppy+mount+problem)
which worked for me when my problem recurred after i installed several software  to the point that i can no longer identify which one caused the problem

---

### Post by panty31772 on 2007-01-08
This worked for me hopefully it will help !

sudo gedit /etc/fstab

add this line "                                                                                                           /dev/fd0        /media/floppy0  auto rw,users,noauto,fmask=111,dmask=000  0   0 "

sudo mkdir /media/floppy0

mount /media/floppy0

click the icon on desktop select properties , device , /dev/fd0

only problem i have is drive has to be unmounted and remounted in order to read new disks

---

### Post by burtoni on 2007-01-27
> **panty31772 said:**
> This worked for me hopefully it will help !

sudo gedit /etc/fstab

add this line "                                                                                                           /dev/fd0        /media/floppy0  auto rw,users,noauto,fmask=111,dmask=000  0   0 "

sudo mkdir /media/floppy0

mount /media/floppy0

click the icon on desktop select properties , device , /dev/fd0

only problem i have is drive has to be unmounted and remounted in order to read new disks

I have been following this thread for a while now and none of the suggestions seem to work.  Whenever I try and mount (either /media/floppy0 or /dev/fdo) I get the error "/dev/fdo is not a valid block device".  CDROM's and USB devices are auto-mounted without a problem.  Is there something similar to makedev that can be used to create the proper device, or is there an option in mount that will allow me to mount it as a raw device.

Ian.

---

### Post by panty31772 on 2007-02-11
> **burtoni said:**
> I have been following this thread for a while now and none of the suggestions seem to work.  Whenever I try and mount (either /media/floppy0 or /dev/fdo) I get the error "/dev/fdo is not a valid block device".  CDROM's and USB devices are auto-mounted without a problem.  Is there something similar to makedev that can be used to create the proper device, or is there an option in mount that will allow me to mount it as a raw device.

Ian.
at a glance here it looks like you have to change "fdo" to "fd0" , that will most likely solve your problem    !
:oops:

---

### Post by magichsjx on 2007-02-13
I am also having problem mounting the floppy drive. it does not show under the disk manager. I tried panty's and it helps I could read a floppy and execute it but I wish someone would post how one can permanently mount a floppy just like a cdrom drive. :)

---

