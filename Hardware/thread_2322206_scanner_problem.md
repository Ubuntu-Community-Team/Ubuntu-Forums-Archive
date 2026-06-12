---
title: "scanner problem"
date: 2016-04-26
forum: Hardware
---

### Post by pedro_rodriguez2 on 2016-04-26
I have Ubu 14.04 on one partition and I just updated from Ubu 15.10 to Ubu 16.04 on another partition. In 14.04, xsane works fine. In 15.10, I could not get xsane to find the scanner. Now I upgraded to 16.04 and xsane still finds no device.

The scanner works fine in 14.04. Never worked in 15.10, won't work now in 16.04. The scanner is part of an all in one scanner printer Epson L351. It works fine in 14.04. 

This is the output of sane-find-scanner and scanimage -L

> pedro@pedro-275E4E-275E5E:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04b8 [EPSON], product=0x08a1 [EPSON L350 Series]) at libusb:004:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
pedro@pedro-275E4E-275E5E:~$ 


Don't know what a pipe error is. but the scanner is detected.

> pedro@pedro-275E4E-275E5E:~$ sudo scanimage -L
[sudo] password for pedro: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
pedro@pedro-275E4E-275E5E:~$ 



 I have the correct settings in /etc/sane.d/epson.conf

> # usb 0x4b8 0x110
#[EPSON L350 Series]) at libusb:004:003

usb 0x04b8 0x08A1 

# And for the scanner module, use the following configuration:
usb /dev/usbscanner0

usb /dev/usb/scanner0

This has gone on a long time now. **Any tips out there please?** Permissions?? 

I tried running xsane as root, got danger warnings, went ahead, but still no devices found.

I borrowed a simple canon flatbed usb powered scanner. Xsane finds it and it works. I did not have to set anything at all. Just works, as does my Epson in 14.04.

What is wrong here? I was hoping the upgrade would solve the problem, then I could move to 16.04 completely.

---

### Post by pedro_rodriguez2 on 2016-04-27
I went to the Epson webpage, downloaded and installed epkowa, which installs iscan, which is like their spin of xsane I suppose. 

I noticed in /etc/epkowa/epkowa.conf that it said:

> # For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
# 
   usb 04b8 08a1
#
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1).
# A sample configuration for the Epson Perfection 1650 (Epson GT-8200),
# which has a product ID of 0x0110, would look as follows:
#
#usb 0x04b8 0x0110

"at your peril" gave me the idea to mask this line in epson.conf and epson2.conf so I wrote a few ###

Long story short, now it works!!

Problem may have been multiple .conf files in /etc/sane.de pointing at the same machine! No idea, but it works! Took me a year!

---

### Post by oldrocker99 on 2016-04-27
Thanks for showing how you solved the problem. Please mark this thread as [SOLVED], using Thread Tools at the top right.

---

### Post by syd2 on 2016-04-28
Hi There,

I am facing same issue with my pixma MG3640 while trying to configure with 14.04.

Usb is detecting as scanner(came to know this through sane-find-scanner)

But scanimage -L is empty. 

Seemingly canon is not providing any linux drivers for this at the moment. If you have any suggestion please let me know.

Thanks,

---

### Post by pedro_rodriguez2 on 2016-04-30
It's frustrating isn't it? Drove me crazy for a year!

Try setting the values of the Vendor ID and Product number from sane-find-scanner in /etc/sane.d/pixma.conf

You can get the Vendor ID and Product Number by entering lsusb in a termminal too! If it sees your scanner, they should show up!

You need to be root to do this. In a terminal 

sudo gedit

You will have to enter your admin password, that will open gedit as root. Open /etc/sane.d/pixma.conf or whatever .conf is for your scanner,then just enter this line anywhere. (All the other lines will be commented out with #). At the bottom is good. 

You need this format: usb YourVendorID   YourProductNumber The example below is mine:

usb 04b8 08a1



Of course, replace the 2 hexadecimal numbers with your Vendor ID and product number. See if xsane finds your scanner then.

This worked for me in 14.04, but not in 15.10 or 16.04. In 16.04, I put hash tags in front of everything, and it works! Figure that out!

---

### Post by yoshii on 2016-04-30
Wow i'm impressed with how you got it to work.  
I have a hardware scanner too (forget which brand) and it works in v14.04 without issues.  
I'm afraid to try it in v16 after experiencing and reading about some of these types of issues.  

There's no printer drivers for my hardware except for one crazy old long script written and it edits a lot of system folders so I never ran it.  

I just put stuff on flash drive and print from Windows at my local library.

---

### Post by pedro_rodriguez2 on 2016-05-01
I borrowed a friend's little Canon scanner, it's a flatbed usb powered scanner. Works in Ubuntu without any problem, no configuration at all. Plug it in, scan. They only cost about 300 RMB now here in China, say $ 50. My Epson multi machine was more sensitive, but it works now! I think these scanner printer machines can confuse the system.

Printer and scanner are not the same.

What does 

lsusb 

show on your system?

I have the old version of Ubu on 1 partition and the newer version on another partition. When I get 16.04 working correctly, I'll move to it completely.

---

### Post by syd2 on 2016-05-01
Hello pedro_rodriguez2,

Thanks for your detailed explanation and time taken to review this.

The same steps I tried here, pixma.conf is having same entries as there in lsusb.

========
root@SydLap:~# scanimage -V
scanimage (sane-backends) 1.0.26git; backend version 1.0.26




root@SydLap:~# sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x178a [MG3600 series]) at libusb:002:005
found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:002:002




root@SydLap:~# scanimage -L

No scanners were identified. If you were expecting something different....
===============================================

Dont know where I am doing wrong, this is 14.04 version and I dont see much help specific to my problem in common forums out there.

If anyone got a clue here on how to proceed, this would be appreciated deeply.

Thanks,

---

### Post by pedro_rodriguez2 on 2016-05-03
OK, try this, it can't do any harm:

In /etc/sane.d I have a file 

canon_dr.conf

It lists a lot of canon scanners. I don't see your one, but you can append it. Use gedit as root.

at the bottom, just add the data from sane-find-scanner:

# my crazy Canon scanner
usb 0x04a9 0x178a

See if that works!

---

### Post by syd2 on 2016-05-04
Hi,

Seems like I am unlucky, my crazy scanner is not at all detecting.

Funny part is I can see two lines with sane-find-scanner, the second one stays there evenif the scanner is not connected(as a history: I got sane-find-scanner catch my MG3640 only after a manual sane update using git)
======
found USB scanner (vendor=0x04a9 [Canon], product=0x178a [MG3600 series]) at libusb:002:005
found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:002:002


They say no driver roll out for linux, too bad if it is true. My customer has got a bad impression with linux already lol..
[http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg3640.aspx?type=drivers&language=EN&os=Linux%20%2832-bit%29](http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg3640.aspx?type=drivers&language=EN&os=Linux%20%2832-bit%29)

Anyway, thanks for your time, if you got anything further please post here. Meanwhile I will try other tips and will surely update here if I manage to get this working.

Thanks,

---

### Post by pedro_rodriguez2 on 2016-05-06
Have a look here for some more tips! I can't get the scanner to network, so I asked at linuxquestions, which pointed me back here for tips.

[http://www.linuxquestions.org/questions/showthread.php?p=5539288#post5539288](http://www.linuxquestions.org/questions/showthread.php?p=5539288#post5539288)

---

### Post by pedro_rodriguez2 on 2016-05-07
Look here as well if you have not got your scanner working, it may help you!

[https://feeding.cloud.geek.nz/posts/setting-up-a-network-scanner-using-sane/](https://feeding.cloud.geek.nz/posts/setting-up-a-network-scanner-using-sane/)

---

### Post by syd2 on 2016-05-15
Hi Pedro,

Thanks for the links, I am troubleshooting with scanner(I got it back only now hence the delay) and have you ever got any issue with scanimage detecting scanner?

From the urls provided, I can see that in your case you had scanner detection with scanimage command, I am yet to reach on that phase.

For me this is where I am stuck, I think it has to do with driver for the same. I have sane-find-scanner detecting properly, scanimage is falling with no scanner detection.

Since vendor is not providing any drivers, I have to check for the bypass methods like wine or ndiswrapper to make it work on linux, even tried with 16.04 but results are the same.

---

