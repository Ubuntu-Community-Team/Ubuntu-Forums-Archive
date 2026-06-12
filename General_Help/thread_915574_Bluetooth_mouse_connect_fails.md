---
title: "Bluetooth mouse connect fails"
date: 2008-09-10
forum: General Help
---

### Post by compu73rg33k on 2008-09-10
When i plug in my bluetooth dongle, the bluetooth manager comes up notifying me that it's now discoverable. When I try to connect to my mouse which shows up in the Browse Device... dialog, it fails to connect to the mouse and outputs ```
Couldn't display "obex://[00:12:A1:61:20:0C]/".
Error: Host down
Please select another viewer and try again.
```
When I execute the command ```
sudo hidd --connect 00:12:A1:61:20:0C

``` it connects fine.

dmesg | tail gives the following```
[ 6200.511960] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 6203.429820] input: BluePacket Build 2006/7/21 16:28                 as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/hci0/acl0012A161200C/input/input10
[ 7151.393567] usb 2-8: USB disconnect, address 4
[ 8574.875979] input: BluePacket Build 2006/7/21 16:28                 as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/hci0/acl0012A161200C/input/input11
```

---

### Post by isaac.xps on 2008-09-27
I'm having the same exact problem, but until I saw your post I did not think to use the terminal to connect it.  At least now I can use it each time I manually connect it, so thanks for that!

I've tried downloading blueman and when I use that it is able to connect, but after connecting it immediately disconnects.  I wonder why?

Anyone seen and fixed this problem before?

---

### Post by isaac.xps on 2008-09-27
So after some searching I found this thread:
[http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse](http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse)

The only difference is that the folder he calls "bluez-utils" is called "bluetooth" on my computer.

Hope this helps!

---

