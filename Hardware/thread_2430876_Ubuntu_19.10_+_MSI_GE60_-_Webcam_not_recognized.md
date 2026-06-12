---
title: "Ubuntu 19.10 + MSI GE60 - Webcam not recognized"
date: 2019-11-08
forum: Hardware
---

### Post by jin-valiant on 2019-11-08
Hi all,

I recently installed Ubuntu 19.10 on a MSI GE60 Apache Pro laptop and, while it works great and all devices are recognized, I found the following issue:

If I boot directly on Ubuntu, the OS can't find the webcam. If I run lsusb -t, I get this:
```

thisuser@MSI-GE60-2PE:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 4: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 3: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M

```

Running v4l2-ctl --all returns this:
```

thisuser@MSI-GE60-2PE:~$ v4l2-ctl --all
Cannot open device /dev/video0

```

However, if I first boot on Windows and open the MSI control panel application (MSI SCM) and enable the webcam from there, I can reboot into Ubuntu and this time the webcam is recognized and I can use it normally:
```

thisuser@MSI-GE60-2PE:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 4: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 3: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
        |__ Port 4: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 4: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M

```

```

thisuser@MSI-GE60-2PE:~$ v4l2-ctl --all
Driver Info:
    Driver name      : uvcvideo
    Card type        : BisonCam, NB Pro: BisonCam, NB 
    Bus info         : usb-0000:00:1a.0-1.4
    Driver version   : 5.3.1
    Capabilities     : 0x84a00001

```

Any ideas how can I make Ubuntu recognize the webcam without having to boot into Windows first? I've looked at the BIOS but I can't find anything specific to the webcam, and I'm not sure if editing any of the USB options would make a difference.

Thanks in advance!

---

### Post by jkeenan on 2019-12-19
I am experiencing the same problem on a laptop with Ubuntu 18.04 LTS installed.  I rarely use the built-in webcam, but I know that it was working from 2014 up until several months ago, having used it in both Zoom and Google Hangouts.  Now, when I run 'cheese', I get error output starting with this:
[FONT=Courier New]** Message: 17:27:23.663: cheese-application.vala:211: Error during camera setup: No device found[/FONT]
I also get the following output from the command-line invocations attempted by the original poster.
[FONT=Courier New]$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 2: Dev 2, If 0, Class=Hub, Driver=hub/4p, 12M
        |__ Port 1: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 1: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 2: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 7, If 1, Class=Human Interface Device, Driver=, 1.5M
    |__ Port 3: Dev 3, If 0, Class=Mass Storage, Driver=ums-realtek, 480M
    |__ Port 7: Dev 6, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M

$ v4l2-ctl --all
Failed to open /dev/video0: No such file or directory
$ ls -l /dev/video*
ls: cannot access '/dev/video*': No such file or directory
[/FONT]

I tried Func+F6 (since F6 has a webcam icon on it), but this had no effect.  Any suggestions?

Thank you very much.
Jim Keenan

---

### Post by jkeenan on 2019-12-20
After extensive internet searching, I came across a suggestion deep in [this AskUbuntu thread]("https://askubuntu.com/questions/461657/integrated-webcam-not-detected-after-update-to-14-04").  I did:

[FONT=Courier New]sudo apt-get install guvcview
modprobe uvcvideo # not sure whether this was necessary
reboot
Func+F6 # toggle camera on
cheese
Func+F6 # toggle camera off
[/FONT]

With Func+F6 toggled on, cheese now finds the camera; hopefully Zoom, Skype will as well.

With Func+F6 toggled on, I now get these 2 additional lines in the output of [FONT=Courier New]lsusb -t[/FONT]:

[FONT=Courier New]    |__ Port 8: Dev 11, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 8: Dev 11, If 1, Class=Video, Driver=uvcvideo, 480M
[/FONT]


What I don't understand:  Why did I have to install guvcview now in order to get the Func+F6 toggle on/off capability when I had that capability for at least 5 of the nearly 6 years I've owned this machine?

---

### Post by agiient on 2020-07-30
I had this issue and it was motherboard issue.

Take a look at this article: [https://ubuntuforums.org/showthread.php?t=2143433](https://ubuntuforums.org/showthread.php?t=2143433)

I had to turn on IOMMU, but lost USB 3.0. That was ok because I'm only using USB keyboard, mouse, and was trying to get my webcam to work. Nothing special that needed USB 3.0. Hope this helps some.

---

### Post by CelticWarrior on 2020-07-30
@agiient

Likely not the same issue...
And in your case, if you enabled IOMMU then likely you need an additional boot parameter - *iommu=soft* - in order to have all the hardware working properly.

---

