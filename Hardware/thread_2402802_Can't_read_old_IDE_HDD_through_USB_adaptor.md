---
title: "Can't read old IDE HDD through USB adaptor"
date: 2018-10-04
forum: Hardware
---

### Post by flix3 on 2018-10-04
Hi.

I'm using Ubuntu 18.04.1 64bit.

Basically I must read an old IDE HDD to recover some files.
To do so, I'm currently using an "USB 3.0 TO IDE/SATA" adaptor based on the chip: **1f75:0611 Innostor Technology Corporation** (S611).

After all the connections, the HDD seems to spin correctly, but I cannot see its drive on the Desktop.
Opening the application named "**Disks**" I can see this:

[ATTACH=CONFIG]281257[/ATTACH]

Basically the disk is detected as "Generic ATA/ATAPI Device" with no media and no size.

The problem is that I can't access it. I can't even format it.

Can somebody help me ?

Further data:

Output of **lsusbs -vvv**:
```
Bus 004 Device 002: ID 1f75:0611 Innostor Technology Corporation 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x1f75 Innostor Technology Corporation
  idProduct          0x0611 
  bcdDevice            0.06
  iManufacturer           4 
  iProduct                5 
  iSerial                 6 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           44
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
```

Output of **sudo hdparm -I /dev/sdb**:
```
/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
```

Of course programs like **gparted** don't detect the drive.

Any help please?

---

### Post by Autodave on 2018-10-04
You say it is spinning, but do you hear any clicking from inside when it first starts?  The arm could be sticking.  You may want to try rebooting the machine with the HD connected.

---

### Post by flix3 on 2018-10-05
> **Autodave said:**
> You say it is spinning, but do you hear any clicking from inside when it first starts?  The arm could be sticking.  You may want to try rebooting the machine with the HD connected.

Thanks for the tip, but after a reboot everything stays the same.

And when it first starts (when I turn its switch on for the first time) I can hear a beep and a spinning noise that is similar to every other HDD.
I've tried even connecting the USB when it's already on with the same result.

But I'm not sure this is enough to exclude the arm-sticking problem or not... 
I'm not sure what you mean when you say "any clicking"... I just hear the beep and the spinning noise and nothing else.


What looks strange to me is that, even if the Master Boot Record can be broken, I can't even format it... 
so I guess the problem is not in the content of the disk.

[**Edit:**] I'm afraid that maybe Ubuntu does not detect it as an HDD, but as a generic drive without any media inside...

---

### Post by flix3 on 2018-10-05
Hey! Now for the first time it works! And @Autodave was right (I heard two or three "click" noises).

Don't know what changed (and I hope it's persistent...)...

Any way, now I've got something like:

[ATTACH=CONFIG]281258[/ATTACH]

I can format the drive now. 

But I must recover some video files that are supposed to be inside (it was a HDD inside a TV-Blue-Ray Philips device as far as I was told). How can I do it ?

---

### Post by QIII on 2018-10-05
Hello, flix3!

Please do not include large images in your posts.  There are those who have slow connections or data limits, making large images problematic.

Instead, use the forum attachment functionality provided by the "paper clip" button above the text entry box.  That will create a thumbnail that others can expand if they choose.

Thanks!

---

### Post by Autodave on 2018-10-05
Don't format it until you get the files off of it.  It certainly sounds like the arm was sticking inside of the drive: I have seen that before on older drives and especially after they have sat for quite awhile. Can you click on the icon on your screen and open the drive to view its contents?

---

### Post by flix3 on 2018-10-05
> **Autodave said:**
> Don't format it until you get the files off of it.  It certainly sounds like the arm was sticking inside of the drive: I have seen that before on older drives and especially after they have sat for quite awhile. Can you click on the icon on your screen and open the drive to view its contents?

Nope (there is no icon on the screen). Now I'm trying using a recover program called **photorec**.

---

### Post by Autodave on 2018-10-05
No icon is not good.  You may have more problems with that drive assuming you can get it formatted at all.

---

### Post by flix3 on 2018-10-06
> **Autodave said:**
> No icon is not good.  You may have more problems with that drive assuming you can get it formatted at all.

Nope: I have solved all problems now!

Basically **photorec** was able to recover 14 big .mpg files from the raw "unformatted" drive.

After the recovery, I've reformatted it (using NTFS, because I've discovered that FAT32 does not support files bigger that 4 GB, and Windows users needed to access it) and recopied the recovered files back.

Now that the HDD is formatted, the icon appears on the Desktop correctly.

Thanks, @Autodave for your help (it was very useful indeed)!

---

