---
title: "automounting mp3 player"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by THEBIGEYE on 2007-04-02
i had to do a reinstall of edgy, and when i did my mp3 player wont automount  i ran syslog then pluged in device here is the output. it seems to be having trouble making a lock on the device. ```
 Apr  3 02:29:40 ian-desktop usbmount[15481]: cannot acquire lock /var/run/usbmount/.mount.lock
Apr  3 02:29:40 ian-desktop usbmount[15502]: cannot acquire lock /var/run/usbmount/.mount.lock
Apr  3 02:29:49 ian-desktop dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  3 02:29:49 ian-desktop dhclient: DHCPACK from 192.168.0.1
Apr  3 02:29:49 ian-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Apr  3 02:29:49 ian-desktop dhclient: bound to 212.139.59.215 -- renewal in 120 seconds.
Apr  3 02:31:49 ian-desktop dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  3 02:31:49 ian-desktop dhclient: DHCPACK from 192.168.0.1
Apr  3 02:31:49 ian-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Apr  3 02:31:49 ian-desktop dhclient: bound to 212.139.59.215 -- renewal in 116 seconds.
Apr  3 02:33:25 ian-desktop kernel: [17185763.072000] usb 1-5: USB disconnect, address 5
Apr  3 02:33:25 ian-desktop kernel: [17185763.312000]  6:0:0:0: rejecting I/O to dead device
Apr  3 02:33:31 ian-desktop kernel: [17185768.668000] usb 1-5: new full speed USB device using ohci_hcd and address 6
Apr  3 02:33:32 ian-desktop kernel: [17185769.608000] usb 1-5: configuration #1 chosen from 1 choice
Apr  3 02:33:32 ian-desktop kernel: [17185769.616000] scsi7 : SCSI emulation for USB Mass Storage devices
Apr  3 02:33:32 ian-desktop kernel: [17185769.616000] usb-storage: device found at 6
Apr  3 02:33:32 ian-desktop kernel: [17185769.616000] usb-storage: waiting for device to settle before scanning
Apr  3 02:33:36 ian-desktop kernel: [17185774.620000] usb-storage: device scan complete
Apr  3 02:33:36 ian-desktop kernel: [17185774.628000]   Vendor: SigmaTel  Model: MSCN              Rev: 0100
Apr  3 02:33:36 ian-desktop kernel: [17185774.628000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Apr  3 02:33:36 ian-desktop kernel: [17185774.636000] SCSI device sda: 251328 2048-byte hdwr sectors (515 MB)
Apr  3 02:33:36 ian-desktop kernel: [17185774.644000] sda: Write Protect is off
Apr  3 02:33:36 ian-desktop kernel: [17185774.644000] sda: Mode Sense: 3e 00 00 00
Apr  3 02:33:36 ian-desktop kernel: [17185774.644000] sda: assuming drive cache: write through
Apr  3 02:33:37 ian-desktop kernel: [17185774.664000] SCSI device sda: 251328 2048-byte hdwr sectors (515 MB)
Apr  3 02:33:37 ian-desktop kernel: [17185774.668000] sda: Write Protect is off
Apr  3 02:33:37 ian-desktop kernel: [17185774.668000] sda: Mode Sense: 3e 00 00 00
Apr  3 02:33:37 ian-desktop kernel: [17185774.668000] sda: assuming drive cache: write through
Apr  3 02:33:37 ian-desktop kernel: [17185774.668000]  sda: sda1
Apr  3 02:33:37 ian-desktop kernel: [17185774.684000] sd 7:0:0:0: Attached scsi removable disk sda
Apr  3 02:33:37 ian-desktop kernel: [17185774.684000] sd 7:0:0:0: Attached scsi generic sg0 type 0
Apr  3 02:33:37 ian-desktop usbmount[15997]: cannot acquire lock /var/run/usbmount/.mount.lock
Apr  3 02:33:37 ian-desktop usbmount[16017]: cannot acquire lock /var/run/usbmount/.mount.lock
Apr  3 02:33:45 ian-desktop dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Apr  3 02:33:45 ian-desktop dhclient: DHCPACK from 192.168.0.1
Apr  3 02:33:45 ian-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Apr  3 02:33:45 ian-desktop dhclient: bound to 212.139.59.215 -- renewal in 143 seconds. 
```

i have looked thru the forums and google with no joy i can mount by hand but i like to get issued solved as ive just convinced my wife to change over thanks in advance if anyone can help

---

### Post by mlissner on 2007-04-04
This is a guess, but I think that file is one that Ubuntu creates to keep a note that the USB volume is connected. 

You might just open that file and see what's in it. That could lead to a quick solution. Alternatively, I'd try rebooting, if you haven't already. Not the best help, I know, but it's a thought.

---

### Post by robenroute on 2007-04-04
I've had nothing but shoddy USB connections between my Edgy box and my mp3 player (and also my Palm T5). A few days ago, I installed Feisty on a separate partition and all the shoddiness of the USB connections had gone.

You could try the Fiesty live CD and see how that goes....

Good Luck.

---

### Post by THEBIGEYE on 2007-04-04
cheers gonna wait till final release but plan to upgrade (by fresh install of course)

---

### Post by MST3Kakalina on 2007-04-15
Have you tried using **pmount** in the terminal?  I was having similar problems, but then someone suggested using pmount.  It functions exactly like mount, but wraps it so that you don't need to dick around with fstab.  It only works with removable media, but that's exactly what an MP3 player is.

---

### Post by zero244 on 2008-03-23
Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your password.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scsi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

---

