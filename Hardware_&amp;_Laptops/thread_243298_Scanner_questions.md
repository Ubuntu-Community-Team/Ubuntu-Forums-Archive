---
title: "Scanner questions"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by mrw on 2006-08-24
I've installed my Epson Perfection 3170 scanner but Xsane detects it only in root - normal user doesn't see the scanner. How do I fix this???

I also have an Acer 2720S film scanner which is not detected at all. Anyone have info on this??

mrw

---

### Post by zxee on 2006-08-24
Your film scanner has "basic" support see the sane link [http://www.sane-project.org/cgi-bin/driver.pl?manu=acer&model=2720s&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=acer&model=2720s&bus=any&v=&p=)
 I didn't check the support level on the epson but you can do that when you download the backend for the film scanner. 
To get the scanner ready for the normal user you may need to make a link to the scanner and use lsusb to determine the device address. i.e. /dev/??? and then chmod ug+x to get it working for non root user.

---

### Post by mrw on 2006-08-24
This is what I get with lsusb.

Bus 002 Device 003: ID 04b8:0116 Seiko Epson Corp.

How do I get the dev/??? from this??

The film scanner does not seem to be supported.

---

### Post by zxee on 2006-08-24
What does sane-find-scanner typed in a terminal output?
Or try dmesg and look through the output. Also the sane site has more complete documentation on setting up your scanner. I don't know why you say the film scanner isn't supported. The supported devices search engine shows it to be supported "basic" see the site for a defination of that.

---

### Post by zeroconf on 2006-08-25
I have HP ScanJet 5p SCSI scanner and XSane does not detect it even as root :(

I wrote about this problem also here:
[http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

... and at the end of here:
[http://ubuntuforums.org/showthread.php?t=11718&highlight=scanjet+5p+scanner](http://ubuntuforums.org/showthread.php?t=11718&highlight=scanjet+5p+scanner)

In Edubuntu 5.10 this scanner worked...

---

### Post by mrw on 2006-08-25
sudo sane-find-scanner shows the epson:

found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:002:003

sane-find-scanner gives this result:

found USB scanner (vendor=0x04b8, product=0x0116) at libusb:002:003

In any case runnng xsane only works in root mode.

---

