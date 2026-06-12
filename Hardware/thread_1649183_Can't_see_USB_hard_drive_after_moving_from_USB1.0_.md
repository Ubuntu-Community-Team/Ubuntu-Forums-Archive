---
title: "Can't see USB hard drive after moving from USB1.0 port to USB2.0 port"
date: 2010-12-19
forum: Hardware
---

### Post by bjsiders on 2010-12-19
Hi!  I have an older Dell box (AMD pre-Athlon) running Ubuntu and it obviously doesn't have any USB 2.0 ports on it.  I recently bought a 2 TB external USB drive and plugged it into the on-board USB 1.0 ports, and moved some files over.  The next day, the USB 2.0 expansion card I bought arrived, and shut the box down, installed the card, moved the USB drive over to a 2.0 port, and booted the machine.

Now I can't seem to view the contents of the disk, I get the following error:

[FONT="Courier New"]bjsiders@archaelicos:/mnt/iomega$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.1G  4.7G  4.0G  54% /
varrun                125M  244K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   48K  125M   1% /dev
devshm                125M   12K  125M   1% /dev/shm
/dev/sdb               37G   16G   20G  46% /mnt/data
/dev/sdc1             1.9T   28G  1.7T   2% /mnt/iomega
gvfs-fuse-daemon      9.1G  4.7G  4.0G  54% /home/bjsiders/.gvfs
bjsiders@archaelicos:/mnt/iomega$ ls
ls: reading directory .: Input/output error
[/FONT]

Just before this happened, I had moved our last 10 years of family pictures over to this drive, including my children's births, etc, so this issue is critically important (to me).

Sadly, I'm not sure how to diagnose and fix this.  This is a brand new Iomega drive, out of the box less than 48 hours, I seriously doubt the drive is actually busted.  I'm running Gnome on the desktop and at the moment it's upgrading to the latest Ubuntu (I installed Ubuntu on here years ago, it's a few versions back, I'm finally upgrading it).
 
Any pointers would be greatly appreciated, thank you!

---

### Post by bjsiders on 2010-12-20
Some more information on this problem.

(1) If I plug the drive back into the old USB1 port, I can unmount it and remount it and view the file system/contents, so I am pretty sure the disk is not the problem.

(2) dmesg yields the following:

[58280.663459]  =======================
[58280.663530] Buffer I/O error on device sdc1, logical block 1289
[58280.663542] lost page write due to I/O error on sdc1
[58285.343467] usb 1-1: USB disconnect, address 3
[58297.652839] usb 4-3: new high speed USB device using ehci_hcd and address 11
[58312.772052] usb 4-3: device descriptor read/64, error -110
[58328.003928] usb 4-3: device descriptor read/64, error -110
[58328.231317] usb 4-3: new high speed USB device using ehci_hcd and address 12
[58343.350540] usb 4-3: device descriptor read/64, error -110
[58358.589822] usb 4-3: device descriptor read/64, error -110
[58358.819817] usb 4-3: new high speed USB device using ehci_hcd and address 13
[58369.239276] usb 4-3: device not accepting address 13, error -110
[58369.359299] usb 4-3: new high speed USB device using ehci_hcd and address 14
[58379.778758] usb 4-3: device not accepting address 14, error -110

The disk does not show up in /dev or /proc/partition through the new USB 2.0 card.
 
Could this be a simple matter of needing to upgrade Ubuntu to get the right driver for this expansion card?  My upgrade is running right now and should finish this evening, I'll post again if that fixes it.

---

