---
title: "Root Access needed for Using HDD"
date: 2010-04-16
forum: Hardware
---

### Post by arjunbajaj on 2010-04-16
Hey, 

I have a problem. I have a 95gb ext4 partition on my laptop. The total Size is 160 gb.
I cannot use the drive means i can mount it but i cannot paste data on that drive.
In the [SIZE=2]properties of that drive it tells me that i'm not the owner of the drive[/SIZE]. I am the only user on the laptop and i even have root access but i cannot edit the properties of that drive.

Please help me fast............thnx........

---

### Post by ajgreeny on 2010-04-16
To automount at boot time a linux file-system drive:-
1.  Make a mountpoint folder in media with ```
sudo mkdir /media/linux
``` but use whatever folder name you want.

2.   Add a line to your /etc/fstab file similar to this:-
```
/dev/sda# /media/linux ext4 defaults, relatime 0 1
``` but change the mountpoint to whatever you made in step 1, and also make sure you get the /dev/sda# right.

3.  Run ```
sudo mount -a
``` in terminal to mount everything listed in fstab, including your 95GB partition, provided you got all the device names and mountpoints correct.

EDIT:-
4.  Change ownership of the mountpoint folder to yourself with ```
sudo chown username:username /media/linux
``` This will allow you to write to files that are within that folder, provided those files are already yours.

---

