---
title: "Problem with my scanner"
date: 2009-01-15
forum: Hardware
---

### Post by coniglia on 2009-01-15
i have an ubuntu 8.04 (hardy) system, and a benq-5000 scanner connected via usb
after installing sane, sane utilities, and xsane every time i try to scan an image or even preview it, the program close itself and gives me this error message:
"User defined signal 1" :confused: :confused:
whether running it using the terminal (sane) or using the  gtk app (xsane) and even with a root account (sudo) enabled.

but I'm sure the system can reach my scanner cause it can power it and warming it up for 20 sec. before opening xsane

now, every time i need to scan an image i have to run windows to scan it there.
 
  please could anybody tell me what this message mean? and from where the problem is? is it the driver or something in settings or something wrong with sane itself??

---

### Post by albinootje on 2009-01-15
> **coniglia said:**
> i have an ubuntu 8.04 (hardy) system, and a benq-5000 scanner connected via usb
after installing sane, sane utilities, and xsane every time i try to scan an image or even preview it, the program close itself and gives me this error message:
"User defined signal 1" :confused: :confused:


According to this page : [http://www.sane-project.org/sane-mfgs.html#Z-BENQ](http://www.sane-project.org/sane-mfgs.html#Z-BENQ) you're scanner should work well.
> 
5000 USB Good : Color / grayscale scans working up to 1200 DPI

Is your user in the group scanner ?
Find out with this command :
```

groups

```

How did you install sane and the other applications you mentioned ?
Via add/remove or Synaptic package manager ?

Can you post the output of :
```

sudo update-usbids
lsusb
scanimage -L

```

---

### Post by coniglia on 2009-01-15
thanks for ur reply

1. yes, my user is in the scanner group

2. i installed the applications via the terminal 

3. lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04a5:20f8 Acer Peripherals Inc. (now BenQ Corp.) Benq 5000
Bus 002 Device 002: ID 03f0:7904 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 06a2:0003 Topro Technology, Inc. 
Bus 001 Device 001: ID 0000:0000  


4. scanimage -L
device `snapscan:libusb:002:003' is a Acer FlatbedScanner42 flatbed scanner


i hope that help in solving the problem, thanks again for ur reply

---

### Post by albinootje on 2009-01-15
> **coniglia said:**
> 
4. scanimage -L
device `snapscan:libusb:002:003' is a Acer FlatbedScanner42 flatbed scanner

Looks all pretty good.
After a quick search engine search for the error you got, there's not many results..  Here's someone with the same error :
[http://lists.alioth.debian.org/pipermail/sane-devel/2008-June/022331.html](http://lists.alioth.debian.org/pipermail/sane-devel/2008-June/022331.html)

If I were you, I would ask your question on the sane-devel mailinglist.

---

### Post by coniglia on 2009-01-16
it's alrgiht, i'll go and post it there, thanks dear

---

