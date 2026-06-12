---
title: "AnyDATA ADU-E100H CDMA Modem doesn't work"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by r@ver on 2006-05-05
Hi all :)

I'm trying to get the AnyDATA ADU-E100H CDMA modem working in several machines and Linux distros, but unsuccessfully :(

I tryed  for example Ubuntu Breezy 2.6.10 and 2.10.16 kernels, Debian, and now I'm running Dapper 2.6.15-21 kernel (I also tryed on Asus WL500g router with custom firmware). 

There are two different scenarios, deppending on which kernel is running and/or modules are loaded.

In kernels prior to 2.6.13 (I think) there wasn't specific support. The way to do it was manually loading usbserial module.

-------------------------------------------------------------------------------
~$ sudo modprobe usbserial vendor=0x16d5 product=0x6501

[4301531.300000] usbcore: registered new driver usbserial
[4301531.300000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[4301531.301000] usbserial_generic 2-1:1.0: generic converter detected
[4301531.302000] usb 2-1: generic converter now attached to ttyUSB0
[4301531.302000] usbserial_generic 2-1:1.1: generic converter detected
[4301531.303000] usb 2-1: generic converter now attached to ttyUSB1
[4301531.303000] usbcore: registered new driver usbserial_generic
[4301531.303000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
-------------------------------------------------------------------------------

The problem here is that I only can dial once. I'm unable to establish another ppp connection without unplugging and plugging the device again. It seems that the connection to the modem is not properly endend at driver level (??) :confused: 

After firt dial, when I connect to the modem with a terminal app i.e. picocom, I continue to receive some strange stuff. Note that I checed that the ppp connection was really terminated on the operator's network.

-------------------------------------------------------------------------------
~$ pon z020 nodetach
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf727c867> <pcomp> <accomp>]
... ... ...

~$ poff -a

... ... ...
Script /etc/ppp/ip-down started (pid 11011)
sent [LCP TermReq id=0x2 "User request"]
Script /etc/ppp/ip-down finished (pid 11011), status = 0x0
rcvd [LCP TermAck id=0x2]
Connection terminated.

~$ picocom -b 115200 /dev/ttyUSB0

picocom v1.4

port is        : /dev/ttyUSB0
flowcontrol    : none
baudrate is    : 115200
parity is      : none
databits are   : 8
escape is      : C-a
noinit is      : no
noreset is     : no
nolock is      : no
send_cmd is    : ascii_xfr -s -v -l10
receive_cmd is : rz -vv

Terminal ready
~&#65533;}#&#65533;!}!}(} }5}"}&} } } } }#}%&#65533;#}%}%}&&#65533;V&#65533;}]&#65533;}!~~&#65533;}#&#65533;!}!})} }5}"}&} } } } }#}%&#65533;#}%}%}&&#65533;V&#65533;}]&#65533;&#65533;~~&#65533;}#&#65533;!}!}*} }5}"}&} } } } }#}%&#65533;#}%}%}&&#65533;V&#65533;}]s&#65533;~~&#65533;}#&#65533;!}%}*} }$&#65533;
-------------------------------------------------------------------------------

AnyDATA support was added to 2.6.13 newer kernel versions. There is module called anydata, which is automatically loaded when the device is plugged. 

-------------------------------------------------------------------------------
[4301306.655000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[4301306.784000] anydata 2-1:1.0: anydata converter detected
[4301306.784000] usb 2-1: anydata converter now attached to ttyUSB0
[4301306.786000] anydata 2-1:1.1: anydata converter detected
[4301306.786000] usb 2-1: anydata converter now attached to ttyUSB1
-------------------------------------------------------------------------------

The problem is that though I can connect to the device with a terminal application, now I can't get either response to AT commands or establish a ppp connection :(

What's wrong? 

Thanks in advance :)

---

### Post by r@ver on 2006-05-08
Hi all :)

In addition to my previous post, if I remove and reload usbserial module again (anydata module unloaded) after de first dial, the modem still doesn't work. It is necessary do unplug and replug it.

 Help pls! :confused: :( :)

---

### Post by jhellan on 2006-07-21
In the next dapper kernel, the AnyDATA problem will be fixed. See [https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/38191](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/38191). As I write, the current kernel is  linux-image-2.6.15-26-686 2.6.15-26.45.

I recently got one of these modems. Thanks to friendly people in the Czech user community, I think I was able to solve the problems. I wrote a page about what I found out. See [http://jk.ufisa.uninett.no/anydata/]("http://jk.ufisa.uninett.no/anydata/").

---

