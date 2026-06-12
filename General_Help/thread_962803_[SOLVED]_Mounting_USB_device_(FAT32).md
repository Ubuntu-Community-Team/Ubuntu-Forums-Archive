---
title: "[SOLVED] Mounting USB device (FAT32)"
date: 2008-10-29
forum: General Help
---

### Post by cmb11 on 2008-10-29
Hey guys, here's my problem:

when i plug my usb flash drive (A-DATA 16.2GB) nothing happens.. nothing shown under "places" nor in /media or in /mnt , really nothing changes when I plug it.. I tried it on :frown: windows vista :frown: on the same laptop and it worked without a single error...

some outputs that might help:


    dmesg | tail


[ 4278.985593] usb 5-1: new high speed USB device using ehci_hcd and address 65
[ 4289.380251] usb 5-1: device not accepting address 65, error -110
[ 4289.492037] usb 5-1: new high speed USB device using ehci_hcd and address 66
[ 4299.884757] usb 5-1: device not accepting address 66, error -110
[ 4909.975048] usb 5-2: new high speed USB device using ehci_hcd and address 67
[ 4910.109446] usb 5-2: configuration #1 chosen from 1 choice
[ 4910.110634] scsi26 : SCSI emulation for USB Mass Storage devices
[ 4910.111069] usb-storage: device found at 67
[ 4910.111074] usb-storage: waiting for device to settle before scanning
[ 4915.105099] usb-storage: device scan complete

after a while:

[ 5002.723704] usb 5-2: new high speed USB device using ehci_hcd and address 68
[ 5017.815249] usb 5-2: device descriptor read/64, error -110
[ 5033.009466] usb 5-2: device descriptor read/64, error -110
[ 5033.225393] usb 5-2: new high speed USB device using ehci_hcd and address 69
[ 5048.316169] usb 5-2: device descriptor read/64, error -110
[ 5063.511205] usb 5-2: device descriptor read/64, error -110
[ 5063.726887] usb 5-2: new high speed USB device using ehci_hcd and address 70
[ 5074.120571] usb 5-2: device not accepting address 70, error -110
[ 5074.232425] usb 5-2: new high speed USB device using ehci_hcd and address 71
[ 5084.626066] usb 5-2: device not accepting address 71, error -110




 cat /var/log/messages | tail


Oct 29 22:19:15 h4x0r-CB kernel: [ 4217.870303] scsi 25:0:0:0: Device offlined - not ready after error recovery
Oct 29 22:19:15 h4x0r-CB kernel: [ 4217.981802] usb 5-1: new high speed USB device using ehci_hcd and address 63
Oct 29 22:19:45 h4x0r-CB kernel: [ 4248.484679] usb 5-1: new high speed USB device using ehci_hcd and address 64
Oct 29 22:20:16 h4x0r-CB kernel: [ 4278.985593] usb 5-1: new high speed USB device using ehci_hcd and address 65
Oct 29 22:20:26 h4x0r-CB kernel: [ 4289.492037] usb 5-1: new high speed USB device using ehci_hcd and address 66
Oct 29 22:30:48 h4x0r-CB kernel: [ 4909.975048] usb 5-2: new high speed USB device using ehci_hcd and address 67
Oct 29 22:30:48 h4x0r-CB kernel: [ 4910.109446] usb 5-2: configuration #1 chosen from 1 choice
Oct 29 22:30:48 h4x0r-CB kernel: [ 4910.110634] scsi26 : SCSI emulation for USB Mass Storage devices
Oct 29 22:30:59 h4x0r-CB kernel: [ 4920.708209] usb 5-2: reset high speed USB device using ehci_hcd and address 67
Oct 29 22:31:29 h4x0r-CB kernel: [ 4951.210451] usb 5-2: reset high speed USB device using ehci_hcd and address 67

after a while:

Oct 29 22:30:59 h4x0r-CB kernel: [ 4920.708209] usb 5-2: reset high speed USB device using ehci_hcd and address 67
Oct 29 22:31:29 h4x0r-CB kernel: [ 4951.210451] usb 5-2: reset high speed USB device using ehci_hcd and address 67
Oct 29 22:32:00 h4x0r-CB kernel: [ 4981.712074] usb 5-2: reset high speed USB device using ehci_hcd and address 67
Oct 29 22:32:10 h4x0r-CB kernel: [ 4992.217562] usb 5-2: reset high speed USB device using ehci_hcd and address 67
Oct 29 22:32:21 h4x0r-CB kernel: [ 5002.611265] usb 5-2: USB disconnect, address 67
Oct 29 22:32:21 h4x0r-CB kernel: [ 5002.611579] scsi 26:0:0:0: Device offlined - not ready after error recovery
Oct 29 22:32:21 h4x0r-CB kernel: [ 5002.723704] usb 5-2: new high speed USB device using ehci_hcd and address 68
Oct 29 22:32:51 h4x0r-CB kernel: [ 5033.225393] usb 5-2: new high speed USB device using ehci_hcd and address 69
Oct 29 22:33:22 h4x0r-CB kernel: [ 5063.726887] usb 5-2: new high speed USB device using ehci_hcd and address 70
Oct 29 22:33:32 h4x0r-CB kernel: [ 5074.232425] usb 5-2: new high speed USB device using ehci_hcd and address 71




NOTE: it was working on linux (auto-mounting and everything was fine), but yesterday I moved some files from linux backtrack 3 'iso' to the usb disk (files are: (boot and bt3)) in order to make a bootable usb and since then I'm not beeing able to access it on linux. I then formatted it using vista and (fat32). The device's manual says it support linux kernel 2.4 or later.. I tried it on other distributions and it also didn't work...

other usb flash disks are auto-mounting... So obviously there is something wrong with my usb disk.. I formatted it around 5 times since yesterday and i used different data systems (FAT32 - NTFS) but nothing solved the problem (I'm formatting it usinf my vista partition because as I said there is no problem in accessing the usb flash disk in windows). Before doing any formats the usb came with (MS-DOS) file system.

So please help me diagnose the problem...

One more question: when they say the usb disk is compatible with linux, does a format erase this compatibility ???

---

### Post by alienprdkt on 2008-10-29
sudo mount -t vfat <device> <mount_point>

---

### Post by cmb11 on 2008-10-29
sudo mount -t vfat <device> <mount_point>  

how can I get <device> and <mount_point> ???? :confused:

btw I edited my post, so please check it again..

---

### Post by alienprdkt on 2008-10-29
fdisk -l

see what deice is your ubuntu

/dev/sda(?) and which one is external /dev/sdb(?)

sudo mount -t vfat /dev/sda /dev/sdb

---

### Post by Wayne_V on 2008-10-29
Don't have a solution for you but the following output might help troubleshoot:

# df
# lsusb -v
# lshw
# lsmod | grep usb
# cat /proc/scsi/scsi
# cat /proc/scsi/usb-storage/*

---

### Post by cmb11 on 2008-10-29
sorry alienprdkt... I'm new to linux...

fdisk -l  shows nothing !!

and nothing changes in /dev/ when i plug my usb..

The only change i can see is in /dev/bus/usb/005/ where a file appear each time i plug my usb and then after about 2 mins it disappears.. 

Thank you sooo much for helping me...

---

### Post by alienprdkt on 2008-10-29
#sudo bash 
#fdisk -l

What did you try for an auto mount? before it messed things up.

---

### Post by cmb11 on 2008-10-29
@Wayne_v: lsusb -v and lshw are huge... if you want I can attach the output in a text file

df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113297636   3302604 104285132   4% /
varrun                  516892       104    516788   1% /var/run
varlock                 516892         0    516892   0% /var/lock
udev                    516892        48    516844   1% /dev
devshm                  516892        12    516880   1% /dev/shm
df: `/home/gap/.gvfs': Transport endpoint is not connected


lsmod | grep usb

usb_storage            73664  0 
libusual               19108  1 usb_storage
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
usbcore               146412  7 usb_storage,libusual,uvcvideo,hci_usb,ehci_hcd,uhci_hcd


 cat /proc/scsi/scsi

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: MATSHITA Model: DVD-RAM UJ-850S  Rev: 1.05
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: TOSHIBA MK1234GS Rev: AH00
  Type:   Direct-Access                    ANSI  SCSI revision: 05


cat /proc/scsi/usb-storage/*
 
cat: /proc/scsi/usb-storage/*: No such file or directory

---

### Post by cmb11 on 2008-10-29
@alienprdkt:

fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14217   114198021   83  Linux
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda5           14218       14593     3020188+  82  Linux swap / Solaris


Btw other USBs still automatically mount now... The problem is only with one usb that was working perfectly on linux yesterday but today after copying some files to it from linux (backtrack boot file) it's not!! it's still working flawlessly on windows!!

---

### Post by Wayne_V on 2008-10-29
Are you able to "rmmod ehci_hcd" ?  If so, try that and then reseat your drive.

Has anything else changed?   Are you using the same USB port?   Any other/new USB devices plugged in?

---

### Post by cmb11 on 2008-10-29
#sudo rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules


Btw I tried three usb ports and I always get the same problem.. A friend of mine suggested to format the usb with ext3 file system.. Any idea how i can do that in linux since windows only support fat32 and ntfs. I don't care if I won't be able to use it in windows... I just want it to work on linux.

---

### Post by Wayne_V on 2008-10-29
That's interesting since lsmod shows that ehci_hcd is loaded:
[INDENT]lsmod | grep usb

usb_storage            73664  0 
libusual               19108  1 usb_storage
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
scsi_mod              151436  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
usbcore               146412  7 usb_storage,libusual,uvcvideo,hci_usb,**ehci_hcd**,uhc  i_hcd

[/INDENT]Have you rebooted since this all started (with all other usb devices unplugged if possible)?   You may want to review this page as well:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273)

Until you can get usb_storage to recognize the drive and create device files for it you won't be able to force a mount or reformat or anything like that.

---

### Post by Wayne_V on 2008-10-29
Maybe even a full power cycle, not just a reboot ....

---

### Post by cmb11 on 2008-10-29
I already rebooted many times... 
I even did a clean ubuntu installation lol!! 

Btw thank you soooo much for posting the bug report link. I'm going to try some solutions posted there and i'll let u know what happens..

---

### Post by cmb11 on 2008-10-29
The problem is solved !!!!!!!!!!!!!!!!!!!!!!!! :popcorn: And now my usb device is mounted automatically and its working flawlessly!!:):):):) 

Thank you Wayne_v for the link!!!!!!! Here's the solution posted in the bug report:
"
 Mario Italo wrote on 2008-10-09:

I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.
I hope this help someone.
"
Thank you alienprdkt and Thank you Wayne_v !!!

---

### Post by cmb11 on 2008-10-29
But the only thing I didn't understand is why this was working yesterday and today it required some system modifications to work again !?!?!?

---

