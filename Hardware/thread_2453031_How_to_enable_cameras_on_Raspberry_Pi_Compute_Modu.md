---
title: "How to enable cameras on Raspberry Pi Compute Module 3+ and Ubuntu 20.04"
date: 2020-11-02
forum: Hardware
---

### Post by adzio1 on 2020-11-02
I'm trying to configure dual camera support in Ubuntu Server 20.04.1 on the Raspberry Pi Compute Module 3+ hardware.

Regular camera module support on common Raspberry Pi boards like 3B+ works fine in 20.04 with fswebcam + gstreamer. I followed the official instructions at [https://www.raspberrypi.org/documentation/hardware/computemodule/cmio-camera.md](https://www.raspberrypi.org/documentation/hardware/computemodule/cmio-camera.md) and used the .dts file they supplied ([https://www.raspberrypi.org/documentation/hardware/computemodule/dt-blob-dualcam.dts](https://www.raspberrypi.org/documentation/hardware/computemodule/dt-blob-dualcam.dts)) for CM3+.

First, I confirmed that compiling the dt-blob.bin file and dropping it to /boot/dt-blob.bin made it work in Raspbian: I could capture images from either of the cameras.  However, after switching to Ubuntu Server 20.04.1 and compiling the same suggested .dts and dropping it to /boot/firmware/dt-blob.bin I have nothing. '/dev/video0' and '/dev/video1' are not created; the output of 'gpio readall' seems to suggest the gpio changes were not applied. start_x=1 is present in /boot/firmware/usercfg.txt

Qs: has anyone made this work with their CM3+? Does the .dts from Raspbian need modifications to work with Ubuntu; any other configuration changes needed on top of what's required for Raspbian? Does the .bin file need to be packaged with initrd like in the case of overlays([https://wiki.ubuntu.com/CustomizeLiveInitrd#Modify_the_initrd](https://wiki.ubuntu.com/CustomizeLiveInitrd#Modify_the_initrd))?

Thanks

---

### Post by adzio1 on 2020-11-11
Apparently 'start_x=1' is only accepted when present in /boot/firmware/config.txt, not in boot/firmware/usercfg.txt; making that change enabled '/dev/video0' but how do I enable '/dev/video1' on CM3+?  $ v4l2-ctl --list-devices bcm2835-codec-decode (platform:bcm2835-codec): 	/dev/video10 	/dev/video11 	/dev/video12 	/dev/media1  bcm2835-isp (platform:bcm2835-isp): 	/dev/video13 	/dev/video14 	/dev/video15 	/dev/video16 	/dev/media0  mmal service 16.1 (platform:bcm2835-v4l2): 	/dev/video0

---

### Post by adzio1 on 2020-11-14
It appears that the loop in drivers/staging/vc04_services/bcm2835-camera/bcm2835-camera.c is not executed for each camera present and configured in RPi CM3+, resulting in only one camera exposed to the end user.  The value of MAX_BCM2835_CAMERAS of 2 should be respected; something in the code/default configuration/environment is affecting this functionality. 'bcm2835-v4l2: V4L2 device registered as video1' is missing in the Ubuntu dmesg.  Filed [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/1904306](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/1904306)

---

### Post by adzio1 on 2020-12-14
For future reference: turned out to be a config issue; commenting out dtparam=i2c_arm=on from /boot/firmware/syscfg.txt loosely based on the findings in the following post [https://www.raspberrypi.org/forums/viewtopic.php?f=98&t=174347&start=25#p1120478](https://www.raspberrypi.org/forums/viewtopic.php?f=98&t=174347&start=25#p1120478) enabled /dev/video1 and the secondary camera in Ubuntu 20.

---

