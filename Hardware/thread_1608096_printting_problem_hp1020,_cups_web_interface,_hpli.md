---
title: "printting problem: hp1020, cups web interface, hplip"
date: 2010-10-28
forum: Hardware
---

### Post by lenberman on 2010-10-28
Hi, I am running 10.4.1 on a lenovo 7400s and am unable to print from my laptop to my HP 1020 when I plug it into the USB port.  I have been trying to solve this for a while and may have made things worse in the process.


>>>> If I try to look at cups opening [http://localhost:631](http://localhost:631), I get a blank page.    (From what I see in messages, I am running ipp://localhost:631 for some reason.)

>>>> If I look at /etc/log/messages, when I plug the printer in I see:

Oct 28 15:21:35 t400s udev-configure-printer: Disabled printer ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-1020 as the corresponding device was unplugged or turned off
Oct 28 15:21:58 t400s kernel: [116421.090086] usb 1-1: new high speed USB device using ehci_hcd and address 11
Oct 28 15:21:58 t400s logger: loading hp_laserjet_1020 firmware 001 011
Oct 28 15:21:58 t400s kernel: [116421.260898] usb 1-1: configuration #1 chosen from 1 choice
Oct 28 15:21:58 t400s kernel: [116421.263925] usblp0: USB Bidirectional printer dev 11 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
Oct 28 15:21:59 t400s kernel: [116422.589974] usb 1-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Oct 28 15:22:01 t400s /usr/sbin/hplj1020: foo2zjs: loading HP LaserJet 1020 firmware /usr/share/foo2zjs/firmware/sihp1020.dl to /dev/usb/lp0 ...
Oct 28 15:22:01 t400s udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-1020
Oct 28 15:22:01 t400s udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Hewlett-Packard-HP-LaserJet-1020
Oct 28 15:22:01 t400s /usr/sbin/hplj1020: foo2zjs: ... download successful.
Oct 28 15:22:23 t400s kernel: [116446.283227] usblp0: removed


>>>> I have hplip installed.  When I open the HP Device manager and try to 'Install Required Plugin', I get a message saying plugin-installation failed.  When I try to print a page, I see messages in the event log which suggest the job prints but nothing actually comes out.

I have no idea how to proceed and would appreciate any help.

Thanls.
--Len

---

