---
title: "getting the SPD3400CC external DVD writer to work"
date: 2008-10-18
forum: Hardware
---

### Post by AmberWillow on 2008-10-18
I'm trying to connect the SPD3400CC to my eee-pc
From what i found on the net it worked on feisty, all it needed was a reboot. Which i found odd, but worth a shot. no luck though.
i'm running eeebuntu, 8.04


dmesg gives me the following info:
> 
[   64.566700] usb 5-3: USB disconnect, address 2
[   71.193595] usb 5-3: new high speed USB device using ehci_hcd and address 5
[   71.234034] usb 5-3: configuration #1 chosen from 1 choice
[   71.275318] scsi4 : SCSI emulation for USB Mass Storage devices
[   71.283411] usb-storage: device found at 5
[   71.283419] usb-storage: waiting for device to settle before scanning
[   71.945254] usb-storage: device scan complete
[   71.946314] scsi 4:0:0:0: CD-ROM            PHILIPS  SPD3400CC        JP04 PQ: 0 ANSI: 0
[   71.947194] scsi 4:0:0:0: Attached scsi generic sg3 type 5


and thats all. I've tried to put in both a CD and a DVD, but that doesnt even register on dmesg. mounting /dev/sg3 says no block device.

i found one other dmesg log online that showed the drive being loaded, which had the following line:
sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form3 cdda tray

i'm guessing i need that to appear as well to get things working, and i think its simply a lack of certain packages i'm missing.. i can't figure out what though.

any help would be appreciated,
Amber Willow

---

### Post by AmberWillow on 2008-10-23
is there anyone who knows what modules are needed to automount an external DVD? or if there is something else I'm doing wrong?

Much obliged,
Amber

---

