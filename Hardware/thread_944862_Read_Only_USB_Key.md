---
title: "Read Only USB Key"
date: 2008-10-11
forum: Hardware
---

### Post by patryk77 on 2008-10-11
Hey,

I have in my possession a USB key which is given out by the Quebec employment ministry, or something along those lines.

Now, I think it's ridiculously small, and pretty useless, but would like a second opinion and get more info about it before I throw it away. (Always liked learning about technology)

What interests me about it, is that it is read-only, and it seems to mount as a CD-ROM.

Is there a way to make it writable? Does it only have 42, or maybe 64 KB of memory? Can I format it with a different filesystem? Is there a way to format a regular USB key using the iso9660 fs to create a read-only key the same way? Are there any commands I can use to get more info about it?

Thanks for any answers. Here is what I have gotten so far (omitting the parts which do not apply to it):

```
sudo lsusb -v -v -d 1130:9801

Bus 004 Device 002: ID 1130:9801 Tenx Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1130 Tenx Technology, Inc.
  idProduct          0x9801 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                2 USB Flash Disk
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval             255

```

```
mount

/dev/scd1 on /media/AUTORUN type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
```


```
df -h

/dev/scd1              42K   42K     0 100% /media/AUTORUN
```



```
cat /media/AUTORUN/autorun.inf 
[AutoRun]
open=explorer.exe "http://www.emploiquebec.net/webki"
```

(That is the only file on it)


```
sudo lshw

     *-scsi
          physical id: 1
          bus info: usb@4:2
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrom2
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/AUTORUN
             version: 1.00
             capabilities: removable audio
             configuration: ansiversion=2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /media/AUTORUN
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
```

---

### Post by cariboo on 2008-10-11
IF you haven't already installed gparted, install it,gparted is available from the repositories. Once it is installed, go to System-->Aadministration-->Partition Editor you can the repartion and reformat the device. Make sure that the device is not mounted before you try anything.

Jim

---

### Post by dr4c4n on 2010-02-20
Did you ever figure this out? I know gparted will not enable you to format this, and the only other options I have seen online were windows tools such as chip genius. However if you look to the site for finding the specific chip firmware you need for use with the chip genius software. It is not there. (at least I haven't found it with my google search powers). If you do come across a method to reflash your usb device please let me know, as i'd be interested in the outcome of this little experiment. Thanks :)

---

