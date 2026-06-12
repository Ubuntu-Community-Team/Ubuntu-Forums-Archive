---
title: "Firewire external drive not working in Jaunty"
date: 2009-05-13
forum: Hardware
---

### Post by Obnoticus on 2009-05-13
I upgraded my laptop install from Intrepid to Jaunty about 2 weeks ago, and noticed that my external firewire/usb hard drive is no longer recognized by Ubuntu when plugged into the computer's firewire port.  The drive's LED flashes after being plugged in, but I cannot see the drive itself in Nautilus, and fdisk -l shows this:

```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

lsmod shows this:
```

sunny@sunny-laptop:~$ lsmod|grep 1394
ohci1394               42036  1 
ieee1394              108288  2 sbp2,ohci1394

```

and dmesg|grep 1394 shows the following:
```

sunny@sunny-laptop:~$ dmesg|grep 1394
[   11.995414] ohci1394 0000:08:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.048121] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.325187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003b7ffd8]
[  149.353476] ieee1394: Error parsing configrom for node 0-00:1023
[  149.353902] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  155.724885] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e100034a9]
[  155.727389] scsi5 : SBP-2 IEEE-1394
[  155.727510] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x20 (firmware_revision 0x012804, vendor_id 0x005077, model_id 0x000001)
[  156.730260] ieee1394: sbp2: Logged into SBP-2 device
[  156.730406] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]

```

and:

```
sunny@sunny-laptop:~$ dmesg|grep sbp
[  155.727510] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x20 (firmware_revision 0x012804, vendor_id 0x005077, model_id 0x000001)
[  156.730260] ieee1394: sbp2: Logged into SBP-2 device
[  156.730406] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]

```

The hard drive itself works just fine when it is connected thru my USB port.  I can see the files and read and write to it without any problem. And in Vista I can access this drive whether it is plugged in through firewire or usb.  Can anyone help me out on this?

---

### Post by Obnoticus on 2009-05-13
anyone? *bump*

---

### Post by ulrith on 2009-07-09
I've just plug new PCI firewire card for my external hdd - no new disk in Nautilus. I use Ubuntu 9.04.

fdisk -l

```
nothing
```

lsmod

```
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
```

dmesg|grep 1394

```
[    5.432244] ohci1394 0000:04:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.482005] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.504449] ohci1394 0000:04:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.557201] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.772214] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800011bb532]
[    6.880157] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[000a48000000300a]
```

dmesg|grep sbp

```
nothing
```

HDD works with USB cable just fine.

May be you can give me any ideas...

---

### Post by ulrith on 2009-07-09
P.S. Regards to Big Apple! :-)

---

### Post by slambrick on 2009-07-16
Hi I found this article. I assume you havent resolved it yet so try it.

[http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how](http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how)

---

### Post by mdwy62 on 2009-07-24
I tried to follow the ideas in this link above 

([http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how](http://www.kdenlive.org/forum/toubleshooting-firewire-capture-ubuntu-jaunty-904-how))

but without success. I'm trying to get the firewire edition of the iomega Go Drive to work. It works fine with a usb cable.

Here are the steps I took (which didn't work).

sudo gedit /etc/modules

added the lines:

raw1394
dv1394
video1394

Then created the file

/etc/udev/rules.d/45-firewire.rules

containing

KERNEL=="raw1394", GROUP="disk"

Rebooted.

Any thoughts? Thanks.

---

### Post by mdwy62 on 2009-07-24
I opened System>Administration>Users and Groups>Manage Groups

I don't see a "disk" group. 

Under my own Privileges, I see that I do not have FUSE checked, nor mounting tape drives.  Is there any problem with giving myself access to these groups? 

Seems like I should change the group setting in the firewire rules file I created to "FUSE"?  

Could anyone confirm that these are reasonable changes to make? Is FUSE capitalized?

---

### Post by tormod on 2012-03-13
I know this is an old thread, but this might help someone who finds it when searching:

The "vendor_id 0x005077" in the dmesg output means the firewire controller in your drive is from Prolific which is known to have broken firmware. The "firmware_revision 0x012804" in particular (I found this thread by searching for "0x012804"...) goes nuts when it receives certain SCSI enquiries (that their Windows drivers are not using, it seems).

See [https://bugzilla.kernel.org/show_bug.cgi?id=42914](https://bugzilla.kernel.org/show_bug.cgi?id=42914) for more information and a link to a mailing list thread with a workaround that works for me: Disable the *scsi_id* utility which is launched by *udev* when the drive is plugged in, using the command:```
chmod a-x /lib/udev/scsi_id
```

---

