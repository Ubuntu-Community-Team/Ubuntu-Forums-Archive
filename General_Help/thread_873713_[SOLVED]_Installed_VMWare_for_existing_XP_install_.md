---
title: "[SOLVED] Installed VMWare for existing XP install - can no longer mount NTFS partitio"
date: 2008-07-29
forum: General Help
---

### Post by bg1256 on 2008-07-29
The title sums it up, I suppose.

I installed VMWare according to a HowTo on the forums, and it worked great. I can now access my existing XP install from within Ubuntu.

However, I can no longer mount the partitions used by the virtual machines, that is, my C:\ drive and E:\ drive, even when VMWare is not running.

Is this normal? 

Here is the error message I receive:

"Cannot Mount volume.

Unable to mount the volume Documents.

$LogFile indicates unclean shutdown (0, 1). Failed to mount '/dev/sda2': Operation not supported Mount is denied because NTFS is marked to be in use. choose one action: Choice 1: If you have Windows then disconnect the external device by clicking on the "safely remove hardware' icon in the Windows taskbar then shutdown Windows cleanly. choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda2 /media/Documents -o force       Or add the option to the relevant row in the /etc/fstab file:   /dev/sda2 /media/Documents ntfs-3g force 0 0 "

Any ideas?

---

### Post by bg1256 on 2008-07-29
Well, I think I just solved my own problem.

The last time I used VMWare, I forgot to shut down windows before killing the virtual machine. I restarted Windows, shut it down, and now i can access my drives again.

Sorry for the needless post; perhaps someone else will eventually benefit.

---

