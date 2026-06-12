---
title: "USB bootable and security to installed volume"
date: 2008-11-14
forum: General Help
---

### Post by allochthonous on 2008-11-14
I am a bit of a Linux/Ubuntu noob, so pardon the basic question.  I have been playing with the Ubuntu bootable USB version that you can create from the Live CD and it is truly amazing.  I want to be able to use it to open/public access points with my laptop without risk to my data on my hard drive (Vista).  Currently in my testing at home I remove the hard drive to accomplish this.  This would be a bit of a pain to do while out and about. 

How do I "hide" or protect my NTFS volume from attacks or prying eyes while using the USB Ubuntu?

Is it as easy as simply unmounting the volume? Does this truly hide the volume from all parts of the OS?

Thanks,

Paul

---

### Post by DerHesse on 2008-11-14
> **allochthonous said:**
>  
How do I "hide" or protect my NTFS volume from attacks or prying eyes while using the USB Ubuntu?

 
Hi Rocky,
if you have created a persistent installation on your pen-drive you can simply remove any other drives from the configuration file.
 
To do this, simply copy the content of your fstab file by opening that file e.g. from the comand prompt (Konsole):
 
```
$ gedit /etc/fstab.  
```
 
then paste the content here.
 
To uncomment all unnecesary items, this file needs editing.
Me or somebody else will give you advice how to proceed, once you have replied. :)
 
Cheers 
DerHesse

---

### Post by C.S.Cameron on 2008-11-14
With a persistent install your HDD will come unmounted and should be secure.
If you want to access it you need to mount it.

---

### Post by allochthonous on 2008-11-16
The drive/partitions do appear in "Computer" but it does look like they are unmounted.  However, all one has to do is double click and the drives are mounted and accessible.  So if they are unmounted, they are safe?  I think I would prefer that they do not appear at all.

This is the content of that file:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


Also, when I set up the boot USB drive, I could specify how much of the drive to devote to settings. I intentionally left a bit of space on the drive open.  Is there any way to access that space inside Ubunutu?  For example, i create a document in Ubuntu and want it to be available if I plug the drive into a Windows box? Or vice versa?

Thanks,

PK

---

### Post by allochthonous on 2008-11-18
Anyone?

pk

---

### Post by C.S.Cameron on 2008-11-18
You can make a folder inside Places, Computer, File System /cdrom.
This will be accessible to windows.
The more space you use for persistence, the less space you will have here.

---

### Post by allochthonous on 2008-11-19
Hmmm..I see.  So would any documents saved within the persistence space be accessible outside of Ubuntu?  I am guessing not.  

How about my Windows volume(s)?  How can I hide them completely from the Ubuntu OS?  This is a Dell, so there is a Recovery, a MediaDirect, and an OS partition on the HDD.

pk

---

