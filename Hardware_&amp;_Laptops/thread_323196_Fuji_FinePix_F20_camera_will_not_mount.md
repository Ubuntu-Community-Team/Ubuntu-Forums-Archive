---
title: "Fuji FinePix F20 camera will not mount"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by Kethinov on 2006-12-21
When I connect my Fuji FinePix F20 camera to my machine, I get a dialog box that says "Camera Import - A camera has been detected. There are photos on the camera. Would you like to add these pictures to your album?" With options "Ignore" and "Import photos." When I select "Import photos," I get an error that says "An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

When I plug in the camera, dmesg says:

```
[17194743.400000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17194743.560000] usb 2-1: configuration #1 chosen from 1 choice
```

According to guides I saw in the internet, I can manually mount the camera using device /dev/sda1 or /dev/sdb1 etc. But there is no /dev/sd in /dev associated with my camera... what can I do?

(I also cannot get the camera to mount on a Mac, or Windows in VMWare.)

---

### Post by bman77 on 2006-12-31
I had this same issue.  I solved the problem by using the information in this post from solitary [http://ubuntuforums.org/showthread.php?t=327613]("http://ubuntuforums.org/showthread.php?t=327613")
The only difference is you will use this line instead in your /etc/udev/rules.d/45-libgphoto2.rules file:
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="01c0", MODE="0660", GROUP="plugdev"

---

