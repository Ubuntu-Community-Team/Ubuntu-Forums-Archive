---
title: "OmniVision OV2640 Webcam"
date: 2010-05-10
forum: Hardware
---

### Post by birdwin on 2010-05-10
Hello all.

Since a Lucid reformat, my webcam hasn't worked at all.

lsusb says:

Bus 002 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam

gstreamer-properties doesn't list it as a device using any plugin.

Thanks in advance.

---

### Post by irishbreakfast on 2010-05-20
flan_suse at #ubuntu suggested the following script which got my OV2640 camera working. The order of the module loading seems to be important. (I have not verified this for my machine) Of course, the changes can be done via /etc/modules. 


> #!/bin/sh

# A script to re-enable OmniVision OV2640 Webcam

# Unload the modules first
rmmod uvcvideo gspca_ov519 gspca_main vloopback videodev v4l1_compat v4l2_common

# Reload the required modules
modprobe gspca_ov519
modprobe v4l1_compat
modprobe v4l2_common
modprobe uvcvideo

# Exit

exit 0

---

### Post by dmelo on 2010-06-15
In my case, it worked by just reloading the uvcvideo module. Like is described here [http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron]("http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron") .

---

### Post by birdwin on 2010-06-15
Worked perfectly, thanks!

---

