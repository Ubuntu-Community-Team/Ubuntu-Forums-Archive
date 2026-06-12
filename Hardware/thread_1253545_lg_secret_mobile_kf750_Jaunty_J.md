---
title: "lg secret mobile kf750 Jaunty J"
date: 2009-08-30
forum: Hardware
---

### Post by akinnon on 2009-08-30
Hi,
I'm a windows programmer and part time lecturer by day, but by night I'm fixing peoples computers for them. I love ubuntu and desperately hate windows, but i have to stick with it because thats what most of my customers and students use (unless i convert them). When I come across someone who hates windows and is having bucket loads of issues (especially vista), and all they do is browse the web, email, maybe some word processing, I convert them to ubuntu. normally this is fantastic, and everyone's happy. 

however, I have a laptop here (dell inspiron 1525, no bluetooth) which needs to be able to read multimedia from an LG mobile phone.

When connected, I get a mobile broadband device dialog which asks a few questions, and adds the ability to use the phone as a kind of modem. not what I want, but it asks every time i plug in, so I gave in and answered its questions. I go to places menu and select computer. there I find a usb drive entry. When I click this, I get an error Unable to mount location, No media in the drive.

I've been trawling the web looking for help on this. I've tried GmobileMedia which seems to do nothing at all. I've tried phone manager and wammu. wammu worked!! :P BUT there's no way to browse the phone :( and retrieve any pictures or videos taken with the phone. 

I want to be able to access the phone as a usb drive. is this possible?

Regards,
kinnon

---

### Post by akinnon on 2009-08-30
Further to this ( i'm a bit of a noob at ubuntu ) managed to dig the following out of the kern.log:
[SIZE="1"]
Aug 30 23:05:55 laptop kernel: [  776.599485] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, ffff88003cc26080/3cc26080 (bad dma)
Aug 30 23:05:55 laptop kernel: [  776.599943] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-4, CDC Ethernet Device
Aug 30 23:06:03 laptop kernel: [  784.792064] usb 2-3: new high speed USB device using ehci_hcd and address 4
Aug 30 23:06:03 laptop kernel: [  784.948216] usb 2-3: configuration #3 chosen from 1 choice
Aug 30 23:06:03 laptop kernel: [  784.949637] cdc_acm 2-3:3.1: ttyACM0: USB ACM device
Aug 30 23:06:03 laptop kernel: [  784.969338] cdc_acm 2-3:3.3: ttyACM1: USB ACM device
Aug 30 23:06:03 laptop kernel: [  784.986475] cdc_wdm 2-3:3.7: cdc-wdm0: USB WDM device
Aug 30 23:06:03 laptop kernel: [  785.010354] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 30 23:06:03 laptop kernel: [  785.011907] usb-storage: device found at 4
Aug 30 23:06:03 laptop kernel: [  785.011910] usb-storage: waiting for device to settle before scanning
Aug 30 23:06:03 laptop kernel: [  785.030777] usb0: register 'cdc_ether' at usb-0000:00:1d.7-3, CDC Ethernet Device, 02:80:37:0e:03:00
Aug 30 23:06:08 laptop kernel: [  790.008441] usb-storage: device scan complete
Aug 30 23:06:08 laptop kernel: [  790.009433] scsi 6:0:0:0: Direct-Access     LGE      MMC Flash Card      1 PQ: 0 ANSI: 0
Aug 30 23:06:08 laptop kernel: [  790.039301] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug 30 23:06:08 laptop kernel: [  790.039371] sd 6:0:0:0: Attached scsi generic sg2 type 0[/SIZE]

debug file says:
[SIZE="1"]
Aug 30 23:06:03 laptop kernel: [  785.011907] usb-storage: device found at 4
Aug 30 23:06:03 laptop kernel: [  785.011910] usb-storage: waiting for device to settle before scanning
Aug 30 23:06:08 laptop kernel: [  790.008441] usb-storage: device scan complete
Aug 30 23:06:18 laptop kernel: [  799.884033] usb0: no IPv6 routers present[/SIZE]

any help?

---

### Post by akinnon on 2009-08-31
OK, I GIVE UP. I'll advise customer to transfer pictures to memory card and use the SD card slot. If anyone can provide more info in future I would appreciate it, as this in my eyes is a failure. 

Basic needs of most of my customers:
Web browser
word processor
printing
Email
MSN Chat
Music Player
DVD Player
Digital Photos

Normally all the above have been no bother with ubuntu. This is the first one to need their phone browsable via a usb cable and should really be supported.

Hope this provides some help to others.

kinnon.

---

