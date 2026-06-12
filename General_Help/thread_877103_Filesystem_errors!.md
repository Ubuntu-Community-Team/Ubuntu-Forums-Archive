---
title: "Filesystem errors!"
date: 2008-08-01
forum: General Help
---

### Post by pumakuma on 2008-08-01
Recently I was trying to resize my ubuntu partition.. I had forgotten I had installed ubuntu through wubi and so I booted into vista and opened up 'PowerQuest Partition Magic' as that was a tool I was familiar with.. After a few errors with that program, due to the fact that it's not compatible with vista and that vista has a built in partition manager.. I found the website for LVPM and decided to reboot in ubuntu and follow the instructions. Upon rebooting Ubuntu popped up an error stating that the NTFS Filesystem couldn't be found and that I should run the FDISK Utility under windows, then it continued to start up ubuntu. Ubuntu (somehow) still works although all my permissions are messed up and alot of my programs don't launch. I opened GParted to see what was going on and found '/dev/sda/' unallocated space 230gb and that was the only entry. I have also run 'sudo fdisk -l' which returned: 

pumakuma@pumakuma-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000008

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240640    7  HPFS/NTFS
/dev/sda3   *        1280       30075   231295160    7  HPFS/NTFS
/dev/sda4           30075       30402     2620416    f  W95 Ext'd (LBA)
/dev/sda5   *       30076       30402     2619392   dd  Unknown


- All of my files from windows and ubuntu still exist but windows refuses to boot although the windows boot manager loads and vista recovery doesn't know how to fix it.. one new thing i've noticed is:
pumakuma@pumakuma-laptop:~$ sudo fdisk -l

/dev/sda5   *       30076       30402     2619392   dd  Unknown

which I haven't noticed until all this mess happened.. and by the looks of it it is 'bootable' and seems to start and end over an existing filesystem. Any help would be much appreciated!

Thanks

---

### Post by minhmeoke on 2008-08-02
If you have the vista CD, then I think you can do a "repair" install, which overwrites a few system files that are needed for booting. However, this will overwrite the boot menu also, so you will not be able to boot ubuntu, therefore if it doesn't work, you will need a livecd to access your data.

Maybe Ago will have a better idea...

---

### Post by pumakuma on 2008-08-02
I have tried booting the vista cd many times.. The repair options are limited. I remember in XP you could just pop in the cd and it would overwrite the core files which sounds like exactly what I need right now.. Vista has like a list something like: Startup Repair, System Restore Point, Complete System Restore, Memory Diagnostic Tests, Command Prompt, Dell Factory Restore... i have run startup repair many times to no avail. and i have tried running the two system restores but only got errors.. otherwise if i try to continue on the disk it tries to have me install vista from scratch.. I just am trying to make sure non of my data gets deleted. I use ubuntu 95% of the time and would really love to keep those settings as they are more important to me than windows.. but i figure in order to fix this i have to reinstate the fact that my harddrive is in an ntfs filesystem although fdisk already shows it as one..

---

### Post by minhmeoke on 2008-08-02
Yes, I meant the "startup repair", but apparently that is not working for you. It would probably be best if you could back up all your data to an external harddrive, or burn it to a CD/DVD before trying anything else. Can you access your Vista partition from Ubuntu (in the Places menu)? If not, then you can burn a livecd, and use it to back up your data onto an external usb harddrive.

Also, did Vista stop working immediately after you used 'PowerQuest Partition Magic' or did LVPM break it? Have you tried running chkdsk /r?

You should file a bug report or question for LVPM at the launchpad site: [https://bugs.launchpad.net/lvpm](https://bugs.launchpad.net/lvpm) , and ask tuxcantfly, the creator of lvpm, for a solution. The "/dev/sda5 * 30076 30402 2619392 dd Unknown" is definitely wrong. It should be repairable, unfortunately I do not know how. Theoretically you could unmark the bootable flag on /dev/sda5 with fdisk, but there is the risk that sda5 is not an actual partition, and could make ubuntu unbootable.

---

