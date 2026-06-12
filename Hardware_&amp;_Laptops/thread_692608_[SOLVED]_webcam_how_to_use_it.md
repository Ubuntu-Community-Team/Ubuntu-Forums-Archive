---
title: "[SOLVED] webcam how to use it"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by rudedcam on 2008-02-09
I have a built in webcam in my laptop and i cannot (don't know how to setup) use it.
I've been to this documentation [https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")
without success:
I've insatalled **camorama**. when i try to start the program it gives me this
> Could not connect to video device (/dev/video0).
Please check connection.

I've also installed **xawtv** but when i click on it, nothing at all happens.

obviously amsn tells me there's no webcam connected.

can anybody help?

---

### Post by cdtech on 2008-02-10
What laptop are you using?

Please display the results:
```
lsusb
```

Thanks

---

### Post by moephan on 2008-02-10
I have used a program called "cheese" with good success. However, on some laptops the web cam is initially turned off in the bios, I think to save battery power or something.So you might want to check the bios settings to make sure the camera is on. 

Cheers, Rick

---

### Post by rudedcam on 2008-02-10
```
lsusb
Bus 005 Device 004: ID 0db0:6877 Micro Star International 
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
```

i  have a  [MSI VR600]("http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1119")

I'll check in the bios if i can find anything, I'll update soon

---

### Post by vivalant on 2008-02-10
Rudedcamk, try the Generic SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) . That driver will work with the mentioned applications

---

### Post by chavanak on 2008-02-10
Even am not able to use my webcam. Am having a hp dv6602au lappie.
The output of lsusb is as follows:

Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



Any suggestions??

---

### Post by rudedcam on 2008-02-10
i have installed "trial generic SN9CXXX" (for gutsy) (the driver for feisty had unsatisfied dependency) and it is unfortunately not working.

i've been into the bios but couldn't see anything that look like a webcam. anyhow, nothing at all was disable or "off". i could post a couple of pics to show how it looks if you'd like moephan. just ask me if you think it's relevant.

if we can fix this, i'll add a funny avatar taken from the webcam to my profile :lolflag:

---

### Post by intel on 2008-02-11
Microdia 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam

0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 
All of the above webcams are unsupported under Linux

[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

Please join this Group, to help each other get better support for these webcams from Linux.

---

### Post by rudedcam on 2008-02-12
```
lsusb
Bus 005 Device 004: ID 0db0:6877 Micro Star International 
[COLOR="Red"]Bus 005 Device 003: ID 0c45:624f Microdia [/COLOR]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
```

does that mean i'm f***ed and bounded to windows for ever???

I'll check the link, thanks intel

---

### Post by vivalant on 2008-02-12
Rudedcam, note that SN9CXXX driver for Gutsy is a trial version and might be expired. Please do "dmesg" to see what happens with your driver/webcam. It works without problems on my laptop with the same camera, although I have bought the unlimited-time version.

---

### Post by rudedcam on 2008-02-13
i haven't realised how complicated linux could get.

SN9CXXX i installed was in fact the limited version (allowed to be working one day out of 2). today is the day the driver is allowed to work....
[[img]http://img2.freeimagehosting.net/uploads/th.2ee7d95924.jpg[/img]](http://img2.freeimagehosting.net/image.php?2ee7d95924.jpg)

to have an unlimitted version to see myself upside down everyday of the week i'd have to pay "per request"
> if you ask or want
the time unlimited version of the SN9CXXX driver N times, you will
have to contribute N times. No updates, no bug-fix releases will
be sent to you. Once again, you will only receive a single, time unlimited
release of the SN9CXXX driver corresponding to the trial version that
you have tested. Nothing more. 


this is why i have a doal boot with windows on it.

thanks everybody for all the help

---

### Post by vivalant on 2008-02-13
Rudedcam, I posted a comment about this matter sometime ago:

[http://ubuntuforums.org/showthread.php?t=681051](http://ubuntuforums.org/showthread.php?t=681051)

(By the way, your video seems upside down, you may want to use the vflip=1 module parameter to fix the problem. It works for me)

---

### Post by rudedcam on 2008-02-13
> use the vflip=1 module parameter to fix the problem
what is and where is the "module parameter"?
how do i get to it?

thx

can we ask ubuntu to create a driver for that somewhere on their todo list?

---

### Post by vivalant on 2008-02-13
Rudedcam, to fix the upside-down image issue, open a terminal and do:

sudo echo "options sn9cxxx vflip=1" >> /etc/modprobe.d/options

and reboot.

I do prefer paying my 5 euros for the existing driver than waiting for other two years or buy other external webcams. I made my request for collecting the money for the driver but the powers behind Ubuntu do not seem to be interested enough.

---

### Post by rudedcam on 2008-02-15
vivalant, excuse my ignorance but i do not know how to use the last instruction you gave me.

...i used the terminal:
```
 sudo echo "options sn9cxxx vflip=1" >> /etc/modprobe.d/options
bash: /etc/modprobe.d/options: Permission denied

```
then still in the terminal:
```
sudo echo "options sn9cxxx vflip=1" 
[sudo] password for rudecam:
options sn9cxxx vflip=1

```

so i went into the text file at /etc/modprobe.d/options
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
```
and i am not sure what to do.

i'm sorry once again, i wish i could be more knowlegable of linux.
thanks

---

### Post by vivalant on 2008-02-15
Rudedcam, do this instead of the previous command (be careful with ' and "):

sudo sh -c 'echo "options sn9cxxx vflip=1" >> /etc/modprobe.d/options'

---

### Post by rudedcam on 2008-02-16
hell yeah! it does work now:)

thanks alot for the help:D

---

