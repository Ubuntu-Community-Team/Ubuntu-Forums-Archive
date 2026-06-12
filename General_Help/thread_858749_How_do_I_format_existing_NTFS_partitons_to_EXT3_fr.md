---
title: "How do I format existing NTFS partitons to EXT3 from the Ubuntu OS?"
date: 2008-07-13
forum: General Help
---

### Post by tmcarson1 on 2008-07-13
I have a hard drive, with 3 partitions.

2 are both NTFS or windows partitions for storage
1 has the ubuntu install on it

I would like to format the other two ntfs partitions over to EXT3 from within ubuntu.

Is there a GUI program I can download from the repositories that will guide me in this process?

Thanks for your help!

---

### Post by estyles on 2008-07-13
I believe that gparted can do this.  Just install gparted from the repositories.  If it's on the same drive as your active partition, you might have to run it from the LiveCD.  Not entirely sure.

Just to be sure - you know that changing the file format of a partition will completely erase any data on it, right?

---

### Post by sandysandy on 2008-07-13
have a look here

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

regards

---

### Post by tmcarson1 on 2008-07-13
> **estyles said:**
> I believe that gparted can do this.  Just install gparted from the repositories.  If it's on the same drive as your active partition, you might have to run it from the LiveCD.  Not entirely sure.

Just to be sure - you know that changing the file format of a partition will completely erase any data on it, right?

Thanks for the reply, will check into that.  And yes I do realize it will erase things on there, but I need to since I am switching to ubuntu and dropping windows.

Thanks again for the help!

---

### Post by tmcarson1 on 2008-07-13
> **sandysandy said:**
> have a look here

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

regards

Ok, that worked perfectly, I reformatted the partition to EXT3 now, and it is mounted, BUT, it won't give me access to read and write to it now.

Can anyone tell me how to change the permissions on this partition, I would like to use it as storage for my ubuntu media files.

Thank you

---

### Post by estyles on 2008-07-13
If you can't change the permissions as your current user, try doing ```
sudo nautilus
``` in terminal, then browsing to the mount point (probably /media/disk or something simlar), and right-click, choose Properties, and check the Permissions tab.

---

### Post by SlalomMan on 2008-07-14
If you're switching to ubuntu, why don't you just delete those partitions and then expand your ubuntu partiton instead of having 3 separate ones?

Also, if anyone finds a solution to the drive issue, I'm having a problem changing the permissions on my MicroSD card.

---

### Post by jonian_g on 2008-07-14
Go to add/remove and install "Storage Device Manager".
Once installed go to System>Admin>Storage Device Manager.
When the program starts chose on the left column the partition (sdb, sdf etc., you can see it in gparted).
On the right give a name to your partition "ex. external, data etc.". Then click the "assistant" button and on the first tab check "the file system is mounted at boot time",if you want the partition to be always mounted and at misc tab check "user allowed to use reserved space" and next to "resuid=" put your username.
Press ok and then the "mount" button. Your partition will be mounted and you will see an icon on your desktop and you will have write permissions.

---

