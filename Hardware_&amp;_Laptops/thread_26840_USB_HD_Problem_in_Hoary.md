---
title: "USB HD Problem in Hoary"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by rverlind on 2005-04-14
I have problems mounting an external USB HD on Hoary. The same HD mounts without any problem on WinXP and used to mount without any problem on Debian Sarge (without automount, etc.).

Does anybody have an idea what the problem might be? (Below the `tail -f /var/log/syslog' output and the lspci output.)

I am not sure that this is an USB problem, since cdrecord --scanbus gives problems regarding scsi (output also below). CD burning works fine with K3B nevertheless.

I hope somebody can give me a hint where to look,
Ruben


**tail -f /var/log/syslog after reboot when plugging in usb HD :**
[I]Apr 14 11:01:12 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 2
Apr 14 11:01:12 localhost kernel: usb 3-1: device descriptor read/64, error -71
Apr 14 11:01:21 localhost kernel: usb 4-5: new high speed USB device using ehci_hcd and address 3
Apr 14 11:01:21 localhost kernel: SCSI subsystem initialized
Apr 14 11:01:22 localhost kernel: Initializing USB Mass Storage driver...
Apr 14 11:01:22 localhost usb.agent[8490]:      usb-storage: loaded successfully
Apr 14 11:01:22 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Apr 14 11:01:22 localhost kernel: usbcore: registered new driver usb-storage
Apr 14 11:01:22 localhost kernel: USB Mass Storage support registered.
Apr 14 11:01:22 localhost kernel: usb-storage: device found at 3
Apr 14 11:01:22 localhost kernel: usb-storage: waiting for device to settle before scanning
Apr 14 11:01:27 localhost kernel:   Vendor: Maxtor 7  Model: Y250P0            Rev: YAR4
Apr 14 11:01:27 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 04

<<Execute sudo fdisk -l in another terminal>>

Apr 14 11:02:43 localhost kernel: usb 4-5: reset high speed USB device using ehci_hcd and address 3
Apr 14 11:02:44 localhost kernel: usb 4-5: scsi_eh_0 timed out on ep0in
Apr 14 11:02:44 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:02:49 localhost kernel: usb 4-5: scsi_eh_0 timed out on ep0in
Apr 14 11:02:49 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:02:49 localhost kernel: usb 4-5: reset high speed USB device using ehci_hcd and address 3
Apr 14 11:02:50 localhost kernel: usb 4-5: scsi_eh_0 timed out on ep0in
Apr 14 11:02:50 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:02:55 localhost kernel: usb 4-5: scsi_eh_0 timed out on ep0in
Apr 14 11:02:55 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:02:55 localhost scsi.agent[8645]:      sd_mod: loaded sucessfully
Apr 14 11:02:55 localhost kernel: scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 0 lun 0
Apr 14 11:02:55 localhost kernel: scsi0 (0:0): rejecting I/O to offline device
Apr 14 11:02:55 localhost last message repeated 3 times
Apr 14 11:02:55 localhost kernel: sda : READ CAPACITY failed.
Apr 14 11:02:55 localhost kernel: sda : status=0, message=00, host=0, driver=04
Apr 14 11:02:55 localhost kernel: sda : sense not available.
Apr 14 11:02:55 localhost kernel: sda: assuming drive cache: write through
Apr 14 11:02:55 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Apr 14 11:02:55 localhost kernel: usb 4-5: USB disconnect, address 3
Apr 14 11:02:55 localhost kernel: usb-storage: device scan complete
Apr 14 11:02:56 localhost udev[8723]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Apr 14 11:02:56 localhost udev[8723]: creating device node '/dev/sda'
Apr 14 11:02:56 localhost kernel: usb 4-5: new high speed USB device using ehci_hcd and address 4
Apr 14 11:02:57 localhost kernel: usb 4-5: khubd timed out on ep0in
Apr 14 11:02:57 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:03:01 localhost /USR/SBIN/CRON[8814]: (rverlind) CMD (cp /home/rverlind/.signature /home/rverlind/.evolution/signatures/signature-0)
Apr 14 11:03:02 localhost kernel: usb 4-5: khubd timed out on ep0in
Apr 14 11:03:02 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:03:02 localhost kernel: usb 4-5: new high speed USB device using ehci_hcd and address 5
Apr 14 11:03:03 localhost kernel: usb 4-5: khubd timed out on ep0in
Apr 14 11:03:03 localhost kernel: usb 4-5: device descriptor read/64, error -110
Apr 14 11:03:06 localhost hal.hotplug[8812]: timout(10000 ms) waiting for /block/sda
Apr 14 11:03:06 localhost udev[8822]: removing device node '/dev/sda'
Apr 14 11:03:08 localhost kernel: usb 4-5: khubd timed out on ep0in
Apr 14 11:03:08 localhost kernel: usb 4-5: device descriptor read/64, error -110[/I]


**lspci output :**
[I]0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)[/I]


**sudo cdrecord --scanbus output :**
[I]Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .[/I]

---

