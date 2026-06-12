---
title: "Canon Imageclass mf244dw Scanner not working"
date: 2017-05-11
forum: Hardware
---

### Post by jcg-computertech on 2017-05-11
I know there is no driver support for this all-in-one. I have connected it manually for the Printer and I have both the USB and wireless printing working in 16.04 using PCL 6, the printer works great, but I cannot get the scanner working. I am a bit of a noob when it comes to Linux so I guess I am missing something.

Here is what I get when I run sudo sane-find-scanner
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


[SIZE=5]_**found USB scanner (vendor=0x04a9 [Language Error], product=0x27d2 [Language Error]) at libusb:003:002**_[/SIZE]
found USB scanner (vendor=0x1415 [OmniVision Technologies, Inc.], product=0x2000 [USB Camera-B4.09.24.1]) at libusb:002:003
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x1bad [Mad Catz, Inc.], product=0xf027 [Mad Catz FPS Pro GamePad]) at libusb:008:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


So then I tried sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

of course xsane doesn't find any scanner and neither does simple scan

As near as I can tell this scanner is just not supported by sane on the backend and that is the reason the usb port says language error.

Any help would be much appreciated.

---

### Post by pdc on 2017-05-11
so this doesn't yet appear on the SANE list of printers: 

I would suggest you join the sane development mailing list; [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel) they are a very friendly and helpful group; so many similar devices are listed and fully supported; your lsusb says ```
04a9:27d2
``` so one would hope it is just a question of adding that ID to a config file somewhere; they would be the best ones to tell you what to do; 

but as you have the hardware, you may well be able to help them by running some stuff for them; so two-way helpful; 

______________

you can see on the standard SANE page [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) how many Canon devices are completely supported; and for others, they only need testers so we hope you can get this resolved; please let us know how it goes

you have done very well to get it printing well with PCL 6

---

### Post by jcg-computertech on 2017-05-14
Thank You for your help.

I have signed up and am waiting for a response from them to continue.

I will make a quick mention to anyone reading this post that I do have a better way for the printer now. I have downloaded the basic driver file for linux from Canon's website and it seems to me that all printers that are supported by canon are in this one file called 
[COLOR=#000000][FONT=&quot]UFR II/UFRII LT Printer Driver for Linux V3.31
after downloading I extracted and ran 2 cups .deb files for 64bit called
[/FONT][/COLOR]cndrvcups-common_3.71-1_amd64
cndrvcups-ufr2-us_3.31-1_amd64
after doing this I went back to printers and installed a new one, and on the list of printers was
Canon MF240 Series UFRII LT CNUS for USB or (IP address) for Network
and those were not in the list before. After selecting one of those options the default is to use a Generic driver but that will not work so I picked Canon and the printer MF220, which googled is actually called a
LBP151dw. This printer looks a lot like my all-in-one, just missing the scanner (probably has very similar guts inside). My printer is working both USB and wireless with this driver and the pages come out just a touch clearer, hard to notice but if you print something in color the gray shade that gets printed is clearer and less pixelated than with the PCL 6 driver.

Just got to get the scanner going and hopefully with any luck, get it working with wireless.

---

