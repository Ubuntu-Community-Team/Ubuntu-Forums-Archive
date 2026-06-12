---
title: "backup and re install"
date: 2008-07-28
forum: General Help
---

### Post by timboellis on 2008-07-28
I have been testing the newer version of Ububtu as a Windows install meathod and reasonablt happy to transfer accoss completely ie no partition.

However I have Ubuntu setup perfectly the way I want it installed my worelss graphics sound etc. is there a way to backup all the installed apps, settings and config files including mail so when i go to reinstall i do nto need to redownload and configure it all again?

---

### Post by DagMan on 2008-07-29
It sort of difficult to undertand, but as for your desktop layout you want to save the entire contents of your /home/username folder, including the hidden files.  Just copying normally won't save the hidden files, which are the important ones.  Also, you may have problems with file permissions if you copy the files to an ntfs partition, or fat partition, etc.
The best thing is to store it in a tar file, which is like a zip file.  This will preserve the file permissions.
I think the following should work, open a terminal and do this:
```
tar -cf my-settings.tar . --exclude ./my-settings.tar
```
you may have errors about a file or two because of permission problems.  Don't worry about that.

and then after you install do this from your users home folder
```
tar -xf my-settings.tar
```
I'm not familiar with the file permission ID numbers associated with usernames in a Windows install of Ubuntu, and hopefully it isn't a problem, but in the case that it is, and for example you can't access something or delete something or it says permission denied, you would do this
```
chown USERNAME:USERNAME * -R
```from the home directory of the installed system, and if that doesn't do it, then do the same thing using sudo but make sure you are in your home folder if you use sudo.  Hopefully you'lle just make the tar file, copy it out to somewhere, then copy it to the newly installed folder and unpack it and be done.

There's other settings stored in for example the /etc folder and in a few other places but it will be best to leave them alone as some things might be specific to the install within Windows and will be differant from an actual install on the drive.

The above should go a long way if it is done properly.  The worst thing that can happen is that it doesn't work.

---

### Post by dexter.deepak on 2008-07-29
take a complete backup of your system using rematersys :
```
sudo apt-get install remastersys
```
you will have an exact copy of your present system in the image formed.

---

### Post by DagMan on 2008-07-29
If I understand correctly, he currently has ubuntu set up in a VM with Windows as the host and wants to make a native install of the OS to a partition on the drive.  If that's the case then remastersys will just make a backup of the OS as it was setup for whatever computer the VM appears to be, and not the actual computer the VM is running inside of.  Hard to decipher his post though.
Can you clarify on that point, timboellis, as to what exactly you want to do?  Are you wanting to install ubuntu to the hard drive or just backup the current ubuntu for use in the same manner?

---

### Post by timboellis on 2008-07-29
Cheers exactly what I needed

---

### Post by nutsy.ben on 2009-11-12
Hi guys! 

I would like to do kind of the same.
My ubuntu is on a second hard drive that I 'd like to switch as the first one. (and the first as the second one).


I guess re-writing the GRUB would be sufficient, but I am not feeling confident about it and thought backing up and reinstalling would be enough.

> **dexter.deepak said:**
> take a complete backup of your system using rematersys :
```
sudo apt-get install remastersys
```you will have an exact copy of your present system in the image formed.

Is this code would copy the GRUB ?

---

