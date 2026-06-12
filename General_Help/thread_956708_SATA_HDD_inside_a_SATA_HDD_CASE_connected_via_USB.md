---
title: "SATA HDD inside a SATA HDD CASE connected via USB"
date: 2008-10-23
forum: General Help
---

### Post by castrogeneris on 2008-10-23
[FONT="System"]Hello everyone, I've a 160Gb sata hdd and the same is in a SATA HDD CASE and connected via usb; in an hour or two it always unmounts/losts-connection/fails-to-(be)read/etc... itself. It happens if I'm using any application, so maybe is not an app droping it out... when this happens this is presented in /var/log/messages: [/FONT][SIZE="1"][SIZE="1"][FONT="Arial"]usb 4-4: reset high speed USB device using ehci_hcd and address 17
Oct 23 12:30:01 castrogeneris-laptop kernel: [63790.334761] usb 4-4: reset high speed USB device using ehci_hcd and address 17
Oct 23 12:30:01 castrogeneris-laptop kernel: [63790.878666] usb 4-4: reset high speed USB device using ehci_hcd and address 17
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.584675] usb 4-4: reset high speed USB device using ehci_hcd and address 17
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.992879] usb 4-4: USB disconnect, address 17
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.994629] sd 8:0:0:0: Device offlined - not ready after error recovery
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995354] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995367] end_request: I/O error, dev sdb, sector 64
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995375] printk: 6 messages suppressed.
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995390] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995423] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995443] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995473] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995488] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995503] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995517] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995531] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995545] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.995559] lost page write due to I/O error on sdb1
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.997536] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 23 12:30:02 castrogeneris-laptop kernel: [63791.997547] end_request: I/O error, dev sdb, sector 21443
Oct 23 12:30:03 castrogeneris-laptop kernel: [29436.866174] usb 4-4: new high speed USB device using ehci_hcd and address 20
Oct 23 12:30:03 castrogeneris-laptop kernel: [63792.970428] usb 4-4: new high speed USB device using ehci_hcd and address 21
Oct 23 12:30:04 castrogeneris-laptop kernel: [29437.506585] usb 4-4: new high speed USB device using ehci_hcd and address 22
Oct 23 12:30:04 castrogeneris-laptop kernel: [63794.279661] usb 4-4: new high speed USB device using ehci_hcd and address 23
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368921] printk: 3967 messages suppressed.
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368936] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368947] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368954] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368962] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368969] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368976] lost page write due to I/O error on sdb1
Oct 23 12:30:38 castrogeneris-laptop kernel: [29471.368983] lost page write due to I/O error on sdb1[/FONT][/SIZE][/SIZE]...can that reset in the beginning be the clue...? Thankx

---

### Post by dcstar on 2008-10-25
> **castrogeneris said:**
> Hello everyone, I've a 160Gb sata hdd and the same is in a SATA HDD CASE and connected via usb; in an hour or two it always unmounts/losts-connection/fails-to-(be)read/etc... itself. It happens if I'm using any application, so maybe is not an app droping it out... when this happens this is presented in /var/log/messages:

*Oct 23 12:30:01 castrogeneris-laptop kernel: [63790.334761] **usb 4-4: reset high speed USB device** using ehci_hcd and address 17*
.........

If the USB port shuts down - because of a power management setting or other issue, possibly the power required for the drive is overheating the USB controller after a time - then you will have this problem.

It looks like the USB port is shutting down, the question is why.

---

### Post by castrogeneris on 2008-10-25
Thanks, so it's a hardware issue then... i thought i was mounting erratically the device. The laptop has 2 usb ports maybe i should connect it to the other one. Last Night it happened again, and maybe you should know that this HDD contains music and Virtual disks (.vdi) and also know that it unmounts and mounts itself in a diferent location, so the apps doesn't find the files and everything's #$%#$&. So, should i revise hardware or software? .... By the way today I have a bigger trouble the laptop restarts itself any moment even with a live cd inside... this last sounds worst, what can it be???

---

### Post by dcstar on 2008-10-25
> **castrogeneris said:**
> 
.........
By the way today I have a bigger trouble the laptop restarts itself any moment even with a live cd inside... this last sounds worst, what can it be???

You seem to have major hardware issues, the USB might just be a symptom of a bigger problem.

---

### Post by castrogeneris on 2008-10-29
Hi, something I noticed is that when I turn on the laptop, the little fan beggins to spin... for 2 seconds only and then stops spining and finally shuting down the Laptop... Can this be fixed? or I should say goodbye to my old little IBM Thinkpad C40 tank? That'll be a shame, I feel this laptop is just one of the best suited for Linux...

---

