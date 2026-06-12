---
title: "3dconnexion space navigator PE : problems"
date: 2014-02-07
forum: Hardware
---

### Post by Keith_Beef on 2014-02-07
I've been reading around this for a while, and can't seem to get anywhere with it. I know that I had it working a couple of years ago and used it successfully in Gimp, though I never really found it all that useful. Now, I'd like to get it working again to try it out with Medusa 4 CAD.

Before plugging in the space navigator

```
$ lsusb -t
4-1.1:1.2: No such file or directory
4-1.1:1.3: No such file or directory
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 2, Class=vend., Driver=, 12M
        |__ Port 1: Dev 3, If 3, Class=app., Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 4, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 4: Dev 6, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 4: Dev 5, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 5, If 1, Class=HID, Driver=usbhid, 1.5M
```

After plugging in the space navigator

```
[ 1540.176262] usb 1-2.3: new low-speed USB device number 7 using ehci_hcd
[ 1540.286632] logitech 0003:046D:C626.0006: fixing up rel/abs in Logitech report descriptor
[ 1540.308942] input: 3Dconnexion SpaceNavigator as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/input/input15
[ 1540.309077] logitech 0003:046D:C626.0006: input,hidraw0: USB HID v1.10 Multi-Axis Controller [3Dconnexion SpaceNavigator] on usb-0000:00:1a.7-2.3/input0
```

```
$ lsusb -t
4-1.1:1.2: No such file or directory
4-1.1:1.3: No such file or directory
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 2, Class=vend., Driver=, 12M
        |__ Port 1: Dev 3, If 3, Class=app., Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 4, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 4: Dev 6, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 3: Dev 7, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 5, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 5, If 1, Class=HID, Driver=usbhid, 1.5M
```

Detected! Also shown in jstest, but does not move the axes or show button presses.

```
$ jstest --event /dev/input/js1
Driver version is 2.1.0.
Joystick (3Dconnexion SpaceNavigator) has 6 axes (X, Y, Z, Rx, Ry, Rz)
and 2 buttons (Btn0, Btn1).
Testing ... (interrupt to exit)
Event: type 129, time 1642932, number 0, value 0
Event: type 129, time 1642932, number 1, value 0
Event: type 130, time 1642932, number 0, value 0
Event: type 130, time 1642932, number 1, value 0
Event: type 130, time 1642932, number 2, value 0
Event: type 130, time 1642932, number 3, value 0
Event: type 130, time 1642932, number 4, value 0
Event: type 130, time 1642932, number 5, value 0
```


So, I made a udev rule, following the instructions given at the page below.
[http://www.arrowhead.net/blogs/blog-2012-04-01.shtml]("http://www.arrowhead.net/blogs/blog-2012-04-01.shtml")

```
sudo bash -c 'echo KERNEL==\"event[0-9]*\", ATTRS{idVendor}==\"046d\", ATTRS{idProduct}==\"c626\", SYMLINK+=\"input/spacenavigator\", GROUP=\"plugdev\", MODE=\"0664\" > /etc/udev/rules.d/90-spacenavigator.rules'

```
Unplugged the space navigator and plugged it back in again.

```
[ 3884.938582] usb 1-2.3: USB disconnect, device number 7
[ 3910.992344] usb 1-2.3: new low-speed USB device number 8 using ehci_hcd
[ 3911.102715] logitech 0003:046D:C626.0007: fixing up rel/abs in Logitech report descriptor
[ 3911.125025] input: 3Dconnexion SpaceNavigator as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/input/input16
[ 3911.125174] logitech 0003:046D:C626.0007: input,hidraw0: USB HID v1.10 Multi-Axis Controller [3Dconnexion SpaceNavigator] on usb-0000:00:1a.7-2.3/input0
```

An entry is created in /dev/input/
```
$ ls -al /dev/input/spacenavigator 
lrwxrwxrwx 1 root root 7 Feb  3 12:44 /dev/input/spacenavigator -> event13
```

Jstest no longer works at all on this device.
```
jstest --event /dev/input/spacenavigator 
Driver version is 0.8.0.
jstest is not fully compatible with your kernel. Unable to retrieve button map!
Joystick (Unknown) has 2 axes and 2 buttons.
Testing ... (interrupt to exit)

jstest: error reading: Invalid argument
```

And jstest-gtk still detects the space navigator as being on /dev/input/js1 and doesn't detect any axis or button events.

Another niggling annoyance, but not limited to the space navigator, is that when I click on the button labelled "Properties" in jstest-gtk, I get **two** windows showing me the the axes and buttons of the selected device.

Dumping the values of the device using od gets nothing at all on /dev/input/spacenavigator and just gets some values that never change from /dev/input/js1.
```
od -x /dev/input/spacenavigator 
```


```
$ od -x /dev/input/js1
0000000 072c 003b 0000 0081 072c 003b 0000 0181
0000020 072c 003b 0000 0082 072c 003b 0000 0182
0000040 072c 003b 0000 0282 072c 003b 0000 0382
0000060 072c 003b 0000 0482 072c 003b 0000 0582

```

I've tried starting  spnavd and spnavd_ctl but this seems to make no difference&#8230; 
 
```
sudo service spacenavd start
sudo spnavd_ctl x11 start
```

Any ideas what else I need to do?

---

### Post by yan7 on 2014-06-10
Hello, I have a question.

After I plugged in my spacenavigator, the ubuntu can just detect it as an "event" device (like /dev/input/event6).
But your result is that the ubuntu dectect it both as an "event" device (like /dev/input/event6) and "joystick" device (like /dev/input/js1).

Can you help me? Thanks a lot!

---

