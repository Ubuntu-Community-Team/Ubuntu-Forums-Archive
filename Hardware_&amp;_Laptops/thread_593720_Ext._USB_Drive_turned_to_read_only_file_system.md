---
title: "Ext. USB Drive turned to read only file system"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by nc_jed on 2007-10-27
I have been futzing around trying to get NFS working between my laptop and desktop, and in the process, I think I have changed my external USB HD to a read only file system.

```
blake@ubuntu:/media$ cat .hal-mtab
/dev/sdc1       1000    0       vfat    nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec       /media/IOMEGA_HDD
blake@ubuntu:/media$ cd IOMEGA_HDD
blake@ubuntu:/media/IOMEGA_HDD$ cal > cal.txt
bash: cal.txt: Read-only file system
```

The 'futzing around with NFS' thing is significant as I have been half heartedly trying to follow several different howto's to set the desktop machine (which the USB drive is connected to) as the server, and specifically, the USB drive as the NFS shared folder.  I thought I might have tried to chmod/chown/chgrp to change the ownership/specs, etc.  To top it off, I would have done this from the laptop via SSH, so .bash-history is not any help.

```
blake@ubuntu:/media/IOMEGA_HDD$ ls -al
total 202148
drwx------ 13 blake root     32768 1969-12-31 19:00 .
drwxr-xr-x 10 root  root      4096 2007-10-26 23:07 ..
drwx------  5 blake root     32768 2007-10-21 12:18 Documents
drwx------  7 blake root     32768 2007-10-19 22:51 downloads
drwx------  5 blake root     32768 2007-05-27 15:10 icons
-rwx------  1 blake root 204014349 2007-04-22 11:09 mail-backup-20070422.tar.gz
drwx------ 97 blake root     32768 2007-10-22 23:22 music
drwx------ 24 blake root     98304 2007-10-14 22:02 pics
drwx------  6 blake root     32768 2007-10-17 20:12 system_backup
-rwx------  1 blake root     28898 2007-04-21 10:22 thunderbird address book.ldif
drwx------  2 blake root     32768 2007-10-19 20:16 .Trash-blake
drwx------  2 blake root     32768 2007-10-19 22:51 .Trash-root
drwx------  4 blake root     32768 2007-10-08 23:11 Websites
```

Any ideas?  Any more info that you need to diagnose (I realize my details of what might have happened to cause it are light, so please bear with me).

Thx, Blake.

---

### Post by Caffeine_Junky on 2007-10-28
hmmm, I think this is a bit out of my league, so I give it a friendly....

....bump  :)

Good Luck

---

### Post by nc_jed on 2007-10-28
Problem resolved.  Resolution steps for other poor schlubs that find themselves in similar situation (or if I do in the future and Google it for another fix).

[LIST=1]
[*]Unmount drive (Desktop > Unmount)
[*]Power off drive.
[*]Rename symlink to drive (/home/blake/USBHB to /home/blake/USBHB-delete) 
[*]Power drive back on.
[*]Use nautilus script '[Create Symbolic Link]("http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/create_symbolic_links")' to, um, create a symbolic link.
[*]Move that symlink from the Desktop to ~.
[*]Done.
[/LIST]

---

### Post by nc_jed on 2007-10-29
> **nc_jed said:**
> Problem resolved.  Resolution steps for other poor schlubs that find themselves in similar situation (or if I do in the future and Google it for another fix).

[LIST=1]
[*]Unmount drive (Desktop > Unmount)
[*]Power off drive.
[*]Rename symlink to drive (/home/blake/USBHB to /home/blake/USBHB-delete) 
[*]Power drive back on.
[*]Use nautilus script '[Create Symbolic Link]("http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/create_symbolic_links")' to, um, create a symbolic link.
[*]Move that symlink from the Desktop to ~.
[*]Done.
[/LIST]

aaaaand not.  After a few minutes it goes back to read f-ing only.

Bump

](*,)

---

### Post by nc_jed on 2008-01-25
Seemed to only be a problem (or at least become noticed) when I also plugged in the USB iPod Nano.  

Unfortunately, I have never gotten this iPod to work with Linux.  Anyone want to buy a 1 GB iPod nano?

---

### Post by nc_jed on 2008-04-03
ok, really for real this time, it's fixed, and it was the stupidest thing.

In a nutshell, I moved the USB cable around, and it seems to be working.

Last summer, I bought a combo PCI card/3.5" drive USB 2.0 / Firewire thingee (sabrenet, i think).  Anyway, I have my USB External HD (Iomega if it matters) plugged into one of the PCI cards USB ports in the back of the machine.  Months pass.  Wife buys an iPod Shuffle.  I plug it into the front 3.5" bay thingee because it seems like a handy spot for it.  Like always, the little drive icon auto mounts to the desktop and the File Manager pops up to show me drive contents.  Within seconds, the iPod unmounts (uncleanly i might add) and the USB HD I have goes into read-only mode.  I guess now would be a good time to mention that the 3.5" front USB panel/hub thingee is plugged into a header on the PCI USB card (oh, and did I mention that's where the USB HD was plugged in?)

After giving up on this for months, I decided to give it another try and just happened to plug it in in the back, to a motherboard USB port.  No issues.  None.  At all.  Rhythmbox pops up, i copy music over, etc.  Eject.  I'm just waiting on it to get enough of a charge to see if it actually plays, but after that I think we're good.

I just wanted to close this out should anyone else have the same issues with this setup.

cheers!

---

### Post by cybercookie72 on 2008-05-09
Greetings...

I know this is late to post and all...I was looking up USB drive mount stuff and saw this...

plz forgive me if this is WAY off but had to post just in case it isn't...READ ONLY.... doesn't that mean you can read/copy?  If that is true can't you copy the files then nuke the drive with gpart and put them back... wouldn't that make the files yours again?  OH well thought I would add my two cents....good luck alls:popcorn:

---

