---
title: "Getting things working on HP G5000 laptop"
date: 2009-12-12
forum: Hardware
---

### Post by GuitarJim1987 on 2009-12-12
Hello everybody

My brother has the HP G5000 Laptop and due to various issues regarding the recovery of windows vista I suggested switching over the ubuntu. I have the latest distro (9.10) installed now however I have a couple of issues. 

1) using proprietary drivers (downloaded using a now occupied wired connection) I cannot get the internal wireless card to connect to our wireless network at home. I haven't tried ndiswrapper just yet as I cannot find any unpacked drivers in order to obtain the appropriate .inf files.  

2) No sound - I haven't messed about with this too much as I can't connect to the internet in order to download any drivers.   Does anybody here have any advice they could give. I have searched these forums however I have not found anything but I think I'm searching for the wrong things as google was fruitless too... 

Please help! Many thanks

---

### Post by hansdown on 2009-12-12
Hi GuitarJim1987.

Take a look at this, and see if it helps.

[http://ubuntuforums.org/showthread.php?t=528618](http://ubuntuforums.org/showthread.php?t=528618)

You will need an internet connection to use.

---

### Post by GuitarJim1987 on 2009-12-12
Thanks hansdown, did see that but dismissed it as it's the wrong model laptop but with have a look through.

EDIT - ok so I am getting no luck with either ndiswrapper plus the vista drivers. Used cabextract to get the .inf file from the driver .exe but I get two messages saying "unable to confirm hardware present" and another saying "unable to locate network configuration tool".

EDIT2 - Had a go installing the Broadcom STA drivers however the computer just crashes almost straight after. On next boot in the drivers windows it states that they are "installed but not in use" and there is no wireless option in the network monitor applet. I have to get this working! I have seen others having no problems

---

### Post by GuitarJim1987 on 2009-12-12
Right I have now ascertained that the laptop has a Broadcom BCM4311 wireless adapter. I have followed all the advice here;[http://ubuntuforums.org/archive/index.php/t-1305906.html](http://ubuntuforums.org/archive/index.php/t-1305906.html), which still hasn't worked. Currently have fwcutter installed but not activated and the STA drivers are active but not running.

Getting a little frustrated now.

---

### Post by hansdown on 2009-12-12
Nice work GuitarJim1987.

Sorry for the link I posted.

If you don't get it working with 9.10, you can try installing 9.04, as it is supposed to work well.

---

### Post by GuitarJim1987 on 2009-12-13
Got it sorted. Turns out it was simply a case of ticking the box in the permission area of 'users and groups' that enables connection to wireless networks. For some reason 9.10 defaults as off so no wonder it was crashing and not letting me connect!

Everything is sorted now and up and running. Thanks for the help

---

### Post by hansdown on 2009-12-13
Glad you fixed it GuitarJim1987.

---

