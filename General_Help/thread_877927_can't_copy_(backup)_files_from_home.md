---
title: "can't copy (backup) files from /home"
date: 2008-08-02
forum: General Help
---

### Post by MountainX on 2008-08-02
I tried to copy everything in my /home partition to another drive (on the same computer) as a backup. The operation fails (hangs) every time.

I narrowed it down to a problem with the folder /home/.gcjwebplugin. Inside that folder are two zero-byte files (of type pipe). 

Can anyone explain these files to me and why they make the file copy operation hang? Shouldn't the operation handle this with either an error message or something other than an infinite hang?

Thanks.

---

### Post by ajgreeny on 2008-08-02
I am baffled as to why that is happening, but have you tried using grsync or even rsync to do the backup?  It will make future backups much quicker if you use one or other of those, and it may be able to handle the zero byte files better.

Also what format type is the other drive?  It may be better to backup to ext3 if you want to keep all the permissions etc etc. though I don't see why it should stop the current operation.

---

### Post by MountainX on 2008-08-02
I have not tried rsync or grsync yet. I am fairly new to Linux, so rather than just "work around" this issue by using another application, I would really like to understand it. 

Does it mean I have a hardware problem? A software (OS) problem somewhere? How can I track it down?

Right now I have a mix of NTFS and Ext3, but I am slowly getting rid of all the NTFS formatted stuff. 

One of my next steps is to learn more about security with NFS. But for now, I want to understand what is going on here before I start risking my more important data as I switch from a Windows world to a Linux world.

---

### Post by russlar on 2008-08-02
If I may suggest not using the cp -rp command, or drag and drop through the GUI, to back up your /home. ajgreeny suggested rsync to back up, and that is probably the best way to do it. I use rsync -av --delete /home {destination}. The -a flag tells rsync thta this is an archive, the -v flag makes the process verbose (prints on screen each file as it's copied), and the --delete flag removes files from the destination that no longer exist on the source.

---

### Post by linfidel on 2008-08-02
> **MountainX said:**
> I have not tried rsync or grsync yet. I am fairly new to Linux, so rather than just "work around" this issue by using another application, I would really like to understand it. 

Does it mean I have a hardware problem? A software (OS) problem somewhere? How can I track it down?

I doubt that this is an OS or hardware problem, actually.  The files are named pipes, used by gcjwebplugin, a java plugin for Mozilla.  You can create your own named pipe, named test,  by typing:
mkfifo test
If you do "ls -al", you will see that the permissions will be "prw-r--r--", where the p means it's a named pipe.  You can use chmod to change the permissions like any other file, or chown to change the owner.  But, I don't think you can copy it even if you have full permissions.  It seems to hang forever when I try it with the test file, even with R/W permissions.

I don't really know the solution, unfortunately.

---

### Post by MountainX on 2008-08-02
Thanks for the explanations

---

