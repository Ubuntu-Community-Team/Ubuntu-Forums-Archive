---
title: "Not Privledged ?"
date: 2008-08-07
forum: General Help
---

### Post by Ashejoe on 2008-08-07
Each time I plug in my USB Thumb drive, I get the error message "NOT PRIVILEGED TO MOUNT"  How do I become "privileged" ?? 

Also, (if I may ?), why is it that my dual boot Ubuntu 8.04 / Vista machine will not allow me to access the Vista partition when I'm in Ubuntu ?

Thanks

---

### Post by kidux on 2008-08-07
Check to see that you have been given permission to access external devices by going to Systen->Users and Groups. Unlock it, then check the properties of your user name, then click the User Privileges tab. The first checkbox should be what you"re looking for.

---

### Post by Taxman415a on 2008-08-07
> **Ashejoe said:**
> Also, (if I may ?), why is it that my dual boot Ubuntu 8.04 / Vista machine will not allow me to access the Vista partition when I'm in Ubuntu ?

Thanks

In general it will. Not sure why it doesn't by default for you. Can you give us the output of ```
sudo fdisk -l
```. Basically you just need to set up your fstab ([https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)) file and mount the Windows partition that fdisk shows you. I believe ntfs-3g is installed by default, but if it is not, ```
sudo aptitude install ntfs-3g
``` should get it for you.

---

### Post by Ashejoe on 2008-08-07
Thanks for the reply Kidux... but.... even after following your suggestion, I continue to be told the "CAN NOT MOUNT VOLUME.... You are not privileged to mount the volume".

I did notice that when I went into  SYSTEM --> ADMINISTRATION --> USERS and GROUPS as you instructed, then proceeded to make the changes you noted, they didn't "stick".... so to speak.

After I closed USER SETTINGS, then re-opened the USERS and GROUPS, I had to once again "unlock it" ??  Even with this window opened and supposedly unlocked, I still was not allowed to access the Thumb Drive... which the system did recognize as having been plugged in.

Sorry

---

### Post by damoxc on 2008-08-07
Once you've added yourself to the group you will unfortunately need to log out of gnome and then back in for the changes to take effect. Give this a try.

---

### Post by Ashejoe on 2008-08-07
Taxman415A, here is what I get when I run the command line you asked for:
======================
desktop:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bf53399

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156286976    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 4110 MB, 4110228480 bytes
16 heads, 63 sectors/track, 7964 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7965     4013863+   b  W95 FAT32
================================
As indicated, this is a internal hard drive with 160-GB total capacity.  (120-GB Vista / 40-GB Ubuntu 8.04)  I've tried what little I know about mounting a hard drive.  I've also tried a few utilities out of the Ubuntu repository that supposedly allow one to access a FAT32 file system ??

What I find a bit strange, is that Ubuntu 8.04 DOES recognize my portable hard drive which is FAT32, but not my internal hard drive ??

Does it matter that the way I installed Ubuntu 8.04 was via Windows Vista using that new Install Routine that Ubuntu 8.04 included ??

---

### Post by Ashejoe on 2008-08-07
Thank You damoxc... but... it didn't work I'm sorry to report.

Not only did I log off and log back on, but I also fully re-booted my system. 

Same thing... it's like the "unlock" just doesn't "take".  It's "accepted" without any error messages.  But when I close the Window and restart it, it, the "UNLOCK" function is again active on my user name ??

---

### Post by damoxc on 2008-08-07
The "Unlock" button is to give the program administrative rights in order to modify the system, in this case the users and groups.

Highlight your user, then select properties.

Open the User Privileges tab and ensure that the first item in the list is checked.

---

### Post by Ashejoe on 2008-08-07
> **damoxc said:**
> The "Unlock" button is to give the program administrative rights in order to modify the system, in this case the users and groups.

Highlight your user, then select properties.

Open the User Privileges tab and ensure that the first item in the list is checked.

Thanks damoxc... but I did do that and it still the same-ole... same-ole... it just won't "take" ????

Also, even though I've followed taxman415a's instructions and ran "sudo aptitude install ntfs-3g"  (which did do "something" ... I could see the system cranking away with all kinds of lines appearing in the terminal indicating something was being modified), I also still can not access the Windows Partition on my internal hard drive.  

It just seems so strange that I can access the portable hard drive via a USB port, but not a Thumb Drive ?  And when I attempted to mount the internal hard drive, all that shows up is the Ubuntu 8.04 partition.

I don't know, maybe I should just reinstall Ubuntu ??

---

### Post by damoxc on 2008-08-07
Oh, it's an internal drive, give:
```
sudo mount /dev/sda1 /mnt
```
a try from the terminal.

Of course replace /dev/sda1 with the correct device for your partition.

---

### Post by Taxman415a on 2008-08-07
> **Ashejoe said:**
> It just seems so strange that I can access the portable hard drive via a USB port, but not a Thumb Drive ?  And when I attempted to mount the internal hard drive, all that shows up is the Ubuntu 8.04 partition.

I don't know, maybe I should just reinstall Ubuntu ??

No need to reinstall, I'm just a little confused. You have a 160GB drive with windows, and NTFS filesystem, and Ubuntu installed through wubi, that makes sense. That drive is reported as /dev/sda with only one partition. That's fine. Then your second drive is a 500GB one that is also NTFS formated and shows up as /dev/sdb. The third is a 4GB flash drive with Fat32 filesystem and that is /dev/sdc.
What's confusing is when you say "I can access the portable hard drive via a USB port, but not a Thumb Drive ?" what do you do to access the portable drive (I'm assuming that's the 500GB drive) since that's ntfs just the same as your 160GB drive. And how can't you access the thumb drive, it's a Fat32, so it should just show up in the Places menu. In fact all of them should.

Lastly you say "And when I attempted to mount the internal hard drive, all that shows up is the Ubuntu 8.04 partition."  What commands did you use for this? If I understand you right, you used the Wubi installer to install Ubuntu through Windows, so you don't actually have an Ubuntu partition when you do that. It just creates files on the Windows system like installing a program. So what Ubuntu are you seeing? Please give more details.

---

### Post by Ashejoe on 2008-08-07
Hi Again Taxman415a:
I'll try to explain this the best I can given my limited Linux experience.

Yes, you're correct, I did use the "wubi" feature to install Ubuntu 8.04 onto my computer's 160-GB internal hard drive.  This internal hard drive had already been formatted and running Vista SP1 prior to the wubi installation of Ubuntu 8.04. I allocated 120-GB to Vista, and 40-GB to Ubuntu 8.04.  

Regardless, all I can "see" is the 40-GB Ubuntu partition .... not the remaining 120-GB Vista partition on this internal SATA hard drive.  It just will not show up / call up / mount / etc.  It's like that 120-GB is completely invisible to Ubuntu.

The 500-GB external hard drive was originally formatted 18+ months ago on my old Windows XP laptop.  Neither Vista nor Ubuntu 8.04 has had any problems reading or writing to that portable hard disk, which is connected via a USB-2 port.  I don't know what to tell you other than when I boot up under Ubuntu 8.04, there's an icon already there on the desktop for this portable hard drive with no action required on my part to access it.

The 4-GB Sandisk Thumb Drive has no problem working under Vista, but it won't allow me to "mount" it when I boot up under Ubuntu 8.04.  Again, Ubuntu appears to recognize this Thumb Drive was just plugged in, it just won't allow "me" to mount it.  Instead I keep getting that "not privileged" error message.

I've been playing around with this all night, and I think I've totally screwed something up.  Now, I can't even access the USERS AND GROUPS window, nor, can I type anything into the Terminal window !  (In both cases the "window" calls up, but, it won't let you enter anything.  No key strokes are accepted, nor, are any mouse clicks once either window opens up.  I'm sure "I" messed that up though in my trial and error efforts to get the Thumb Drive and Windows Partition to mount.

I don't know if I've adequately answered your question or not ?  Honestly, given the relative simplicity of uninstalling / reinstalling Ubuntu 8.04, I may just remove it, then, reinstall it.  Thank goodness it doesn't require "activation" like Windows does.

Thanks again for your suggestions.  They truly are most appreciated.

---

### Post by Taxman415a on 2008-08-08
Given that you are inexperienced with Ubuntu it may be less headache for you to reinstall, especially if you have backed up any important data. Just be assured that you don't need to do that to fix things like you do in Windows. It may just be a little easier for you than digging for answers. Also since the Wubi installer doesn't create a partition for Ubuntu, it just installs it like a program, it's really just meant for testing Ubuntu. If you realize you like it, you may want to boot windows, uninstall ubuntu (I think from add/remove programs is the way Wubi is set up to remove it) and then boot from the Ubuntu install cd and install it the normal way. Then you would actually create an Ubuntu partition by shrinking the Windows partition 120GB or so and creating a 40GB partition for Ubuntu.

You may find that some of your problems came from the Wubi installation. 

But if you want to try to keep fixing this, I don't have ideas on the not priviledged error message, but what commands have you tried to mount the 160GB NTFS partition? I don't have a Wubi installation or else I would try testing it for you to see if you have to do anything different.

As for the terminal and user/groups tool locking up, that is very strange. If you have no unsaved open documents, try pressing ctrl-alt-backspace it will kill and restart the graphical interface which should fix those problems unless something is really hosed. Usually ctrl-alt-backspace is a good substitute for rebooting especially if it is just an interface or user program issue.

---

### Post by Ashejoe on 2008-08-10
Yea... that's what I ended up doing Taxman415a....completely wiping out Ubuntu 8.04 via the Windows Vista "Add-Remove Programs" function.

The Ubuntu WUBI function that allows one to make a dual boot Windows / Linux system was one of Ubuntu's principle selling points to me.  In the paste, when I've played around with other Linux Distributions, I had to do like you suggested... load them from "outside" of Windows.

While this wasn't especially hard to do, the real obstacle was removing Linux and trying to re-allocate the hard disk space back to Windows after I messed up the Linux installation ! 

Inevitably, Windows would not give back that space without one hell of a fight.  Even utility programs like Partition Magic would find it difficult to work with Windows installations that had been ahhhhh "polluted" with something other than a Microsoft approved product !

That left me little choice, (given my over all experience level), other than to fully reformat the hard disk.  That's when the real fun came in.... having to call up Microsoft when my CD-Key number was rejected during their damn "Product Activation" step.  Even though I had not changed anything in my computer's hardware profile, it ALWAYS got rejected as already having been used.

Microsoft's insane "Product Activation" mandate was the one thing that really turned up my interest in Linux.  Of the roughly 10 distributions I've played around with so far, Ubuntu has been, without a single doubt, THE BEST one out there.  And sincerely, one of the primary things that makes it the best in my mind, is the sincere help I've always received from the Ubuntu online community !!

---

