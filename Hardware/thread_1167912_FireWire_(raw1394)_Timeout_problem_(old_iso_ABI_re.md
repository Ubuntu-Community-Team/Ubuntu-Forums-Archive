---
title: "FireWire (raw1394) Timeout problem (old iso ABI removed)"
date: 2009-05-23
forum: Hardware
---

### Post by zulmo on 2009-05-23
Hello,

I am running Ubuntu 9.04 on MacBookPro 4.1.
I have a device (a haptic device called Phantom Omni) that is to be connected via FireWire (IEEE1394).

I installed the device driver, then installed basic s/w library for the Omni, configured the device (the system can read in the serial number of the device), and then tested the device using the test program that comes with the device library.

I've already set the permission using
> chmod o+rw /dev/raw139

The test program instantly shuts down right after showing a GUI.

Below is the status:

$ /sbin/lsmod | grep raw1394
raw1394                32732  0 
ieee1394               94660  2 raw1394,ohci1394

$ /usr/sbin/PHANToMTest 
Timeout reading from 1394 bus, exiting...
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 1794 requests (1788 known processed) with 0 events remaining.

$ dmesg | grep 1394
[    2.734704] ohci1394 0000:0d:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.785501] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[97104000-971047ff]  Max Packet=[4096]  IR/IT contexts=[4/8]
[    4.107502] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000b99008192d808]
[    4.107877] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[001ff3fffe66a868]
[ 2841.730334] ieee1394: raw1394: /dev/raw1394 device initialized
[ 2943.290410] raw1394: old iso ABI has been removed
[ 2943.290692] raw1394: old iso ABI has been removed
[ 2943.301266] raw1394: old iso ABI has been removed
[ 2943.311550] raw1394: old iso ABI has been removed
[ 2943.321795] raw1394: old iso ABI has been removed
[...... same message keeps going on further down...]

So I googled for a while, and I think I've found the reason: 
   old legacy isochronous ABI of raw1394 (1st generation iso ABI) that uses 
   two request types RAW1394_REQ_ISO_SEND, RAW1394_REQ_ISO_LISTEN 
   have been deprecated.

My device basically updates its hardware status using callback functions, so I think the device driver is built based on old raw1394 library, and hence does not work with current versions. 

So, what should I do? Is there any way to downgrade to old (really old, maybe kernel 2.4 level) 1394 drivers? How should I do it? 

I'd appreciate any help...

---

### Post by Gallaz on 2009-06-06
I've exactly the same problem ! Do you find a solution ?

---

### Post by Radarsat-1 on 2009-07-02
Hi,

I have the same problem as well.  However, since their driver is proprietary, I think there's not much we can do but petition them to fix the issue and release a new version.  It would be great if they could keep their software up-to-date with Linux, but I guess they won't do it without getting many requests.

---

### Post by shankar_mg on 2009-07-13
Hi,
  I got the same error message too. I have emailed Sensable corp. citing this problem. Did you get any replies from Sensable about this issue ?

Thanks,
Shankar

---

### Post by forsslund on 2009-11-09
Hi,
Well, you can downgrade to kernel 2.6.22-14 found in 7.10:

```

sudo sh -c "echo deb http://old-releases.ubuntu.com/ubuntu/ gutsy main >>  /etc/apt/sources.list"
sudo apt-get update
sudo apt-get install linux-image-2.6.22-14-generic linux-headers-2.6.22-14-generic 
```

but we really should help sensable with coding a free driver

---

