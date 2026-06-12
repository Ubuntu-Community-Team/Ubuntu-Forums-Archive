---
title: "CanoScan 5000F - Not detected"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Ivalde on 2005-07-26
After some ups and downs my Ubuntu system is now up and running proparly...
Being a Windows power user and a Linux noob it has worked fairly well, but I have felt pretty darn stupid a couple of times... needing to google for really simple things

But, to my question:
I have a CanoScan 5000F (USB) that I am very happy about and I would like it to work with Ubuntu. Trying to use XSane it only replies "No device found". Reading from XSane home page, this scanner is not supported, nor does it have a Linux driver at all (to my understanding).

Is there anyway to get this scanner to work (partly/full)?
- By using some generic driver?
- By wrapping/copy a windows driver?

Any help would by useful, just to get it up, so I can scan and recive any file with decent dpi into Gimp would be great.

Best
/Ivalde

---

### Post by Ivalde on 2005-07-28
Bump...

Nobody that have the slightest idea?
This the one thing, still keeping me in the M$Windows environment....

/Ivalde

---

### Post by vanth13 on 2007-08-03
yes it's very sad... not using it on ubuntu... anyone?

---

### Post by cmargolin on 2007-08-03
Same problem here.  If you use the search box you will find a number of postings that say the there is no driver for the 500F.

---

### Post by gifancy on 2007-11-20
I have the same scanner and recently moved to Ubuntu 7.10, and the problem still exists. Will continue to dual boot to Windows XP until solution found. This seems to be the only hardware problem I have. :)

---

### Post by sihelset on 2007-12-10
Ubuntu 7.10 64 bits, - same problem, but with Canon 3200F
When running sane-find-scanner I get
found USB scanner (vendor=0x04a9, product=0x2216, chip=GL841?) at libusb:005:007
..
so maybe there is just one more thing that needs adjustment before it runs ?
Anybody who have installed CanoScan scanners on 64 bit ubuntu ?

---

### Post by Tsutsumi Hozan on 2008-04-04
Having also had this problem a few years back when I first moved to using Ubuntu I found that XSane does not have support for the CanoScan 5000F and that a project was underway to create a driver, however it is a French project and therefore hard for me to understand what is going on :(

Sane project page which mentions that the 5000F is not supported:
[http://www.sane-project.org/unsupported/canon-5000f.html]("http://www.sane-project.org/unsupported/canon-5000f.html")

Project for device driver development:
[https://gna.org/projects/canoscan5000F]("https://gna.org/projects/canoscan5000F")

If I recall the problem here is possibly that there is difficulty in obtaining information on how the scanner works and therefore driver development is slow.

Hope this helps.

---

### Post by Seti on 2008-04-04
have you tried
```
sudo xsane
``` ???
you will get a warning about running xsane as root. Just ignore it. If xsane now finds your scanner, you know its a permissions issue.

---

