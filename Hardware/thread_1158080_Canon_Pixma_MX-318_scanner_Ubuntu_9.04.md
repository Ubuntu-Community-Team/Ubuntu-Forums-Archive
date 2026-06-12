---
title: "Canon Pixma MX-318 scanner /Ubuntu 9.04"
date: 2009-05-13
forum: Hardware
---

### Post by sakusa on 2009-05-13
Ubuntu 9.04 doesn't seem to support this Canon model, so I rolled back to 8.04, followed the instructions at
 [http://www.linuxfoundation.org/en/OpenPrinting/Database/DriverPackages](http://www.linuxfoundation.org/en/OpenPrinting/Database/DriverPackages)
got the recommended x86 32bit (DEB for LSB3.2) Gutenprint driver package and used the Canon MP 180 option. Having got the printer working , I've upgraded back to 9.04.

But the scanner doesn't even show up (unfortunately, I forgot to test whether the scanner was recognized after the rollback to 8.04). 

Now, based on a similar thread I came across, I tried :
                                 ~$ sane-find-scanner 
  
   # sane-find-scanner will now attempt to detect your scanner. If the 
   # result is different from what you expected, first make sure your 
   # scanner is powered up and properly connected to your computer. 
  
   # No SCSI scanners found. If you expected something different, make sure that 
   # you have loaded a kernel SCSI driver for your SCSI adapter. 
  
 found USB scanner (vendor=0x04a9, product=0x1728) at libusb:001:006 
   # Your USB scanner was (probably) detected. It may or may not be supported by 
   # SANE. Try scanimage -L and read the backend's manpage. 
  
   # Not checking for parallel port scanners. 
  
   # Most Scanners connected to the parallel port or other proprietary ports 
   # can't be detected by this program. 
  
   # You may want to run this program as root to find all devices. Once you 
   # found the scanner devices, be sure to adjust access permissions as 
   # necessary. 
 
So, I tried 
                                 $ sudo scanimage -L 
   
 No scanners were identified. If you were expecting something different, 
 check that the scanner is plugged in, turned on and detected by the 
 sane-find-scanner tool (if appropriate). Please read the documentation 
 which came with this software (README, FAQ, manpages). 
                                   

$ scanimage -L 
  
 No scanners were identified. If you were expecting something different, 
 check that the scanner is plugged in, turned on and detected by the 
 sane-find-scanner tool (if appropriate). Please read the documentation 
 which came with this software (README, FAQ, manpages). 
 
Could somebody please help on what my next steps should be?
Thanks in advance
sakusa

---

### Post by sakusa on 2010-03-21
Thankfully, this problem went away with the upgrade to Ubuntu 9.10! The same scanner worked quite easily without any fiddling, so here's a big thank you to whoever took the trouble to fix this hassle!

---

