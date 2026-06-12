---
title: "Copy of big files to USB-Harddisk becomes slower and slower"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by dschneider on 2008-03-27
Hi Cracks,

I have a big problem with external USB HD. When I try to copy big files e.g. VMware containers, the progress bar becomes slower and slower and the estimated resttime becomes more and more. For example nautilus says on start of copying a 1 GB file, that it will run for 4 mins. After 20 mins, it says that it will need further 13 mins, and it will become more and more. The copy process comes actually to an end, but it consumes very long time! A copy process with 20GB had done 5GB after 8 hours!
I tested other external harddisks and other USB-Ports on the workstation, but no difference. The Harddisks are formatted with NTFS. I need this, because it has to run on another computer with windows xp.
When plugging the HD via USB, it is detected in a right way, and all seems to be well:

Mar 25 08:43:16 dschneidern kernel: [84135.116374] usb 8-4: new high speed USB device using ehci_hcd and address 4
Mar 25 08:43:16 dschneidern kernel: [84135.249685] usb 8-4: configuration #1 chosen from 1 choice
Mar 25 08:43:16 dschneidern kernel: [84135.250046] scsi11 : SCSI emulation for USB Mass Storage devices
Mar 25 08:43:21 dschneidern kernel: [84140.255443] scsi 11:0:0:0: Direct-Access SAMSUNG MP0804H 0811 PQ: 0 ANSI: 0
Mar 25 08:43:21 dschneidern kernel: [84140.257305] sd 11:0:0:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
Mar 25 08:43:21 dschneidern kernel: [84140.258546] sd 11:0:0:0: [sdb] Test WP failed, assume Write Enabled
Mar 25 08:43:21 dschneidern kernel: [84140.259426] sd 11:0:0:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
Mar 25 08:43:21 dschneidern kernel: [84140.260673] sd 11:0:0:0: [sdb] Test WP failed, assume Write Enabled
Mar 25 08:43:21 dschneidern kernel: [84140.260679] sdb: sdb1
Mar 25 08:43:21 dschneidern kernel: [84140.757786] sd 11:0:0:0: [sdb] Attached SCSI disk
Mar 25 08:43:21 dschneidern kernel: [84140.757825] sd 11:0:0:0: Attached scsi generic sg3 type 0

I'm on ubuntu 7.10 with kernel 2.6.22-14 on X86_64.
In /var/log/messages, there are no hints while copying.
In top, I can see a process mount.nfs-3g, which consumes 98% of CPU-performance
Has anyone an idea of the reason for this?

Many thanks for all suggestions
Best regards
Daniel

---

### Post by dschneider on 2008-03-28
Is there no one, who can help me???
I need some hints - please.

Regards
Daniel

---

### Post by jeff.sadowski on 2008-04-06
Did you ever get this figured out?
Did you ask on VMware forums?

I seem to be having maybe the same issue?

I am trying to copy a file from one virtual disk to another inside a virtual machine and it seems to go really slowly..

I am using dd and I recently learned how to get dd to display information

example: dd if=/dev/sda1 of=/dev/hda1
in another window I type
watch -n 30 kill -USR1 `ps h -C dd|awk '{print $1}'|tail -n 1`
the watch command tells kill to send the last run dd command the USR1 signal every 30 seconds

anyways I am only getting 1.5 MB/s when copying.
 where as from file to file on the real disk outside of vmware I get around 26 MB/s

My VMware's disks seems really slow.
Could this be because Ubuntu is running vmware not as the root user?

---

