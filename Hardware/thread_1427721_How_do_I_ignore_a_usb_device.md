---
title: "How do I ignore a usb device?"
date: 2010-03-11
forum: Hardware
---

### Post by updatelee on 2010-03-11
Ive tried using quirks in 

/etc/modprobe.d/modprobe.conf
and also in usbhid.conf
and also as a command line option in grub2's grub.cfg

the usb device shows as two in lsusb

Bus 004 Device 004: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 004 Device 003: ID 08bb:2901 Texas Instruments Japan 

everything I do I just cant get linux to leave the device alone. Its an icom PCR-2500 and Id like to use it in vmware with windows XP, but linux keeps trying to use it and obviously doesnt have a clue how.

Ive blacklisted the kernel modules it uses

blacklist cp210x
blacklist snd_usb_audio

the problem is that 08bb:2901 also attaches itself t usbhid which I need for my keyboard and mouse, so I cant blacklist that module. So I tried getting usbhid to ignore it via quirks but with no resolve, it keeps attaching itself.

options usbhid quirks=0x08bb:0x2901:0x0004

in the two conf files in /etc/modprobe.d/

and even

usbhid.quirks=0x08bb:0x2901:0x04

in grub2's grub.cfg

any idea's how to tell linux to stop attempting to utilize this hardware ?

---

### Post by updatelee on 2010-03-11
also in an effort to beter understand how kernel modules are loaded Im trying to determine how does the kernel actually know what module to load ?

Ive looked in /lib/modules/[my kernel]/

and 0x08bb and 0x2901 dont apear anywhere, CP210x does in modules.usbmap but none of the product ID or vendor ID's for my device do

---

### Post by updatelee on 2010-03-12
I read others just turn the power off to the device through sysfs, this isnt what I want but I thought I would try it to see if vmware could turn it back on....

echo suspend > /sys/bus/usb/4-1.1/power/level

locks the entire computer up... grrr

---

### Post by updatelee on 2010-03-14
so attempting to use udev I ignore all three usb devices that appear on lsusb even though only two apear to vmware

updatelee@silverstone:~$ cat /etc/udev/rules.d/10-usb.rules 
ATTRS{idVendor}=="0424", ATTRS{idProduct}=="2502", OPTIONS=="ignore_device"
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", OPTIONS=="ignore_device"
ATTRS{idVendor}=="08bb", ATTRS{idProduct}=="2901", OPTIONS=="ignore_device"

lsusb doesnt show any different now with the device on or off.

/sys/bus/usb/devices

still shows them though

OFF
```

updatelee@silverstone:~$ ls -l /sys/bus/usb/devices/
total 0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3:1.0 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3:1.1 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 4-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 5-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 6-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 7-0:1.0 -> ../../../devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb1 -> ../../../devices/pci0000:00/0000:00:12.2/usb1
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb2 -> ../../../devices/pci0000:00/0000:00:13.2/usb2
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb3 -> ../../../devices/pci0000:00/0000:00:12.0/usb3
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb4 -> ../../../devices/pci0000:00/0000:00:12.1/usb4
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb5 -> ../../../devices/pci0000:00/0000:00:13.0/usb5
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb6 -> ../../../devices/pci0000:00/0000:00:13.1/usb6
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb7 -> ../../../devices/pci0000:00/0000:00:14.5/usb7

```

ON
```

updatelee@silverstone:~$ ls -l /sys/bus/usb/devices/
total 0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3:1.0 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 3-3:1.1 -> ../../../devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 4-0:1.0 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.1 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1:1.0 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.1:1.0 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.1:1.1 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.1
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.1:1.2 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.2
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.1:1.3 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.3
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.2 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.2
lrwxrwxrwx 1 root root 0 2010-03-14 20:33 4-1.2:1.0 -> ../../../devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.2/4-1.2:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 5-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 6-0:1.0 -> ../../../devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 7-0:1.0 -> ../../../devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb1 -> ../../../devices/pci0000:00/0000:00:12.2/usb1
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb2 -> ../../../devices/pci0000:00/0000:00:13.2/usb2
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb3 -> ../../../devices/pci0000:00/0000:00:12.0/usb3
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb4 -> ../../../devices/pci0000:00/0000:00:12.1/usb4
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb5 -> ../../../devices/pci0000:00/0000:00:13.0/usb5
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb6 -> ../../../devices/pci0000:00/0000:00:13.1/usb6
lrwxrwxrwx 1 root root 0 2010-03-14 20:25 usb7 -> ../../../devices/pci0000:00/0000:00:14.5/usb7

```

now when I try and connect them to vmware I get an 'error code 4' grr

vmware.log
```

Mar 14 20:34:30.924: vmx| USB: Connecting device 0x4001808bb2901
Mar 14 20:34:30.953: vmx| USBGA: Failed to connect device 4001808bb2901, error (4)
Mar 14 20:34:30.953: vmx| USBG: CONNREQ: Dequeued head request after 28 ms for [name:Texas\ Instruments\ Japan\ USB\ Audio\ CODEC vid:08bb pid:2901 path:4/1/1 speed:full family:audio,hid]
Mar 14 20:34:30.953: vmx| Msg_Post: Warning
Mar 14 20:34:30.953: vmx| [msg.usb.connectFailed] The connection for the USB device "Texas Instruments Japan USB Audio CODEC" was unsuccessful. The VMware USB Arbitrator returned error code 4.
Mar 14 20:34:30.953: vmx| ----------------------------------------
Mar 14 20:34:35.738: vmx| LOADAVG: 0.22 0.35 0.52
Mar 14 20:34:35.829: vmx| USB: Connecting device 0x4001910c4ea60
Mar 14 20:34:35.860: vmx| USBGA: Failed to connect device 4001910c4ea60, error (4)
Mar 14 20:34:35.860: vmx| USBG: CONNREQ: Dequeued head request after 30 ms for [name:Cygnal\ Integrated\ CP2101\ USB\ to\ UART\ Bridge\ Controller vid:10c4 pid:ea60 path:4/1/2 speed:full family:vendor]
Mar 14 20:34:35.860: vmx| Msg_Post: Warning
Mar 14 20:34:35.860: vmx| [msg.usb.connectFailed] The connection for the USB device "Cygnal Integrated CP2101 USB to UART Bridge Controller" was unsuccessful. The VMware USB Arbitrator returned error code 4.
Mar 14 20:34:35.860: vmx| ----------------------------------------

```

I also tried upgrading to vmware 7.1beta with no resolve.

no one else has usb issues with vmware ?

---

### Post by updatelee on 2010-03-28
Well I upgraded to Lucid to see if that would help and wow, im not impressed with udev at all.

I cant get it to ignore_device at all after some searching

[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001116.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001116.html)
[http://git.kernel.org/?p=linux/hotplug/udev.git;a=commit;h=cdae488a3fbca5a61b3f8ea0651730cfa2da9cb0](http://git.kernel.org/?p=linux/hotplug/udev.git;a=commit;h=cdae488a3fbca5a61b3f8ea0651730cfa2da9cb0)

the ignore_device OPTION has been REMOVED from the udev src !!!! 

> 
remove "ignore_device"

There is no way to ignore an event these days. Libudev events can
not be suppressed. It only prevents RUN keys from being executed,
which results in an inconsistent behavior in current setups.


well isnt that just great. anyone got any idea's now how to tell your OS to ignore usb devices ? udev doesnt even attempt anymore and modprobe quirks is useless. 

this is going downhill haha

---

### Post by shenki on 2010-04-08
I am experiencing the same issue with Ubuntu Lucid and Vmware Player.

I added the following lines to the end of /etc/modprobe.d/blacklist.conf

```
blacklist cp210x
blacklist usbserial
```

Then un-plugged and re-inserted the USB device.

HTH

---

### Post by updatelee on 2010-04-08
I ended up getting my icom pcr1500 and pcr2500 working with

[http://www.r00t.cz/SW/R2500](http://www.r00t.cz/SW/R2500)

I guess the icom software has issues with vm's

still doesn't solve the ubuntu issue that there should be some way to ignore devices

---

