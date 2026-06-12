---
title: "Fprint demo with authentec aes2501"
date: 2010-11-25
forum: Hardware
---

### Post by timbuktoo on 2010-11-25
hello Ubuntu Forums:
I need help with fprint demo. it is not recognizing the aes2501 biometric fingerprint reader on my HP laptop which I put lucid LTS on. it says that it cant open the device.

and while I'm at It I might as well ask how to set up fprint to unlock my laptop- either give a password OR scan a finger

thankyou in advance
-timbuktoo

---

### Post by humanoverdrive on 2011-07-14
run the program from the terminal with the command "sudo fprint_demo"
that should get the program to run and have your fingerprint driver recognized. when i try to access fprint from applications > accessories, it says that it "could not open device" referencing my fingerprint driver; however by running the program from the terminal with root privileges (sudo) it is magically able to open the device!

as for how to get ubuntu to let you use fprint to login to ubuntu, im still trying to figure that one out myself :/

---

