---
title: "Telescope camera problem"
date: 2022-06-23
forum: Hardware
---

### Post by rickticktock on 2022-06-23
I say chaps,
              I can't get the camera on my telescope to work these days. Not on Windows64 or Ubuntu. Haven't tried a Raspberry Pi. It's there, Bus 002 Device 005. There's Sonix SN9C102 chip inside. Is there a way to make "guvcview" use it?

richard@Sam:~$ lsusb
Bus 001 Device 004: ID 2232:1024 Silicon Motion Webcam SC-13HDL11624N [Namuga Co., Ltd.]
Bus 001 Device 003: ID 8087:07da Intel Corp. Centrino Bluetooth Wireless Transceiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0c45:602a Microdia Meade ETX-105EC Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

TTFN
      rickticktock

---

### Post by Autodave on 2022-06-23
Did it ever work on either Linux or Win?

---

### Post by rickticktock on 2022-06-24
Years ago it worked on Win95, 32-bit, and I recently took up astronomy again. All my computers are 64-bit OS

---

### Post by Autodave on 2022-06-24
32/64 bit shouldn't matter for the camera.  Sounds like either your camera died or possibly a bad cable.

---

### Post by rickticktock on 2022-06-24
but lsusb gives 
Bus 002 Device 005: ID 0c45:602a Microdia Meade ETX-105EC Camera

so there must be some life in there. BTW Meade is the manufacturer of the telescope. Cable works OK with Deskjet 1220c.
Other people on other forums lament the lack of a driver for this Sonix chip which was in many webcams.

---

### Post by TheFu on 2022-06-24
A web-search for the USB ID, found this: [https://cateee.net/lkddb/web-lkddb/USB_GSPCA_SONIXB.html](https://cateee.net/lkddb/web-lkddb/USB_GSPCA_SONIXB.html) ... so it seems there are drivers.  

If you already have the drivers on your system, they should show up in an **lshw** report. 

If they are already loaded, then is the question just how to use the menu to selected the device?  

Try using any common webcam software, pointing it at the correct name. Cheese and guvcview are simple.  I've never been impressed with cheese, but guvcview isn't too complicated and just worked.

---

### Post by rickticktock on 2022-06-24
Brill! Much thanks!:KS
guvcview -h
then, when I figured that out,
guvcview -d /dev/video2
did the trick.
guvcview by itself started the application, but no camera choosing. Command line rules!
TTFN
rickticktock.

---

