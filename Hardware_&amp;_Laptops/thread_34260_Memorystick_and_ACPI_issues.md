---
title: "Memorystick and ACPI issues"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by anders.ostling on 2005-05-14
Hi all

First let me say congratulate the Ubuntu developers to a really great product! I have been jumping between RH/FC and Slackware for the last 6 years, with an occasincal visit to Suse and other novelities. This is my first experience of a DEB system, and I have noticed that I have a lot to learn, which is a good thing!

The reason for deflecting from the FC camp was that RH seems to dismiss the desktop users, and I as a heavy laptop user were suffering. I really hope the Ubuntu will fit me better. These first two days looks promising, I already have 

* GPRS (Vodafone) IP connection over my Sony Ericson V800 via Bluetooth.
* Syncing my Palm Zire 72 with Evolution is working again (yessss)
* Wireless connection (ipw2100) worked out of the box

However, all of us know, there is still room for improvment. I have three specific problems that I would like to solve (with your help of course).

1. When I attach my SE V800 phone via the USB cable, the message log says all the usual stuff, including that it has found the sda device. But it does not list any partitions (it's a 256 MB FAT memorystick duo) or tries to mount it automagically. I tried to mount it by hand using /dev/sda1, and that worked fine and the folder appeared on the desktop. But when I tried to open the folder, I sent nautilus into deep coma. Coult not even kill-9 but had to restart the system.

kernel: usb 2-2: new full speed USB device using uhci_hcd and address 6
kernel: cdc_acm 2-2:1.1: ttyACM0: USB ACM device
kernel: cdc_acm 2-2:1.3: ttyACM1: USB ACM device
kernel: scsi2 : SCSI emulation for USB Mass Storage devices
usb.agent[20791]:      usb-storage: already loaded
usb.agent[20725]:      cdc-acm: already loaded
usb.agent[20706]:      cdc-acm: already loaded
kernel:   Vendor: Sony Eri  Model: Memory Stick      Rev: 0000
kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
kernel: SCSI device sda: 975872 512-byte hdwr sectors (500 MB)
kernel: sda: Write Protect is off
kernel: SCSI device sda: 975872 512-byte hdwr sectors (500 MB)
kernel: sda: Write Protect is off
kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
scsi.agent[20995]:      sd_mod: loaded sucessfully

What bothers me a bit is that it loads the cdc-acm driver. If I remember correctly, this is for USB networking, is'nt it? 

EDIT: I have used an SD card in an USB adapter. Works just fine to browse and copy files to/from, so USB storage seems to be ok. The filesystem were FAT on the SD card.

2. Power saving. I was really hoping that the ACPI suspend (mem or disk) should work, but when I choose Suspend to disk from the System menu, the LCD panel goes into a psychadelic dance and the hard drive lamp is more or less contant on for several minutes. I have tried twice with the same result. Only resort has been to power of with brute force. One advice was to disable the parallell port in BIOS since the IRQ could interfer with ACPI. I have done that. Any other advice for a Dell D800?

EDIT: I found the page HoaryPM, and updated the /etc/default/acpi-support. Added ACPI_SLEEP=true, and after a restart I was able to suspend (to memory). However, the wakeup was not successful and I had to hard-reset the system to recover from the lockup.

3. As I mentioned, I had an FC3 installation before.  I kept the LVM config since my home directory was in an LV. During boot, Ubuntu tries to fsck the /home partition but fails complaining that the partitiions has "too new features". A simple CTRL-D exits and the boot continues as normal. I guess that the ext3 tools are newer in FC3 than in Ubuntu. Any good advice on how I can update or otherwise get rid of this "error message"?

Last thing; I was a bit surpirised that NetworkManager was missing from Ubuntu. I installed it from a third party, but it was not really working so it had to go. Then I found the "netapplet" package, and it seems to be more or less equivalent, except the automatic switching of networks. Any ideas on if there is plans to implement that feature, or if NM is "on its way" to Ubuntu?

Best regards and happy Ubunting!

Anders 
IKEA IT Sweden

---

