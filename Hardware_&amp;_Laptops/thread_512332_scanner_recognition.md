---
title: "scanner recognition"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Notrium on 2007-07-29
I run Ubuntu 6.06 but cannot get it to recognise my Epson scanner perfection 1250. I have searched high and low and these two are not matched anywhere. Does this mean I need a new scanner?
I do not mean scanner 1250 PHOTO by the way; just plain 1250

---

### Post by Bachstelze on 2007-07-29
```
sudo apt-get install sane-utils
sudo sane-find-scanner
```

Your scanner should appear there.

---

### Post by madc on 2007-07-29
"sudo apt-get install sane-utils
sudo sane-find-scanner"


i've added these two lines and after that it was written:
"found USB scanner (vendor=0x05d8, product=0x4007 [USB Scanner], chip=GT-6816) at libusb:002:002"

after  scanimage -L :
"device `artec_eplus48u:libusb:002:002' is a Trust 240H Easy Webscan Gold USB flatbed scanner"

but, when i started xsane image scanner it was written again:
"Failed to open device 'artec_eplus48u:libusb:004:002':
Invalid argument"

what can i do?

---

### Post by Bachstelze on 2007-07-29
What kind of scanner do you have (i.e. how is it connected to the PC) ?

---

### Post by madc on 2007-07-29
...usb scanner

---

### Post by mooscape on 2007-07-29
I have a similar problem.  I have upgraded from Dapper to Feisty (Ubuntu Studio). Now my scanner no longer works.  It is an Epson Perfection 2480 Photo that worked perfectly under Dapper.  I cann't remember what I did to get it working and now run around in circles.

The relevant details (sane-find-scanner):  
> found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:005:002
 
and for  scanimage -L:  >  device `snapscan:libusb:005:002' is a EPSON EPSON Scanner flatbed scanner

I am sure it was quite easy to get working, but am now at a loss as to what I did in Dapper....

---

### Post by madc on 2007-07-30
so, this is my solution on "Trust 240H Easy Webscan Gold USB flatbed scanner"

first i've installed xsane and after that i extracted windows drivers through wine into my dir .wine/downloads/drivers, and there i've found file named 1200.usb
after that i copied file 1200.usb to my new created dir /usr/share/sane/**artec_eplus48u**/ and renamed it into Artec48.usb

and that was that, everything is working now like a charm!:guitar:

---

### Post by mooscape on 2007-07-30
Tried extracting the epson driver  > epson11373.exe using wine. That went very well, but did not find any files marked .usb.  I have opened all the .CAB files with cabextract.  The only possible usable file is Esfw42.bin.  ](*,)

---

### Post by madc on 2007-07-30
> **mooscape said:**
> Tried extracting the epson driver   using wine. That went very well, but did not find any files marked .usb.  I have opened all the .CAB files with cabextract.  The only possible usable file is Esfw42.bin.  ](*,)

when you start "xsane image scanner" what does it say?

---

### Post by mooscape on 2007-07-30
Output  from > xsane image scanner:
Failed to open device 'scanner'  invalid argument

---

### Post by Bachstelze on 2007-07-30
And when you try this ?

```
scanimage > image.pnm
```

---

### Post by mooscape on 2007-07-30
Hymn to Life:

> mooscape@mooscape-laptop:~$ scanimage > image.pnm
[snapscan] Scanner warming up - waiting 5 seconds.
mooscape@mooscape-laptop:~$ scanimage > image.pnm
[snapscan] Scanner warming up - waiting 8 seconds.
[snapscan] Scanner warming up - waiting 33 seconds.
mooscape@mooscape-laptop:~$ 


And here's what happened:
1. The first time I ran your instruction, the scanner warmed up and scanned.  ( the "image.pnm" was saved to my home file).    But as the scan arm returns it get stuck at halfway across the scanner.
2. The second time I ran your instruction it said waiting 8 seconds, then it said waiting 33 seconds, then it started to scan (this is the first time it has scanned twice in a row = usually gives error messages)

I really appreciate you getting me even this far! :KS

---

### Post by Bachstelze on 2007-07-30
I have the very same problem with my Agfa, which uses the same SANE backend. No, I haven't found a way around this. Funny thing is, the problem appears only in Linux and not in Free- or OpenBSD, though they're using SANE too.

You know what you have to do ;)

---

### Post by mooscape on 2007-07-30
PS :   I tried it again directly and noticed that the scanner reset itself and then made a good quality scan (2552 x 3507 pix) with no colour problems.

> mooscape@mooscape-laptop:~$ scanimage > image2.pnm
[snapscan] Scanner warming up - waiting 8 seconds.
[snapscan] Scanner warming up - waiting 33 seconds.
mooscape@mooscape-laptop:~$ 


It's arm still does not return...

---

### Post by mooscape on 2007-07-30
> You know what you have to do 

Of course:   AAAAAAAAAAAAAAAAAAAAAAAAAARGH!!!!!!!!!  ](*,)

... that feels better already....

---

### Post by Bachstelze on 2007-07-30
I actually meant switching to BSD but do as you wish :p

---

### Post by mooscape on 2007-07-30
Hymn to Life

In Bug #85488 in sane-backends (Ubuntu), I found:

> install the software
sudo aptitude install scanbuttond

now start the daemon as normal user
scanbuttond.

Thats all there is to it.   It appears the bug causes the USB to suspend. This fixes the problem. (Though why is there a problem in Feisty in the first place? Dapper and Edgy are fine.)

---

### Post by nhojnesnah on 2008-02-07
thanks mooscape. I'm following your steps with the same scanner and have got to your step "Failed to open device 'scanner' invalid argument" but then I see a bit missing in your thread between here and the next step where your scanner works, but bumpily.
What did you do to get there cos my gutsy says it cannot open a firmware file when I try 
"scanimage > image.pnm"
Am I supposed to have loaded some replacement firmware files from somewhere ?

---

