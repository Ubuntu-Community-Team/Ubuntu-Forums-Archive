---
title: "NTFS HDD w/ Win7 to Ubuntu and now back"
date: 2013-01-16
forum: Hardware
---

### Post by Monegaskeren on 2013-01-16
Hello everybody.
I am a very ubuntu user and I am trying to setup a homeserver running Ubuntu server 12.10.

Since I have never worked with anything but windows, I am following this - so far excellent - guide: [http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

I have a 2TB Hitachi drive in my win7 pc formatted as NTFS, containing all my media and other storage, including homevideos and private photos.

I made backup of most of my data including the very important parts, and tried to mount the HDD in my ubuntu-server-PC, using webmin 1.610.
I added the HDD as a physical drive, then got cold feet and deleted it again, and now i cannot read the disk in win7.

I thought i could mount the drive and keep all files, but now I am afraid I lost it all, and want it back!

Can anyone help?

-Johnny

---

### Post by ahallubuntu on 2013-01-16
Simply mounting a partition on an external hard drive doesn't modify its contents, although you have to UN-mount it properly (you can't simply pull out the USB cable at will) or you could mess up the contents.  Same is true for Windows 7 - you must "safely remove" any external drive or you could corrupt the data on the drive.

So - exactly what did you do?  What do you mean "deleted it?"

In Windows, you can try running an Error Check to see if chkdsk can fix any filesystem issues that could have been caused by not removing the drive properly in Ubuntu.  But it's possible you formatted the drive in Ubuntu and erased everything on it.

FYI, next time I urge you to use Desktop Sharing in Ubuntu not Webmin to start playing with a home server.  Desktop Sharing (aka "Remote Desktop") lets you see/control the screen of the Ubuntu machine on your local machine, as if you were sitting in front of it with a keyboard.  Also, Ubuntu 12.04 LTS is probably a better choice for a beginner in this situation than 12.10 for various reasons.

---

