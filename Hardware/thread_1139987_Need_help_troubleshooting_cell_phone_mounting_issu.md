---
title: "Need help troubleshooting cell phone mounting issue in Jaunty"
date: 2009-04-27
forum: Hardware
---

### Post by bedhead75 on 2009-04-27
I'm having trouble mounting my cell phone when I plug it into a USB cable connection.  My LG Shine (VX-8700) shows up as connected to "Bus 006 Device 002" when I type "lsusb" in the terminal, but it doesn't list as a connected device when I type "df".  When I was using Hardy or Interpid, I believe it would also show up as "/dev/ttyACM0", but not in Jaunty.  Bitpim lists "/dev/ttyACM0" as an inoperable port, even when run as root so I don't think this is a USB permissions problem.  Here is the output given by "dmesg" in the terminal after connecting the phone:

[ 7019.108011] usb 6-2: new full speed USB device using uhci_hcd and address 2
[ 7019.271321] usb 6-2: configuration #1 chosen from 1 choice
[ 7019.298318] cdc_acm 6-2:1.0: ttyACM0: USB ACM device
[ 7019.301177] usbcore: registered new interface driver cdc_acm
[ 7019.301180] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 7086.232274] usb 2-4: usbfs: interface 0 claimed by usb-storage while 'python' sets config #1
[ 7086.235184] usb 6-2: usbfs: interface 0 claimed by cdc_acm while 'python' sets config #1
[ 7086.236513] usb 6-2: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -71
[ 7086.237513] usb 6-2: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -71
[ 7086.237610] usb 6-2: usbfs: interface 0 claimed by cdc_acm while 'python' sets config #1
[ 7086.239512] usb 6-2: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -71
[ 7086.240551] usb 6-2: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -71

 
     Can anyone tell me what additional steps I can take to troubleshoot, and how to file a bug report if necessary?

---

### Post by bedhead75 on 2009-04-29
bump

---

### Post by pdump on 2009-05-30
I have a similar problem, but my only experience with cell phone mounting is through Windows.
I installed the moto4lin package, and according to their [wiki]("http://moto4lin.sourceforge.net/wiki/System_Configuration") you need the USB ACM driver. As far as I understand, I don't have it so it's not installed in Jaunty by default. I can't figure out how to install it though.

EDIT: Forgot to add that dmesg doesn't show anything when I connect the phone, but it does list things when I connect any other USB device and they do work.

---

### Post by bedhead75 on 2009-06-05
I think the ACM driver might be installed by default.  I never installed it manually .  After one of the updates, Jaunty now recognizes my phone each time I plug it in without a problem, and the previous dmesg errors I described earlier are now a thing of the past; however, Bitpim still isn't able to open the port.  
     I am able to properly use the Windows version of Bitpim when I run XP in Virtualbox, so this sounds like a problem in the Linux version of Bitpim.

---

