---
title: "Contents of External Hard disk cannot be accessed"
date: 2013-06-24
forum: Hardware
---

### Post by avinash0161 on 2013-06-24
I have a seagate external USB hard disk(500 gb). One day it was working fine and the other day when I plugged it into my Windows OS, it was listed as Local Disk instead of Expansion Drive which is its usual name. Also, no information about the disk was displayed(like the one which says 'x GB free of y GB'). If I click onto the Local disk, the windows explorer stops responding. 

So, I turned to Ubuntu for help. When I inserted the disk into the USB port, the disk was listed as Expansion Drive but it didn't open which it should have automatically. So I clicked on the Expansion drive to mount it and the following error came: 
[COLOR=#ff0000]DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

[/COLOR][COLOR=#000000]After waiting for much long, it said that it couldn't mount the drive with the following error:

[/COLOR][COLOR=#ff0000]DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/COLOR][COLOR=#000000]
 
Now, I checked the fdisk -l option in the shell and this is what it printed as output:-

[/COLOR][INDENT][COLOR=#ff0000]*Disk /dev/sda: 500.1 GB, 500107862016 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Units = sectors of 1 * 512 = 512 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Sector size (logical/physical): 512 bytes / 4096 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*I/O size (minimum/optimal): 4096 bytes / 4096 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Disk identifier: 0xd610bb10*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*   Device Boot      Start         End      Blocks   Id  System*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*/dev/sda1   *      206848   157573119    78683136    7  HPFS/NTFS/exFAT*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*/dev/sda2       157573120   876421119   359424000    7  HPFS/NTFS/exFAT*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*/dev/sda3       876423166   976771071    50173953    5  Extended*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Partition 3 does not start on physical sector boundary.*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*/dev/sda5       876423168   884234239     3905536   82  Linux swap / Solaris*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000][I]/dev/sda6       884236288   976771071    46267392   83  Linux

[/I][/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Disk /dev/sdb: 500.1 GB, 500107859968 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Units = sectors of 1 * 512 = 512 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Sector size (logical/physical): 512 bytes / 512 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*I/O size (minimum/optimal): 512 bytes / 512 bytes*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*Disk identifier: 0x569f2049*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]*   Device Boot      Start         End      Blocks   Id  System*[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000][I]/dev/sdb1              63   976768127   488384032+   7  HPFS/NTFS/exFAT

[/I][/COLOR][/INDENT]
[COLOR=#000000]Also, I used GParted. It gave me the complete info about my hard disk. I attempted data rescue but no file systems could be found there. can anyone tell me any other way to get my data back from that hard disk(Few videos and docs are really important). [/COLOR]

---

