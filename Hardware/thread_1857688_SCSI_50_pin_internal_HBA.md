---
title: "SCSI 50 pin internal HBA"
date: 2011-10-10
forum: Hardware
---

### Post by Fenderian_Mayhew on 2011-10-10
SOLVED Jumpers on tape drive was the solution. new problem diverted to [http://ubuntuforums.org/newthread.php?do=postthread&f=332](http://ubuntuforums.org/newthread.php?do=postthread&f=332)

Hey. I've got 2 SCSI controllers one is the AHA-2940u2w the other is the AHA-2940U. The u2w Does nothing on both my linux and windows XP system and the U causes a freeze at boot for linux but works fine on ubuntu.
 I am trying to find a good pci SCSI controller for use in a desktop system with my Tape drive (DDS3 Scsi). any recommendation or tips will be appreciated.
I cant find any helping info in the sea of "Windows XP Driver" websites and the only linux driver i can find is for 2.6 im running 2.8

---

### Post by Fenderian_Mayhew on 2011-10-13
Bump and update 
OK. the card which works under windows xp is a Compaq 185202-001 with the AHA-2940u s1 chip. 
I don't understand why this card Causes a Hang on boot for ubuntu 11.04 but it does. 
If anyone has used this card on ubuntu before please tell me which one and what you do.

---

### Post by Fenderian_Mayhew on 2011-11-13
Seccond Bump

The device seems to create boot errors in linux which prevents it from runing. However in windows it works without a hitch. does anyone know someone who made this model work in general. 

I plan to try hooking jumpers to the 2 points and re testing.

---

### Post by Fenderian_Mayhew on 2011-11-13
activating the jumper on the HBA seems to have granted access to the adapter. it lists as working in disk utility I still can't see the tape drive. will keep forums posted about progress

---

### Post by Fenderian_Mayhew on 2011-11-13
Okay pining the scsi drive as scsi0 causes a loop or fail at boot. going to find any documentation on the drive i can

---

