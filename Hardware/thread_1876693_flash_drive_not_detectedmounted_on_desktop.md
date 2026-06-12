---
title: "flash drive not detected/mounted on desktop"
date: 2011-11-06
forum: Hardware
---

### Post by brotherz on 2011-11-06
My problem is that when I plug a flash drive into my USB port, nothing appears on the desktop and it does not appear to mount.
 

 specs:
 Ubuntu 11.10 (xfce desktop) (I also tried it with the Gnome 2D desktop with same results)
 Dell with Intel Pentium 2 CPU, 3.2 GHz  i686 32-bit
 nVidia Corporation NV44A [GeForce 6200] 
 

 In settings editor (Xfconf) I have enabled: automount drives, automount media, and autobrowse.
 

 (The flash drive is detected perfectly well on an e-Machine running ubuntu 10.04, producing an icon on the desktop when inserted.  The output of  'lsusb', 'fdisk -l', and 'mount' are all as expected with this device on the e-Machine.)
 

 Although nothing appears on the Dell 11.10 desktop when I plug in the flash drive, command 'lsusb' shows it as the Memorex device:
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 03f0:4212 Hewlett-Packard  
 Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305  
 **Bus 001 Device 005: ID 12f7:1a00 Memorex Products, Inc. TD Classic 003B ** 
 

 command 'mount' (it doesn't appear):
 /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)  
 proc on /proc type proc (rw,noexec,nosuid,nodev)  
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)  
 fusectl on /sys/fs/fuse/connections type fusectl (rw)  
 none on /sys/kernel/debug type debugfs (rw)  
 none on /sys/kernel/security type securityfs (rw)  
 udev on /dev type devtmpfs (rw,mode=0755)  
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)  
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)  
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)  
 none on /run/shm type tmpfs (rw,nosuid,nodev)  
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)  
 gvfs-fuse-daemon on /home/leslie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=leslie)  
 

 command 'fdisk -l' (it doesn't appear):
 Disk /dev/sda: 120.0 GB, 120034123776 bytes  
 255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x000f0ddd  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *        2048   232347647   116172800   83  Linux  
 /dev/sda2       232349694   234440703     1045505    5  Extended  
 /dev/sda5       232349696   234440703     1045504   82  Linux swap / Solaris
 

 lspci | grep USB gives:
 

 00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)  
 

 I am concerned about trying to put this drive into another one of my USB ports on this machine in case it will somehow disable the port (I need them for my other devices like printers etc.) That may be a completely unreasonable concern.
 

 In my research I have discovered approaches like 'sudo rmmod uhci_hcd' and other more specific ways of unbinding ehci_hcd support from the PCI device, where you specify the exact PCI location.  I can't tell from the above lspci list which would be the location of the USB in question, that has my flash drive.
 

 Furthermore, this latter fix takes me beyond my 'comfort zone' since I am not used to kernel commands.  But I am willing to go there if someone more expert tells me this is the best thing to do.
 

 Any advice on fixing this problem?  Thanks in advance.

---

### Post by ajgreeny on 2011-11-06
Are you certain that the usb socket is a good one?

No output from ```
sudo fdisk -l
``` is a bit worrying on that score;  I presume you used the sudo prefix?  I think you must have to get the output that you got.

---

### Post by brotherz on 2011-11-07
> **ajgreeny said:**
> Are you certain that the usb socket is a good one?

No output from ```
sudo fdisk -l
``` is a bit worrying on that score;  I presume you used the sudo prefix?  I think you must have to get the output that you got.

(Yes, sudo fdisk -l) On the assumption that it must be a bad socket, I plugged the drive into a different USB slot and it detected/mounted just fine.  What that teaches me is that if the socket is bad, the device can be detected with 'lsusb' but nothing more can happen.

Thank you for reading and responding to my question.  If it's not too much trouble, can you point me to somewhere where I can learn about fixing a bad USB socket, or give me some general guidance?

---

### Post by brotherz on 2011-11-07
To add to the previous, this usb port does accurately detect my audio headset and display its information.  And my mouse works on it.   So I guess if it is a socket problem, it affects flash drives but not other devices?

---

### Post by ajgreeny on 2011-11-07
Sorry, I have absolutely no idea about that.  It seems odd that some devices work in the socket but others don't, but that is the total sum of my ability here, I'm afraid.

---

### Post by brotherz on 2011-11-07
> **ajgreeny said:**
> Sorry, I have absolutely no idea about that.  It seems odd that some devices work in the socket but others don't, but that is the total sum of my ability here, I'm afraid.

But thanks so much, anyway. Since I can do everything I need to do, it is okay if there are some little mysteries left over.  Thanks again for the support.

---

