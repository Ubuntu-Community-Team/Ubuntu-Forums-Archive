---
title: "problem with SANE scanner"
date: 2018-04-17
forum: Hardware
---

### Post by bjlockie on 2018-04-17
I'm having a problem with my scanner.
It used to work then stopped working then worked.
Now it doesn't work but it is detected.

$ scanimage -L
device `plustek:libusb:010:002' is a Canon CanoScan LiDE25 flatbed scanner
$ scanimage >/tmp/image.pnm
scanimage: no SANE devices found

I don't know if it's hardware related. :-(

---

### Post by rbmorse on 2018-04-18
Could certainly be hardware. Try a different USB cable connecting to a different USB port on the computer, if possible.

---

### Post by bjlockie on 2018-04-22
I bought a Canon Lide 220.
Stand alone scanners are hard to find, most stuff available is a combo (which I don't have room for).
'

---

### Post by rbmorse on 2018-04-22
heeheee.  That's the same solution I used when I got tired of fighting my older Epson flatbed that needed a proprietary driver. Happy with the Canon.

---

### Post by pedro_rodriguez2 on 2018-04-23
Do this:

1. look here: [https://askubuntu.com/questions/547364/canoscan-lide-120-on-ubuntu-14-04](https://askubuntu.com/questions/547364/canoscan-lide-120-on-ubuntu-14-04)
2. sudo add-apt-repository ppa:rolfbensch/sane-git 
3. sudo apt update
4. sudo apt -y install sane libsane libsane-common sane-utils libsane-extras

You may have to repeat 4. Some parts don't install the first time. Also, you may get a system problem error report on boot. 

BUT, my Epson L350 printer scanner works now, and my Canon 120 LiDE

I only bought the Canon because I could not get the Epson L350 printer scanner to work! After getting the Canon to work with new repository files, the Epson worked too!

I think it loads new things in /etc/sane.d/dll.d but I am not an expert!

I am very glad I found this info! Good Luck! Let me know if it works!

---

### Post by asad990 on 2018-04-24
[COLOR=#222222][FONT=&quot]If you want, you can test your scanner locally employing a tool like XSane. To receive your scanner running, you require a firmware file. The second manner is to place the barcode scanner into presentation mode. The issue is the scanner. If you still have problems it may also help in case you completely get rid of the package. The reset problem occurs with different front-ends also.
[/FONT][/COLOR]

---

### Post by sevendogsbsd on 2018-04-24
The Sane web site states this model is supported:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide25&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide25&bus=any&v=&p=)

For my Canon LiDE 220, I need at least sane-backends version 1.0.25. Here is the backend your scanner is using:

[http://www.sane-project.org/man/sane-plustek.5.html](http://www.sane-project.org/man/sane-plustek.5.html)

---

### Post by bjlockie on 2018-04-24
> **rbmorse said:**
> heeheee.  That's the same solution I used when I got tired of fighting my older Epson flatbed that needed a proprietary driver. Happy with the Canon.

The Canon LIDE 220 works fine so I suspect the other scanner wore out.

---

### Post by bjlockie on 2018-04-25
> **rbmorse said:**
> heeheee.  That's the same solution I used when I got tired of fighting my older Epson flatbed that needed a proprietary driver. Happy with the Canon.

Do you know what the stand is for?

---

### Post by mircsicz on 2018-04-27
So it doesn't consume to much space on your desk!?!

---

### Post by kenj69 on 2018-06-05
Did you get your scanner to work? Post #5 has the essentials.

Maybe this topic will help --> [https://ubuntuforums.org/showthread.php?t=2388273](https://ubuntuforums.org/showthread.php?t=2388273)

-=Ken=-

---

