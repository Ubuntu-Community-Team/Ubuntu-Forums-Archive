---
title: "Brother Printer DCP-J4110DW"
date: 2014-02-25
forum: Hardware
---

### Post by MickM on 2014-02-25
I Have just  bought a new Brother Printer model DCP-J4110DW I have tried to download a driver from the Brother solutions site. I downloaded the driver and installed via the GDebi Package Installer, It tells me It is installed. I then try to install the new printer but nothing happens. Please help I am desperate.
Mick M

I am using Lubuntu 13.10

---

### Post by spjackson on 2014-02-27
I have one of these working fine with Ubuntu 10.04 (64-bit) for both printing & scanning via wifi. I can't remember exactly what I did to get it working, but it wasn't difficult. How are you connecting wireless/wired/USB?

---

### Post by gifford on 2014-02-28
Yes, how are you connecting to the printer. For my own experience, using the command line and following the instructions on the Brother site has always worked for me.
Are you using Brothers European site or the US? The instruction pages are different.

---

### Post by djahma on 2014-08-07
I'm connecting to that printer by usb and I installed the printer as per the "driver install tool" [here]("http://support.brother.com/g/b/downloadlist.aspx?c=fr&lang=fr&prod=dcpj4110dw_eu_as&os=128&flang=English").
The printer works now, but not the scanner.

Then I installed [the udev rules]("http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=fr&lang=fr&prod=dcpj4110dw_eu_as&redirect=on#u13.04"). Still not working.
So I added the lines to /lib/udev/rules.d/40-libsane.rules```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
``` and again the scanner won't work.

One thing I have noticed though, is that when using simple-scan or Xsane, when I launch the scan, the printer wakes up (the printer screen switches on), but it doesn't scan and fails with the error message "Failed to scan, unable to start scan" in simple scan; and with "Failed to start scanner: invalid argument" in Xsane. What argument is it talking about? good question...

Here is what dmesg has to say about it:
> [ 3737.937336] usb 2-2: new high-speed USB device number 7 using xhci_hcd
[ 3737.958940] usb 2-2: New USB device found, idVendor=04f9, idProduct=02c2
[ 3737.958950] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3737.958955] usb 2-2: Product: DCP-J4110DW
[ 3737.958959] usb 2-2: Manufacturer: Brother
[ 3737.958963] usb 2-2: SerialNumber: BROM3F455195
[ 3737.962153] usblp 2-2:1.0: usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04F9 pid 0x02C2
[ 3737.962467] usb-storage 2-2:1.2: USB Mass Storage device detected
[ 3737.962698] scsi6 : usb-storage 2-2:1.2
[ 3738.962075] scsi 6:0:0:0: Direct-Access     Brother  DCP-J4110DW      1.00 PQ: 0 ANSI: 2
[ 3738.962797] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 3738.966353] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 3758.043296] usb 2-2: usbfs: interface 0 claimed by usblp while 'xsane' sets config #1
[ 3762.709417] usb 2-2: usbfs: interface 0 claimed by usblp while 'xsane' sets config #1
[ 3762.709452] usb 2-2: usbfs: process 30810 (xsane) did not claim interface 1 before use
[ 3779.550791] usb 2-2: usbfs: interface 0 claimed by usblp while 'scan-thread' sets config #1
[ 3780.606726] usb 2-2: usbfs: interface 0 claimed by usblp while 'scan-thread' sets config #1
[ 3780.606764] usb 2-2: usbfs: process 31540 (scan-thread) did not claim interface 1 before use
Any idea?

---

### Post by djahma on 2014-08-09
Further to my previous message, I've just discovered that the first attempt to scan fails in Xsane, but not following attempts. If I close and start Xsane again, the first attempt to scan fails again but succeeds from the second attempt onward. This behaviour does not happen with simple-scan with which scanning always fail.

ADDENDUM: closing in to that issue, I discovered 2 commands. First **sane-find-scanner** which doesn't find the device. And **scanimage** where I get info on the device:
> gman@ThinkPad:~$ scanimage -L
device `brother4:bus2;dev1' is a Brother DCP-J4110DW USB scanner
gman@ThinkPad:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 056a:00ec Wacom Co., Ltd 
Bus 001 Device 006: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 005: ID 5986:029d Acer, Inc 
Bus 001 Device 004: ID 04f3:0254 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 04f9:02c2 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any idea how to make it work outright?

---

### Post by Joespam on 2014-09-16
I'm attempting to use a Brother MFC-4420C scanner and am receiving the same error message: i.e.
process 4512 (xsane) did not claim interface 1 before use.  I would appreciate it if you would post any solution that you find.
Thanks.

---

### Post by djahma on 2014-09-21
Have you tried using the printer over a network? I recently had a chance to try that at my father's, and it worked flawlessly.
Over a USB connection, the scanner only works for me after the second attempt (the first attempt gives the same error you have), and not with all software: Xsane and gscan2pdf. With simple-scan, it only works over a network.

---

