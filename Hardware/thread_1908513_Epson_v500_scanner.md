---
title: "Epson v500 scanner"
date: 2012-01-13
forum: Hardware
---

### Post by debili on 2012-01-13
Hi all,

did anybody get this, or a similar type, scanner to work? lsusb lists it as Seiko Epson Corp. Perfection V500 (GT-X770) but no app detects it. I've tried to install iscan-data_1.13.0-1_all.deb > successfully. but iscan_2.28.1-3.ltdl7_amd64.deb won't install at all. as if the software centre couldn't handle it properly..

would anybody have an idea please?

---

### Post by debili on 2012-01-14
nobody?

---

### Post by debili on 2012-01-14
ok I got it working, needed to install older packages; also, my software center needed to be reinstalled. 

i needed 
iscan-network-nt_1.1.0-2_amd64.deb iscan-data_1.11.0-1_all.deb iscan_2.27.1-4_amd64.deb

plus 

libltdl3 from [http://askubuntu.com/questions/71137/how-can-i-get-an-epson-tx560wd-scanner-working](http://askubuntu.com/questions/71137/how-can-i-get-an-epson-tx560wd-scanner-working)

sorry for asking for support in such a trivial problem;)

---

### Post by DaveNicko on 2012-01-18
This is useful to me as I'm thinking of buying an Epson V500 for scanning negatives - thanks for posting! Have you used it for negative scanning, or are you planning to?

Dave.

---

### Post by debili on 2012-04-28
hello Dave, i'm using it almost exclusively for negatives scanning
, works great especialy with VueScan - can detect& separate photos on a negative strip

---

### Post by Peter-E on 2012-11-05
> **debili said:**
> ok I got it working, needed to install older packages; also, my software center needed to be reinstalled. 

i needed 
iscan-network-nt_1.1.0-2_amd64.deb iscan-data_1.11.0-1_all.deb iscan_2.27.1-4_amd64.deb

plus 

libltdl3 from [http://askubuntu.com/questions/71137/how-can-i-get-an-epson-tx560wd-scanner-working](http://askubuntu.com/questions/71137/how-can-i-get-an-epson-tx560wd-scanner-working)

sorry for asking for support in such a trivial problem;)

Well, I tried all of that in Precise i386 but no joy, the scanner is still not recognised.
lsusb says:
Bus 001 Device 008: ID 04b8:0130 Seiko Epson Corp. Perfection V500 (GT-X770)
so the scanner is there all right.

I want to upgrade my Lucid distro to precise (64bit) but I am afraid to loose the scanner functionality. I just test it on a laptop now with 32bit Precise.
Why was a reinstall of the software center necessary? I use a fresh install on this laptop. I will now replace it with an AMD64 version. On the Avasys pages I cannot find any support for Ubuntu 12.04 LTS. 

btw. the link you quouted in your previous post opens a page in Japanese... I'm afraid I cannot read that.

Any suggestions?
Thanks in advance.
Peter

---

### Post by robinofsussex on 2013-02-03
> **Peter-E said:**
> Well, I tried all of that in Precise i386 but no joy, the scanner is still not recognised.
lsusb says:
Bus 001 Device 008: ID 04b8:0130 Seiko Epson Corp. Perfection V500 (GT-X770)
so the scanner is there all right.

I want to upgrade my Lucid distro to precise (64bit) but I am afraid to loose the scanner functionality. I just test it on a laptop now with 32bit Precise.
Why was a reinstall of the software center necessary? I use a fresh install on this laptop. I will now replace it with an AMD64 version. On the Avasys pages I cannot find any support for Ubuntu 12.04 LTS. 

btw. the link you quouted in your previous post opens a page in Japanese... I'm afraid I cannot read that.

Any suggestions?
Thanks in advance.
Peter

> **debili said:**
> Hi all,

did anybody get this, or a similar type, scanner to work? lsusb lists it as Seiko Epson Corp. Perfection V500 (GT-X770) but no app detects it. I've tried to install iscan-data_1.13.0-1_all.deb > successfully. but iscan_2.28.1-3.ltdl7_amd64.deb won't install at all. as if the software centre couldn't handle it properly..

would anybody have an idea please?


I went to the epson web page and downloaded three deb files, which installed via the software tool in ubuntu. You have to install the data one first. But it works brilliantly. I have been scanning and playing with some 6x4.5 negs and general paper scanning. Nowe the only thing I need windoze for is black mesa source.....

---

