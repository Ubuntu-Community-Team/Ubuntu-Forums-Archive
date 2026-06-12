---
title: "USB doesn't work with 6.10"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by victor_c26 on 2007-01-12
I had 6.06 installed on this machine and USB worked fine. My Logitech USB mouse was detected and worked fine, and my USB flash drive was detected and auto mounted.

But now that I re-formatted and installed 6.10, USB functionality suddenly disappeared. Everytime I boot Ubuntu with my Logitech mouse on a USB port, it hangs at the splash boot screen as soon as grub loads the partition. Once I switch my mouse over to the PS/2 port, Ubuntu boots just fine.

Then when I try using my USB flash drive, it just isn't detected. It doesn't even appear in the Computer folder. Like the USB ports weren't even connected to the Motherboard headers. Except they are. Everything works in Windows just fine.

Motherboard MSI MS-7093

Boot options: noapic nolapic, pci=noacpi

---

### Post by victor_c26 on 2007-01-14
Nobody knows what the issue might be?

---

### Post by Sef on 2007-01-14
Do you have a laptop?  I've had the same problem with Xubuntu on my laptop.

---

### Post by victor_c26 on 2007-01-14
Nope, it's a desktop computer.

---

### Post by chiisu on 2007-01-20
I've had this issue both with Edgy (Ubuntu and Xubuntu) and Fedora Core 6

---

### Post by maumau on 2007-01-20
hi everybody ):P 
I've the same problem on Edgy, too
My usb pendrive is not now mounted after a crash occured
installing an icon set.
Another pen is normally mounted.

I try to mount it in fstab after made a mount point in /media.
Normally using /dev/sda1  not recognized.

This is my   lsusb
> mauri@ubuntu:~$ lsusb
Bus 006 Device 013: ID 07ab:fc03 Freecom Technologies USB2-IDE IDE bridge
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1241:1166 Belkin 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


This the output of  tail -f /var/log/messages
> Jan 20 21:51:42 ubuntu kernel: [17203523.408000] usb 6-3: new high speed USB device using ehci_hcd and address 19
Jan 20 21:51:42 ubuntu kernel: [17203523.544000] usb 6-3: configuration #1 chosen from 1 choice
Jan 20 21:51:42 ubuntu kernel: [17203523.544000] scsi15 : SCSI emulation for USB Mass Storage devices
Jan 20 21:51:42 ubuntu kernel: [17203523.652000] usb 6-4: reset high speed USB device using ehci_hcd and address 13
Jan 20 21:51:42 ubuntu kernel: [17203523.920000] usb 6-4: reset high speed USB device using ehci_hcd and address 13
Jan 20 21:51:42 ubuntu kernel: [17203523.924000] usb 6-3: USB disconnect, address 19



this the same output of the pendrive correctly mounted
> Jan 20 21:54:43 ubuntu kernel: [17203705.112000] usb 6-3: new high speed USB device using ehci_hcd and address 20
Jan 20 21:54:44 ubuntu kernel: [17203705.348000] usb 6-3: configuration #1 chosen from 1 choice
Jan 20 21:54:44 ubuntu kernel: [17203705.360000] scsi16 : SCSI emulation for USB Mass Storage devices
Jan 20 21:54:49 ubuntu kernel: [17203710.376000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 4.10
Jan 20 21:54:49 ubuntu kernel: [17203710.376000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jan 20 21:54:49 ubuntu kernel: [17203710.388000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Jan 20 21:54:49 ubuntu kernel: [17203710.388000] sda: Write Protect is off
Jan 20 21:54:49 ubuntu kernel: [17203710.400000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Jan 20 21:54:49 ubuntu kernel: [17203710.400000] sda: Write Protect is off
Jan 20 21:54:49 ubuntu kernel: [17203710.400000]  sda: sda1
Jan 20 21:54:49 ubuntu kernel: [17203710.404000] sd 16:0:0:0: Attached scsi removable disk sda
Jan 20 21:54:49 ubuntu kernel: [17203710.404000] sd 16:0:0:0: Attached scsi generic sg0 type 0


many thanks :grin:

---

### Post by maumau on 2007-01-20
I try again
```
sudo mkdir /media/pendrive
```
```
sudo gedit /etc/fstab
```
add the line
```
/dev/sda1 /media/pendrive vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8   0  0
```
than
```
sudo mount -a
```
output
> special device /dev/sda1 does not exists
 
.................. of course  ](*,) 

the same  when I made
> sudo mount -t vfat /dev/sda1 /media/pendrive

---

### Post by maumau on 2007-01-21
I resolv it running in the term

```
sudo modprobe -r ehci-hcd
```
than insert the flash-drive

you need several attempts (or just one)
try try and try  :grin: 

ciao ):P

---

### Post by maumau on 2007-01-21
> I've had the same problem with Xubuntu on my laptop.

it work fine also in Xubuntu-Dapper ;) 

bye

---

