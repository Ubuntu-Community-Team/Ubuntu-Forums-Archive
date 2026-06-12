---
title: "My Book External Drive will not mount"
date: 2008-05-25
forum: Hardware
---

### Post by Woodsyx on 2008-05-25
I have a 2TB My Book Premium Edition II external drive.(NTFS Formatted) I am connecting it via USB and the drive shows up when I go to Places > Computer.

When I double click on it I get an error message. 
"Unable to mount location
can't mount file"

Is there any way to fix this. I have tried ejecting it in a windows system first, the NTFS configuration tool, and plugging it in after I boot up.

Also if Ubuntu can't see it is it possible for me to open it in a Windows VM?


Thanks.

---

### Post by Prospero2006 on 2008-05-25
To the command line!

After you plug in the drive, type:
(You may need to prefix some of this with sudo.)
```

dmesg

```
You should see it listed there as /dev/sdX1 
(The X will be a letter between A-Z)

If you type dmesg within a minute of plugging in the drive, it will be at the end of the output.

ok, now create a mount point
```

mkdir /mnt/2gig

```

Mount the drive to the directory
```

mount /dev/sdX1 /mnt/2gig

```

If that doesn't work, please post the output.

---

### Post by Woodsyx on 2008-05-25
Ok here is the output I got.


[75223.853237] usb 5-2.2: USB disconnect, address 11
[75243.484457] usb 5-2.2: new high speed USB device using ehci_hcd and address 13
[75243.599304] usb 5-2.2: configuration #1 chosen from 1 choice
[75243.606082] scsi10 : SCSI emulation for USB Mass Storage devices
[75243.606630] usb-storage: device found at 13
[75243.606635] usb-storage: waiting for device to settle before scanning
[75243.616583] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2.2/5-2.2:1.1/input/input20
[75243.640073] input,hidraw4: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-2.2
[75248.594530] usb-storage: device scan complete
[75248.595654] scsi 10:0:0:0: Enclosure         WD       My Book Device   104a PQ: 0 ANSI: 4
[75248.599364] scsi 10:0:0:1: Direct-Access     WD       My Book          104a PQ: 0 ANSI: 4
[75248.600499] scsi 10:0:0:0: Attached scsi generic sg4 type 13
[75248.604353] sd 10:0:0:1: [sdd] 3907026944 512-byte hardware sectors (2000398 MB)
[75248.605471] sd 10:0:0:1: [sdd] Write Protect is off
[75248.605478] sd 10:0:0:1: [sdd] Mode Sense: 10 00 00 00
[75248.605482] sd 10:0:0:1: [sdd] Assuming drive cache: write through
[75248.607343] sd 10:0:0:1: [sdd] 3907026944 512-byte hardware sectors (2000398 MB)
[75248.608337] sd 10:0:0:1: [sdd] Write Protect is off
[75248.608343] sd 10:0:0:1: [sdd] Mode Sense: 10 00 00 00
[75248.608347] sd 10:0:0:1: [sdd] Assuming drive cache: write through
[75248.608353]  sdd: sdd1
[75248.616572] sd 10:0:0:1: [sdd] Attached SCSI disk
[75248.616643] sd 10:0:0:1: Attached scsi generic sg5 type 0

---

### Post by Prospero2006 on 2008-05-25
mkdir /mnt/newdrive
mount /dev/sdd1 /mnt/newdrive

?

---

### Post by Woodsyx on 2008-05-26
> **Prospero2006 said:**
> mkdir /mnt/newdrive
mount /dev/sdd1 /mnt/newdrive

?

Sorry I didn't know what was supposed to go where the X was.

I got this as an error message.


Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdd1 /mnt/newdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdd1 /mnt/newdrive ntfs-3g force 0 0



I tried the force mount and got this in return.

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.


I will try shutting it down in windows tomorrow morning when I have access.

---

### Post by Marat Galiev on 2008-05-26
mount -t ntfs-3g /dev/sdd1 /mnt/newdrive -o force

Try this.

---

### Post by Woodsyx on 2008-05-26
Ok well it says it's mounted but all I see in the Places > Computer folder is USB Drive and when I try to open it I still get the unable to mount error message. Is there any other way to try and open it?

---

### Post by Marat Galiev on 2008-05-27
Mount it manually.
Try 
**sudo mount -t ntfs-3g /dev/you hard drive /media/hdd**

---

