---
title: "Can't get my Android Phone recognized by Ubuntu 12.04.3 (Precise)"
date: 2013-11-11
forum: Hardware
---

### Post by Bill Dubinski on 2013-11-11
Good Evening, thank you in advance for your time and helping me with my question/solution. 

  I recently upgraded from Ububtu 10.04 LTS to 12.04 LTS. When I was  using 10.04, I was able to plug in my Android Phone and Lucid would  instantly recognize I had plug it in and was able to read off my SD  card. This is not the case in Precise as it was in Lucid. Precise does  not recognize my phone/SD card at all. 


  Does anybody have a solution(s) for this issue? 


  My phone information is a Samsung Model SPH M820 BST 
Android Version 2.3.6 
Kernel Version 2.6.35.7 
Build Number GINGERBREAD FF19


  This can not be an issue with the phone its self, cause as I still  have Lucid installed on one of my HDD's in my computer, if I boot up in  Lucid, plug the phone into the USB cable as usual, the phone would ask  me if I want to charge or Mass storage, I choose Mass storage like usual  and Lucid still recognizes it like usual. But not Precise. Phone asks  me "charge" or "mass storage" I choose mass storage and nothing. It is  not listed under the "Places" tab as it was in Lucid as I am using  (GNOME Fallback) in Precise and the drive is not located in the  "computer" folder either. 

  Any suggestions/solutions would be GREATLY appreciated. Again, than you all for your time and your work you do here. 
  
Thanks, Bill

---

### Post by Bill Dubinski on 2013-11-12
As an update to my question/problem. I have narrowed this issue to some issue between the relationship between Ubuntu and Android. Since I found my mini SD card to USB reader, I unmounted my SD card from my phone, inserted it into my SD to USB reader, inserted it into my computer and a dialog box pops up asking me "what I want to do". There I am able to access the file system. It is not a major issue, but plugging in the phone sounds much easier and since it worked in 10.04 (Lucid), it should be the same prosedure in 12.04 (Precise), I would think. 

With the SD card in my phone and with it plugged in, I can't even access it using gMTP or another app of the like, Ive tried two. It sinply as if is not even plugged in. 

Does anybody get this?

---

### Post by Bill Dubinski on 2013-11-13
This is my terminal output when striking the code lsusb into the terminal

$ lsusb
Bus 001 Device 012: ID 04e8:f000 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 002: ID 04a9:174e Canon, Inc. 
Bus 002 Device 003: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 015: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 014: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

Entry one, It reads the phone is connested, but can not see it under "Places" or in any disk utility.

---

### Post by Bill Dubinski on 2013-11-13
Okay, another update to my issue which is more frustrating. My wife has a laptop also running Ubuntu 12.04, hook my phone to her laptop, same issue as my desktop. Hook HER Motorola phone running Android Version 2.3.5 (older than mine) and Kernel number 2.6.32.9 (also older than mine) to HER laptop running 12.04 and it pops up with a dialog box asking "what do you want to do". Very interesting! Take her phone over to my desktop, plug it in, it does not ask me "what I want to do" but atleast it lists it under the "Places" tab in GNOME and I have access to her SD card through my computer, but I can not access my Samsung's external SC card to my own computer. 

If anybody understands what is going on, I would be greatly appreciative. 

Thank you!

---

### Post by Bucky Ball on 2013-11-14
***Thread closed.***

Duplicate here: [http://ubuntuforums.org/showthread.php?t=2187824&p=12847462#post12847462](http://ubuntuforums.org/showthread.php?t=2187824&p=12847462#post12847462)

---

