---
title: "How does USB work | Xilinx Spartan 3E driver problem"
date: 2009-10-31
forum: Hardware
---

### Post by armandas on 2009-10-31
Hi.

I have a Xilinx Spartan 3E development board, which connects to my laptop through USB. On Ubuntu 9.04 I somehow managed to make the whole thing work, but I am having problems with 9.10.

Now I managed to do things by hand, but since I don't know what exactly happens when a USB device is plugged in, I cannot make things automatic. To the point.

After driver installation, a [FONT="Courier New"]xusbdfwu.rules[/FONT] file is created in [FONT="Courier New"]/etc/udev/rules.d[/FONT] with the following content:
```
# version 0003
SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0008", MODE="666"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0007", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusbdfwu.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0009", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xup.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000d", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_emb.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000f", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xlp.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0013", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xp2.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0015", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xse.hex -D $TEMPNODE"

```
(BTW: I tried renaming the file to [FONT="Courier New"]50-xusbdfwu.rules[/FONT] (not sure why), but that didn't change anything.)

I did install [FONT="Courier New"]fxload[/FONT], but when I plug the device, nothing happens. Here's what [FONT="Courier New"]dmesg | tail[/FONT] gives me:
```
[ 4463.472139] usb 2-1: new high speed USB device using ehci_hcd and address 15
[ 4463.609074] usb 2-1: configuration #1 chosen from 1 choice
```

Now using [FONT="Courier New"]lsusb[/FONT], I found my device:
```
armandas@ouroboros:~$ lsusb 
Bus 006 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 002 Device 015: ID 03fd:000d Xilinx, Inc. 
Bus 002 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```

So I tried running the command from rules file:
```
armandas@ouroboros:~$ sudo /sbin/fxload -v -t fx2 -I /usr/share/xusb_emb.hex -D /dev/bus/usb/002/015 
microcontroller type: fx2
single stage:  load on-chip memory
open RAM hexfile image /usr/share/xusb_emb.hex
stop CPU
write on-chip, addr 0x1d3d len   10 (0x000a)
...
write on-chip, addr 0x0bfd len   79 (0x004f)
... WROTE: 7458 bytes, 85 segments, avg 87
reset CPU
```

And amazingly, it worked! The LED on the board lit up. Note however, that I had to run this as root, so some permission settings are missing as well.

Could anyone please advice me on how to make this work on its own? I could write a script to do just that, but there must be a proper solution.

---

### Post by armandas on 2009-11-01
I read udev manual and tried to play around with the rules file, but I don't seem to be able to make it work. I checked device properties using
```
udevadm info --attribute-walk --name=/dev/bus/usb/002/015
```
and copied some parameters to rules file:
```
SUBSYSTEM=="usb", ATTR{idVendor}=="03fd", ATTR{idProduct}=="000d", MODE="666", RUN+="touch /home/armandas/Desktop/it_worked.txt"
```

I tried both restarting udev and --reload-rules to make sure changes are detected.

I also tried leaving only SUBSYSTEM=="usb" to make it generic, but that didn't help either. What am I missing?

---

### Post by rndhro on 2009-11-03
Hi,
I had the same problem. Seems to work now and all I've done was changing $TEMPNODE to lowercase:
```

SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0008", MODE="666"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0007", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusbdfwu.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0009", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xup.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000d", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_emb.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000f", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xlp.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0013", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xp2.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0015", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xse.hex -D $tempnode"

```

---

### Post by armandas on 2009-11-03
That did actually help, I just had to delete the BUS=="usb" part. Thanks for the tip!

---

### Post by noleti on 2009-12-03
Excellent, same problem here, and fix worked! I filed a bug []("https://bugs.launchpad.net/launchpad/+bug/492011")[#492018]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/492018")[]("https://bugs.launchpad.net/launchpad/+bug/492011") for this, as Udev seems to have required this unexpected change. Maybe this will help others as well.

Cheers, Ole

> **rndhro said:**
> Hi,
I had the same problem. Seems to work now and all I've done was changing $TEMPNODE to lowercase:
```

SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0008", MODE="666"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0007", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusbdfwu.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0009", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xup.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000d", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_emb.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000f", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xlp.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0013", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xp2.hex -D $tempnode"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0015", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xse.hex -D $tempnode"

```

---

### Post by noleti on 2009-12-04
Got feedback on the Bug

[quote=Scott James Remnant]
           /etc/udev/rules.d/xusbdfwu.rules is listed as a custom rule file you have created, and as given in the Forums it is quite simply wrong.

Without knowing more, it should probably look more like:
 SUBSYSTEM=="usb", ACTION=="add", ATTR{idVendor}=="03fd", ATTR{idProduct}=="0007", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusbdfwu.hex -D %N"

        
    

[/quote]

---

