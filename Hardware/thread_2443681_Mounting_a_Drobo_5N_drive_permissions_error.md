---
title: "Mounting a Drobo 5N drive permissions error"
date: 2020-05-18
forum: Hardware
---

### Post by douglapsley on 2020-05-18
I'm trying to mount a Drobo 5N in Ubuntu 18.04.4 using a credentials file and /etc/fstab.

Network share names:

//DroboNAS.local/DougiOnly/

I've tried mounting at /media/DougiOnly/ and /mnt/DougiOnly/ and /home/dougi/DougiOnly/

Currently /home/dougi/DougiOnly/ from a suggestion in one of the forums, although I'm not sure this is good practice.

nano /etc/fstab I have:

//DroboNAS.local/DougiOnly/ /home/dougi/DROBO_DougiOnly cifs credentials=/home/dougi/.smbcredentials,users,rw,iocharset=utf8,vers=1.0,sec=ntlm 0 0

...where /home/dougi/.smbcredentials is a credentials file with username and password.

I can view the content of the folders and they show up in file manager in the left hand column.  However, I cannot write anything to the folders on there (and yes, they do have read write access on the actual Drobo share itself).  Deja Dupe is therefore unable to back up to them.

I had it working fine on my 16.04 machine, but upgrading to 18.04.4 and setting up the share again seems to be problematic.

Any ideas please?

---

