---
title: "issues with mounting ATA/IDE disk in modular bay - ubuntu 6.10 Edgy"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by JeffH.other on 2007-05-11
Hi, 

I'm running ubuntu 6.10 Edgy on a Dell d820. I've mounted a hitachi travelstar 
ATA/IDE disk (NTFS filesystem, my old winXP system disk) in a modular disk 
caddy, popped out the dvd drive, and stuck in the disk caddy.

the disk I placed in the caddy is known-good, i'd had it hooked up via an 
external USB enclosure, whereupon it was recognized automagically and mounted 
as "/dev/sdb1". but i need to copy mega gigabytes of stuff off of it, so i 
thought mounting it internally will yield better xfer rates (i have to copy a 
bunch of stuff into a winXP virt machine, and vmware 5.5 as yet only supports 
usb 1.1).

plus, i have another disk I'll eventually want to mount in this way (in 
modular bay) more or less permanently as a 2nd hard drive, so i need to figger 
this out.

I'd tried figuring out if I needed to do anything special before removing the 
dvd drive, but couldn't find anything, and with no disc in it, umount didn't 
want to do anything, so i just took it out.

upon insertion of the hard drive caddy, I get these messages continuously in 
the system log...
                                  .
                                  .
                                  .
[17194717.584000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17194717.584000]    : Current [descriptor]: sense key: Aborted Command
[17194717.584000]     Additional sense: No additional sense information
[17194719.160000] usb 4-1: reset low speed USB device using uhci_hcd and 
address 12
[17194719.600000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.600000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.600000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.600000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.600000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 
00 00 00 00
[17194719.604000] sr: Current [descriptor]: sense key: Aborted Command
[17194719.604000]     Additional sense: No additional sense information
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] ata2: translated ATA stat/err 0x51/04 to SCSI SK/ASC/ASCQ 
0xb/00/00
[17194719.604000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
                                  .
                                  .
                                  .


I attempted to mount the disk in various ways, partially to see what device it 
is mapped to...

 
# mount -t ntfs /dev/sdb1 /media/oldc
mount: special device /dev/sdb1 does not exist

# mount -t ntfs /dev/hda0 /media/oldc
mount: special device /dev/hda0 does not exist

# mount -t ntfs /dev/sda2 /media/oldc
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


So, does the above hint that it is /dev/sda2 ?  My ubuntu system disk is 
/dev/sda1 fwiw (and also a hitachi travelstar AFAIK).


Any help will be appreciated, thanks,


=JeffH

---

### Post by JeffH.other on 2007-05-18
HI folks -- does anyone have any ideas on how to dynamically mount an ATA/IDE disk as outlined above? winblows does it, so ubuntu/linux oughta be able to -- thoughts?

thanks,

=JeffH

---

### Post by =JeffH on 2007-06-03
*bump*

Others have essentially the same question [over here in this other thread]("http://ubuntuforums.org/showthread.php?t=355179")...

[http://ubuntuforums.org/showthread.php?t=355179](http://ubuntuforums.org/showthread.php?t=355179)


thanks,

=JeffH

---

### Post by =JeffH on 2007-06-08
Ok, so I figured out how to mount an NTFS (v3.1) disk (physically in a hard disk caddy (dell d820)). 

There were five key things to do. The first was to use the "[FONT="Lucida Console"]fdisk -l[/FONT]" command to see what device the disk was been "seen" as...

```
[FONT="Lucida Console"]Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS[/FONT]
```

So it turns out it was recognized as [FONT="Lucida Console"]/dev/sdb[/FONT].


The second was to install the "[FONT="Lucida Console"]ntfs-3g[/FONT]" driver and all dependencies, then shutdown, physically insert the caddy, and reboot.

The third thing was to realize that the device to mount was "/[FONT="Lucida Console"]dev/sdb1[/FONT]" rather than just "[FONT="Lucida Console"]/dev/sdb[/FONT]".

The fourth was to make the user who would be using the drive (me) be the owner of the mount point directory (see note 2 below) 

And the fifth was to then use this (precise) mount command..

    ```
mount /dev/sdb1 [mount point]  -t ntfs-3g -O utf8,uid=1000,gid=1000,umask=0111
```

Unmounting is simply "[FONT="Lucida Console"]umount /dev/sdb1[/FONT]"

Note 1: The values for "[FONT="Lucida Console"]uid[/FONT]" and "[FONT="Lucida Console"]gid[/FONT]" need to be the ones for the user (likely you ;)  who will need access to the drive (get 'em outta [FONT="Lucida Console"]/etc/passwd[/FONT] and [FONT="Lucida Console"]/etc/group[/FONT]), and the [FONT="Lucida Console"]umask[/FONT] is the permissions to give the identified user to the drive. "[FONT="Lucida Console"]man ntfsmount[/FONT]" discusses all this (tho experimenting just now with different [FONT="Lucida Console"]umask[/FONT] values indicates that they might be being ignored, don't know for sure).

Note 2: I spent a ton of time experimenting with  [FONT="Lucida Console"]ntfsmount[/FONT] and different permissions on the mount point (prior to attempting the actual mount command) before I found combo that resulted in my having "[FONT="Lucida Console"]rw[/FONT]" permissions to the drive and all its directories. I finally found that setting the mount point owner and group to me prior to mounting with the command above is what worked. Otherwise it would end up with only [FONT="Lucida Console"]root[/FONT] having access to the mounted drive, which was suboptimal. 

Note 3:  version info..

```
Linux  2.6.17-11-generic #2 SMP Fri May 18 23:39:08 UTC 2007 i686 GNU/Linux

ntfs-3g: 20060920-0ubuntu2

mount: mount-2.12r

```

Note 4: This does not address the second-order question about "hot-swapping" of the drive, unfortunately. The only way I could get it to work was if I booted with the drive caddy plugged in.  :(    

see also this so-far unanswered (as of date of orig posting of this post) thread...

  [Setting up SATA Hot Swap]("http://ubuntuforums.org/showthread.php?t=355179")  
  [http://ubuntuforums.org/showthread.php?t=355179](http://ubuntuforums.org/showthread.php?t=355179)

---

### Post by kansei on 2007-06-27
I'm stuck in the same boat, and my question went unanswered on the Arch Linux forums as well.

I get no messages in dmesg upon insertion of the drive caddy. I know on my ThinkPad when you push the button to release the modular bay it sends signals and can be set up (as it does in windows) to automatically unmount the device before you physically remove it. Since the modular bay is an IDE device, I don't know if just unmounting the partition is enough to make pulling the drive 'safe'.

For me, the second hard drive is in the laptop most of the time, only occasionally swapped out for the DVD burner. Needing to restart to burn a CD is getting tiring, hence coming here to look for a solution.

---

### Post by =JeffH on 2007-07-03
Yes, I agree wrt it being a pain to have to shut down to swap out the modular bay disk caddy. And yes, there must be some notification going on, also on my D820 (and C610s). Oh, tho on those systems, I have to manually tell windoze of my intention to swap out the drive, and it sez whether it's ok to do so or not. 

In KDE's Konqueror, on the popup menu for my modular bay 2nd disk, I get an "unmount" item, so it seems to know that it's a "manually" mounted device (in the Properties dialog, it terms the item "Mounted Hard Disk Drive").

Does this recent post here by EnglishRob in the related thread have hints that might be helpful:

[http://ubuntuforums.org/showpost.php?p=2941904&postcount=6]("http://ubuntuforums.org/showpost.php?p=2941904&postcount=6")

?    

I'm going to mess around with those hints at some point in the future. In the meantime, I'm ripping/burning CDs on a separate dedicated old machine. 

=JeffH

---

