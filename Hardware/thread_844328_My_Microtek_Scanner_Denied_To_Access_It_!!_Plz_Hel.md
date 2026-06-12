---
title: "My Microtek Scanner Denied To Access It !! Plz Help"
date: 2008-06-29
forum: Hardware
---

### Post by dgkalmegh on 2008-06-29
:(HI FRIENDS  I AM NEW TO UBUNTU AND  I WANT TO USE MY SCANNER TO SCAN IMAGES

but when I start XSane Image scanner to SCAN images It says that  

    "FAILED TO OPEN DEVICE 'sm3840:libusb:004:002';
     Access to resource has been denied."



plz tell me the solution my scanner is " [COLOR="DarkRed"]MICROTEK  ScanMaker 3840[/COLOR] "

---

### Post by flytripper on 2008-06-29
i believe access to scanners is denied by default.. lemme see if i can find you a fix

---

### Post by flytripper on 2008-06-29
system>admin>users and groups

unlock it and manage groups. then click scanner and check your username where you should find it unchecked.

---

### Post by dgkalmegh on 2008-07-02
thanks friend !!I tried that bt it still giving me that message!

---

### Post by dgkalmegh on 2008-07-04
help me

---

### Post by Gene_s on 2008-07-13
I did this...unlock, etc. and my old Scanmaster 4800 came to life!!

thanks

---

### Post by Gene_s on 2008-08-03
well, now it does not work...still the same denied error...

there was no place to "check username" in the above instructions

---

### Post by elmu.edana on 2008-12-23
I had the same problem and I could solve it by following the instructions given here:

[http://ubuntuforums.org/showthread.php?t=669135](http://ubuntuforums.org/showthread.php?t=669135)

(Of course you have to copy the downloaded file into the folder usr/lib/sane, and you have to do this as root or with sudo)

---

