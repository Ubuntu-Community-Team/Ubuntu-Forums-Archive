---
title: "usb memory stick found but not mounted"
date: 2009-07-08
forum: Hardware
---

### Post by collinsrj on 2009-07-08
I've been using a memory stick on my eee pc 901 running ubuntu. The memory stick appears to be recognised; I get a folder for it in the "Places" menu but when I click it no window appears. A little further checking shows that the device isn't listed when I run "fdisk -l"
I've looked through log files but can't find anything wrong.

See the output of the commands below:

Output of "dmesg" after I plug the device in:

```

[87078.392094] usb 5-4: new high speed USB device using ehci_hcd and address 7
[87078.575652] usb 5-4: configuration #1 chosen from 1 choice
[87078.577655] scsi5 : SCSI emulation for USB Mass Storage devices
[87078.582160] usb-storage: device found at 7
[87078.582185] usb-storage: waiting for device to settle before scanning
[87083.580565] usb-storage: device scan complete
[87083.581949] scsi 5:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[87083.590183] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[87083.593800] sd 5:0:0:0: Attached scsi generic sg3 type 0

```

Output of "lsusb -v" for the device. I checked to see which device by unplugging it and plugging it back in.

```
Bus 005 Device 008: ID 058f:1234 Alcor Micro Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x1234 
  bcdDevice            0.01
  iManufacturer           1 Alcor Micro
  iProduct                2 Mass Storage Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

I ran lsusb to make sure I'd the usb storage module and found the following line in the output:

```

usbcore               141552  7 usb_storage,libusual,uvcvideo,btusb,ehci_hcd,uhci_hcd
```

Any ideas of where else to look or other things to try would be appreciated. 
Thanks

---

### Post by shatterblast on 2009-07-09
I think the issue could occur from either a permissions issue or the format of the USB memory stick.  I would initially suggest FSCK from Terminal for the USB stick, but may become more prudent to check for the partition under GParted.  GParted can be obtained from Synaptic.  It is found under:

System -> Administration -> Synaptic

After that, GParted should show as the Partition Editor under Administration.  Once in the window, it should properly detect the presence of your USB device.  You should have the ability to right click its entry and choose "Check".

Please be careful with these suggestions.  The Partition Editor can potentially destroy all data you have on your USB memory stick.  It is good to safely back-up your data.

---

### Post by collinsrj on 2009-07-09
Thanks for the suggestion. I opened GParted but the USB device isn't listed. In the GParted menu I clicked refresh device to make sure but no joy. I tried unplugging the device and plugging it back in with Gparted open, nothing though.

I tried running "lshw" to see if I could find it but its not listed there. I can see an SD card I've attached listed in both GParted and the lshw, so I'm starting to expect there may be something wrong with the memory stick.

I've used the memory stick on the laptop before without any problems. I tried the memory stick on a Windows box and again the device is found, but again the file system isn't mounted. 

The last time I used it was on the laptop and as far as I can remember I ejected it before physically removing it.

You mentioned FSCK, I've never used this before. I'm not sure what I should point it at if the memory stick isn't listed anywhere. From the man page I gather it looks at the entries in /etc/fstab.

I looked in /etc/fstab but didn't see the device listed there. I didn't see my SD card listed in there either so not quite sure if I'm looking in the right place.

Any ideas?

Thanks.

---

### Post by shatterblast on 2009-07-09
FSCK will only help you if the system will access the USB stick's partition.  I think the Partition Editor's "Check" function uses the same utility anyhow.  I think I've read about a Linux utility that tries to salvage USB memory sticks, but apparently, its rate of success was very low.  I abandoned the idea myself.  I think at least two companies exist out of the many that make USB memory sticks that try to recover data.  However, those same utilities would probably require access to the partition as well.

I recommend checking for a manufacturer's warranty.  I think they can range anywhere between 3 months to 2 years.  I think I saw one even claim a 10 year warranty length.

---

### Post by collinsrj on 2009-07-11
Yep, I'm guessing its just dead. Wasn't an expensive one, so think I'll just bin it.
Its a pity I couldn't find an error message saying why it never mounted
Thanks for your help.

---

### Post by shatterblast on 2009-07-11
I'm guessing a capacitor blew out or something.  I kept one of the much older iPod Shuffles for a long time.  I even used it for technical work on transferring customer files and such.  I had it for somewhat over three years, but it had about a year of continual usage to it.  One day, it just stopped reading the memory itself.  The firmware operated fine and so did the battery.  (Those parts are very inexpensive anyway yet difficult to replace.  It's quite possible to build your own music player, but it can be difficult and time-consuming depending on your part of the world.  In fact, some music players sell for just $5 or less and do better than an iPod worth x10 more.  The funny part is that the same parts can sometimes go into both except for the memory.)

My idea?  I'm going to force my way into it!  All kinds of loud pops went on as I adjusted voltage and tried to load Linux onto it.  I stopped went it started smoking while plugged into my computer.  I just kind of continued to see what would happen.  If it's dead, might as well check what the guts are like.  I don't do that to people of course.

---

