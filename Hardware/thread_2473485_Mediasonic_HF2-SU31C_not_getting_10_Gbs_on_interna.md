---
title: "Mediasonic HF2-SU31C not getting 10 Gb/s on internal hub"
date: 2022-04-06
forum: Hardware
---

### Post by BatteryKing on 2022-04-06
I noticed my transfer rates to an array of four 12 TB helium filled drives in this enclosure do not reach the performance of the individual drives, but instead get an aggregate of up to 248 MB/s, or about 62 MB/s per drive.  I noticed when I ran `lsusb -t` the hub in the encloser showed up as a 5 Gb/s device.  When I ran `lsusb -v`, I saw that SuperSpeedPlus was in the list of available speeds.  I have read elsewhere that you only get about 1/2 the transfer rate of the link speed.  In this case the closest match is 5 Gb/s, not the 10 Gb/s the equipment is rated for.

I have tried some permutations on this to see if I could get better speed and I came up with:
1. Baseline - 10G rated USB-C port to 10G rated USB-C cable to drive cage - See the hub at 5 Gb/s everything else at 10 Gb/s.  Seem to have 5 Gb/s link rate.  Tried two different cables and got the same result.
2. TB3 port on computer - failed to recognize enclosure.
3. TB3 cable - failed to recognize enclosure.  Tried two different TB3 cables.  Basically all permutations where any TB3 hardware was involved led to failure to recognize enclosure.
4. 5 Gb/s cable - Hub and drive bridges show up as 5 Gb/s devices.

```

/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
    |__ Port 2: Dev 3, If 0, Class=Hub, Driver=hub/4p, 5000M
        ID 2109:8822 VIA Labs, Inc. 
        |__ Port 1: Dev 4, If 0, Class=Mass Storage, Driver=uas, 10000M
            ID 2109:0715 VIA Labs, Inc. 
        |__ Port 2: Dev 5, If 0, Class=Mass Storage, Driver=uas, 10000M
            ID 2109:0715 VIA Labs, Inc. 
        |__ Port 3: Dev 8, If 0, Class=Mass Storage, Driver=uas, 10000M
            ID 2109:0715 VIA Labs, Inc. 
        |__ Port 4: Dev 7, If 0, Class=Mass Storage, Driver=uas, 10000M
            ID 2109:0715 VIA Labs, Inc. 

```

```

Bus 006 Device 003: ID 2109:8822 VIA Labs, Inc. USB3.1 Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.20
  bDeviceClass            9 Hub
  bDeviceSubClass         0 
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x2109 VIA Labs, Inc.
  idProduct          0x8822 
  bcdDevice            5.a3
  iManufacturer           1 VIA Labs, Inc.
  iProduct                2 USB3.1 Hub
  iSerial                 3 000000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x001f
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes           19
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               8
        bMaxBurst               0
Hub Descriptor:
  bLength              12
  bDescriptorType      42
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood      175 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.4 micro seconds
  wHubDelay          2292 nano seconds
  DeviceRemovable    0x00
 Hub Port Status:
   Port 1: 0000.0203 lowspeed enable connect
   Port 2: 0000.0203 lowspeed enable connect
   Port 3: 0000.0203 lowspeed enable connect
   Port 4: 0000.0203 lowspeed enable connect
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x0049
  bNumDeviceCaps          5
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000006
      BESL Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           4 micro seconds
    bU2DevExitLat         231 micro seconds
  Container ID Device Capability:
    bLength                20
    bDescriptorType        16
    bDevCapabilityType      4
    bReserved               0
    ContainerID             {30eef35c-07d5-2549-b001-802d79434c30}
  SuperSpeedPlus USB Device Capability:
    bLength                28
    bDescriptorType        16
    bDevCapabilityType     10
    bmAttributes         0x00000023
      Sublink Speed Attribute count 3
      Sublink Speed ID count 1
    wFunctionalitySupport   0x1100
    bmSublinkSpeedAttr[0]   0x00050030
      Speed Attribute ID: 0 5Gb/s Symmetric RX SuperSpeed
    bmSublinkSpeedAttr[1]   0x000500b0
      Speed Attribute ID: 0 5Gb/s Symmetric TX SuperSpeed
    bmSublinkSpeedAttr[2]   0x000a4031
      Speed Attribute ID: 1 10Gb/s Symmetric RX SuperSpeedPlus
    bmSublinkSpeedAttr[3]   0x000a40b1
      Speed Attribute ID: 1 10Gb/s Symmetric TX SuperSpeedPlus
  ** UNRECOGNIZED:  03 10 0b
Device Status:     0x0001
  Self Powered


```

---

### Post by TheFu on 2022-04-06
Bus throughput is theoretical, never actual.  It is more like a speed limit, not a minimum speed.  Getting any spinning disks anywhere near 10Gbps is basically impossible.  Heck, I doubt they'd get closed to 3Gbps.

The slowest part of the chain is the limiting factor in drive performance.  Not having the USB bus be the bottle neck is good, but it doesn't magically make everything else faster.

I did a quick search and the best throughput is about 250MB/s per disk ... that's 2Gbps ... in professionally tuned setups with high end hardware.
Historically, USB storage devices have always had queuing issues.  The USB-storage protocol is lacking commands that SATA has.  SAS is even faster, but that's usually due to higher quality enterprise components.

Mediasonic isn't exactly known for using high-end components.  I have a Mediasonic 4 disk external array.  Over USB3, the performance is less than the eSATA connection.  If I had a better eSATA controller, I think it would be a little faster, but since it is for media storage, it just doesn't matter to me.  Just sayin'.

---

### Post by BatteryKing on 2022-04-16
I went back through with hdparm -t to try to slice it a different way, one drive at a time, 2 drives at a time, 3 drives at a time, and then 4 drives all at once.  What I came up with for raw read rates is the first up to two drives could go at full speed, which with these drives is coming up to ~210 MB/s.  After this I hit a ~440 MB/s cap.  That is 3 drives averaged ~145 MB/s and 4 drive averaged ~110 MB/s.

This is in contrast to the backup I did were I was primarily writing and was seeing more like 62 MB/s per drive on average, which is nearly half the speed.

For a bit of a contrast, when I do hdparm -t on a hardware RAID 6 array of older (and slower) eight 8 TB drives hooked to a RAID controller through a SAS expander, I see read rates of 1,050 MB/s consistently on the dot.  I did a 4.4 TB write to the file system on the drive the other day and it averaged 1.1 GB/s.  That is over twice the aggregate raw read rate of the individual 12 TB drives going through USB 3.1 Gen 2 when all read at the same time and 6x the write rate.

---

### Post by TheFu on 2022-04-16
Don't confuse the units.  MB/s and Mb/s are VERY different.
Writes are very different from reads.
USB is very different from SAS.

---

### Post by BatteryKing on 2022-04-17
I am aware of these differences and this makes the whole thing more complicated to compare.  For example I realize B is 8-bits and b is 1 bit and USB has packet overhead.  So considering overhead and other loses, I consider the ratio for USB to be ~10 bits capability for every 1 byte transmitted.  However USB has all kinds of other stuff going on so the reality is even slower.  So for example when I see 440 MB/s, I think this is way below the 10 Gb/s advertised, instead maybe I am pushing 5 Gb/s link speed to get up to this 440 MB/s to the drives.  Then when I see 246 MB/s, I think maybe it is going at 5 Gb/s, but somehow it is a little less than 50% efficient using the bandwidth.  Maybe this is wrong, so I could use correcting here.

One thought to occur to me is I never disabled atime on the backup array.  That might be slowing things down some.  There is only a small handful of places where I have seen the need for atime, so I usually disable it when I need the performance or am trying to minimize writes, such as to SSDs.

With atime disabled and now copying off of the array, I am seeing an aggregate of ~370 MB/s (reads only), so a little slower than the 440 MB/s I was seeing with the simple hdparm -t command, which is to be expected when you think of file system overhead during a copy operation.

---

### Post by BatteryKing on 2022-04-19
I am trying out a different external USB enclosure now (Sabrent).  With the new enclosure, I seem to be hitting a read wall of ~600 MB/s, which is much faster than what I saw with the Mediasonic enclosure.  This is just straight unplug old enclosure, move drives over, plug in new enclosure in the same spot, and test.  I am seeing over 500 MB/s with the drives in the 90+% utilization range, which is much better than 248 MB/s max I saw with the same drives when they were all hanging at ~100% with a almost the same RAIDZ configuration except without the dedup option.  I am actually hitting a bit of a problem where the source drives are now maxing out a lot, making it harder to confirm the full potential of what this array can now do.

Another thing I think I should point out is I kept having problems with the drive labels in /dev/disk/by-id to be wrong / corrupt, which makes it harder for ZFS to figure out which drives are in the array.  The thing is before the whole enclosure went into storage where now my safe storage spot is too small for the new enclosure, but the new enclosure is tool-less and uses springs to hold the drives in place, so I also picked up protective cases for the individual hard drives when moving them to storage.  I have noticed in the past bare hard drives do not react to well with abrupt contact with concrete when moving to and from storage, so need some extra protection when they are out of the enclosure.  The spring loading for the new enclosure is important as I have also had issues with drives popping out of the array during backups.  The ZFS resilver capability is something you like to keep handy, but don't want to actually use, especially when the problem is the enclosure is not maintaining reliable contact with the drives in it.

So yeah, it looks like this Mediasonic enclosure is either garbage or its support in Linux is messed up.  This Sabrent enclosure (DS-SC5B) is already proving to work much better.

---

### Post by TheFu on 2022-04-19
I have an addonics enclosure and an old Mediasonic one.  The addonics was cheap - discovered them before storage enclosure prices went crazy - but it performs better.  I use it for RAID1 with mdadm.  The Mediasonic is for media, so no RAID at all.

I understand the ZFS dedup is highly dependent on RAM. Thought the recommended ratio was 1GB RAM for every TB of storage.  From my quick reading, most people find that dedup isn't worth it most of the time, unless you happen to be backing up the same stuff over and over. If I put on my Linux Backup hat, then I'd say if you are backing up the OS, then you're doing Linux backups wrong.  But that's a different thread.

---

### Post by BatteryKing on 2022-04-26
I can clarify a bit.  I have a project where dedup is used heavily for backups.  I don't have direct control of the box, but I do see major performance problems.  I was dorking around with dedup here to better understand how exactly it kills performance.  Normally I don't use dedup.  The box I was testing it out on has 128 GBs of RAM, so should be enough for dedup as long as I don't fire up all of the stuff that caused me to put this much RAM in the system in the first place.  This is getting out of my main goal of making sure the enclosure is working as intended, so maybe I should have held off that testing until I had a better shake down of this new hardware.

---

