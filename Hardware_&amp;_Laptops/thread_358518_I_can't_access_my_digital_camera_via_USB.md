---
title: "I can't access my digital camera via USB"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by simonbrezovnik on 2007-02-10
Hi all this is my firs post and I have proudly lost my virginity. I have recently moved from Mandriva to Ubuntu and am finding it impossible to get my Kodak P850 digital camera to work on my Toshiba Satellite laptop. All of my other usb devices work fine for example my printer, mouse and memory stick. Bellow is a list of errors that I get.

[COLOR="DarkOrange"]I got this error using the F-Spot application

Error connecting to camera
Received error "Could not claim the USB device" while connecting to camera[/COLOR]

[COLOR="Red"]I got this error using the gThumb image viewer application

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.[/COLOR]

[COLOR="Blue"]I got this error using the gtkam application

Could not initialize camera.[/COLOR]

Could someone please help me. :?:

---

### Post by gradedcheese on 2007-02-11
The first thing to check is if the camera was mounted.  USB cameras act just like USB thumb drives and the like.  Does the camera come up as an disk icon on the desktop or anything like that?  What about if you open the terminal (Applications->Terminal) and run "mount"? (post the results here if you need to).

---

### Post by simonbrezovnik on 2007-02-11
The camera does not appear on the desk top. Below is the output i get when i  execute the mount command.

simonbrezovnik@thirsty-laptop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

The last line is a usb memory stick.

ps the end of the last line should read u t f 8 ) minus the spaces. It appears that last bit of text is used for an  smiley.

---

### Post by grendel38 on 2007-02-22
hello!  I have the same camera, and a Panasonic Toughbook (prehistoric I know).  I had the same problem.  This fixed it:

[http://www.ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb](http://www.ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb)

good luck

---

