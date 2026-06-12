---
title: "USB not recognized by Maverick, but XP can?"
date: 2011-02-18
forum: Hardware
---

### Post by MR2Quick on 2011-02-18
I have a USB flash drive that I am trying to access in Maverick.  When I plug it in during a Windows XP session, it recognizes it as a USB device, but nothing more.  I can't browse it, copy files to or from it, or format it.  

When I plug it in during a 10.10 session, it does not do anything with the USB key.  Is there a way to see where it gets mounted to, if it actually does get mounted?

any and all help is greatly appreciated!

Thanks!

---

### Post by coffeecat on 2011-02-18
If both Windows and Ubuntu are having problems with it, it could be failing. You say that when you plug it in to 10.10, it does not do anything, I presume you mean a Nautilus browser window doesn't open. Does anything appear in the Places menu or in the Places left pane in a Nautilus window?

Let's see if the system recognises it even if it is not being mounted. In Ubuntu, plug the USB stick in, open a terminal and post the output of these two commands:

```
dmesg | tail
sudo fdisk -lu
```

By the way, you're still showing Jaunty/9.04 in your profile.

---

### Post by MR2Quick on 2011-03-04
Thank you for the heads up on the profile update!

Here are the results from the terminal:

```
petey@Ubuntop:~$ dmesg | tail
[   17.328713] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   17.916646] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   17.916649] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   17.916838] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.306362] dell-wmi: Received unknown WMI event (0x11)
[   19.579800] dell-wmi: Received unknown WMI event (0x11)
[   21.267116] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   28.116012] eth0: no IPv6 routers present
[   31.526081] lo: Disabled Privacy Extensions
[  295.365096] usb 6-2: new low speed USB device using uhci_hcd and address 2
petey@Ubuntop:~$ sudo fdisk -lu
[sudo] password for petey: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2dbec3bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       275326974   488396799   106534913    5  Extended
/dev/sda2   *          63   275325865   137662901+   7  HPFS/NTFS
/dev/sda5       275326976   479645695   102159360   83  Linux
/dev/sda6       479647744   488396799     4374528   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I am assuming the "lo-speed usb disk" is the usb key. **EDIT: after unplugging the USB key, I'm not too sure about that statement anymore.  I did realize that I have a USB wireless mouse attached, so that's probably whats registered as the usb key. ****EDIT EDIT:  re-running the dmesg shows that "USB disconnect, address 2".  So the computer is seeing the USB key, but is not mounting it.  true?

Thanks!

---

### Post by coffeecat on 2011-03-04
> **MR2Quick said:**
> So the computer is seeing the USB key, but is not mounting it.  true?

Sorry, no. The system is not seeing it at all. Here's my "dmesg | tail" after plugging in a working USB flash drive:

```
[ 1499.565390] sd 9:0:0:0: [sde] Write Protect is off
[ 1499.565399] sd 9:0:0:0: [sde] Mode Sense: 43 00 00 00
[ 1499.566882] sd 9:0:0:0: [sde] No Caching mode page present
[ 1499.566889] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 1499.571624] sd 9:0:0:0: [sde] No Caching mode page present
[ 1499.571630] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 1499.572646]  sde: sde1
[ 1499.576127] sd 9:0:0:0: [sde] No Caching mode page present
[ 1499.576133] sd 9:0:0:0: [sde] Assuming drive cache: write through
[ 1499.576139] sd 9:0:0:0: [sde] Attached SCSI removable disk
```In my case the system is seeing my drive as sde. That's because I have an internal second drive (sdb) and a card reader that takes care of sdc and sdd. In your case I would expect that your usb drive would be seen as sdb, but there's not a hint of sdb, nor any other drive apart from sda (your one internal drive) with either dmesg or fdisk.

Don't worry that my output says "Attached SCSI removable disk". It says that for USB drives - it's a historical remnant.

Is the drive still non-operational in Windows? If so, it's probably a goner.

---

### Post by MR2Quick on 2011-03-04
I actually just tried it on a co-workers machine.  It recognized the drive but would ask for a driver for it.  After some scrounging around, it requires a "sentinal" driver pack for it and thats the only way it will work.  I have no idea why it would require that, but I'm thinking the drive might be toast.

---

### Post by coffeecat on 2011-03-04
Googling 'Sentinel driver' came up with this:

[http://www.rowley.co.uk/crossworks/safenet_install.htm](http://www.rowley.co.uk/crossworks/safenet_install.htm)

I wonder if the flash drive is formatted in some weird and wonderful way that requires a driver for Windows and which also makes it invisible to Ubuntu. In which case, if you could reformat it in Windows it might then be detectable in Ubuntu.

If it isn't toast, that is.

---

