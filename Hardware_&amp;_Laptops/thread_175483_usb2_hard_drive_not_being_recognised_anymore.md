---
title: "usb2 hard drive not being recognised anymore"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by tam9 on 2006-05-13
Hi all,

First of all for informational purposes I am running Dapper.

I have a 500gb external usb2 hdd which I have been using for the past couple of days. Anyway, I rebooted my machine and when I try to mount the hdd it just says:
'tam@spud:~$ sudo mount -t ext3 /dev/sda1 /mnt/big
mount: special device /dev/sda1 does not exist'

Well at that point I thought I should check to see if the modules are present and here is the output from that also:

tam@spud:~$ lsmod |grep usb
usb_storage            74176  0
scsi_mod              139496  4 sd_mod,usb_storage,sr_mod,sbp2
usbcore               129668  4 usb_storage,ehci_hcd,ohci_hcd

dmesg reports this whenever I put in the usb2 cable:
[4294852.023000] usb 4-4: USB disconnect, address 2
[4295590.979000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[4295953.814000] Initializing USB Mass Storage driver...
[4295953.814000] usbcore: registered new driver usb-storage
[4295953.814000] USB Mass Storage support registered.
[4296229.694000] Driver 'sd' needs updating - please use bus_type methods
[4296247.023000] usb 4-4: USB disconnect, address 3
[4296249.229000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[4296249.733000] usb 4-4: device not accepting address 4, error -71
[4296249.835000] usb 4-4: new high speed USB device using ehci_hcd and address 5


Now at the moment I really don't know what else I can do to get the hdd working and was hoping that some member of the list knows where I am going wrong or can give some handy tips so that I can resolve my problem.

Many thanks in advance.

Tam.

---

### Post by tam9 on 2006-05-15
anyone?

---

### Post by rakhesh on 2006-05-15
Just curious. Did u dist-update ur system recently? 

I had a 300GB external HDD that used to work well in Dapper till abt a month ago. Then it got spoilt, and last week I went ahead and brought a new 100GB external HDD. The new HDD does not work in Ubuntu for some reason. It works in Fedora Core 5 and Windows XP, so I know the drive as such is working fine. 

The only changes I can recollect having done to my system is maybe do a dist-upgrade. So am wondering if u too did something similar and now its not working. 

I have a thread for my question [here]("http://ubuntuforums.org/showthread.php?t=175966&highlight=external+HDD"). No one's answered it yet.

---

