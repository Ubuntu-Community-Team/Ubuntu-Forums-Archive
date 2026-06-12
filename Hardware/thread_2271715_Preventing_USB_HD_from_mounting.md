---
title: "Preventing USB HD from mounting"
date: 2015-04-01
forum: Hardware
---

### Post by c7n2 on 2015-04-01
I've bought an external USB HD which holds some stuff I need occasionally, not that often. I'd like to keep plugged into my machine because sometimes I need to use it remotely, but when it's plugged in it always gets mounted which means that it's always spinning and making noise, whether it's being accessed or not. I want it to not be mounted unless I explicitly mount it. I can't make it not mount, it always always mounts whatever I do.

Doing,

udisks --unmount /dev/sdb1 && udisks --detach /dev/sdb

makes it unmount and go quiet but then it immediately mounts again and spins back up. Here's what dmesg says is going on,

[ 1034.702969] usb 3-2: USB disconnect, device number 6
[ 1035.095129] usb 3-2: new SuperSpeed USB device number 7 using xhci_hcd
[ 1035.111581] usb 3-2: New USB device found, idVendor=174c, idProduct=55aa
[ 1035.111590] usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 1035.111595] usb 3-2: Product: USB 3.0 Device
[ 1035.111599] usb 3-2: Manufacturer: Intenso
[ 1035.111602] usb 3-2: SerialNumber: 31000000000000006072
[ 1035.112527] usb-storage 3-2:1.0: USB Mass Storage device detected
[ 1035.112639] usb-storage 3-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[ 1035.112692] scsi9 : usb-storage 3-2:1.0
[ 1036.111683] scsi 9:0:0:0: Direct-Access     Intenso  USB 3.0 Device   0    PQ: 0 ANSI: 6
[ 1036.112039] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 1036.112197] sd 9:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1036.112200] sd 9:0:0:0: [sdb] 4096-byte physical blocks
[ 1036.112406] sd 9:0:0:0: [sdb] Write Protect is off
[ 1036.112408] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1036.112608] sd 9:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1038.407761]  sdb: sdb1
[ 1038.408660] sd 9:0:0:0: [sdb] Attached SCSI disk

I've tried a bunch of things: nautilus settings though dconf-editor, adding

SUBSYSTEM=="usb", ENV{UDISKS_AUTO}="0"

to my rules.d, setting noauto in my fstab. Nothing I've seen suggested has worked. Any ideas would be greatly appreciated.

I'm using ubuntu 14.04.

---

### Post by kerry_s on 2015-04-01
settings-> details-> removable drives, check the box never prompt or start...

---

### Post by sudodus on 2015-04-01
Welcome to the Ubuntu Forums :-)

I don't know of any easy solution to your problem. Mounting with **noauto** works for me, to keep the drive unmounted until mounted manually. But it will still be spinning.

- If you are a new user of linux, I think you should ***avoid complicated commands***, that might damage your HDD.

- If you have experience with linux, you might try ***hdparm*** and the option **-S** 'upper case S' (avoid lower case s) or **--idle-immediate** or **--idle-unload** according to the manual

```
man hdparm
```

```
       -S     Put  the  drive  into idle (low-power) mode, and also set the standby (spindown) timeout
              for the drive.  This timeout value is used by the drive to determine how  long  to  wait
              (with  no disk activity) before turning off the spindle motor to save power.  Under such
              circumstances, the drive may take as long as 30 seconds to respond to a subsequent  disk
              access, though most drives are much quicker.  The encoding of the timeout value is some&#8208;
              what peculiar.  A value of zero means "timeouts are disabled": the device will not auto&#8208;
              matically  enter  standby  mode.   Values  from 1 to 240 specify multiples of 5 seconds,
              yielding timeouts from 5 seconds to 20 minutes.  Values from 241 to 251 specify  from  1
              to  11  units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours.  A value of
              252 signifies a timeout of 21 minutes. A value of  253  sets  a  vendor-defined  timeout
              period  between 8 and 12 hours, and the value 254 is reserved.  255 is interpreted as 21
              minutes plus 15 seconds.  Note that some older drives may have very different  interpre&#8208;
              tations of these values.

```

---

