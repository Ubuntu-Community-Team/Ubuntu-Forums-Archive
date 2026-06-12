---
title: "UDEV / External USB HDD assignment / head scratcher"
date: 2015-02-16
forum: Hardware
---

### Post by RedShoeRider on 2015-02-16
Good Afternoon, All:

I'll be the first to admit that this is my first foray into UDEV, but after reading as much as I can, I'm still stumped. 

Here's the setup:
I have a 4TB WD 3.5HDD in a StarTech external USB enclosure. Thanks to a backup process I want to run, I need to to always assign to the same mount point, say, /dev/sdq. So, in reading, I find that a udev rule should be my ticket. From reading, I go with this (it happens to be /sdf right now):

```
udevadm info --query all --path /sys/block/sdf --attribute-walk
```

And I get ton of stuff. This is the part that I think is the HDD itself:

looking at parent device '/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/host10/target10:0:0/10:0:0:0':
    KERNELS=="10:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{rev}=="0   "
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="7"
    **ATTRS{model}=="2105            "**
    ATTRS{state}=="running"
    ATTRS{queue_type}=="none"
    ATTRS{iodone_cnt}=="0xe7"
    ATTRS{iorequest_cnt}=="0xe7"
    ATTRS{device_busy}=="0"
    ATTRS{evt_capacity_change_reported}=="0"
    ATTRS{timeout}=="30"
    ATTRS{evt_media_change}=="0"
    ATTRS{max_sectors}=="240"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{queue_depth}=="1"
    **ATTRS{vendor}=="ASMT    "**
    ATTRS{evt_soft_threshold_reached}=="0"
    ATTRS{device_blocked}=="0"
    ATTRS{evt_mode_parameter_change_reported}=="0"
    ATTRS{evt_lun_change_reported}=="0"
    ATTRS{evt_inquiry_change_reported}=="0"
    ATTRS{iocounterbits}=="32"
    ATTRS{eh_timeout}=="10"

(I added the bolding)
Every example of this udev output that I've read showed the Vendor and Model as the actual Vendor and Model number, not some seemlingly random crap.  In looking though the whole output, there's nothing that even imples Western Digital. But, what do I know, so I made a udev rule in /etc/udev/rules.d/10-usb.rules  that reads:
```
ATTRS{vendor}=="ASMT    ", ATTRS{model}=="2105            ", SYMLINK+="/dev/sdq"
```

Upon rebooting.....nothing changes. The drive is assigned to either /sdf or /sde. 

So.....two questions:
1) Am I looking at the right part of the udevadm output?
2) If I am, what am I doing wrong?

Thanks so much!
-Red

---

### Post by TheFu on 2015-02-16
No need to use udev at all.
Use UUIDs or Labels.  These are static per partition.
You can mount either through the fstab or autofs.
Look under  /dev/disk/by-* for the mapping between device and either UUID or label.

---

