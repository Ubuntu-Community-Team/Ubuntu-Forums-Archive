---
title: "USB Printers stop working after upgrade"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Hawk_008 on 2007-11-26
After I upgraded to 7.10 I lost all printer functionality. I have 2 different USB printers, a canon and an epson. After setting them up I get the error a few different errors 

 unable to open usb port file: Permission denied
 unable to open parallel port device file: Permission denied
 /usr/lib/cups/backend/canon(or epson) failed

I messed with the apparmour to allow printing a while back, did nothing.
uninstalled and reinstalled, nothing.
Second printer, nothing.

Any direction would be greatly appreciated.

Thanks

---

### Post by matt_30 on 2007-12-05
i have exactly the same problem and can not seam to find the answer

the error when it holds the job is

"Unable to open parallel port device file: Permission denied"

even though its a usb printer (epson stylus photo 915)

matt@base-unit:/dev$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 007: ID 04b8:0602 Seiko Epson Corp. Stylus Photo 895 Card Reader
Bus 002 Device 006: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 005: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

matt@base-unit:/dev$ tail /var/log/cups/error_log
D [05/Dec/2007:12:50:19 +0000] cupsdAuthorize: No authentication data provided.
D [05/Dec/2007:12:50:19 +0000] Get-Jobs ipp://localhost:631/printers/epson
D [05/Dec/2007:12:50:19 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [05/Dec/2007:12:50:19 +0000] cupsdCloseClient: 10
D [05/Dec/2007:12:50:22 +0000] cupsdAcceptClient: 10 from localhost (Domain)
D [05/Dec/2007:12:50:22 +0000] cupsdReadClient: 10 POST / HTTP/1.1
D [05/Dec/2007:12:50:22 +0000] cupsdAuthorize: No authentication data provided.
D [05/Dec/2007:12:50:22 +0000] Get-Job-Attributes ipp://localhost:631/jobs/152
D [05/Dec/2007:12:50:22 +0000] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [05/Dec/2007:12:50:22 +0000] cupsdCloseClient: 10

---

### Post by dingletec on 2007-12-17
Did you happen to check if your user is in the tty group in /etc/group?

---

### Post by pwaldo on 2008-01-17
I have this problem also.  Any resolution?

---

### Post by pwaldo on 2008-01-17
FYI, I have a parallel printer that still works fine...

---

### Post by pwaldo on 2008-01-17
OK, well here's an ugly solution:
sudo chmod 666 /dev/usb/lp0
I have no idea why this works, as I am in the lp group and the file looks like this:
crw-rw---- 1 root lp 180, 0 2008-01-16 21:39 /dev/usb/lp0

---

### Post by Yellow Pasque on 2008-01-17
That sounds like a bug to me. I would suggest searching Launchpad for a similar issue and reporting it if there's no issue open for it.

---

