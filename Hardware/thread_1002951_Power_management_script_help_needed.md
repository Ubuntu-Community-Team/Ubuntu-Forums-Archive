---
title: "Power management script help needed"
date: 2008-12-05
forum: Hardware
---

### Post by smbm on 2008-12-05
Hi

I've been using this script:

```
#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo 0 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level
  hal-disable-polling --enable-polling --device /dev/cdrom
  modprobe uhci_hcd
  compiz --replace
else
# Turn on aggressive power savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level
  hal-disable-polling --device /dev/cdrom
  modprobe -r uhci_hcd
  metacity --replace
fi
```

From this excellent thread: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) for a while now to control certain aspects of power management for me.

The one aspect that's not working though is the window manager replacement commands at the end of each section. 

This has a drastic impact on battery life for me so I've been trying to get it working all evening.

I've got a hunch it's because the scripts are being executed as root but I'm not sure.

Does anyone have any ideas how to make it work correctly.

1000 thank yous in advance.

Tom

---

### Post by iggykoopa on 2008-12-05
they need to be:
metacity --replace &
compiz --replace &

the & makes the process run in the background

---

### Post by smbm on 2008-12-05
> **iggykoopa said:**
> they need to be:
metacity --replace &
compiz --replace &

the & makes the process run in the background

Hi

Thanks for the reply.

I tried that, it doesn't work.

Any other ideas?

Cheers

---

### Post by iggykoopa on 2008-12-05
I'm not sure why it wouldn't work for you...thats how I do it in the power management gui I'm making and thats run as root as well. Are you sure the script is actually being run?

---

### Post by smbm on 2008-12-05
> **iggykoopa said:**
> I'm not sure why it wouldn't work for you...thats how I do it in the power management gui I'm making and thats run as root as well. Are you sure the script is actually being run?

Hmm, do you have a link for your GUI? I'm intrigued.

Everything else in the script is working except that.

The commands work fine if I put them in a terminal or alt+f2, if I sudo them in a terminal everything goes a bit weird.

Does anyone know of a way to get a system script to launch a program on behalf of a user in that users environment?

---

### Post by iggykoopa on 2008-12-05
the thread for the gui is here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . for running the command as a different user you may be able to try something like:
su [your username] -c "commands"
i.e.:
su iggykoopa -c "metacity --replace &"

---

