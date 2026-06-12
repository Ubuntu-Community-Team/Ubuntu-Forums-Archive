---
title: "[SOLVED] External USB HDD Not Mounting"
date: 2008-06-07
forum: Hardware
---

### Post by SyntheticShield on 2008-06-07
Hello all.  Im new to ubuntu, not so new to Linux but not all that experienced either.

Ive use Fedora Core and PCLinuxOS and liked PCLinuxOS best between the two but after some issues with setting up ethernet and such with PCLOS I decided to try some other distros.  I installed ubuntu and am kinda impressed as most everything worked out of the box so to speak.  Ethernet, Wireless, Printer, everything seems to be working perfectly.

However, I have a Seagate FreeAgent Desktop 250gb USB HDD that is not mounting.  It is formatted ntfs as I used it on my windows set up and it works fine there (dual booting).  But when I plug it into my laptop I get a pop up that states 'Cannot Mount The Volume'.  It gives me a long detail as to why but I am not sure how to resolve the issue.  I'll have to type out the message, so here goes:

$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: 

Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g /dev/sda1/media/disk -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1/media/ disak ntfs-3g force 0 0.

Since Im dual booting, I'll go back to windows and do as the message states.  I ran the command but didnt get anywhere with it as it was wrote in the pop up message.

If the windows part doesnt work, is there anything else I can do?  Im trying to learn the command line aspects of Linux, but Ive got a ways to go.  Any help would be much appreciated.

---

### Post by SyntheticShield on 2008-06-07
Well I booted into windows and did the Safely Remove Hardware thing, then booted back into ubuntu and everything is working properly now.  External drive is mounting as it should and I am able to access the contents of the drive.

I never knew the drive itself had a record of being in use or not disconnected properly.

---

