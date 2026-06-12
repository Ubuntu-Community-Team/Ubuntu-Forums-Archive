---
title: "Rosewill R2S-B USB enclosure"
date: 2010-12-07
forum: Hardware
---

### Post by PistolChad on 2010-12-07
I admit I am a Ubuntu noob.  I recently installed 10.10 desktop and absolutely LOVE it.  I have a lot of command line Solaris experience in a work environment, but have never dealt with new hardware.

I have a Rosewill R2S-B USB enclosure.  Ubuntu does not recognize it.  Looking at their website [http://rosewill.com/products/1336/productDetail.htm](http://rosewill.com/products/1336/productDetail.htm) it doesn't even claim Linux support.

I have googled around about how to mount a USB drive, but it doesn't appear Ubuntu even knows the USB drive is attached to be able to mount it.

Does anyone have any guidance?

---

### Post by coffeecat on 2010-12-07
It's unusual for USB drives not to be automounted when you plug them in, but it happens occasionally. Could be an enclosure firmware issue. Let's see if it's being seen at all. Plug it in, switch it on and then from a terminal:

```
dmesg | tail
```and...

```
sudo fdisk -lu
```Also, let's see if we can get the product ID. Useful for googling.

```
lsusb
```Post those outputs in [noparse]```

```[/noparse] tags and we can take it from there. You can use the # icon in the message toolbar to wrap the output in code tags.

---

### Post by Fafler on 2010-12-07
Ubuntu should normally take care of all of it.

Are you sure there's a filesystem on it? If not, please consider which type you want, ext4 for most features and better performance or NTFS for Windows compatibility.

Try opening a terminal and type
```
tail -f /var/log/messages
```
Now connect or reconnect the enclosure and post the output here.

---

### Post by PistolChad on 2011-01-02
> **coffeecat said:**
> 
```
dmesg | tail
```


```
[226509.665026] wlan0: no IPv6 routers present
[231564.218447] dell-wmi: Received unknown WMI event (0x11)
[231587.790496] dell-wmi: Received unknown WMI event (0x11)
[235793.217788] dell-wmi: Received unknown WMI event (0x11)
[237279.262730] dell-wmi: Received unknown WMI event (0x11)
[238907.215103] dell-wmi: Received unknown WMI event (0x11)
[238907.481246] dell-wmi: Received unknown WMI event (0x11)
[239818.210368] dell-wmi: Received unknown WMI event (0x11)
[239819.992536] dell-wmi: Received unknown WMI event (0x11)
[248706.704730] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
```

> **coffeecat said:**
> 
```
sudo fdisk -lu
```


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0076

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   468520959   234259456   83  Linux
/dev/sda2       468523006   488396799     9936897    5  Extended
/dev/sda5       468523008   488396799     9936896   82  Linux swap / Solaris

```


> **coffeecat said:**
> 
```
lsusb
```

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

> **Fafler said:**
> Are you sure there's a filesystem on it? 


Yes, XFS is on it.  The drive came from a different external USB 2.0 enclosure that I had hooked up to a buffalo linkstation.  The old enclosure died.  I bought this new one, popped the drive in it and the linkstation did not detect it.  It is certainly possible the drive itself has failed.  I will grab a different drive and put it in it and see if it is detected.

> **Fafler said:**
> 
```
tail -f /var/log/messages
```


I got NO new lines in the log after reconnecting the device.

It is like Ubuntu doesn't even know there is a USB drive attached at all.

---

### Post by PistolChad on 2011-01-02
Sorry to waste everyone's time.

I figured out the problem.  There is a dip switch for either "BIG" or "JBOD".  I had thought from RTFM that "JBOD" was to ONLY be used if you had 2 disks in it and to use "BIG" if you want to mount and treat each of the 2 disks individually or if you only had a single disk.

Well "BIG" mode didn't work with a NTFS drive and the enclosure plugged into Windows, so I tried "JBOD" just for the heck of it and it was detected.  I put back in the XFS drive and it worked in Ubuntu and also in the linkstation.

Problem solved...sorta.

---

