---
title: "MyBook 500GB - you do not have permission!"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by monomaniacpat on 2008-02-25
I just got a 500GB MyBook external HDD primarily for use with mac. However, I would also like to be able to store films and music on there, so that I may use it with other computers. 

Sadly, whenever I try to write to the disc in Ubuntu, I get a warning saying I do not have write permission. I have tried using root with nautilus, but I get the same response.

Any ideas? I am using Gutsy.

Thanks.

---

### Post by jblackthorne on 2008-02-25
Most likely, the issue is simply that your Mac set the acl (access control list) parameters on the folder you are trying to write to such that your current user account does not have write permissions.  That is easily resolved.  First, let's confirm the drive itself is writable by root:

1.Type <alt><F2> to bring up the run application dialog box
2.enter “gksudo nautilus”
3.enter your password when prompted
4.Browse to the location of your connected MyBook (it will be at a path under /media with something like /media/MyBook)
5.You are now connected to the MyBook with root permissions, bypassing the acl issue if one exists.  
6.Now, try to create a folder.  Does that work?  

If the above works, then the probem is ACL related.  Fixing that would be a bit tricky in that your Mac and Gutsy do not share the same accounts.  As a result, changing ownership of a directory to an account on one system will break the other.  Instead of changing ownership, it is better to change  permissions.  If you are comfortable with the console, you can change permissions with the command:

(in a console)
* sudo -s (to become root)
* cd /media/<yoru MyBook device>
* sudo chmod 777 -R <a folder you wish to make world writable>

(in Nautilus)
right click on a MyBook folder desired
select “Properties”
click the “Permissions” tab
Do not change the owner, just change group and Others Folder Access to “Create and delete files”
Click “Apply permissions to enclosed files”

If all goes well, the above should do it.  :)

---

### Post by monomaniacpat on 2008-02-25
Thanks for your assistance. Unfortunately the above did not work. The options to make a new folder in the MyBook directory were greyed out under the "File" menu and holding the relevant keyboard shortcut obviously didn't work for the same reason.

Any further ideas?

---

### Post by jblackthorne on 2008-02-25
Did you format the MyBook drive on your Mac by chance? Let's find out some more details about it.  Can you please:

* Plug in the MyBook.  
* Right-click on the icon that auto-mounts and appears on the desktop and choose "Properties"

* Click the Permissions tab
  - Is your current login account the owner?
  - Does Folder Access show "Create and delete files"?

* On the Volume tab
  - What is the mount point?
  - what file system type.  I assume it is vfat
  - please print the entire "File System Line" in this post.  A read/write mount should look something like:

example:
File System vfat rw nosuid nodev uid=1000 fmask=0077 dmask=0077

---

### Post by jespdj on 2008-02-26
What filesystem type is the disk formatted with? If it is NTFS, then maybe [this thread](http://ubuntuforums.org/showthread.php?t=707717) is useful - try what logos34 suggests: install and run ntfs-config.

If it's not NTFS, then that's not going to help...

---

### Post by monomaniacpat on 2008-02-26
Thanks again.

See below for screenshots of the two properties tabs you asked for.

I was surprised to see the file system as hfsplus - never even heard the name before!

EDIT: sorry about the encroachment of the second screenshot - it is still clearly legible.

---

### Post by jblackthorne on 2008-02-27
Ah.  That solves it.  The MyBook came by default with a fat32 filesystem.  Fat32 is a Microsoft filesystem, but it works well on both Mac and Linux too.  For some reason, it seems that you reformatted the drive as HFS+ (probably journaled too).  HFS+ is a Mac proprietary file system.   At this point, you have two choices:

1. Reformat the drive to be fat32 (Recommended)

An easy way to format is to use the Gnome Partition utility.  This is not installed by default, but you can easily install it by:

* System/Administration/Synaptic Package Manager
* Install "gparted"

* Plug in the MyBook
* Find the icon on the desktop, right-click on it, click "Unmount"
* Access the program in "System/Administration/Partition Editor"

WARNING: Be sure you click the drive pull-down on the right to select the proper drive! /dev/sda is your installed hard disk.  Don't touch anything on that!  Your MyBook will be a whole other device, such as /dev/sdb.

* Choose the device corresponding to the MyBook on the right (probably /dev/sdb
* You will see one existing partition of type HFS
* Right-click on that partition, select Format To: Fat32 

NOTE: Of course, reformatting the drive will destroy all data, so back up all contents first.

2. Do some more advanced reading on how to mount a HFS+ file system in linux (requires a manual mount in the fstab).

Considering it sounds like you are new to Linux, my suggestion would be option 1.  Again, Fat32 is compatible with every operating system out there and very portable.  Thus, it will still work on your Mac and Linux box too.


Hope that helps!

---

### Post by Yellow Pasque on 2008-02-27
You won't have to reformat if you use the commands in the follIowing link's section on "disabling journaling"
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

