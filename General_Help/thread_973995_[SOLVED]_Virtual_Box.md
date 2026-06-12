---
title: "[SOLVED] Virtual Box"
date: 2008-11-07
forum: General Help
---

### Post by garystam on 2008-11-07
Currently have Ubuntu 8.10 installed on full partition and running Virtual Box with Windows XP for the few programs I need from Windows. How do I get VB to recognize a USB flash drive/backup hard drive for the Windows XP stuff?

---

### Post by Therion on 2008-11-07
Have you installed Guest Additions and added yourself to the USB Users Group?  See the **Prepare Booting Your VM** section of this tutorial for adding yourself to the USB Users Group... 'Bout halfway down the page.

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by tarps87 on 2008-11-07
You will need to follow this:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
It has changed in Ubuntu 8.10 and you now need to add the lines as well.
The guest additions are for things like seamless windows so you shouldn't need to install but they are fun to mess about with :)

---

### Post by garystam on 2008-11-07
> **Therion said:**
> Have you installed Guest Additions and added yourself to the USB Users Group?  See the **Prepare Booting Your VM** section of this tutorial for adding yourself to the USB Users Group... 'Bout halfway down the page.

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)
When I opened the terminal and copied/pasted to the terminal to enable usbfs I got:
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac

It didn't match what you said would come up, but I did reboot ubuntu and it did free up the cursor from being locked into the VM.....sooooo....usb didn't show up in the VM and still need some help!

Your blog is awesome, by the way!

---

### Post by garystam on 2008-11-07
> **tarps87 said:**
> You will need to follow this:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
It has changed in Ubuntu 8.10 and you now need to add the lines as well.
The guest additions are for things like seamless windows so you shouldn't need to install but they are fun to mess about with :)
I followed your instructions for Ubuntu/Intrepid but got a message that permission denied, only "root" can do that. Should I install that first - I looked at it and it said it would install about 143MB when installing root. HELP....

---

### Post by ju2wheels on 2008-11-07
The process changed in Intrepid from the way Hardy used to do it, do not use instructions for Hardy.

1. Install Virtualbox from their website, I believe only the non-ose (open source) version supports usb so be sure to select that one. Anyone feel free to correct me if I am wrong there...

2. Add your user to the vboxusers group [Applications->Accessories->Terminal]:
```

sudo adduser your_user_name vboxusers

``` 

3. Add the following line to /etc/fstab: none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 as follows:

```

gksudo gedit /etc/fstab

```

and add to the end of the file:

```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Save the file and reboot.

---

### Post by garystam on 2008-11-08
> **ju2wheels said:**
> The process changed in Intrepid from the way Hardy used to do it, do not use instructions for Hardy.

1. Install Virtualbox from their website, I believe only the non-ose (open source) version supports usb so be sure to select that one. Anyone feel free to correct me if I am wrong there...

2. Add your user to the vboxusers group [Applications->Accessories->Terminal]:
```

sudo adduser your_user_name vboxusers

``` 

3. Add the following line to /etc/fstab: none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 as follows:

```

gksudo gedit /etc/fstab

```

and add to the end of the file:

```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Save the file and reboot.
Thanks, added user name per step #2. However, where am I adding the lines to in step #3? I must be really thick...

---

### Post by ju2wheels on 2008-11-08
For step 3, after you run the command "gksudo gedit /etc/fstab" you should get a window that pops up with the file /etc/fstab in it. Then you add the two lines I listed to the bottom of /etc/fstab.

Edit: To "run" that command you have to type it into the command terminal which you can open by going to Applications->Accessories->Terminal.

---

### Post by garystam on 2008-11-08
> **ju2wheels said:**
> For step 3, after you run the command "gksudo gedit /etc/fstab" you should get a window that pops up with the file /etc/fstab in it. Then you add the two lines I listed to the bottom of /etc/fstab.

Edit: To "run" that command you have to type it into the command terminal which you can open by going to Applications->Accessories->Terminal.
Did it! So now should a USB icon show up in the Details of Virtual Box OSE, because it doesn't, or will USB just work??

---

### Post by ju2wheels on 2008-11-08
Refer back to step 1, Virtualbox OSE (Open Source Edition) does not have USB support. You have to install the closed source version from their website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) You can either download it from their site using the links at the top or add the repositories by following the instructions on the bottom of the page.

---

### Post by garystam on 2008-11-08
> **ju2wheels said:**
> Refer back to step 1, Virtualbox OSE (Open Source Edition) does not have USB support. You have to install the closed source version from their website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) You can either download it from their site using the links at the top or add the repositories by following the instructions on the bottom of the page.
It works perfectly, with your help! Thanks for helping a newbie.

---

