---
title: "Mad Dog External DVD Writer"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by locald on 2006-02-22
Hi,

I am trying to make my new Mad Dog externel DVD burner work on Ubuntu 5.10. It has an USB cable connected to the system. It actually worked for a little while. Here is the message in /var/log/messages earlier.

Feb 21 07:17:10 localhost kernel: [4294700.268000] Uniform CD-ROM driver Revision: 3.20
Feb 21 07:17:10 localhost kernel: [4294700.280000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Feb 21 07:17:10 localhost kernel: [4294700.281000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
Feb 21 07:17:10 localhost kernel: [4294700.659000] NET: Registered protocol family 17
Feb 21 07:17:10 localhost kernel: [4294704.589000]   Vendor: MAD DOG   Model: MD-16XDVD9A4      Rev: 1.F0
Feb 21 07:17:10 localhost kernel: [4294704.589000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Feb 21 07:17:10 localhost kernel: [4294704.597000] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Feb 21 07:17:10 localhost kernel: [4294704.598000] Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 5

Now, it seems that the system doesn't recognize the burner anymore. When the external burner is plugged in, the following messages appeared in /var/log/messages.

Feb 22 01:09:58 localhost kernel: [4294858.778000] usb 5-5: new high speed USB device using ehci_hcd and address 3
Feb 22 01:09:59 localhost kernel: [4294858.932000] scsi3 : SCSI emulation for USB Mass Storage devices
Feb 22 01:09:59 localhost usb.agent[8406]:      usb-storage: already loaded
Feb 22 01:10:04 localhost kernel: [4294863.954000]   Vendor: USB 2.0   Model: Storage Device    Rev: 0111
Feb 22 01:10:04 localhost kernel: [4294863.954000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 22 01:10:04 localhost kernel: [4294863.957000] SCSI device sdb: 4294967291 512-byte hdwr sectors (2199023 MB)
Feb 22 01:10:04 localhost kernel: [4294863.960000] SCSI device sdb: 4294967290 512-byte hdwr sectors (2199023 MB)
Feb 22 01:10:04 localhost kernel: [4294863.960000]  /dev/scsi/host3/bus0/target0/lun0:<6>sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294863.962000]     Additional sense: No additional sense information
Feb 22 01:10:04 localhost kernel: [4294863.967000] sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294863.967000]     Additional sense: No additional sense information
Feb 22 01:10:04 localhost kernel: [4294863.969000] sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294863.969000]     Additional sense: No additional sense information
Feb 22 01:10:04 localhost kernel: [4294863.969000]  unknown partition table
Feb 22 01:10:04 localhost kernel: [4294863.969000] Attached scsi disk sdb at scsi3, channel 0, id 0, lun 0
Feb 22 01:10:04 localhost kernel: [4294863.970000] Attached scsi generic sg2 at scsi3, channel 0, id 0, lun 0,  type 0
Feb 22 01:10:04 localhost scsi.agent[8457]:      sd_mod: loaded sucessfully (for disk)
Feb 22 01:10:04 localhost kernel: [4294864.202000] sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294864.202000]     Additional sense: No additional sense information
Feb 22 01:10:04 localhost kernel: [4294864.205000] sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294864.205000]     Additional sense: No additional sense information
Feb 22 01:10:04 localhost kernel: [4294864.207000] sdb: Current: sense key: No Sense
Feb 22 01:10:04 localhost kernel: [4294864.207000]     Additional sense: No additional sense information

Has anyboby had luck to make this type of burner work on 5.10?

Thanks in advance.

---

### Post by suRoot on 2006-02-22
I have this burner & it works perfectly for me.

The most obvious question would be whether you've been playing around with the kernel - you haven't installed a new kernel or recompiled, have you?

Can you confirm the burner is working on another machine?

---

### Post by locald on 2006-02-22
Thanks for the information, suRoot. No, I didn't change anything. The output of "uname -a" is llike,

Linux ubuntu-dell 2.6.12-10-686 #1 Mon Feb 13 12:18:37 UTC 2006 i686 GNU/Linux

In fact, it did work for a little while. After that, the system fails to recognize the hardware.

---

### Post by ubuntuB on 2006-02-25
You are not alone, I have been unable to get my Mad Dog DVD writer working on any of my Ubuntu or Windows systems. My old pentium with Vector Linux is the only OS that it functions on, unless I remove it from the external case and mount it internally. Admittedly, I have not spent alot of time on it. I found this post while searching for a solution. Should I find a fix, I will definately post here.

---

### Post by Halfling Rogue on 2007-10-09
I've got [the same problem]("http://ubuntuforums.org/showthread.php?t=561630") with my WD external hard drive.

---

