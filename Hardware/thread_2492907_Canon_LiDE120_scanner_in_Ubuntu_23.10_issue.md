---
title: "Canon LiDE120 scanner in Ubuntu 23.10 issue"
date: 2023-11-27
forum: Hardware
---

### Post by undone-se on 2023-11-27
Hi! I've been using Ubuntu for about 8 years. I bought a Canon LiDE 120 scanner in 2017 and have used it a handful of times every year. I last used it 4 days ago in Ubuntu 23.04. Yesterday I finally upgraded to Ubuntu 23.10, with no apparent upgrade issues (or so I thought).

Today, when I tried to scan with it using Document Scan (44.0), it scans for about 25 seconds (in 1200dpi Image mode) and then the scanner stops while a popup on Document Scan (44.0) says Failed to scan - Error communicating with scanner.

I then tested gscan2pdf (another software I use now and then) and after pushing "Rescan for devices" the scanner turns to life again after a few moments. But 10 seconds after starting to scan (in 600 dpi) it dies again and gscan2pdf reports: "Error device during I/O".

I did some further tests with Document Scan in text-mode (600dpi) and sometimes it makes it through a complete page and sometimes it doesn't. I tried checking syslog for USB-messages using ```
$ tail -f /var/log/syslog | grep USB
``` and when the scanner dies it reports:

```
2023-11-27T11:26:34.090551+01:00 undone-Z97-D3H kernel: [ 7105.576218] usb 3-10: USB disconnect, device number 22
2023-11-27T11:26:34.402566+01:00 undone-Z97-D3H kernel: [ 7105.885253] usb 3-10: new high-speed USB device number 23 using xhci_hcd
2023-11-27T11:26:34.550544+01:00 undone-Z97-D3H kernel: [ 7106.034829] usb 3-10: New USB device found, idVendor=04a9, idProduct=190e, bcdDevice= 7.04
2023-11-27T11:26:34.550557+01:00 undone-Z97-D3H kernel: [ 7106.034845] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0

```
Is it possible that my scanner is developing a hardware issue or is it more likely that is related to Ubuntu 23.10? I can't say I've had any issues with the scanner prior to this.

---

### Post by undone-se on 2023-11-27
Hmm, after turning the computer off, reseating / readjusting the USB-cable to the scanner and restarting, I was able to scan several pages until it started failing again. So maybe it is a hardware issue or the USB-cable. &#129300;

---

