---
title: "WebCam install"
date: 2009-02-01
forum: Hardware
---

### Post by Individul on 2009-02-01
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c312 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 093a:2625 Pixart Imaging, Inc. 
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Web Cam Genius iSlim 310.

What need to do ?

---

### Post by alexmaco on 2009-02-01
First of all, you need to find out if support for your cam is included in the kernel.

If not, search for an open-source driver, because genius doesn't supply linux drivers for you cam. You will also most likely find installation instructions on it's site.

---

### Post by Individul on 2009-02-01
*First of all, you need to find out if support for your cam is included in the kernel.*

How can i do that ?

*If not, search for an open-source driver, because genius doesn't supply linux drivers for you cam. You will also most likely find installation instructions on it's site.*

Where ?.

Thaks for reply.

---

### Post by alexmaco on 2009-02-01
Well, I probably should be more clear next time.

5-10 minutes of googling:
"linux kernel webcam support" - revealed gspca is the module responsible for webcam support - aditional googling yelded this list :
[http://lwn.net/Articles/291036/]("http://lwn.net/Articles/291036/")

It doesn't seem to be in there so what's left is searching for a driver, that unfortunately I couldn't find so far.

TIP: before buying something it's worth checking what drivers the manufacturer offers.

PS: no offense, just trying to be helpful but:
    1 - google is a great asset - it's usually recommended to spend a couple of minutes searching before asking - it often happens that your problem is fairly common and a solution is available
    2 - you aren't always going to find solutions just ready-and-waiting for you. The chances are that there isn't a linux driver for the iSlim 310 at all, just like for my Microdia cam unfortunately.

---

### Post by Individul on 2009-02-01
Ok thanks for your time :)

---

### Post by AndrewLP on 2009-12-25
Is it possible to install another driver (maybe they use the hardware available in other webcams)?

---

### Post by no2498 on 2009-12-31
get (cheese) (wxcam) (xawtv) an try the cam first

---

