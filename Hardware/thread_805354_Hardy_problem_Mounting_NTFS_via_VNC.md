---
title: "Hardy problem: Mounting NTFS via VNC"
date: 2008-05-23
forum: Hardware
---

### Post by gripen40k on 2008-05-23
Hi, I ran in to a rather aggravating problem with the new Hardy release concerning mounting an NTFS drive using the gnome gui while in a VNC session. It's a mouthful I know but here is what I was doing and how I managed to fix the problem:

While in a VNC session, I wanted to mount a drive called 'DATA'. This drive was available under 'Places' in the drop down menu. Clicking on it while in Gutsy would ask you for your password and then mount the thing and allow you to view its contents. In Hardy however clicking on it brings up a warning message like:
"Cannot mount volume
Error org.freedesktop.dbus.error.accessdenied"
And then talks about a security policy that prevents me from sending a message to a recipient.

To fix this, I just went to the terminal and put in:
```
sudo blkid
```
To find the id of my DATA drive (which will be something like /dev/sda2)
I then used that info in the following:
```
sudo gnome-mount -vbd /dev/sda2
```
Which will allow you to mount/view/write your files.

This was annoying so I found a post that allowed me to auto mount the drive by editing fstab:
```
sudo gedit /etc/fstab
```
And then adding the line:
```
/dev/sda2  /media/data  ntfs  defaults,umask=007,gid=46 0 1
```
Where the sda2 was determined from before and the /media/data is the name of the drive.

Hope this helps anyone who might have been having problems with mounting a drive remotely. Note I haven't tested the auto-mount thing yet (don't want to restart my computer) so hopefully it works.

---

