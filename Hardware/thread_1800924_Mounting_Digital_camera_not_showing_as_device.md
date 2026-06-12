---
title: "Mounting Digital camera: not showing as device"
date: 2011-07-09
forum: Hardware
---

### Post by Browser_ice on 2011-07-09
I was expecting my Ubuntu 10.04 to automaticaly see my old HP 612 digital camera as soon as I plugged it in, but it does not.  I checked with BLKID and it does not even show up as a visible device. I does see my cell when I plug it but not my digital camera.

Suggestions ?

Following another thread, I did the following 
> >~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 011: ID 03f0:6302 Hewlett-Packard PhotoSmart 318/612**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:1004 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

>~$ gvfs-mount -l
Drive(0): 160 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): 160 GB LVM2 Physical Volume
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Drive(1): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
>~$ dmesg | tail -20
[11453.543671] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[11453.556202] sd 5:0:0:0: [sdb] Adjusting the sector count from its reported value: 3842049
[11453.558679] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[11453.558688]  sdb:
[11453.859636] sd 5:0:0:0: [sdb] Adjusting the sector count from its reported value: 3842049
[11453.862645] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[11453.862655] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[11635.584174] usb 6-1: USB disconnect, address 7
[11749.236554] usb 6-1: new full speed USB device using uhci_hcd and address 8
[11750.094197] usb 6-1: configuration #1 chosen from 1 choice
[11778.681155] usb 6-1: USB disconnect, address 8
[11785.140092] usb 6-1: new full speed USB device using uhci_hcd and address 9
[11795.913399] usb 6-1: configuration #1 chosen from 1 choice
[12153.409254] usb 6-1: USB disconnect, address 9
[12174.572566] usb 6-1: new full speed USB device using uhci_hcd and address 10
[12175.429349] usb 6-1: configuration #1 chosen from 1 choice
[12817.304646] usb 6-1: USB disconnect, address 10
[12937.120582] usb 6-1: new full speed USB device using uhci_hcd and address 11
[12937.977354] usb 6-1: configuration #1 chosen from 1 choice
>:~$ 

But from here I am lost on what to do next.

---

### Post by shosto on 2011-07-10
My wife has a similar problem.  Her camera is sometimes automounted and others times it isn't.  Did some research and came up with a small shell script to use with nautilus to mount it, when automount fails.  Instructions are contained in the script itself.

---

### Post by Habe on 2012-07-12
> **shosto said:**
> Fix_camera.sh
```
#!/bin/bash

#
# Nautilus script to fix up usb connected camera that still
# appears in "lsusb" output.  Will look for an existing nautilus bookmark,
# remove it, and then add it back with the updated USB ID.
#
# Install to $HOME/.gnome2/nautils-scripts/
#
# Customize the following to your environment
# CAMERA_BOOKMARK is the string that appears in the nautilus window
CAMERA_BOOKMARK="Canon PS G12"

# USB_ID can be obtained from running lsusb in a terminal
# Bus 002 Device 002: ID 046d:c408 Your Camera Vendor Name
#                        ^^^^^^^^^ 
USB_ID="04a9:320f"

#
# To use:
#    Connect camera
#    Open nautilus window, and see if camera is mounted, if not continue
#    Click menus: File -> Scripts -> Fix_Camera.sh
#    Click the bookmark, as defined below, camera should now be mounted.
#
#CAMERA_MAKER="Canon, Inc."
TMP_FILE=/tmp/gtk-bookmarks-${USER}-camera-fix
BOOKMARKS_FILE=$HOME/.gtk-bookmarks
CAMERA_DETECTED=0
# Set a sane path
PATH=/bin:/usr/bin

lsusb | grep -iq "$USB_ID"
if [ $? -eq 0 ]; then
    BUS_ID=`lsusb | grep $USB_ID | awk '{print $2}'`
    DEV_ID=`lsusb | grep $USB_ID | awk '{print $4}' | sed -e s/://g`
    BM_STR="gphoto2://[usb:${BUS_ID},${DEV_ID}]/ $CAMERA_BOOKMARK"
    CAMERA_DETECTED=1
fi

# Check for existing bookmarks file.  There should be one...
if [ -f $BOOKMARKS_FILE ]; then
    # Remove the old bookmark
    grep -vi "${CAMERA_BOOKMARK}" $BOOKMARKS_FILE  > $TMP_FILE 
fi

if [ $CAMERA_DETECTED -eq 1 ]; then
    echo $BM_STR >> $TMP_FILE
fi
cat $TMP_FILE > $BOOKMARKS_FILE 
rm -f $TMP_FILE

exit 0

```

The script file must be marked as executable.

If lsusb gives ".... ID 03f0:4002 Hewlett-Packard PhotoSmart  635/715/720/735/935 (storage)" you need to change the PC connection mode  within the menu of the camera to PTP.

---

