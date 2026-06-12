---
title: "External hard drive case not showing"
date: 2008-11-07
forum: General Help
---

### Post by sirdouglas on 2008-11-07
I posted this in another forum already, but after bumping it too many times with no responses I'll try here:

I have an external Kingwin hard drive case with a 300gb hard drive installed.  Upon my first time using Ubuntu Ultimate 1.4, the hard drive worked as read-only, but was not writable.  After an upgrade to 7.10, the hard drive appeared as at least existing, although it wouldn't mount and couldn't be opened as read-only or writable. Now I'm upgraded to to Ubuntu 8.10, and nothing happens when plugged in, nothing. It just seems strange that the problem would gradually grow through all the upgrades. Anything that could help me out?

Thanks!

Doug

---

### Post by sirdouglas on 2008-11-10
Pretty please?

---

### Post by tarps87 on 2008-11-10
Do you know what format the drive is?
Can you post the output of ```
fdisk -l
```
l = lower case L

---

### Post by sirdouglas on 2008-11-12
Alright, here's where I'm at... I just plugged in the external hard drive today and something actually happened (it was an error, but at least it was something).  Two boxes popped up, one saying:
 "Unable to mount New Volume
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

And the other:
"Cannot mount volume.
Unable to mount the volume 'New Volume'.
Details:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by      clicking on the 'Safely Remove Hardware' icon in the Windows     taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for     your own responsibility.  For example type on the command line:     mount -t ntfs-3g /dev/sd1 /media/New Volume -o force    Or add the option to the relevant row in the /etc/fstab file:     /dev/sdb1/media/New Volume ntfs-3g force 0 0"

The second error was not able to be high-lighted for me to copy/paste, so I hope I typed it out correctly.

Now after typing "fdisk -l" in the terminal:

"Cannot open /dev/sda
Cannot open /dev/sdb"

Any ideas?

Thanks guys for the help, greatly appreciated!

Doug

---

### Post by tarps87 on 2008-11-12
Try connecting it to a windows machine then clicking "safley remove device". It sounds like you have used it with windows and incorrectly/unsafely removed the device so windows has not removed the lock on it, this usually occurs by just unplugging the drive. It can also happen when duel booting with windows and the windows OS was not correctly shutdown
Once you have done this if it does not work try
```
sudo fdisk -l
```
The previous should have just listed external drive this will list all drives/partitions

As a last resort you will have to force mount the drive.
```
man mount
```
and
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
for information on mounting or post the output of the first command in this post and I will give you more detailed help

---

### Post by sirdouglas on 2008-11-21
Simple- plugged it into a Windows computer, safely removed hard drive, and upon plugging it into the Linux computer it worked!  Even to write onto!  Thanks you so much for the help!

Doug

---

