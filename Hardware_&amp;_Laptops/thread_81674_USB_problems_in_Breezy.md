---
title: "USB problems in Breezy"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by fitz0134 on 2005-10-24
I have a lacie bigger disk (F800) that I want to use from my AMD64 (2.6.12-9-amd64-k8-smp) breezy box.  

When I connect via USB2 I get the folowing error in DMESG:

[525851.708936] usb 2-6: reset high speed USB device using ehci_hcd and address 8
[525854.767136] usb 2-6: device descriptor read/64, error -110
[525869.911320] usb 2-6: device descriptor read/64, error -110
[525870.075104] usb 2-6: reset high speed USB device using ehci_hcd and address 8
[525875.079923] usb 2-6: device descriptor read/8, error -110
[525880.184624] usb 2-6: device descriptor read/8, error -110

I have also tried an x86 live cd of Breezy (ubuntu 2.6.12-9-386) with the same errors.  

At first I thought I had a broken disk but it works fine under windows xp and knoppix 3.9 (Knoppix 2.6.11 #2 SMP). It seems unusal to me that it works with a 2.6.11 kernel and not 2.6.12???

Any help would be greatly appreciated as this will be a very expensive paper weight if I cannot get it to work..

Cheers
Sean

---

### Post by serzz on 2005-10-25
Had exact the same problem, temporary solution is following:

$ sudo modprobe -r ehci_hcd

---

### Post by fitz0134 on 2005-10-25
I have tried:

sudo modprobe -r ehci_hcd

All that happens is that I get the error for ohci_hcd:

[  290.478000] usb 1-3: reset full speed USB device using ohci_hcd and address 6[  293.547937] usb 1-3: device descriptor read/64, error -110
[  308.701889] usb 1-3: device descriptor read/64, error -110

If I remove ohci_hcd instead (sudo modprobe -r ohci_hcd) I get the error from ehci_hcd:

[  470.721562] usb 1-3: reset high speed USB device using ehci_hcd and address 2[  473.779516] usb 1-3: device descriptor read/64, error -110
[  488.922484] usb 1-3: device descriptor read/64, error -110

An of course if I remove both, nothing works.

Please any other suggestions??

---

### Post by devaude on 2005-11-04
I've exactly the same problem:

[4300504.858000] usb 3-3.1: reset high speed USB device using ehci_hcd and address 5
[4300520.904000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
[4300520.904000] SCSI error : <1 0 0 0> return code = 0x50000
[4300520.904000] end_request: I/O error, dev sdb, sector 367643295

It happens instantly during a copy action, for example.

Anyone who can imagine what the problem could be?? :confused:

---

### Post by bubblegum on 2005-11-07
verify the IO scheduler used  (replace hda by your drive):

cat /sys/block/hda/queue/scheduler

if it's not set to "cfq" try it:

sudo echo "cfq" > /sys/block/hda/queue/scheduler

you can eventually try the other schedulers.

---

