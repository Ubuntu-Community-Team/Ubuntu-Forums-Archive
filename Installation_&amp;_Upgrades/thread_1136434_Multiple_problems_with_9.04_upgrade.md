---
title: "Multiple problems with 9.04 upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by reswob on 2009-04-25
I've been using Ubuntu since 7.04.  Every previous upgrade has gone just fine.

I used the alternate CD to do this upgrade as I figured the servers would be hit pretty hard.  However, after the upgrade several problems showed up.

1.  I cannot open any folders.  If I click Places - Home Folder, Places - Computer, or any other folder, I get a window that says 'Starting' but then it goes away and never opens up.  No error messages either.

2.  When I clicked on the Update Manager, it tells me there are a number of updates, but I can only do  partial update.  When I click on the "Partial Update" button, it downloads the updates, but then abruptly closes without installing.

3.  None of my network shares are mounted.  When I do a mount -a I get the following for each drive:

mount: wrong fs type, bad option, bad superblock on //<IP>/<folder>,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

4.  My video settings are screwy.  I have the NVIDIA X Server Settings application loaded, and it worked in 8.10, but when I run it now I get the following:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

And when I try and run 'sudo nvidia-xconfig' I get a message telling me that nvidia-config can't be found.

ARGH...  Any ideas will be helpful.  Please help.

Thanks.

---

### Post by aconsumer on 2009-04-27
Yah.. Im having the same problem as well. Except not the video program in running an old ATI video card. But I cant access my folders or files. No home directory or even mounted drives. Its odd, becuase I know  they are there, just cant open the folders. I can see the files when I search for folders but I cant open them or view pictures or anything. Hopefully will get a fix for this it is quite crazy -=p

---

### Post by reswob on 2009-04-29
OK, I've solved most of my problems.  

1st I did a complete reinstall with the 9.04 CD (NOT the alternative CD).  Here's the result:

1.  Still no folders.
2.  Update manager no longer has a problem
3.  Network shares was my fault.  Forgot to install smbfs.  After the install, works just fine.
4.  9.04 new install asked if I wanted to install NVIDIA driver.  I said OK and now have proper graphics.

As far as problem #1, I kept searching among the forum threads and among the launchpad.net/ubuntu and lanchpad.net/nautilus tickets.  There are multiple threads describing nautilus having this problem going back a couple of years.  I tried many of the suggested solutions with no success.  The solutions that worked turned out to be simply making sure that there was not a CD in the drive when Ubuntu started up.  I removed my CD and voila!  Folders and Desktop worked.  

Anyway, that's my current status.

---

