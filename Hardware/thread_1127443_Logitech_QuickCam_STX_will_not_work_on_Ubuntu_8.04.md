---
title: "Logitech QuickCam STX will not work on Ubuntu 8.04"
date: 2009-04-16
forum: Hardware
---

### Post by gbonitz on 2009-04-16
I am attempting to install a Logitech QuickCam STX on a Ubuntu 8.04 distro (kernal 2.6.24-23-generic). I have seen numerous posts claiming this webcam works righ out of th ebox on this distro. I should be so lucky... The Logitech QuickCam STX I am attempting to use does not work.

lsusb gives this information:
Bus 001 Device 002: ID 046d:08d7 Logitech, Inc. 
idVendor 0x046d Logitech, Inc.
idProduct 0x08d7 

so it appears that my system is recognizing the webcam.

dmesg gives this information:
[ 13.507128] usbcore: registered new interface driver usbfs
[ 13.507171] usbcore: registered new interface driver hub
[ 13.543103] usbcore: registered new device driver usb
[ 13.659012] USB Universal Host Controller Interface driver v3.0
[ 13.659597] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[ 13.659880] usb usb1: configuration #1 chosen from 1 choice
[ 13.659922] hub 1-0:1.0: USB hub found
[ 13.659933] hub 1-0:1.0: 2 ports detected
[ 13.763179] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[ 13.763400] usb usb2: configuration #1 chosen from 1 choice
[ 13.763442] hub 2-0:1.0: USB hub found
[ 13.763453] hub 2-0:1.0: 2 ports detected
[ 14.038743] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 14.226488] usb 1-2: configuration #1 chosen from 1 choice
[ 32.247220] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[ 32.877667] usbcore: registered new interface driver gspca
[ 32.877677] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[ 32.899973] usbcore: registered new interface driver snd-usb-audio

so it appears that the usb ports are there and that gspca is loaded.

When I attempt to run xawtv I get the following messages:
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-23-generic)
xinerama 0: 1280x1024+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

I have also tried cheese and Skype which also do not work but did not appear to give any useful information as to why not. By the way, the same webcam works perfectly on my XP system.

I need help with the next steps to debug this problem - any suggestions? Has anyone else had the same or similar problem? If so what was your solution?

Any help at all will be greatly appreciated.

---

### Post by yahs on 2009-04-17
I have a logitech quickcam stx (Bus 001 Device 004: ID 046d:08ad Logitech, Inc.)

Fortunately it works as soon as it is plugged in. It also works in Intrepid and Jaunty but as they use v4l2 drivers rather than v4l1, Skype works better in hardy (for me)  

I don't use xawtv, but I installed it and ran it.

Here's the messages I got

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-23-generic)
xinerama 0: 1440x900+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=7): Invalid argument

I then got an image from my webcam in the top left corner of the screen, but not as good quality wise as skype.

The webcam works on all the usual programs, Skype, ekiga, cheese and camorama.

To set it up for skype I had to use System, Preferences, Sound and under the Audio Conferencing Tab I chose mic capture (I think Usb audio also worked)
I also ran the program gstreamer-properties from a terminal and under video selected v4l1, under Audio Default input I chose custom and the pipeline shows halaudiosrc udi=/org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_1 (I have a soundblaster audigy card). In Skype options, Sound In is set to usb device
0x46d:0x8ad and sound out audigy 2. Works Perfectly.

I got similar entries as you posted for lsusb and dmesg regarding the webcam. I can plug into any usb port USB1 Or USB2 but unfortunately I haven't got any solutions for you.

---

