---
title: "unable to mount Floppys and CDs"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by gordon33 on 2007-02-19
Hello all 
Following is the history of my problem with mounting  Floppys and CDs and the help of others.

When trying to open a floppy or save something to a floppy I got an error message. "Floppy: Unable to mount the selected volume." Clicking on "Show more details" got this message: "Warning; device /dev/fdo is already handled by/etc/fstab. Supplied label is ignored. mount: could not be determined the file system type and none was specified Error: could not execute mount When trying to open a CD Rom drive I got an error message. "Unable to mount the volume. Their is probably no media in the device." Clicking on "Show more details" got this message: "Warning; device /dev/hdc is already handled by/etc/fstab. Supplied label is ignored. Mount: no medium found Error: could not execute mount completely lost as to what should be done. 
Gordon 

HELLO GORDON
Please describe how you are attempting to "open" the drives. Are you 
clicking on a desktop icon? If so what desktop environment? What distro? Is this an icon created by your distro's install procedure or did you create it your self?

Please open a command shell and execute these commands:
    $ grep fd0 /etc/fstab
and
    $ df -Th | grep fd0
and post any resulting output to the list. If you do this in a shell 
window on your desktop you should be able to copy and paste the entire session into an email window.

There are a lot of different versions of Linux which handle things like 
this in a lot of different ways. A more complete description of your operating environment and your actions are needed to determine what the problem is.
R.M. 

HELLO GORDON
How are you trying "to open a floppy or save something" ?
What distribution are you using?
Please post the contents of:    /etc/fstab
H.G.

Hello R.M. AND H.G.
I am using Ubuntu.  I have been pulling down the menu "Places" choosing 
"Computer" then clicking on "Floppy"
I do remember using the floppy and cd drives before.  But that was 
months ago.  Presently I have been unable to save any thing on a floppy.
Gordon

Hello Gordon
How are you trying "to open a floppy or save something" ?
What distribution are you using?
Please post the contents of:    /etc/fstab 
H.G.


HELLO GORDON
I am not familiar with Ubuntu, but it seems that it should do the
automatic mounting of the floppy whenever you do what you described
and it doesn't do it.
Unless somebody familiar with Ubuntu replies, I could help you only
through the command line.

Please post the contents of the file:  /etc/fstab

Also, WITHOUT any floppy disk inserted, please execute (as root) the 
command:  mount  and copy/paste the contents here.
H.G.

HELLO H.G.
gordon@ubuntu:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
gordon@ubuntu:~$

That is what came up after typing in MOUNT
GORDON

HELLO GORDON
It looks like there is no mounted floppy, so I can't see a reason why
it would complain that there is one already mounted when you insert
it.
What's in your /etc/fstab file?
H.G.

HELLO H.G.
I finlaly learned how to  List the etc/fstab file.   Below are the 
results.  Still unable to use floppy drive.

gordon@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       
1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
gordon@ubuntu:~$
gordon@ubuntu:~$
GORDON

HELLO GORDON
From what you have shown everything seems to be in order.
Ok, insert a floppy (with some data in it) and then on the command
line execute (do not use any Menu or anything):

ls  /media/floppy0

What happens?
You can try a similar exercise with a data CD-ROM, insert it and then
on the command line execute:

ls  /media/cdrom0

and if that doesn't work, try the other CD drive:

ls  /media/cdrom1
H.G.

Hello H.G.
&#61656;	Tried the comand "ls /media/floppy0", "ls /media/cdrom0", and the 
&#61656;	"ls /media/cdrom1". I just get the promp line " gordon@ubuntu:~$"
GORDON

HELLO GORDON
This seems that it is not mounting the floppy.
Now try the following:
1) Insert a floppy (either with some information or formatted)
2) Execute: mount /dev/fd0 /media/floppy0
3) Execute: ls /media/floppy0
Can you see the contents of the floppy?
If not, then execute: mount
and copy/paste the output so I can see if it was mounted or not.
H.G.

Hello H.G.
Here is what happened. with the executables you gave me:

gordon@ubuntu:~$ sudo mount /dev/fd0 /media/floppy0
Password:
mount: you must specify the filesystem type
gordon@ubuntu:~$ ls /media/floppy0
gordon@ubuntu:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
gordon@ubuntu:~$
Gordon

---

### Post by 1aB on 2007-02-19
> **gordon33 said:**
> Hello all 

gordon@ubuntu:~$ sudo mount /dev/fd0 /media/floppy0
Password:
mount: you must specify the filesystem type


The mount failed. Since your /etc/fstab contains the correct settings for mounting a floppy just try 
$ mount /media/floppy0
and then a ls of that dir and report back

---

### Post by gordon33 on 2007-02-19
Here are the results from mount /mesia/floppy0, and ls of that dir.

gordon@ubuntu:~$ mount /media/floppy0
mount: I could not determine the filesystem type, and none was specified
gordon@ubuntu:~$ ls floppy
ls: floppy: No such file or directory
gordon@ubuntu:~$ ls /floppy
ls: /floppy: No such file or directory
gordon@ubuntu:~$

---

