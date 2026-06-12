---
title: "Epson USB printer: &quot;/usr/lib/cups/backend/epson failed&quot;"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by miestrâ on 2007-10-30
My Epson Stylus C41UX (USB) worked fine in Feisty... eventually. The printer reads fine and functional in Gutsy, but whenever I try to print anything, it sends to the printer normally, then the job suspends. The CUPS error is: "/usr/lib/cups/backend/epson failed"

The Debug Printing output:

> Sebastienne:~$ lsmod | grep usb
usblp                  15104  0 
usb_storage            73024  1 
scsi_mod              147084  4 sg,sd_mod,libata,usb_storage
libusual               18448  1 usb_storage
ide_core              116804  4 ide_cd,ide_disk,usb_storage,via82cxxx
usbcore               138632  6 usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
Sebastienne:~$ lpinfo -v
network socket
network beh
direct epson:/dev/usblp0
direct hpfax
direct hp
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct scsi
network smb
Sebastienne:~$ tail -f /var/log/messages
Oct 30 20:36:20 Sebastienne -- MARK --
Oct 30 20:55:59 Sebastienne kernel: [ 3646.405789] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
Oct 30 20:56:08 Sebastienne kernel: [ 3654.971058] usb 1-2: new full speed USB device using uhci_hcd and address 3
Oct 30 20:56:08 Sebastienne kernel: [ 3655.152911] usb 1-2: configuration #1 chosen from 1 choice
Oct 30 20:56:08 Sebastienne kernel: [ 3655.163013] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005


I brought this up in [another thread]("http://ubuntuforums.org/showthread.php?p=3588913"), but the person in that thread threw up their hands in horror. ;-)

---

### Post by miestrâ on 2007-11-25
*bump* Anyone?

I'm seeing this same problem come up in several different forums via Google, but no-one seems to have any answers. If it's a problem with the backend, has someone done a bug report? I am not skilled in such things and wouldn't know how to begin myself.

---

### Post by j8a on 2008-04-08
I have the same problem with HP printers shared on Samba.

---

