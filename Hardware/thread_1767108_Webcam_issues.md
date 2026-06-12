---
title: "Webcam issues"
date: 2011-05-25
forum: Hardware
---

### Post by Interloper15 on 2011-05-25
Hi guys. I've already posted this over at the Linux Mint forums, however, since I haven't had a response in nearly a fortnight, I thought I'd post here as well, since its a direct descendent of Ubuntu, as I understand it.  Here are the contents of my post there.

(Hi. So) I've looked through  quite a number of threads, a tutorial, and a Ubuntu guide trying to sort  this out.  I'm pretty sure my webcam *was* working, and has since  stopped.

I'm using Mint 10. The webcam is a generic UVC USB  camera based on Etron Technology's chipset. Skype doesn't detect a  webcam, neither does Cheese. It doesn't show up in the Terminal results  of lsusb, but unplugging and replugging it *does* make an impact -
(part of dmesg output)
Code:[ 2916.661588] usb 2-4: USB disconnect, address 6
[ 2919.900195] usb 2-1: new high speed USB device using ehci_hcd and address 7
[ 2920.066967] uvcvideo: Found UVC 1.00 device USB2.0 Camera (1e4e:0102)
[ 2920.068775] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 2920.069684] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input18

Any help would be much appreciated.

I actually discovered this while making an effort to figure out why the  cam wasn't working under Flash - which it never has. From what I've  read, it seems thats a common issue.  The webcam works fine within Virtualbox, under a Windows XP installation, so I figure something must be working right.

Can anyone help out?

---

