---
title: "udev rule to mount based on partition label"
date: 2008-05-06
forum: Hardware
---

### Post by JonnyRo on 2008-05-06
I am using the following rule to run a special logging script every time a USB stick with the partition label "RAYLOGSTICK" is inserted.  

KERNEL=="sd*1", ENV{ID_FS_LABEL}="RAYLOGSTICK", NAME="raylogstick", RUN+="/opt/bin/log_usb.sh"

It seems to work just fine.  The problem is that it appears to trigger for any partition label.

Am I missing something here?  I changed the label to RAYPLDSTICK on the usb key and the rule still triggered.

Here is the udevinfo output for the symlink in question

disk/by-id/usb-Kingston_DataTraveler_2.0_5B770E8900A6-part1 disk/by-uuid/47FD-2848 disk/by-label/RAYPLDSTICK

It appears that udev is aware of the partition's label.  

I have tried several variations of the rule, to no avail.  Any assistance would be greatly appreciated.

---

### Post by rapri on 2008-10-07
May be you've missed that ``='':
KERNEL=="sd*1", ENV{ID_FS_LABEL}=**=**"RAYLOGSTICK", NAME="raylogstick", RUN+="/opt/bin/log_usb.sh"

---

