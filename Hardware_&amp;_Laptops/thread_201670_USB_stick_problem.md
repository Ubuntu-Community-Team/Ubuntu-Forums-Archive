---
title: "USB stick problem"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by mntn on 2006-06-22
Hi there,

I have an USB-stick that won't mount. When I put it in my computer it does nothing, it even seems that it is not visible as a device (ie sda1 or sdb1 etc.). Below some system(log) data: 

dmesg:

[4296271.079000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[4302858.415000] usb 3-1: USB disconnect, address 2
[4302864.581000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[4302883.415000] usb 3-1: USB disconnect, address 3
[4302894.831000] usb 3-1: new full speed USB device using uhci_hcd and address 4

(As you see I connected it three times and removed it 2 times)

lsusb: 

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c03d Logitech, Inc. 
Bus 004 Device 002: ID 413c:2100 Dell Computer Corp. SK-3106 Keyboard
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0d7d:0100 Phison Electronics Corp. PS1001/1011/1006/1026 Flash Disk
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

(It looks like it is on Bus 003 Device004)

I do not know how to mount it and where from?
Anyone knows what is going on?

Regards,

Chris

---

### Post by cotcot on 2006-06-22
Is the automount box in System --> Preferences --> Removable Media and Stations checked ?

---

### Post by mntn on 2006-06-22
Yes, all options are checked there.

---

### Post by kripkenstein on 2006-06-23
Does the USB stick work in other computers? (just to make sure...)

---

### Post by aysiu on 2006-06-23
Usually USB devices just automount, but if necessary you can add it to your /etc/fstab: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mntn on 2006-06-26
Hi,

I just upgraded the kernel to the latest and now I get the following errors in dmesg:

[17189587.336000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17189587.616000] Initializing USB Mass Storage driver...
[17189587.616000] scsi2 : SCSI emulation for USB Mass Storage devices
[17189587.616000] usb-storage: device found at 2
[17189587.616000] usb-storage: waiting for device to settle before scanning
[17189587.616000] usbcore: registered new driver usb-storage
[17189587.616000] USB Mass Storage support registered.
[17189592.620000]   Vendor:           Model: USB DISK          Rev: 2.08
[17189592.620000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17189592.628000] SCSI device sdb: 1 512-byte hdwr sectors (0 MB)
[17189592.632000] sdb: Write Protect is on
[17189592.632000] sdb: Mode Sense: 43 00 80 00
[17189592.632000] sdb: assuming drive cache: write through
[17189592.644000] SCSI device sdb: 1 512-byte hdwr sectors (0 MB)
[17189592.648000] sdb: Write Protect is on
[17189592.648000] sdb: Mode Sense: 43 00 80 00
[17189592.648000] sdb: assuming drive cache: write through
[17189592.648000]  sdb:<6>usb 3-1: reset full speed USB device using uhci_hcd and address 2
[17189597.152000] usb 3-1: device descriptor read/64, error -71
[17189597.376000] usb 3-1: device descriptor read/64, error -71
[17189597.592000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[17189597.712000] usb 3-1: device descriptor read/64, error -71
[17189597.936000] usb 3-1: device descriptor read/64, error -71
[17189598.152000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[17189598.560000] usb 3-1: device not accepting address 2, error -71
[17189598.672000] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[17189599.080000] usb 3-1: device not accepting address 2, error -71
[17189599.080000] usb 3-1: USB disconnect, address 2
[17189599.080000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17189599.080000] end_request: I/O error, dev sdb, sector 0
[17189599.080000] Buffer I/O error on device sdb, logical block 0
[17189599.080000] sd 2:0:0:0: SCSI error: return code = 0x10000
[17189599.080000] end_request: I/O error, dev sdb, sector 0
[17189599.080000] Buffer I/O error on device sdb, logical block 0
[17189599.080000]  unable to read partition table
[17189599.080000] sd 2:0:0:0: Attached scsi removable disk sdb
[17189599.080000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17189599.088000] usb-storage: device scan complete
[17189599.200000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17189599.320000] usb 3-1: device descriptor read/64, error -71
[17189599.544000] usb 3-1: device descriptor read/64, error -71
[17189599.760000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[17189599.880000] usb 3-1: device descriptor read/64, error -71
[17189600.104000] usb 3-1: device descriptor read/64, error -71
[17189600.320000] usb 3-1: new full speed USB device using uhci_hcd and address 5
[17189600.728000] usb 3-1: device not accepting address 5, error -71
[17189600.840000] usb 3-1: new full speed USB device using uhci_hcd and address 6
[17189601.248000] usb 3-1: device not accepting address 6, error -71

lsusb does not show the stick anymore.

I tried it in Windows, and there it does make an entry for the stick ( E: disk), but it is not accessible, because it probably has a corrupted partition table. But there is still information on the stick and I want to save it (for example with an dd command or with fdisk). Does anyone knows what that error -71 means, and how I can mount the stick anyway?

Thanx in advance,

regards, Chris

---

### Post by rattusdatorum on 2006-07-13
*bump*

I have a similar problem here, 2 different usb sticks that work with other computers.

dmesg:
```

[17187745.428000] usb 1-3: device not accepting address 28, error -110
[17187745.540000] usb 1-3: new high speed USB device using ehci_hcd and address 29
[17187755.964000] usb 1-3: device not accepting address 29, error -110
[17187756.296000] usb 1-3: new high speed USB device using ehci_hcd and address 30
[17187767.840000] usb 1-3: device not accepting address 30, error -110
[17187767.952000] usb 1-3: new high speed USB device using ehci_hcd and address 31
[17187779.496000] usb 1-3: device not accepting address 31, error -110
[17187919.700000] ehci_hcd 0000:00:10.3: remove, state 1
[17187919.700000] usb usb1: USB disconnect, address 1
[17187919.704000] ehci_hcd 0000:00:10.3: USB bus 1 deregistered
[17187919.704000] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[17187943.952000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[17187944.184000] usb 3-1: new low speed USB device using uhci_hcd and address 3
[17187944.416000] usb 3-1: new low speed USB device using uhci_hcd and address 4
[17187944.824000] usb 3-1: device not accepting address 4, error -71
[17187944.936000] usb 3-1: new low speed USB device using uhci_hcd and address 5
[17187945.344000] usb 3-1: device not accepting address 5, error -71

```
did: sudo modprobe -r ehci-hcd     

lsusb: doesn't show them

---

### Post by Teroedni on 2006-07-14
so have you tried to mount them?

---

### Post by rattusdatorum on 2006-07-14
> so have you tried to mount them?
yes, but I couldn't find out what dev, hence no :)

---

### Post by Teroedni on 2006-07-14
most probably /dev/sdb1


or you could check in gksu disks-admin

---

### Post by rattusdatorum on 2006-07-14
nope no /dev/sdb1

have I mentioned that I have kubuntu (tried to search something in system settings but couldn't find anything)

---

### Post by Teroedni on 2006-07-14
```
cat /proc/partitions
```


not sure if this will show it but try it and we will now8)

---

### Post by rattusdatorum on 2006-07-14
hmm

```

   3     0   58605120 hda
   3     1   12289693 hda1
   3     2          1 hda2
   3     5   29696121 hda5
   3     6   15358108 hda6
   3     7    1253038 hda7
 253     0   12289693 dm-0
 253     1   29696121 dm-1
 253     2   15358108 dm-2
 253     3    1253038 dm-3

```

but dm-0 to dm-3 don't show up in /dev/ :confused:

---

### Post by Teroedni on 2006-07-14
no that is not important

are you sure lsusb doesnt show anything 

and try this
```

mkdir /media/usbdisk
```

```

sudo mount -t vfat /dev/sdb1 /media/usbdisk
```

---

### Post by rattusdatorum on 2006-07-14
> are you sure lsusb doesnt show anything 
yes, tried with both sticks, but now I don't have any available :(

---

### Post by Teroedni on 2006-07-14
> **rattusdatorum said:**
> yes, tried with both sticks, but now I don't have any available :(

huh? 
you havent got the usb-sticks now?

---

### Post by rattusdatorum on 2006-07-14
nope, it was in my office, some coworkers handed me the thingies, but I want to get it fixed, also I don't get it why there is a problem anyway, mine works fine.

---

### Post by Teroedni on 2006-07-14
Okay 
But try it next time with theese 2 command and  post here if it worked;



```
sudo mkdir /media/usbdisk
```



```
sudo mount -t vfat /dev/sdb1 /media/usbdisk
```

---

### Post by rattusdatorum on 2006-07-17
well, device doesn't exist :(

lsusb takes a long time and even ctrl-c takes a few seconds (problably one minute) to take effect!!

```
[17189372.528000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[17189373.528000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17189384.072000] usb 4-4: device not accepting address 3, error -110
[17189384.184000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[17189395.728000] usb 4-4: device not accepting address 4, error -110
[17189395.840000] usb 4-4: new high speed USB device using ehci_hcd and address 5
[17189406.264000] usb 4-4: device not accepting address 5, error -110
[17189406.376000] usb 4-4: new high speed USB device using ehci_hcd and address 6

```
well it seems linux tries all addresses!

btw. my own usb stick also doesn't work anymore!!!

need help!

---

### Post by rattusdatorum on 2006-07-18
*bump*

---

### Post by Teroedni on 2006-07-20
what gives ```
fdisk -l

```

---

### Post by rattusdatorum on 2006-07-20
nothing?!?

---

### Post by Teroedni on 2006-07-20
hmm
did you changed your kernel recently?

---

### Post by rattusdatorum on 2006-07-20
I think so, but just with apt-get upgrade, if this is possible.

---

### Post by rattusdatorum on 2006-07-20
thx, I started with an older kernel and it works now, BUT the following
questions remain:

1) why did it happen?
2) what can I do about it?
3) will the problem be solved with the next kernel?
4) how can I support the "debuggers" out there?

---

