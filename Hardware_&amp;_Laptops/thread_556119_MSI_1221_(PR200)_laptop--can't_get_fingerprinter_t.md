---
title: "MSI 1221 (PR200) laptop--can't get fingerprinter to work"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by leptons on 2007-09-20
I've got a MSI 1221 laptop and on it there is a fingerprint sensor 

looking from the driver support website for this model:
[http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1208](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1208)

it seems to be a UPEK relating fingerprint sensor.

I tried to install thinkfinger. Struggled for a while and finally installed the program successfully. however, when I try to test and enroll a finger print using thinkfinger (3.0) it says no device found or something similar.

after giving up and coming back and googling once again, I try to follow the instruction on this website:
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

everything (bioapi and the driver) installed fine but however, when i run the sample program to enroll a fingerprint it gives:
BioAPI_ModuleLoad failed, BioAPI Error Code: 6477 (0x194d)

when I run lsusb, I get:
> 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0db0:a97a Micro Star International 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 147e:2016  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


is there any hope for me to have a working fingerprint sensor?

---

### Post by ceminino on 2007-09-21
it seems UPEK provides a Linux driver here [http://www.upek.com/support/dl_linux_bsp.asp](http://www.upek.com/support/dl_linux_bsp.asp) 
you should give it a try. I was planing to buy this laptop myself, any other issue with ubuntu? 



> **leptons said:**
> I've got a MSI 1221 laptop and on it there is a fingerprint sensor 

looking from the driver support website for this model:
[http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1208](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1208)

it seems to be a UPEK relating fingerprint sensor.

I tried to install thinkfinger. Struggled for a while and finally installed the program successfully. however, when I try to test and enroll a finger print using thinkfinger (3.0) it says no device found or something similar.

after giving up and coming back and googling once again, I try to follow the instruction on this website:
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

everything (bioapi and the driver) installed fine but however, when i run the sample program to enroll a fingerprint it gives:
BioAPI_ModuleLoad failed, BioAPI Error Code: 6477 (0x194d)

when I run lsusb, I get:


is there any hope for me to have a working fingerprint sensor?

---

### Post by 22bsti on 2007-09-22
i have this same laptop, as for ubuntu support, i wouldn't worry too much as this laptop is the same as a laptop sold by a prominent linux system builder that has thier support forum here.  From my personal expierence sound works video works the web cam works (though i have never used it so i cannot comment on that).  The system builder has a custom install disk thats just a modified ubuntu 7.04 desktop image.  From what i understand its just a regular disk with a kernel with better support for the intel video hardware but dont quote me on that.  I would have bought from them (the linux system builder) but i didnt see it till after i had already purchased the laptop on newegg (which isnt carried any more)


bottom line msi PR200 = darter ultra2 (unless im mistaken though they are nearly identical except for the optional mpci express tv tuner card)

hope this helps

---

### Post by ceminino on 2007-09-23
That's really good news, though the MSI web site only provides zindows drivers.  I just ordered it, I hope gutsy will come out before the laptop comes... What was nice is that I didn't have to pay for a zindows license! I also got the DVB-T tuner, any chance it will work on linux?

---

### Post by leptons on 2007-09-23
> **22bsti said:**
> i have this same laptop, as for ubuntu support, i wouldn't worry too much as this laptop is the same as a laptop sold by a prominent linux system builder that has thier support forum here.  From my personal expierence sound works video works the web cam works (though i have never used it so i cannot comment on that).  The system builder has a custom install disk thats just a modified ubuntu 7.04 desktop image.  From what i understand its just a regular disk with a kernel with better support for the intel video hardware but dont quote me on that.  I would have bought from them (the linux system builder) but i didnt see it till after i had already purchased the laptop on newegg (which isnt carried any more)


bottom line msi PR200 = darter ultra2 (unless im mistaken though they are nearly identical except for the optional mpci express tv tuner card)

hope this helps

really? the webcam works? I've trying to figure out how to get it work in Camorama...and nothing works so far...it seems that the webcam on this laptop is fairly common among other laptops (it's called bison something...it can be identified by the "1.3 MEGA PIXELS" at the bottom right corner and "DIGITAL CAMERA" at the top left corner)

also, is there anywhere that I can find out what the "modified ubuntu" is about? and perhaps get a hold of one of them?

---

### Post by dahlheim on 2007-09-25
while a little less than easy to use/integrate, the webcam definitely does work.  look here for more info on the uvc (usb video class) driver, and the program called videoview:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by 22bsti on 2007-09-27
by modified ubuntu disk image i mean that the disk is a modified ubuntu install image, it is designed specifically for Santa Rosa platform computers

---

