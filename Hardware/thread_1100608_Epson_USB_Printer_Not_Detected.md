---
title: "Epson USB Printer Not Detected"
date: 2009-03-19
forum: Hardware
---

### Post by kioskgroup on 2009-03-19
I have a TM-T88IV Epson thermal printer which im trying to set up with the newest version of ubuntu. The printer is not detected via usb, even on a clean boot with the printer on. I would like to know how go about activiating this printer, if at all possible.

I also have another thermal kiosk printer with the model name: HWASUNG USB Printer I F. This generic printer was detected by ubuntu, but printing fails, i have tried a few different drivers for this device, but no successful prints, what am i doing wrong? How can i make these printers work? Any help would be well appreciated.

---

### Post by cariboo on 2009-03-19
According to [th openprinting database]("http://openprinting.org/show_printer.cgi?recnum=Epson-TM-T88IV") the printer should work.

What is the output of:

```
lsusb
```

when the printer is plugged in.

Could also include the output of:

```
dmesg | tail -n10
```

when you plug the printer in.

Jim

---

### Post by kioskgroup on 2009-03-24
Sorry it took so long to write back, the ubuntu wired network stopped working after i installed 278 updates....so i did a clean install and everything worked fine, anyway back to the real problem...i did the commands you asked and here are the results:

kioskgroup@kioskgroup-desktop:~$ lsusb
Bus 004 Device 003: ID 054c:014f Sony Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

kioskgroup@kioskgroup-desktop:~$ dmesg | tail -n10
[305843.214636] type=1503 audit(1237901334.809:18): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214662] type=1503 audit(1237901334.809:19): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214688] type=1503 audit(1237901334.809:20): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214713] type=1503 audit(1237901334.809:21): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214736] type=1503 audit(1237901334.809:22): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214761] type=1503 audit(1237901334.809:23): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214786] type=1503 audit(1237901334.809:24): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.214812] type=1503 audit(1237901334.809:25): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=8079 profile="/usr/sbin/cupsd"
[305843.332843] ppdev0: registered pardevice
[305843.380348] ppdev0: unregistered pardevice

---

### Post by cariboo on 2009-03-26
The printer is detected by lsusb, but not dmesg. THe driver file for your printer is called javax.usb RI for Linux, and it is located [here]("http://sourceforge.net/project/showfiles.php?group_id=21114").

Jim

---

### Post by lemontemayor on 2009-09-03
I have the same printer Epson Tm-t88IV and the same problem not being able to make it work.  I have ubuntu 8.04.  Noted the site to unload the driver but I do not know how to install it.
 
Any suggestions?
 
Luis

---

