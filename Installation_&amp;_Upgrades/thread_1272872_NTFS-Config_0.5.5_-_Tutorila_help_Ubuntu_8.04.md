---
title: "NTFS-Config 0.5.5 - Tutorila help Ubuntu 8.04"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by squirtmph on 2009-09-22
**What I did**: by default ubuntu has read only ntfs support. 
 you can add read write support by installing [COLOR=Red]ntfs-3g[/COLOR] in the same manner as installing unrar. ----> I have use _synaptic graphical package manager_

Here what it say the window after installed:
> $ log file indicate showdown (0,1) failed to mount '/dev1': operation not supported mount is denied because NTFS is marked to be in use. 
Chose one option 
Choice 1 
If you have windows then disconnect the external devide. 
Choice 2 
If you don't have windows then you can use the "force' option for you own responsibilities for example: 
Type the command line. 
[COLOR=red]mount-t ntfs-3g/dev/sdb1/media/freeagent drive -0 force[/COLOR] 
OR 
add the option to the relevant row in the: 
/etc/fstabfile: 
[COLOR=darkred]/dev/sdb1/media/freeagent/drive ntfs-3g force 0 0[/COLOR]
[B]How do i do this it sound very complected for firs time novice like me, i just wanted to read the external hard drive like I did before
[/B]If there was no error during installation then the NTFS volume can be mounted in read-write mode for everybody as follows. Unmount the volume if it had already been mounted, replace /dev/sda1 and /mnt/windows, if needed. 
 
 [COLOR=red]mount -t ntfs-3g /dev/sda1 /mnt/windows[/COLOR] 
OR 
You can also make NTFS to be mounted during boot by adding the following line to the end of the /etc/fstab file:  
 
[COLOR=red]/dev/sda1 /mnt/windows ntfs-3g defaults 0 0[/COLOR]

---

