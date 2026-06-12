---
title: "Where is my printer/scanner/device mounted?"
date: 2012-03-21
forum: Hardware
---

### Post by Silvernail on 2012-03-21
I have a Kodak 5300 AIO printer/scanner. I am using it to scan in 20 years of monthly newsletters and converting to PDF's.
I am scanning and saving to a memory card on the printer.

This device shows up:
```

dave@dave:~$ lsusb
Bus 001 Device 007: ID 040a:4026 Kodak Co. 
dave@dave:~$ 

```
Grepping 'dmesg' for anyone of the word combinations above produces no results.

Gimp, Image Viewer, Libreoffice Draw 3, and Shotwell Photo Manager all recognize this device and will download the images from the printer onboard memory card.

I have been using Shotwell to transfer the .jpg images from the memory care in the printer to a folder on my  computer.  Since the scans are in .jpg format, the computer is handling the printer/device as if it were a camera.

I would like to access the printer memory card from a terminal. It would be easier for me to write a script that would do all the things I need.

How do I find where this device is mounted?

---

### Post by wyliecoyoteuk on 2012-03-21
As it is usb storage, it is probably mounted in the /media folder, usually as /media/usb0

using the command 
```
mount
```
in a terminal should show you.

---

### Post by Silvernail on 2012-03-25
I did not find my Kodak device in 'mount'.

I am giving up this project and marking it solved.

---

