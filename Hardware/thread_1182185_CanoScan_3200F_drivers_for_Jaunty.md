---
title: "CanoScan 3200F: drivers for Jaunty?"
date: 2009-06-08
forum: Hardware
---

### Post by InvisibleMan on 2009-06-08
I've found some drivers for various Canon printers, but nothing for my CanoScan 3200F. It works fine on the XP partition via a USB connection but when Xsane scans for devices in Jaunty, I get the error: "No devices available."

I've googled, searched the forums and emailed Canon. Nothing.

Does anyone have any drivers for a scanner: CanoScan 3200F

Thanks

---

### Post by InvisibleMan on 2009-06-09
Canon's reply:


Thank you for writing to us.  We value you as a Canon customer and appreciate the opportunity to assist you.  I am sorry to hear that you are having trouble locating Linux drivers for your 3200F.
 
While considering the desire to provide the best possible support for Canon’s products, Canon must make decisions on which products to support when new operating systems are introduced.  Currently, Canon has decided to support only the Microsoft Windows and the Macintosh operating systems. With this in mind, we do not have drivers available for your operating system. I apologize for any inconvenience this may cause. 
 
Often times, particularly with open source operating systems, there may be drivers that have been developed by a third-party to use with various products. You may want to check the internet and see if you can find any information on well reviewed drivers for your product. 
 
Please let us know if we can be of any further assistance with your 3200F scanner.
 
Thank you for choosing Canon.
 
Sincerely,
 
Mike
Technical Support Representative

---

### Post by Aearenda on 2009-06-09
I have a 5200F and the same problem. It's the only reason I still have a Windows XP system (an old laptop). I only keep it because of the photo negative scanning capability. I won't buy another Canon scanner or camera until they do support Linux.

---

### Post by Steve Francis on 2009-09-29
Anyone know if there is a 3rd party driver for the 3200F?

It's the only piece of hardware that's tying me to Windows XP.

Alternatively, what's a good scanner that works with Ubuntu?

---

### Post by gacb on 2009-12-30
HP is well supported. I have both an HP officejet and a flat scanner working just fine.

---

### Post by jaizan on 2010-01-30
I use:
Ubuntu Netbook Remix & Windows 7 64 bit

The Canon 3200F does not work with either. 

The message is clear -buy a Canon product and find it is not supported on operating systems 3 years down the line.

Their attitude sucks.

---

### Post by Lauri Pirttiaho on 2010-03-02
> **InvisibleMan said:**
> Canon's reply:


Thank you for writing to us.  We value you as a Canon customer and appreciate the opportunity to assist you.  I am sorry to hear that you are having trouble locating Linux drivers for your 3200F.
 
While considering the desire to provide the best possible support for Canon’s products, Canon must make decisions on which products to support when new operating systems are introduced.  Currently, Canon has decided to support only the Microsoft Windows and the Macintosh operating systems. With this in mind, we do not have drivers available for your operating system. I apologize for any inconvenience this may cause. 
 
Often times, particularly with open source operating systems, there may be drivers that have been developed by a third-party to use with various products. You may want to check the internet and see if you can find any information on well reviewed drivers for your product. 
 
Please let us know if we can be of any further assistance with your 3200F scanner.
 
Thank you for choosing Canon.
 
Sincerely,
 
Mike
Technical Support Representative

Hello Mike,

Few years back I spent several months reverse engineering the firmware
of CS 3200F in order to make SANE driver for it. I got as far as getting
preliminary scans but figuring out the proper calibration procedures and
motor control dynamics would have needed significant amount of
additional work.

Several times during the work I tried to get information about the scanner
and the controller chip from Canon and Acer Laboratoies Inc (ALi), the
manufacturer of the controller chip. Both considered the products to be
obsolete and the information about them so highly secret that not an iota
of information could be made available for development of FOSS driver
for it.

Then I got a HP scanner that I can use with Linux so I wrapped up the
project to wait for times to change. I have also a canon printer, LBP 5200,
and I have a feeling I have to scrap that too, as no driver for it either
is coming from anywhere. Thanks to Canon's attitude to Linux and open
software! Fortunately there are color printers available that can be used
with Linux.

Thanks, but no thanks! No more Canons until they can be used with
any computer and OS I choose.

-- Lauri

---

