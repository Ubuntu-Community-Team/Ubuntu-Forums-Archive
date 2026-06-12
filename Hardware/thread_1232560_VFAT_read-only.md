---
title: "VFAT read-only?"
date: 2009-08-05
forum: Hardware
---

### Post by n3pla2000 on 2009-08-05
One week ago I began having problems mounting my Western Digital "My Book". I have had this drive since December 2008 and have not had a single problem. Presently I have figured out a way to by-pass the problem, but not solve it.

First I am using the Kubuntu variation of Ubuntu, I have the 1TB My Book which is actually a little less than a TB after the VFAT file system is put into place. This is an external USB drive. I also have an external Sony USB DVD Drive and a PNY 16GB thumb drive. The DVD Drive mounts read-only on most data DVDs and CDs, the exception being rewritable Discs. The Thumb Drive Mounts as Read-Write. Here is where the problem is...

If the computer is running and I plug-in the My Book, hald mounts the drive automatically which is fine, but it mounts it as read-only which makes it unable to be used. If I unmount the drive using the device-notifier widget on the taskbar, I can not mount the drive manually. If I switch to root user I can mount the drive RW. Mind you now, before I was mounting and unmounting using the device-notifier widget and it always mounted as RW. Now I must do this as root and can not write access it unless I mount it as the root user.

I have tried using the usermount graphical mounter/unmounter it responds with the following message...

"There are no filesystems which you are allowed to mount or unmount.
Contact your administrator."

When I try to mount it with the device-notifier widget it allows that but it mounts it again as read-only?

So for now I must open a terminal drop to root and use the "mount -t vfat -rw /dev/sdc1 /media/My_Book" command. I would rather not drop to root.

Walter

---

### Post by aysiu on 2009-08-06
I don't know what's going on, but maybe there's a better workaround.

Paste this command into the terminal with your My Book plugged in ```
blkid
``` That command should tell you the UUID of of your drive. Then make sure the mount point for it exists: ```
sudo mkdir -p /media/My_Book
``` and make a backup copy of your /etc/fstab file: ```
sudo cp /etc/fstab /etc/fstab.bak
``` and edit it: ```
sudo nano /etc/fstab
``` Append this line at the end of the file: ```
UUID=*allsortsofgibberish* /media/My_Book vfat user,iocharset=utf8,umask=000 0 0
``` where *allsortsofgibberish* is the UUID you got from the *blkid* command.

Save (Control-X, Y, Enter).

Hopefully that'll fix it semi-permanently, but you may still have to use root to unmount the drive.

---

