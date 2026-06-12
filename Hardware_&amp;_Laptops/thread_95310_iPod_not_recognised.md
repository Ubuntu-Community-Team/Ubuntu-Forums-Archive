---
title: "iPod not recognised"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by tazzik on 2005-11-26
Hi,
My ubuntu 5.10 works great however, my iPod mini 2g 4GB is not recoginesed. It does not show on the desktop and in the "filesystem" where it says "Apple iPod music player" if I click on that it says it is unable to mount it. On the extra info part it says there is a bad superblock on /dev/sdb. But when I go to /dev there is no sdb folder there. Shouldn't the iPod be listed in /media/iPod anyway? What I want to know is how to see the iPod, not put music on it but to use it as another HDD, in iTunes on windows, the enable disk use box IS checcked.
Cheers
tazzik

---

### Post by aysiu on 2005-11-27
[QUOTE=tazzik]Hi,
My ubuntu 5.10 works great however, my iPod mini 2g 4GB is not recoginesed. It does not show on the desktop and in the "filesystem" where it says "Apple iPod music player" if I click on that it says it is unable to mount it. On the extra info part it says there is a bad superblock on /dev/sdb.[/quote] That sounds bad. 

> But when I go to /dev there is no sdb folder there. sdb isn't a folder. It's a device. And it should be there. 

> Shouldn't the iPod be listed in /media/iPod anyway? No, that's where /dev/sdb1 or /dev/sdb2 would get mounted. That's not where the device lives. 

> What I want to know is how to see the iPod, not put music on it but to use it as another HDD, in iTunes on windows, the enable disk use box IS checcked. Theoretically, it should just be automounted to /media/IPOD. Since it isn't, let's see what we can do. First of all, after you plug it in, open a terminal (Applications > Accessories > Terminal) and type this in ```
sudo fdisk -l
``` This will tell us what location (/dev/sdb__) the iPod lives in and what filesystem it uses (FAT32 or HFS).

Can you post the output of that command here?

---

### Post by tazzik on 2005-11-27
sorry it took so long:
Disk /dev/hda: 12.0 GB, 12072517632 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         510     4096543+   7  HPFS/NTFS
/dev/hda2             511        1467     7687102+   f  W95 Ext'd (LBA)
/dev/hda5             511         583      586341   82  Linux swap / Solaris
/dev/hda6             584        1467     7100698+  83  Linux

Disk /dev/sdb: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           5       40131    0  Empty
/dev/sdb2   *           6         497     3951990    b  W95 FAT32

---

### Post by teaker1s on 2005-11-27
ipod app in repositories

---

### Post by tazzik on 2005-11-27
what do you mean

---

### Post by aysiu on 2005-11-27
[QUOTE=tazzik]
Disk /dev/sdb: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           5       40131    0  Empty
/dev/sdb2   *           6         497     3951990    b  W95 FAT32[/QUOTE] It looks as if this is your iPod. Assuming it always shows up as /dev/sdb2 (and not /dev/sda1 or /dev/sde1), this solution *may* work: ```
sudo mkdir /mnt/ipod
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then add this line in ```
/dev/sdb2 /mnt/ipod vfat umask=000  0   0
``` Save (Control-X), confirm (y), and exit (Enter). Then turn off your computer, unplug your iPod, turn the computer back on. When you're all settled back into Ubuntu, plug your iPod in again... any luck?

---

### Post by essexman on 2005-11-27
[quote=tazzik]Hi,
My ubuntu 5.10 works great however, my iPod mini 2g 4GB is not recoginesed. It does not show on the desktop and in the "filesystem" where it says "Apple iPod music player" if I click on that it says it is unable to mount it. On the extra info part it says there is a bad superblock on /dev/sdb. But when I go to /dev there is no sdb folder there. Shouldn't the iPod be listed in /media/iPod anyway? What I want to know is how to see the iPod, not put music on it but to use it as another HDD, in iTunes on windows, the enable disk use box IS checcked.
Cheers
tazzik[/quote]

It should be automatic but it isn't.  It is best not to go the old fashioned way and make new directories,  as this can get you into all sorts of tangles.  Breezy uses an unauthodox Hardware Abstraction Layer (HAL)system, and udev for plugins devices, which works very well if you know how.

try: System>>Administration>>Users and groups>>

Then
[LIST=1]
[*]Check the "Show all users and Groups" check box at the bottom left
[*]Select the Groups tab
[*]Click on the groups title bar to alphabetise the groups as you will need to search manually for the required groups.
[*]Find, highlight and select properties for the groups:[LIST=1]
[*]cdrom
[*]disk
[*]floppy
[*]plugdev
[*]hal[/LIST]
[*]Add hal and any users to the group members list for each of these groups except hal.
[*]For hal, just add the users.
[*]restart gnome.[/LIST]when you plug in the ipod, it should now work exactly as you think (as it does on my system).  A temporary directory and mount point, "ipod" is automatically created in /media.  The ipod mounts to this point and a folder automatically opens with the full name of the ipod.

This appears to be better set up in Dapper so the problem should have gone away in 5 months time.

You have to unmount the ipod when you have finished either by right-clicking on the desktop icon or eject /media/ipod from the command line.

I believe a cleaner eject process is being worked on for Dapper, but the right-click-unmount method works fine for me.

To add music it is best to use the gtkpod programme.

---

### Post by linuxted on 2006-01-02
[QUOTE=essexman]It should be automatic but it isn't.  It is best not to go the old fashioned way and make new directories,  as this can get you into all sorts of tangles.  Breezy uses an unauthodox Hardware Abstraction Layer (HAL)system, and udev for plugins devices, which works very well if you know how.

try: System>>Administration>>Users and groups>>

Then
[LIST=1]
[*]Check the "Show all users and Groups" check box at the bottom left
[*]Select the Groups tab
[*]Click on the groups title bar to alphabetise the groups as you will need to search manually for the required groups.
[*]Find, highlight and select properties for the groups:[LIST=1]
[*]cdrom
[*]disk
[*]floppy
[*]plugdev
[*]hal[/LIST]
[*]Add hal and any users to the group members list for each of these groups except hal.
[*]For hal, just add the users.
[*]restart gnome.[/LIST]when you plug in the ipod, it should now work exactly as you think (as it does on my system).  A temporary directory and mount point, "ipod" is automatically created in /media.  The ipod mounts to this point and a folder automatically opens with the full name of the ipod.

This appears to be better set up in Dapper so the problem should have gone away in 5 months time.

You have to unmount the ipod when you have finished either by right-clicking on the desktop icon or eject /media/ipod from the command line.

I believe a cleaner eject process is being worked on for Dapper, but the right-click-unmount method works fine for me.

To add music it is best to use the gtkpod programme.[/QUOTE]



essexman, great post.  Unfortunately this didn't help me.  There was no automatic creation of /media/ipod.  I even tried with a manual creation of the direction of /media/ipod... no luck.


here is a message I get for tail /var/log/messages:

Jan  2 10:53:30 localhost gconfd (user-8579): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan  2 10:53:37 localhost gconfd (user-8579): Resolved address "xml:readwrite:/home/tburmas/.gconf" to a writable configuration source at position 0
Jan  2 10:54:01 localhost kernel: [4294748.285000] usb 4-7: new high speed USB device using ehci_hcd and address 3


Thanks for your help

---

