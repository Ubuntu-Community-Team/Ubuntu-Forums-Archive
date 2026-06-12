---
title: "Installing another hard drive"
date: 2008-09-02
forum: General Help
---

### Post by BlackholeZ on 2008-09-02
My laptop has 2 hard drives, primary 80gb, secondary 100gb. I don't really know how the Ubuntu file system works. When I installed Hardy I partitioned both drives, and mounted the 100gb drive in /100GB/. When I try to write something to that folder I get an error "...cannot be copied because you do not have permissions to create it in the destination. The only thing in the 100GB folder is lost+found, which I cannot access(wtf is it?)

I Just want the two drives set up as separate drives, but I have not been able to find any instructions by searching. Any help is appreciated.

-Dan

---

### Post by silkstone on 2008-09-02
When you format a drive as Ext3 in Ubuntu, by default it is owned by root. You need to use the chown command to change the ownership, along the lines of...

sudo chown username:username /path/to/drive

Be careful not to leave any spaces in the above command after the first /, or the ownership will be applied to the wrong drive or directory.

The Lost+Found folder is for any errors/lost files found by the disk checking routine. You can ignore it.

---

### Post by BlackholeZ on 2008-09-02
Awesome, it worked, Thanks. 

Is there a walkthrough on how to add a hard drive somewhere that I missed? 
Do I have to mount other drives "inside" my primary drive? or can I mount it parallel with my primary drive?

---

### Post by silkstone on 2008-09-02
You can mount a new drive to any mount point you create - they are all separate and are treated as part of the filesystem. It's common to create the new mount point under /mnt or /media.

If you format as Ext3 with gparted, you'll have to go through the same procedure to take ownership of the drive. Also you'll probably have to edit your /etc/fstab file if you want the drive to mount automatically at boot, but cross that bridge when you come to it!

---

### Post by knattlhuber on 2008-09-02
> **BlackholeZ said:**
> Is there a walkthrough on how to add a hard drive somewhere that I missed? 


I found this HOWTO quite helpful
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by Xubuntnoob on 2008-09-13
> **silkstone said:**
> 
If you format as Ext3 with gparted, you'll have to go through the same procedure to take ownership of the drive. Also you'll probably have to edit your /etc/fstab file if you want the drive to mount automatically at boot, but cross that bridge when you come to it!


I'm at that point- what do I need to add/change in the file?

---

