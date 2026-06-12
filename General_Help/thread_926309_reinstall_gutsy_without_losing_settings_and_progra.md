---
title: "reinstall gutsy without losing settings and programs"
date: 2008-09-21
forum: General Help
---

### Post by sagesparrow on 2008-09-21
I'm using Gutsy and am trying to get wifi working.  I followed a number of sets of instructions.  Now I think maybe it would be best to start from a new install as i think there may be vestiges of these attempts in various locations.  Any way to reinstall Gutsy without losing my settings and installed programs?  

If I have to redo too much, I'll probably just live without wifi or just keep troubleshooting.

I'm hesitant to upgrade as I see many problems listed with Hardy.  For the most part Gutsy has been fine (wifi is an exception along with hibernation and a few other things)

---

### Post by Monotoko on 2008-09-21
backup, and do a reinstall, then get what you need from the backup

---

### Post by sagesparrow on 2008-09-21
I like your signature.  You seem like the perfect person to answer this question.

Now, could you explain a little more about backing up?  which directories need backing up?  just copy and save on another partition?  once fresh install is complete substitute those saved directories for the new versions?

thanks

---

### Post by mb_webguy on 2008-09-21
All of your settings are located in your home folder.  Open Nautilus, hit Ctrl-H to view hidden files, and copy everything to a blanc disc, USB drive, or other partition or drive.  After you reinstall, just copy everything back into your home folder.  (Although this is the reason I like having a separate home partition.)

As for backing up programs, it would probably be easier and safer to just reinstall any applications you've installed from the repositories.  If you've installed anything from source or debs you downloaded from the internet, then you can backup the /usr/local/ and /opt/ directories the same way you did your home directory.  You will probably need to be root to do this, so you might as well do this from the command line.

The biggest problem with backing up files is keeping the existing permissions.  If you backup the files to a filesystem that uses Linux-style file permissions, you should be okay.  If you backup the files to a drive formatted as FAT32 or ntfs, you might have a problem when you restore the files, and may need to use the chmod and chown commands to fix the permissions.

---

### Post by sagesparrow on 2008-09-21
great.  that's very helpful and complete.  perhaps i could create a ext3 partition on a flashdrive.  but either way, it's not too bad to change permissions.

thanks

---

### Post by C.S.Cameron on 2008-09-22
The following worked for me copying a home folder.
[http://ubuntuforums.org/showthread.php?t=919612](http://ubuntuforums.org/showthread.php?t=919612)

---

