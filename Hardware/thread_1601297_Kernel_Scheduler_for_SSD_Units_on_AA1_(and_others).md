---
title: "Kernel Scheduler for SSD Units on AA1 (and others)"
date: 2010-10-20
forum: Hardware
---

### Post by andrewsimpson on 2010-10-20
For SSD devices the kernel scheduler has never been totally optimal.  For my Acer Aspire One with an aftermarket SSD upgrade, I have played with adding *elevator=noop* and *elevator=deadline* to GRUB, but it's still a bit of a kludge.

The newer kernels are meant to detect the SSD and adjust the scheduler automatically.  However for many cheaper SSD, like mine, the kernel can't seem to autodetect the SSD.  For a a drive /dev/sda the autodetect is shown by:

```

$ cat /sys/block/sda/queue/rotational
  1

```

An SSD device should be '0' for non-rotational.

To change the kernel parameter we could do 'echo 0 > /sys/block/sda/queue/rotational', but that would have to occur after the boot process.  A better approach is to use udev.

First of all we need to get some unique drive attributes so that udev can identify the drive on initialisation.  This command will show all the attributes for my SSD on /dev/sda1:

```

$ udevadm info -a -p $(udevadm info -q path /dev/sda1)

Looking at device  '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0/block/sda/sda1':

  SUBSYSTEM=="block"
  ...

Looking at parent device '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0/block/sda':
...

Looking at parent device '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0/block':
...

Looking at parent device '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0':

  ATTRS{vendor}=="ATA     "
  ATTRS{model}=="Flash Module     "
  ...

Looking at parent device '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0':
...

```
(Entries are snipped for brevity)

Apparently my SSD vendor is called 'ATA', and the model is 'Flash Module'.  I guess it really was a cheap SSD, but it's not very imaginative naming!

Now choosing some unique identifying attributes - SUBSYSTEM and ATTRS{vendor} (from a parent) - we can write a udev rule that changes the kernel flag:

```

SUBSYSTEM=="block", ATTRS{vendor}=="ATA", ATTR{queue/rotational}="0"

```

You don't have to allow for the whitespace after 'ATA' in the earlier listing above.  

I saved this file as 'lib/udev/rules.d/70-SSD.rules' along with the other udev rules.

Now to test it all works.  No need to reboot, inotify will 'see' the new udev rule immediately...: 

```

$ sudo udevadm test /sys/block/sda
...
parse_file: reading 'lib/udev/rules.d/70-SSD.rules as rules file
...
udev_rules_apply_to_event: ATTR '/sys/devices/.../block/sda/queue/rotational' writing '0' /lib/.../70-SSD.rules:1

```
(Entries are snipped for brevity)

Yep, it works.

So, how does it feel?  Boot up seems about the same, but the system /feels/ more responsive and snappy.  I notice that disk intensive operations such as apt-get will now often return the command prompt, but the HDD light will keep flashing for a while.  I guess the kernel is caching writes more often.

---

