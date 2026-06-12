---
title: "Printer problem.."
date: 2008-12-22
forum: Hardware
---

### Post by ajsup on 2008-12-22
Dear all,

I have been experiencing the problem with my printer (hp laserjet 1000 series) since i started using ubuntu.. I give a command and all it does is shows its printing but the printer doesnt even buzz.. But, It works perfectly well with Windows OS (xp)..  I looked up the net and came across this page

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

It suggested some steps to follow which i did and the result is given below.. Kindly help me with my printing problem.. also, how do i open a bug buddy window.. How do i report a bug without having encountered an error..
Kindly help me with this problem in anyways possible (It is really inconvenient to change the operating system again and again.. I have to print and i love ubuntu)
Kindly help me out.. 
Thanks in advance..

supkota@supkota-desktop:~$ tail -f /var/log/messages
Dec 22 14:10:32 supkota-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Dec 22 14:10:32 supkota-desktop kernel: [   65.762691] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 22 14:10:32 supkota-desktop kernel: [   65.763349] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 22 14:10:32 supkota-desktop kernel: [   65.763771] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 22 14:11:25 supkota-desktop kernel: [  124.546861] UDF-fs: No VRS found
Dec 22 14:16:12 supkota-desktop syslogd 1.5.0#1ubuntu1: restart.
Dec 22 14:30:18 supkota-desktop -- MARK --
Dec 22 14:50:18 supkota-desktop -- MARK --
Dec 22 15:01:52 supkota-desktop kernel: [ 3150.496122] usb 1-2: USB disconnect, address 3
Dec 22 15:01:52 supkota-desktop kernel: [ 3150.496363] usblp0: removed
Dec 22 15:02:34 supkota-desktop kernel: [ 3192.673179] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 22 15:02:34 supkota-desktop kernel: [ 3192.843848] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 15:02:34 supkota-desktop kernel: [ 3192.855870] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 22 15:02:35 supkota-desktop /usr/sbin/hplj1000: foo2zjs: Missing HP LaserJet 1000 firmware file /usr/share/foo2zjs/firmware/sihp1000.dl
Dec 22 15:02:35 supkota-desktop /usr/sbin/hplj1000: foo2zjs: ...read foo2zjs installation instructions and run ./getweb 1000
Dec 22 15:02:35 supkota-desktop /usr/sbin/hplj1000: foo2zjs: Missing HP LaserJet 1000 firmware file /usr/share/foo2zjs/firmware/sihp1000.dl
Dec 22 15:02:35 supkota-desktop /usr/sbin/hplj1000: foo2zjs: ...read foo2zjs installation instructions and run ./getweb 1000

supkota@supkota-desktop:~$ lpinfo -v
network socket
network beh
direct hal:///org/freedesktop/Hal/devices/usb_device_3f0_517_noserial_if0_printer_noserial
direct hpfax
direct usb://HP/LaserJet%201000
direct hp:/usb/hp_LaserJet_1000?serial=0
network socket://203.159.7.35
network socket://203.159.7.23
network socket://203.159.7.45
network http
network ipp
network lpd
direct parallel:/dev/lp0
file cups-pdf:/
direct scsi
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
network smb
supkota@supkota-desktop:~$

---

### Post by azmo35 on 2008-12-22
Hi,I suggest this site 
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
[http://ubuntuforums.org/showthread.php?t=644011](http://ubuntuforums.org/showthread.php?t=644011)
i hope this help in any way.

---

### Post by niklinux03 on 2008-12-22
Hi, 

I would suggest that you delete all detected printers
and that you follow the instructions of the website
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/).
To delete the detected printer go to system ->
administration -> printing.

After you have done everything, you should reboot
your machine.
For me it works with a 1020 printer.

Cu

---

