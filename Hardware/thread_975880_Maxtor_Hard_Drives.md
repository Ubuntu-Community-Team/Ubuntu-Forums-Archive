---
title: "Maxtor Hard Drives"
date: 2008-11-08
forum: Hardware
---

### Post by hgais on 2008-11-08
Okay, this is relatively urgent.  My internal HD is about to die (according to Mac tech support) for whatever reason, and I'm trying to verify whether or not I will be able to back up files and transfer them again on to my new HD.  I have a Maxtor One Touch 4 HD that I purchased about two or three months ago, which, while it worked fine on Mac, has begun to have some issues on Linux.  When I first installed Ubuntu, I was able to drag-drop some files on to my internal from the external, but, for whatever reason, it's no longer working.  I tried changing the permissions via Nautilus on root, but for some reason the permission changes don't stay.

For example, I typed in the terminal:
sudo nautilus (i.e., once I was logged in as root)

In the root file browser, I went to the section One Touch 4, went to preferences, and tried to change it to read/write (as opposed to read-only).  For whatever reason, once I do this, it does not stay (even after supposedly applying the changes).  I could view folders I could not view without being logged in as a superuser, and I could drag/drop on to the root desktop.  However, the issue is -- and I'm worried this will carry over when I have to reinstall Ubuntu again -- my account (hgais) refuses to recognize the drive, because I "don't have the permission."  If anyone could be of any assistance, that would be great.  I have to get a new internal HD tomorrow, so I'm freaking out a bit...

---

### Post by sirebral on 2008-11-08
have you encrypted the drive?

---

### Post by hgais on 2008-11-08
No, I have not.

---

### Post by sirebral on 2008-11-08
maybe you didn't unmount it and you need to remount the drive.

try unmounting the drive and then remounting it.

---

### Post by hgais on 2008-11-09
Also tried that.

---

### Post by sirebral on 2008-11-09
Sorry hgais,

I tried but I cannot fix this.  I think the only advice I can offer is to attempt to unmount the drive by force and then remount it.

I had a similar problem with a drive.  I think I shut it off with the drive on, and then I was unable to access it until I forcefully removed it from a permanent mounted state.

Try this for more info: [http://dsl.ee.unsw.edu.au/dsl-cdrom/unsw/common/cdrom-mounting.html](http://dsl.ee.unsw.edu.au/dsl-cdrom/unsw/common/cdrom-mounting.html)

EDIT:

BTW, Linux seems Plug n' Play safe on entrance, but not on exit.  There is no 'Safely Remove Hardware' feature.

---

### Post by ciscosurfer on 2008-11-09
> **hgais said:**
> Okay, this is relatively urgent.  My internal HD is about to die (according to Mac tech support) for whatever reason, and I'm trying to verify whether or not I will be able to back up files and transfer them again on to my new HD.  I have a Maxtor One Touch 4 HD that I purchased about two or three months ago, which, while it worked fine on Mac, has begun to have some issues on Linux.  When I first installed Ubuntu, I was able to drag-drop some files on to my internal from the external, but, for whatever reason, it's no longer working.  I tried changing the permissions via Nautilus on root, but for some reason the permission changes don't stay.

For example, I typed in the terminal:
sudo nautilus (i.e., once I was logged in as root)

In the root file browser, I went to the section One Touch 4, went to preferences, and tried to change it to read/write (as opposed to read-only).  For whatever reason, once I do this, it does not stay (even after supposedly applying the changes).  I could view folders I could not view without being logged in as a superuser, and I could drag/drop on to the root desktop.  However, the issue is -- and I'm worried this will carry over when I have to reinstall Ubuntu again -- my account (hgais) refuses to recognize the drive, because I "don't have the permission."  If anyone could be of any assistance, that would be great.  I have to get a new internal HD tomorrow, so I'm freaking out a bit...Let's begin to step through this.  

We generally like to avoid logging in as root.  More on this [here]("https://help.ubuntu.com/community/RootSudo") and [here]("http://ubuntuforums.org/showthread.php?p=4782741").  That said, if you are logged in as root, or have elevated yourself via sudo -i for example, you don't need to prepend your commands with sudo.

If you're computer is still under warranty with Apple (you reference Mac tech support), I would suggest taking it to them as soon as possible and have them begin to try to transfer your data for you.  That is the easiest thing you can do.  If it's not under warranty any longer but the data is important to you, I would still suggest you bring it to an Apple store and have them mess with it.  

The permissions problem most likely has to do with disparate filesystems.  Your stock Ubuntu is using ext3 and I don't know what the Maxtor is using but presumeably it is something compatible with Mac OS.  Copying items from the external to the internal probably worked fine, but not the other way around.

Again, if you're seriously concerned about loss of data and don't want to meddle with it, taking it to Apple would be my suggestion.

---

### Post by hgais on 2008-11-09
Someone at the Mac Store noted that it might be the fact that my hard drive was failing (i.e., I could not change permissions because of some sector on my internal hd was screwed up).  I'm not sure if this is the case, but it seems plausible.  However, I can transfer files from Nautilus when I'm logged in as root, so it should be okay-ish when I have to reinstall Ubuntu after getting a new hd. 

The data isn't going anywhere, so I suppose I'm not too worried.

---

### Post by hgais on 2008-11-09
PS: Since I haven't had Ubuntu for long, I did manage to back up most of my data on a CD.  So no worries about that.  I suppose once I reinstall and transfer the files, I can reformat the Maxtor.  Is it possible it was NTFS, which I hear is particularly "liked" by Linux?

---

### Post by ciscosurfer on 2008-11-09
> **hgais said:**
> PS: Since I haven't had Ubuntu for long, I did manage to back up most of my data on a CD.  So no worries about that.  I suppose once I reinstall and transfer the files, I can reformat the Maxtor.  Is it possible it was NTFS, which I hear is particularly "liked" by Linux?These days, NTFS filesystems can be read-write accessible much more easily than in days past.  Sure, it's possible the One Touch used it.  At the same time, as far as I know, it's also just another external hard drive.  Meaning that you could use any filesystem you'd like.

 The ntfs-3g driver is an open source, GPL licensed, third generation Linux NTFS driver which was implemented by the Linux-NTFS project. It provides full read-write access to NTFS, excluding access to encrypted files, writing compressed files, changing file ownership or access rights. 

I would recommend installing ntfs-config (in addition to ntfs-3g, which is already included in 8.10 Intrepid) it will help you in setting up your fstab, labeling, location of the mount point, and read-write access both internal and external.```
ntfs-config
```Some info grabbed from [this page]("http://packages.ubuntu.com/intrepid/ntfs-3g").

---

