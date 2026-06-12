---
title: "Install error"
date: 2008-08-12
forum: General Help
---

### Post by Chondro_Biak on 2008-08-12
I am trying to install 8.10 on the computer I just built and I keep getting hung up... I can't seem to get past the cd check... I am installing the 64bit alternate... 
When I get to the cd devise check it is asking for me to install the date through a floppy drive (I do not have a floppy drive)... I have installed Ubuntu on about 25 different computers before and never had this issue, so I am going to assume this is Mother Board related?

My specs are as follows:

GIGABYTE GA-EP45-DS4P LGA 775 Intel P45 ATX Intel Motherboard
XFX PVT96GYDDU GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16
SAMSUNG SH-S223F DVD Burner
Intel Core 2 Duo E8500 Wolfdale 3.16GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
Kingston HyperX 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 KHX8500D2K2/2G


Any advise would be great...

---

### Post by Taxman415a on 2008-08-12
If 8.10 wasn't a typo, you should download 8.04 instead. 8.10 (Intrepid) hasn't been released yet and is only in testing stages. People don't really give support for the testing version since it's expected to have some brokenness and therefore people are mostly expected to be able to deal with that. Try [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346) if you do want to help out with the testing though.

But if that was just a typo and you have 7.10 or 8.04, can you copy down the specific error message you get? I can't understand what you mean by "asking for me to install the date through a floppy drive". If you don't want to reboot you should be able to get the message from ```
dmesg >dmesgfile
``` and then open that file up or from the /var/log/syslog file.

---

### Post by Mgiacchetti on 2008-08-12
I would download a new cd and test it md5 then run the junk and see what happens.  if you have a flash drive, you could *try* that

---

### Post by Chondro_Biak on 2008-08-12
Sorry, yes that was a typo... I am trying to install 8.04... Was typing to fast... 
I had to rety the install to get he error back... The error is preventing me from installing the OS, so there is nothing on the computer yet... 

The error reads:
Title of error in red letters says, Detect and Mount CDROM
Then is says:
No common CD rom drive was detected. You may need to load additional CD ROM drivers from a driver floppy. If you have such a floppy available now put it in the drive and continue. Otherwise you will be given the option to manually select CDROM modules. 
Load CDROM drivers from a driver floppy? Yes or No

And if I hit NO
Detect and mount installation that failed. Continue
Takes me back to installer main menu


On a side note, how do I install this on a flash drive... I bought one to do this a while back and never got around to it...

---

### Post by Chondro_Biak on 2008-08-12
On another side note

I have never installed a 64 bit version before, however the alternate does not like the other alternated I have seen... The other alternated I have seen you have the option to install in text mode... On the download I have it has the option for normal install... I have downloaded this from 4 different locations and they are all the same... Is that normal for the 64bit version? All the downloaded iso images say they are the alternate , when seen from he desktop

Main issue stilling being that I cant install past the CD ROM screen...

---

### Post by Taxman415a on 2008-08-12
Do you have another operating system on the computer? If so, you can use Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to install to either your hard drive or a USB flash drive without using your CD drive. Basically run Unetbootin and point it to the ISO you have downloaded and it will set up the boot process to boot from that ISO.

Then once you get your system installed it would be very nice to file a bug report for your hardware so that it can hopefully get fixed.

---

### Post by Chondro_Biak on 2008-08-12
I think I have identified the fix... I am going to test it out when I get off work and if it does fix the issue I will post the results as well as a bug report... 

I think I need to change the device to all_generic_ide

---

