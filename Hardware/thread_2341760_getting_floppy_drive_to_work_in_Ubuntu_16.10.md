---
title: "getting floppy drive to work in Ubuntu 16.10"
date: 2016-10-31
forum: Hardware
---

### Post by roadrash on 2016-10-31
Please can someone help me getting the floppy working on my machine.  I need to use it to write some Apple Mac disk images for a old Powerbook 180c but after following a number of guides online I did once get it working following the first part of the article here: [http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubuntu](http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubuntu) but after a reboot i haven't been able to get it to work any more.  I can get it to show in a list of devices sometimes and I installed the fdutils package as it suggested in the above article but the fdmount command failed to work then if I create a mountpoint and mount it there in the normal way it just hangs continuously reading the floppy disk and i have to reset the pc to get out of it. 
please can someone help me get a permanent solution to this that I can use every day.


many thanks
Jon..

---

### Post by howefield on 2016-10-31
As a support request, thread moved to the "*Hardware*" forum.

---

### Post by ajgreeny on 2016-10-31
It is a very long time since I had a floppy disk drive to deal with, and even then it was difficult to get working easily, but I am pretty sure it needed a udisks command similar to that shown in your linked askubuntu page, something like ]```
udisks --mount device_file [--mount-fstype fstype] [--mount-options options
```
which according to man udisks "Mounts the device represented by device_file using the file system fstype and a comma-separated list of options."

Unfortunately I no longer have any record of what exactly my command was, and my memory of it is now completely gone.

---

### Post by roadrash on 2016-10-31
Whats been confusing me has been all the coflicting ways of mounting a floppy and the the change from Udisks now replaced by udisksctl  none have worked for me.
What I was told to do and have done so far is:

sudo modprobe -v floppy

then if i enter:

lsmod | grep -i floppy

I shows "Floppy" in red and then i add me to the group floppy:

sudo adduser $USER floppy

then install fdutils and use the command:

fdmount -l

it returns the following:
NAME   TYPE  STATUS
 fd0  1440K  not mounted

This is all I got and then tried to use another suggestion:

sudo udisks --mount /dev/fd0

which just returns:
sudo: udisks: command not found

Then I discovered udisks has been replaced by udisks2 and the command is now udisksctl and i should try this:

udisksctl mount -b /dev/fd0
which just returns another error : 
Object /org/freedesktop/UDisks2/block_devices/fd0 is not a mountable filesystem.

please can someone make some sense of all this for me so i can mount my floppy drive.

---

### Post by Dennis N on 2016-10-31
My solution was to get a portable 3.5" floppy drive that connects by USB. The one I have is made by TEAC and was < $20 as I recall. Works great.

---

