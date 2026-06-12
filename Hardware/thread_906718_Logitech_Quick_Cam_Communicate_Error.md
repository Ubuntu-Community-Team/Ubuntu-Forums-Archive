---
title: "Logitech Quick Cam Communicate Error"
date: 2008-08-31
forum: Hardware
---

### Post by dublinfireman on 2008-08-31
All,

I have read many different posts and am still confused.  I cannot get my Camera to work in any camera program (Ekiga - Canorama)  I keep getting the error: Error while opening video device /dev/video0.  I have listed certain requests by previous helpers:

lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 054c:01b4 Sony Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:7904 Hewlett-Packard 
Bus 001 Device 002: ID 046d:c315 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

ls -l /dev/video0

crw-rw----+ 1 root video 81, 0 2008-08-31 01:00 /dev/video0


:~$ udevinfo --query=all --name=/dev/video0 --attribute-walk

 looking at device '/devices/pci0000:00/0000:00:1d.1/usb2/2-2/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="GSPCA USB Camera"
    ATTR{stream_id}=="JPEG"
    ATTR{model}=="Logitech QuickCam Communicate S"
    ATTR{pictsetting}=="force_rgb=0, gamma=3, OffRed=0, OffBlue=0, OffGreen=0, GRed=256, GBlue=256, GGreen= 256 "

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb2/2-2/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:129"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 3"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="160mA"
    ATTRS{urbnum}=="3894956"
    ATTRS{idVendor}=="046d"
    ATTRS{idProduct}=="08ad"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:128"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="32"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-18-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.1"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1':
    KERNELS=="0000:00:1d.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x24d4"
    ATTRS{subsystem_vendor}=="0x104d"
    ATTRS{subsystem_device}=="0x8159"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00008086d000024D4sv0000104Dsd00008159bc0Csc03i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

Any help someone can give me PLEASE let me know.

---

### Post by IntuitiveNipple on 2008-08-31
Have you used the driver's debug option to increase the verbosity of messages it writes to the syslogd (/var/log/kern.log , /var/log/debug) ?

If not, unplug the camera then unload the driver:
```

sudo modprobe -r gspca

```
Then, load the driver with the debug option:
```

sudo modprobe gspca debug=5

```
Connect the camera and then make a copy of kern.log
```

cd ~
cp /var/log/kern.log .

```
and then in a text-editor (gedit will do it well: Applications > Accessories > Text Editor) load the copied file (it's in your home directory) and go to the end of the file. Now work back towards the beginning looking for the point where the driver was just loaded (where it starts its verbose logging - you'll see mention of "gspca" a lot). Delete everything from just before that to the start of the file (it's not needed), and save the remainder. Close gedit, then compress the file:
```

gzip kern.log

```
and attach it to a post here so we can look for clues.

Also, post the contents of the file **/etc/modprobe.d/options** so we can be sure there are no forced modules options to catch us out.

---

### Post by dublinfireman on 2008-08-31
Well not to sound too new, but how do you unload the driver???

---

### Post by IntuitiveNipple on 2008-08-31
> **dublinfireman said:**
> Well not to sound too new, but how do you unload the driver???
My apologies, I was typing so fast I forgot to include that bit! I'll put it here and go back and add it to the original post for anyone that discovers it later.
```

sudo modprobe -r gspca

```

---

### Post by dublinfireman on 2008-08-31
I have the camera unplugged and am getting

FATAL: Module gspca is in use.

---

### Post by IntuitiveNipple on 2008-08-31
Okay, leave it unplugged and restart the system. When you're logged-in again open a terminal and use this command to check if the driver is loaded:
```

lsmod | grep gspca

```
If you get anything listed report it, because it shouldn't be loaded unless another device also uses it.

If it isn't loaded at this point, go back to the instructions where it says "Then, load the driver with the debug option".

---

### Post by dublinfireman on 2008-08-31
I can't upload the options file so I'm pasting it

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

---

### Post by dublinfireman on 2008-09-01
Anyone have any luck with this issue?  I'm still stuck

---

### Post by IntuitiveNipple on 2008-09-01
the kernel log looks as I'd expect it to when the device is connected. It adds the video and audio devices:
```

kernel: [  130.875084] Linux video capture interface: v2.00
kernel: [  130.909870] usbcore: registered new interface driver gspca
kernel: [  130.909881] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
kernel: [  136.154870] usb 4-1: new full speed USB device using uhci_hcd and address 2
kernel: [  136.342548] usb 4-1: configuration #1 chosen from 1 choice
kernel: [  136.345438] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
kernel: [  137.182661] usbcore: registered new interface driver snd-usb-audio

```
The previous results show the /dev/video0 device is correctly set-up too.

It looks like the problem is in the applications you're trying to use.

Test the camera with gstreamer-properties, Video tab. Select the input device and Test:
```

gstreamer-properties

```
Test as both V4L and V4L2 source, and report back on your results.

---

### Post by dublinfireman on 2008-09-01
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" is already being used. [v4l_calls.c(174): gst_v4l_open (): /pipeline0/v4lsrc3]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not open device '/dev/video0' for reading and writing. [v4l2_calls.c(443): gst_v4l2_open (): /pipeline1/v4l2src2:
system error: Device or resource busy]

I don't have any software or any other devices open that would be using my webcam.  I tested it on V4L and it worked fine.  I then went to Ekiga and it said it couldn't connect.  I ran the properties again and above is what you see.

---

### Post by IntuitiveNipple on 2008-09-01
> **dublinfireman said:**
>  I tested it on V4L and it worked fine.  I then went to Ekiga and it said it couldn't connect.  I ran the properties again and above is what you see.
That confirms that Ekiga is messing up then, opening the camera connection and not releasing it when it closes.

So the camera is fine but the applications you're trying to use are buggy.

---

### Post by dublinfireman on 2008-09-01
So is there a way to manually release the camera instead of restarting the computer?

---

### Post by VMC on 2008-09-01
> **dublinfireman said:**
> So is there a way to manually release the camera instead of restarting the computer?

I thought the same thing. I kept rebooting for Ekiga, then one day I just unplugged the usb port to the camera and then re-inserted it. Ekiga would then once again work, without having to reboot. There must be a command to do this, I just don't know what it is.

---

### Post by IntuitiveNipple on 2008-09-01
> **VMC said:**
> I thought the same thing. I kept rebooting for Ekiga, then one day I just unplugged the usb port to the camera and then re-inserted it. Ekiga would then once again work, without having to reboot. There must be a command to do this, I just don't know what it is.
Unplugging will do it, yes, since it removes all the device settings from the kernel.

It might be possible to identify and kill all defunct ekiga processes that are holding the device like this:
```

killall ekiga

```

---

### Post by dublinfireman on 2008-09-01
I unplugged the camera and plugged it back in, now it doesn't work at all.  I really don't want to have to restart my CPU everytime so any more ideas?

---

### Post by IntuitiveNipple on 2008-09-01
Restart the PC, and don't use Ekiga with that camera.

---

### Post by VMC on 2008-09-01
> **dublinfireman said:**
> I unplugged the camera and plugged it back in, now it doesn't work at all.  I really don't want to have to restart my CPU everytime so any more ideas?

When you plug & unplug the usb camera what does dmesg say?

---

