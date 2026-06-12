---
title: "Need help backing up a windows disk"
date: 2009-01-09
forum: Hardware
---

### Post by rossco on 2009-01-09
Hi everyone,

I wasn't sure of the appropriate place to post this so I am trying here.  I am trying to back up a windows hard disk to reinstall windows (its my grandfathers).  Problem is that the windows box continually crashes so I can't back it up over the network.  Because of this I decided to connect it to my Ubuntu PC and copy the contents over to back it up at this stage.

I got the hardware side covered and the disk is visible in Nautilus however whenever I click on it it brings up a dialog asking for authentication.  It says "system policy prevents mounting internal media" and asks for my password etc.  I enter it and I get the following error:

logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sdc1' Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g /dev/sdc1 /media/disk -o -force or add the option to the relevant row in the /etc/fstab file: /dev/sdc1/media/disk ntfs-3g force 0 0

Should I type the command it says under option 2 (mount -t ntfs-3g /dev/sdc1 /media/disk -o -force)?

---

### Post by mascer on 2009-01-09
Maybe first try to boot into safe or command mode and run a scandisk to fix the windows disk, be sure to have a clean shutdown.

---

### Post by rossco on 2009-01-15
Hi Mascer,

Thanks for your post.  I thought I'd better come back and thank you.  I did as you suggested and did a clean shutdown which allowed me to mount the windows disk from Ubuntu.  From there it was a piece of cake.  I think the ram was faulty (I replaced it with more ram).

---

