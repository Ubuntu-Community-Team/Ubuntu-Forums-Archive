---
title: "USB printer not recognised"
date: 2010-03-12
forum: Hardware
---

### Post by Nycticorax on 2010-03-12
When I plug in my USB printer, most of the time it is not correctly recognised. A continuous stream of messages are written to /var/log/messages as follows:

```
Mar 12 18:57:08 Trogon kernel: [ 214.552164] usb 1-4: new high speed USB device using ehci_hcd and address XXX
```

where XXX is an integer that changes with each sucessive message (sample of full output below)

The printer is a HP Photosmart D7360. This is with fully up-to-date Ubuntu 9.10. However, the same printer works fine with a different laptop also running up-to-date 9.10. Also, this laptop occasionally (albeit rarely) does recognise the printer. So it seems that the correct drivers are indeed present.

How can I debug this? What might be causing my machine to (most of the time) fail to recognise this USB device?

Thanks,

Dan

```
Mar 12 18:57:08 Trogon kernel: [ 214.552164] usb 1-4: new high speed USB device using ehci_hcd and address 120
Mar 12 18:57:12 Trogon kernel: [ 218.268091] usb 1-4: new high speed USB device using ehci_hcd and address 13
Mar 12 18:57:13 Trogon kernel: [ 219.144096] usb 1-4: new high speed USB device using ehci_hcd and address 17
Mar 12 18:57:19 Trogon kernel: [ 225.336278] usb 1-4: new high speed USB device using ehci_hcd and address 49
Mar 12 18:57:30 Trogon kernel: [ 235.992277] usb 1-4: new high speed USB device using ehci_hcd and address 105
Mar 12 18:57:31 Trogon kernel: [ 237.244262] usb 1-4: new high speed USB device using ehci_hcd and address 111
Mar 12 18:57:32 Trogon kernel: [ 238.120253] usb 1-4: new high speed USB device using ehci_hcd and address 115
Mar 12 18:57:35 Trogon kernel: [ 241.444272] usb 1-4: new high speed USB device using ehci_hcd and address 6
Mar 12 18:57:35 Trogon kernel: [ 241.756268] usb 1-4: new high speed USB device using ehci_hcd and address 7
Mar 12 18:57:36 Trogon kernel: [ 242.068269] usb 1-4: new high speed USB device using ehci_hcd and address 8

```

---

### Post by Nycticorax on 2010-04-05
OK, 98 views and no replies. We are still in need of help here. As was the case before, the USB printer is not being recognised when it is plugged in. It seems that USB ports in general on the laptop are not working. The dmesg output below looks very unhealthy to me. Can anyone suggest a possible software solution for this?

Here's the output of lsusb:

```
> lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And lspci:

```
> lspci | grep -i usb
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

```

And here is some output of dmesg:

```

> dmesg | grep -i usb

[ 8217.604618] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8217.792584] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8217.980557] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8218.168524] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8218.356635] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8218.544588] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8218.788274] usb 1-4: new high speed USB device using ehci_hcd and address 18
[ 8218.856510] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8219.044627] hub 1-0:1.0: unable to enumerate USB device on port 4

< another 10 lines here, same except for initial number>

[ 8221.172253] usb 1-4: new high speed USB device using ehci_hcd and address 30
[ 8221.240350] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8221.484482] usb 1-4: new high speed USB device using ehci_hcd and address 31
[ 8221.552303] hub 1-0:1.0: unable to enumerate USB device on port 4

<more similar lines>

[ 8224.748298] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8224.992264] usb 1-4: new high speed USB device using ehci_hcd and address 49

<more similar lines>

[ 8225.060339] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 8234.156286] usb 1-4: new high speed USB device using ehci_hcd and address 97
[ 8234.233193] hub 1-0:1.0: unable to enumerate USB device on port 4

<continues in similar fashion>
```

---

### Post by ellgor on 2010-04-06
Hi,

You could see if you have an app called "usbmount" installed, it might help, also there are some Hp apps in synaptic that also might help.

Regards, Ellgor.

---

### Post by Neva on 2010-10-08
In my case, I could not see the printer listed on lsusb

Error -71 was typical.

Tried various fixes, they didn't help:
Step 7 here - [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)
```
sudo usermod -a -G lp $USER
```Hotfix here - [http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1)
```
echo -1 > /sys/module/usbcore/parameters/autosuspend
```Then tried the fix in this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9790032](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9790032)

Which is to shut down the computer completely, turn off the power supply for 30mins.

That worked and lsusb shows the printer again.

---

