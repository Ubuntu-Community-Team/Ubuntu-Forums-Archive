---
title: "Digital Camera not accessable"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by knowerrors on 2005-11-13
[Solved - solution below]
Hi all,

I have an Olypus C-4000 that was alwasy accessable using other versions of Debian, simply by using konqueror and going to sda1 in the devices area.  In kubuntu, nothing comes up, even though I have gphoto installed, as well as the Camedia package.  

This is the info that /var/log/messages gives:

Nov 13 12:43:25 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 2
Nov 13 12:43:25 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Nov 13 12:43:25 localhost usb.agent[9376]:      usb-storage: already loaded
Nov 13 12:43:25 localhost usb.agent[9376]:      libgphoto2: loaded successfully
Nov 13 12:43:30 localhost kernel:   Vendor: OLYMPUS   Model: C4100Z/C4000Z     Rev: 1.00
Nov 13 12:43:30 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov 13 12:43:30 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Nov 13 12:43:30 localhost kernel: sda: Write Protect is off
Nov 13 12:43:30 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Nov 13 12:43:30 localhost kernel: sda: Write Protect is off
Nov 13 12:43:30 localhost kernel:  sda: sda1
Nov 13 12:43:30 localhost kernel: Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Nov 13 12:43:30 localhost scsi.agent[9467]:      sd_mod: loaded sucessfully (for disk)

I seems to find and open the camera disk, but I can't find any way to access it, including through digikam.  Can anybody help with this?  
Thanks in Advance
KE

Solution:

Add this line to fstab
/dev/sda1       /mnt/usbstorage vfat rw,user,noauto  0       0

Add a folder named usbstorage to /mnt

All fixed!

---

### Post by tim15856 on 2005-11-16
I've never been able to get my C-4000 to work with Linux. gphoto doesn't list it as being compatible. I always put my SM card in a USB reader to get them on my Linux box. Now that you mention it, I'll have to try it again when I get home.

---

### Post by knowerrors on 2005-11-16
I access the camera either through the desktop - it shows up as a mounted usb-thumb drive, or through Digikam, which I have it listed as a USB Mass Storage Camera, Camera Title "Directory Browse", Camera Mount Patch "/mnt/usbstorage"

Hope this helps... btw, Im using Kubuntu, hence Digikam, which for me is best linux digital photo / camera prog in either Gnome or KDE

BTW- I see others with this same problem with Breezy with various USB storage devices and media players... maybe the solution shown in my first post should be a sticky or something.

---

### Post by tim15856 on 2005-11-17
Perhaps that might also fix a problem that just started. My USB flash stick always mounted and appeared on the desktop. Yesterday, it stopped showing up. I'll try it when I get home.

---

