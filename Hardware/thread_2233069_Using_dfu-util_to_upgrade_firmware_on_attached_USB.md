---
title: "Using dfu-util to upgrade firmware on attached USB device"
date: 2014-07-06
forum: Hardware
---

### Post by kjetil-fleten on 2014-07-06
Hi 

I'm trying to update my sons internet radios firmware from one of our Ubuntu computers; we have 5 Ubuntu, no Mac and no Windows in our household :-) 
The radio can be upgraded via USB, and I have installed dfu-util for the purpose.
When I connect the radio to the PC in download mode, I can see that the radio is connected, but I can't upload firmware because dfu-util tells me there is to many attached devices. There is only one, and thats the radio. I get this ouput:

```
$ dfu-util -l
dfu-util 0.5

(C) 2005-2008 by Weston Schmidt, Harald Welte and OpenMoko Inc.
(C) 2010-2011 Tormod Volden (DfuSe support)
This program is Free Software and has ABSOLUTELY NO WARRANTY

dfu-util does currently only support DFU version 1.0

Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=0, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=1, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=2, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=3, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=4, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=5, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=6, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=7, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=8, name="UNDEFINED"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=9, name="UNDEFINED"
Found Runtime: [03f0:171d] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"

```

And the failure message itselves:
```

$ dfu-util -D zImage-RM50-YD3-V0.45-P-20121210-204454.img1 
dfu-util 0.5

(C) 2005-2008 by Weston Schmidt, Harald Welte and OpenMoko Inc.
(C) 2010-2011 Tormod Volden (DfuSe support)
This program is Free Software and has ABSOLUTELY NO WARRANTY

dfu-util does currently only support DFU version 1.0

More than one DFU capable USB device found, you might try `--list' and then disconnect all but one device
```

Any idéas how I can tell dfu-util which DFU entry to use ?
Or how to remove all the extra DFU's from the same device ?

---

### Post by kjetil-fleten on 2014-08-09
Ok, I found the problem.
Here is the solution, if anyone else runs into the same issue:

First, it helps to use the commands with sudo ;-)
([http://community.spark.io/t/dfu-util-cant-list-address/889/8](http://community.spark.io/t/dfu-util-cant-list-address/889/8))

*sudo sudo dfu-util -l* gives
```
dfu-util 0.5

(C) 2005-2008 by Weston Schmidt, Harald Welte and OpenMoko Inc.
(C) 2010-2011 Tormod Volden (DfuSe support)
This program is Free Software and has ABSOLUTELY NO WARRANTY

dfu-util does currently only support DFU version 1.0

Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=0, name="RAM 0x60000000"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=1, name="uboot"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=2, name="ubootenv"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=3, name="Wificab"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=4, name="bootrecord"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=5, name="kernel"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=6, name="kernel2"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=7, name="root"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=8, name="rootfs"
Found DFU: [1d50:5119] devnum=0, cfg=1, intf=0, alt=9, name="rootfs2"


```

Then address the firmware files to the right Altsetting. In my case, the Internet Radio is a Sagemcom RM-50 with 3 files:```

sudo dfu-util -a 5 -D RM50/zImage-RM50-YD3-V0.45-P-20121210-204454.img1
sudo dfu-util -a 8 -D RM50/rootfs1.squashfs-RM50-YD3-V0.45-P-20121210-204454.img2
sudo dfu-util -a 9 -D RM50/rootfs2.squashfs-RM50-YD3-V0.45-P-20121210-204454.img3
```

Now it works !

---

