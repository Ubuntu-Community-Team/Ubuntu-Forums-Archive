---
title: "Vbox  - can't alter permissions"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by scotc on 2009-07-01
I have Ubuntu 8.04 64bit host and XP guest inside Vbox that has lost permissions.

The harddrive has 3 partitions:  
- XP, 
- Ubuntu (with vbox hosting XP), 
- E: for documents, shared.

Earlier it was all working fine, but now, in XP guest in Ubuntu, I can no longer write to the shared drive (logical E: in my case).

I CAN see the files and OPEN them but the parent directory is showing (in XP) as read only, so I can't save.

I've been through all the obvious things forums have told me to give full access.
- I have reinstalled guest additions
- I have double checked the "shared folders" on the vbox
- I fiddled with Samba with errors and gave up

The permissions broke today sometime during the following changes in Ubuntu:
- I fiddled to get nvidia working
- I sorted the screen res
- I was unsuccessful in getting suspend/resume working ACPI

Also, upon a reboot into Windows XP (the full OS) I found that the shared logical E: was "not formatted".

A few reboots into each OS solved that (for now).

I'm pretty sure this is all a case of how the OSes are "seeing" the e: drive, but I don't have enough skill to tweak it.

Help please, for one of low-linux-skill.

---

### Post by tvtech on 2009-07-01
what version of Vbox are you on? what file system is E: using.  

I just upgraded to Vbox 3.0.0 today and found a bug.  It will read from, but will not write too ext4 drives, not sure about ext3 but I"m assuming it's the same.  It automatically adjusts the permissions under the vbox user group to read only.  very irritating, especially when using programs that automatically back things up!

---

### Post by scotc on 2009-07-01
hello tvtech
I'm on vbox 2.2.4
E: uses ext3, with the file conversion utility whose name I forget.

Update:  I find that it is not all files that won't write.

The problem file is MS Access.  It's from office 97 and is an .mdb file.

Further update:  I'm glad I've only wasted one minute of your time (4 hours of my own).

If I run Access first (in the xp guest) THEN open the file, it's fine.
If I double click on the file in a file browser, I get the read-only warning.

I have found Access to be funny about how the database files are open but this is a new one on me.

Thanks for the help and the quickness

Still, Vbox may have a bug as you say.

---

### Post by tvtech on 2009-07-01
MSoffice was my problem as well today.  I think it may have something to do with how the files are shared over the virtual network via shared folders.  I had a problem the other day where i couldn't relink a merged file.  I would say this is a vbox bug but it didn't crop up until I did my msoffice sp update yesterday? or the day before.....

if you don't have a launchpad or vbox account already I'd say get one and file a bug report for this.

You may want to change how your virtual network interface works between your guest and your host.  This might solve the problem.  But it also may be a translation problem between ntfs and ext file systems.  since windows can't read/write ext or jfs.

---

### Post by tvtech on 2009-07-02
I've been playing around with this a bit.   I don't think it's the networking interface.  I have 4-5 partitions and an ssh server to play with.  Some are formatted NTFS some are not.  I think there is something going on with Vbox specifically, not sure if it was caused by a recent update on Ubuntu's side or not.  

The something going on is it's having trouble translating from NTFS in the windows virtual machine to the EXT file system.  I'd have to dig into the logs to see exactly what's happening.  When I access my NTFS drives as network shares in my Vbox guest I don't have a problem.  I can read/write and the permissions never get reset.  I can even do this with a virtual link through an EXT file system.  However when I try to write back to an EXT file system vbox is resetting the user group permissions for the file.  I can write a file initially to an EXT file system either EXT3 or EXT4 but I can't re-write it because it sets the file permissions as read only.  I then have to go back and change the file permissions in my host OS  to be able to rewrite the file at all.  Very odd behavior.  

Have you found anything else useful?

---

### Post by tvtech on 2009-07-03
I entered a [bug report]("http://www.virtualbox.org/ticket/4381") for this problem over at Virtualbox.org

If you could go there and upload your .log files as well and describe the exact problem you had that will hopefully get this fixed sooner.  

Thanks.

p.s. I found that if you have an instance of Nautilus open in the host OS the Guest OS/Virtual Box doesn't re-assign the permissions of the file.

---

