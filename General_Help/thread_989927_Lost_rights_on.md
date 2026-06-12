---
title: "Lost rights on /"
date: 2008-11-22
forum: General Help
---

### Post by Kargolh on 2008-11-22
I did a sudo chmod o-rwx /
And now my system fails to boot.

I booted in safe mode and dropped to root console but it doesn't reconize my password. So I cannot log as root by this way.

How can I restore rights on / ?
(I have a dual boot Win XP/Ubuntu).

Thanks in advance.

---

### Post by Monotoko on 2008-11-22
hmm....try this:

boot from the LiveCD
mount the partition ubuntu is on
and chmod that back to how it was (it will be in the dir /media/disk, thats what you want to chmod) 

try to reboot

---

### Post by lotharz0r on 2008-11-22
You have to boot from a livecd, mount your root filesystem and then change back your rights.
If you dont know what partition is root you can try using the command fdisk -l and look at the filsystem.
If you got a standard setup with one NTFS partition for windows, one SWAP and one linux partition it should be easy to see which one you need to mount.
Then just do
mount /dev/sdxx /mnt
and change your rights back the way they should be

You are lucky you didnt put on a -R on that command, that would have recursivly changed the rights on everything mounted ;)

---

### Post by Kargolh on 2008-11-22
Thanks to your help the problem is now solved. I managed to change back the rights.

Thanks to both of you.

---

