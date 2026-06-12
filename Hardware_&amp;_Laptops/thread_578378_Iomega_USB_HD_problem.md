---
title: "Iomega USB HD problem"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by Bastaard on 2007-10-17
Today I tried to connect my friends Iomega Hi-speed USB 2.0 200GB external harddisk to Ubuntu to backup my windows partitions (I'm going to make a full switch to Ubuntu) and I was happy to see that it worked plug-and-play.

So I started copying the contents of my HD to the external HD, but after some minutes all of a sudden the drive disconnected and reconnected immediately, at least that's what I think happened. The copying gave me an error (retry didn't work), I got a "please safely remove your hardware" balloon, a new window with the external HD's contents opened up (as if I had just connected the HD) and I had to reinitiate the copying, which after some minutes gave me the exact same error, same symptoms.

I rebooted to Windows and did the copying from there, which worked just fine. The only thing is that Ubuntu created some corrupted files and directories which I am unable to delete, but I guess I'll just have to format the disk for that.

So my question is: what went wrong and how can I solve this problem so I can use the external HD under Ubuntu?

---

### Post by Bastaard on 2007-10-18
Anyone?

---

### Post by mciancio on 2007-11-03
Maybe you have my same problem: I've got an Iomega 360Gb and when I tried to reformat it to ext3 I got the following errors on /var/log/messages

```
Nov  3 00:16:46 localhost kernel: [ 3077.031725] usb 3-6: reset high speed USB device using ehci_hcd and address 22
Nov  3 00:16:51 localhost kernel: [ 3082.272112] usb 3-6: reset high speed USB device using ehci_hcd and address 22
Nov  3 00:16:52 localhost kernel: [ 3082.815742] usb 3-6: reset high speed USB device using ehci_hcd and address 22
Nov  3 00:16:52 localhost kernel: [ 3083.359365] usb 3-6: reset high speed USB device using ehci_hcd and address 22
Nov  3 00:16:53 localhost kernel: [ 3083.879110] usb 3-6: reset high speed USB device using ehci_hcd and address 22
Nov  3 00:16:54 localhost kernel: [ 3084.286763] sd 9:0:0:0: scsi: Device offlined - not ready after error recovery
Nov  3 00:16:54 localhost kernel: [ 3084.286820] sd 9:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Nov  3 00:16:54 localhost kernel: [ 3084.286828] end_request: I/O error, dev sdc, sector 798295
Nov  3 00:16:54 localhost kernel: [ 3084.286845] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286858] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286868] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286879] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286895] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286905] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286915] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286925] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286936] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.286947] lost page write due to I/O error on sdc1
Nov  3 00:16:54 localhost kernel: [ 3084.306041] sd 9:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov  3 00:16:54 localhost kernel: [ 3084.306051] end_request: I/O error, dev sdc, sector 798423
Nov  3 00:16:54 localhost kernel: [ 3084.306302] usb 3-6: USB disconnect, address 22
```

The disk hangs and slows the entire system. Sometimes it disconnects. I've to power off it to return to a normal status.

I don't know what is the problem and what the solution :(

---

### Post by pedrows on 2007-11-03
I have a Iomega 250GB and I'm trying to migrate from windows to Ubuntu. I can mount the drive when I'm using a " Live CD" version from my pendrive and access everything in my Iomega. But when I try to access from the already installed Ubuntu in my new hard drive, I just can't mount it!! 

Anyone could hepl me?

Best Regards.

---

### Post by mciancio on 2007-11-05
> **mciancio said:**
> The disk hangs and slows the entire system. Sometimes it disconnects. I've to power off it to return to a normal status.

I don't know what is the problem and what the solution :(

Now I know what the problem was: the external Iomega USB HD was defective :( I substituted it and the problem disappeared.

Bye

---

### Post by mciancio on 2007-11-05
> **pedrows said:**
> I have a Iomega 250GB and I'm trying to migrate from windows to Ubuntu. I can mount the drive when I'm using a " Live CD" version from my pendrive and access everything in my Iomega. But when I try to access from the already installed Ubuntu in my new hard drive, I just can't mount it!! 


Have you tried to mount it explicitily using 'mount'?
The OS on the usb and the installed one are the same?
Error messages?

---

