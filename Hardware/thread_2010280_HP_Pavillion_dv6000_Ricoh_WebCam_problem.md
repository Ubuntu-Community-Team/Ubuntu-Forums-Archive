---
title: "HP Pavillion dv6000 Ricoh WebCam problem"
date: 2012-06-25
forum: Hardware
---

### Post by salmanmanekia on 2012-06-25
Hi All,

I am new to Linux and today installed the Ubuntu on my HP Pavillion  dv6000 machine. The in built HP webcam is not working for me. I have  tried to follow this forum and googled a bit for this too. I have seen  then this problem is quite persitant and many people have had webcam  problems with ricoh and HP. After going through all the details and  trying a few of it i am still unsuccesful. Here are the relevant  details. 
>> lsusb -v
 idVendor           0x05ca Ricoh Co., Ltd
 idProduct          0x1870 Webcam 1000

I have also tried [ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb") from [http://download.tuxfamily.org/arakhn...webcam-r5u870/]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/")
but to no success..

Thanks !

---

### Post by Redblade20XX on 2012-06-25
Is your user in the video group? If you are and still have no results, try manually compiling the module by following the instructions on the site you've given.  -Red

---

### Post by madjr on 2012-06-25
how did you test your webcam ?

you can try cheese.

[http://www.liberiangeek.net/2011/10/use-your-webcam-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/use-your-webcam-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by salmanmanekia on 2012-06-26
Cheese says no device found ...

---

### Post by salmanmanekia on 2012-06-26
> Is your user in the video group?
I do not know that. How to check that ?

> If you are and still have no results,  try manually compiling the module by following the instructions on the  site you've given
I tried by following the instruction on the website but still no results..Not working.

---

### Post by Redblade20XX on 2012-06-26
> **salmanmanekia said:**
> I do not know that. How to check that ?


I tried by following the instruction on the website but still no results..Not working.

In the terminal type,
```
groups
```

-Red

---

### Post by salmanmanekia on 2012-07-01
Sorry for the late reply. But here it is. 

muhammad@muhammad-HP-Pavilion-dv6000-EY798AV-ABA:~$ groups
muhammad adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by madjr on 2012-07-02
> **salmanmanekia said:**
> Sorry for the late reply. But here it is. 

muhammad@muhammad-HP-Pavilion-dv6000-EY798AV-ABA:~$ groups
muhammad adm cdrom sudo dip plugdev lpadmin sambashare


I have an HP g4 , cam was detected right away.

however a year ago it didnt work correctly, but the linux kernel team keeps adding new hardware compatibility every 6 months. I temporarily used an external usb cam for a while or logged back to windows 2 or 3 times to video chat.

maybe a good idea to try/test the new development releases of ubuntu (currently I believe is 12.10 alpha2) in an usb drive.


And just to be certain, I hope to purchase my next laptop with linux or [ubuntu pre-installed]("http://www.omgubuntu.co.uk/category/hardware-2"). This is why apple only sells mac OS pre-installed , they have much less drivers than linux.

---

### Post by salmanmanekia on 2012-07-03
I already have the latest one i.e 12.04 LTS from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by madjr on 2012-07-03
> **salmanmanekia said:**
> I already have the latest one i.e 12.04 LTS from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

That's the latest stable long term support (LTS) release.

we test new development releases here:

[http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416)

and this is new dev release announcement:

[http://www.phoronix.com/scan.php?page=news_item&px=MTEyOTM](http://www.phoronix.com/scan.php?page=news_item&px=MTEyOTM)

or

[http://ubuntuforums.org/showthread.php?t=2012192](http://ubuntuforums.org/showthread.php?t=2012192)


which we usually test in usb keys and which anyone can pitch in and report issues.

Remember that all this is open source and anyone is welcome to contribute in any way they want. ;)

---

### Post by Redblade20XX on 2012-07-03
Try this,
```
 sudo adduser <user_name> video
```where <user_name> is your user name.
Now see if cheese detects the camera again.

-Red

---

### Post by salmanmanekia on 2012-07-04
> **Redblade20XX said:**
> Try this,
```
 sudo adduser <user_name> video
```where <user_name> is your user name.
Now see if cheese detects the camera again.

-Red
No, still  "No device found "

---

