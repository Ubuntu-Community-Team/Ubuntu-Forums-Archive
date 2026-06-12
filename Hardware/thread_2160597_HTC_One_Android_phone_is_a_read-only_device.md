---
title: "HTC One Android phone is a read-only device"
date: 2013-07-07
forum: Hardware
---

### Post by talmage on 2013-07-07
I need help making Kubuntu 13.04 recognize my brand new HTC One Android phone as a read-write device.  Kubuntu recognizes and automatically mounts the phone as a read-only device. It thinks that the phone is a camera (camera:/) instead of a media player (mtp:/).

These newer Android devices use MTP to communicate with hosts.

I have a Nexus 7 Android tablet that also uses MTP.  Kubuntu automatically recognizes it as a read-write device and as a media player.

I have the kio-mtp MTP KIO client installed and I know that it works because of my experience with the Nexus 7.

I can mount the phone by hand with fuse and mtpfs.  It's still not writable.

I thought that perhaps HAL needed an entry for my phone in /usr/share/hal/fdi/information/20thirdparty/20-libmtp9.fdi, so I made one for the HTC One.  I used one of the HTC One X entries as the starting point.  I changed only the name of the device (in the comment and in in info.product) and the usb.product_id, which I set to "0x0dea" as indicated by dmesg.

That didn't change anything.

I made a small change to /etc/udev/rules.d/51-android.rules and restarted the udev service:

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666", GROUP="plugdev"
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", ATTR{idProduct}="0dea", MODE="0666", GROUP="plugdev"

My addition is the second line.  I can interact with the phone using adb.  For instance, 'adb devices' tells me the hardware id of the phone and 'adb shell' logs me in. It didn't change how Kubuntu mounts my phone.

I even rebooted my computer.  No joy.

I've read most of the suggestions offered by google and Ubuntu Forums.  None of them worked for me.  I'm out of ideas.

---

### Post by talmage on 2013-07-09
It looks like bug [1175595]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/1175595") applies to my HTC One as well as the HTC One SV.

---

