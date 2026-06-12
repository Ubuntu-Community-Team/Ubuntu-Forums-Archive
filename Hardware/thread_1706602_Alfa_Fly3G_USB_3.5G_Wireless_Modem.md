---
title: "Alfa Fly3G USB 3.5G Wireless Modem"
date: 2011-03-14
forum: Hardware
---

### Post by DarellCraighead on 2011-03-14
I am new to Ubuntu (finally had enough of MS BS).  I have *almost* completed the installation of my laptop - but I am still short one device, my Alfa Fly3G Wireless USB Modem.

Alfa posts a Linux driver at:  [http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397](http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397) which I downloaded.

The file contained a .cpp file which I understand is supposed to be compiled - but it fails to compile with the following errors:

user@computer:~/Downloads/Linux$ g++ EP0_Switch_Utility.cpp 
/tmp/cc5azBg3.o: In function `main':
EP0_Switch_Utility.cpp:(.text+0x1e): undefined reference to `usb_init'
EP0_Switch_Utility.cpp:(.text+0x23): undefined reference to `usb_find_busses'
EP0_Switch_Utility.cpp:(.text+0x28): undefined reference to `usb_find_devices'
EP0_Switch_Utility.cpp:(.text+0x2d): undefined reference to `usb_get_busses'
EP0_Switch_Utility.cpp:(.text+0x13c): undefined reference to `usb_open'
EP0_Switch_Utility.cpp:(.text+0x1b4): undefined reference to `usb_control_msg'
EP0_Switch_Utility.cpp:(.text+0x1c4): undefined reference to `usb_close'
collect2: ld returned 1 exit status

I would *really* like to get this device working so I do not have to revert to, dare I say it, Windows.  Any help would be appreciated.

I am attaching the .cpp file renamed as .cpp.txt.

---

### Post by faz. on 2011-03-14
Try posting in the ["networking and wireless"]("http://ubuntuforums.org/forumdisplay.php?f=336") section, my problem got solved there pretty quick.

Good luck

---

### Post by DarellCraighead on 2011-03-14
Ok, solved this - evidently I did not have all the necessary compilers installed...  after installing "other" apps I was able to get beyond this point.  Still doesn't work, but I am going to start a thread in networking and wireless as suggested.

---

