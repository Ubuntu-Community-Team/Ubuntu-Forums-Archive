---
title: "problem with mustek bearpaw 1200cu"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by linux_luke on 2007-12-26
i  have the mustek bearpaw 1200cu that used to work under gutsy
and no matter what i do wont work now

i changed a motherboard a few weeks ago (unrelated i know)
cuz it had a problem, i had gutsy installed and everything worked including the scanner
i did a fresh install and the only thing that was diffrent was the kernel that changed after the new install
from 386 to general i changed that to try and  didnt work
i added the driver from the site and when that didnt work i took it from windows install
the error that i get is:
failed to open device gt68xx:libusb:001:021: invalid argument
when i type scanimage -L the output is
device `gt68xx:libusb:001:021' is a Mustek BearPaw 1200 CU flatbed scanner

under hardware information it's not registerd
anybody have a solution?

---

### Post by linux_luke on 2007-12-31
i read in some post that the firmware test causing problems like i have
does anybody know how to disable that test?

---

### Post by i-Buntu-2 on 2008-01-07
Hi,

I've been having the same problem too and I resolved it by issuing the following command as root (sudo)

chmod a+r /usr/share/sane/gt68xx/PS1Dfw.usb

Replace the PS1Dfw.usb with the name of your firmware file

Hope this works

---

### Post by afeasfaerw23231233 on 2008-01-11
i have exactly the same problem! i newly connect my bearpaw 1200 cu scanner and click applications - graphics - xsane and this appear "failed to open device 'gt68xx:libusb:001:005" invalid argument. and here is what scanimage -L shows: device `gt68xx:libusb:001:005' is a Mustek BearPaw 1200 CU flatbed scanner
please help. bump
> **i-Buntu-2 said:**
> Hi,

I've been having the same problem too and I resolved it by issuing the following command as root (sudo)

chmod a+r /usr/share/sane/gt68xx/PS1Dfw.usb

Replace the PS1Dfw.usb with the name of your firmware file

Hope this works

where to find that firmware file? my  /usr/share/sane/gt68xx/ folder is empty
i check mustek bearpaw's website and no linux driver is available

EDIT: i get that PS1Dfw.usb from this site [http://meier-geinitz.de/sane/gt68xx-backend/](http://meier-geinitz.de/sane/gt68xx-backend/)
copy it to /usr/share/sane/gt68xx/ folder, sudo chmod a+r /usr/share/sane/gt68xx/PS1Dfw.usb but error still appears

---

### Post by afeasfaerw23231233 on 2008-01-12
i get my problem solved. i type scanimage in terminal and it said /usr/share/sane/gt68xx/ps1fw.usb file not found [not PS1Dfw.usb] so i go to this site [http://meier-geinitz.de/sane/gt68xx-backend/](http://meier-geinitz.de/sane/gt68xx-backend/) again and download ps1fw.usb, copy it to /usr/share/sane/gt68xx/ folder, then sudo chmod a+r /usr/share/sane/gt68xx/ps1fw.usb. and xsane work fine! but according to that site only 8 and 12-bit work in this driver ps1fw.usb, but all resolutions work in PS1Dfw.usb .[isn't my scanner capable for 48-bit?] but anyway 8-bit colour is enough for me now. anybody sees this help can download the driver from that site or here. [ps1fw.usb works in my case]

---

### Post by linux_luke on 2008-01-18
i tried the command and already got the firmware
and still got that error when i click on the xsane
itr waits a little bit and than gives me the error
so i think the test thingie fails does anybody know how to cancel that test?
or any other ideas?

---

### Post by AJB2K3 on 2008-01-19
Help I too also have this problem

---

### Post by eel on 2008-04-10
thanks, it worked for me
i allso would like to announce that for the first time i managed to move a file as sudo from terminal rigth at the first try. I normally mess up somewhere in the spelling or i forget to write sudo but on this memorable day i just pulled it of at once. hurray! 

As a celebration gift i wish you all flawless os-es (well not too flawless that wouldn't be much fun)

---

