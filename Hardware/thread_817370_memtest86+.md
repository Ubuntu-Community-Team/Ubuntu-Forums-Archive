---
title: "memtest86+"
date: 2008-06-03
forum: Hardware
---

### Post by dracule on 2008-06-03
I was having software issues, so someone suggested i do a memtest, so i did the ubuntu memtest thats on grub


so far it has found well over four million errors, and it is at 39%.



it is currently doing a "random number sequence"


it started at (this is under the failing address header)

Failing Address
-------------------

0000a5aa[some more numbers] 176.6MB


and ever since it has been returning error after error.

I do not know how to fix this at all.
any help?

---

### Post by nick_h on 2008-06-03
The obvious answer is to buy new memory to replace the faulty module.

How many modules do you have?  If you have more than one you could remove the one causing the problems.  Also it would be worth removing and replacing the modules - re-seating them might possibly cure a fault.

---

### Post by dracule on 2008-06-04
i reseated them, they passed the memtest the first 2 times, but when it rolled over a third time it got the errors again...



so how do i find the type of ram i have to buy?

---

### Post by Hero of Time on 2008-06-05
Does you computer have a good airflow? Memory needs to be cooled too, else it can produce errors. I can change my fan speeds and I had two modules that could show their temperature. When I ran Memtest, the first pass was ok, the second too but later it gave errors. I checked the temperature and it was above 55 C. When I turned up the fans (front intake and rear exhaust), Memtest ran for over 10 hours without any error. First thing to do is check your airflow. If you don't have a see-through panel to read the thermometer, you might want to open your case when you get errors and read it then. Of course, don't use any metal on the memory, as it might short.
With a see-through side panel, you can close your case and position the thermometer so you can read the temperature. There are different kinds of thermometers, so check the one that fits best. A laser readout is the safest, but can also be the most expensive.

---

### Post by dracule on 2008-06-09
checked and rechecked, even put a big box fan, but still crashes. 


what is a command so i know what type of ram to replace it with?

---

### Post by dracule on 2008-06-14
bump..

---

### Post by molochi on 2008-06-15
Do you know what motherboard your system uses? OR If your system is OEM built (HP, Alienware, whatever...) can you list the model and number?

---

### Post by dracule on 2008-06-17
it says hp pavilion 700 on the label by the SN

---

### Post by molochi on 2008-06-19
The HP Pavilion 700 is listed as using PC133 SDRAM, and as supporting up to (2) 256MB DIMMs. HP's bios setup will also list what is installed. I would double check in bios as later 7xx series used DDR.

---

### Post by dracule on 2008-06-19
ok, the bios says (512mb DDR)

so i will look for that i guess, hopefully for less than $50

---

### Post by nick_h on 2008-06-20
> what is a command so i know what type of ram to replace it with?
You can check it with the following command:
```
sudo lshw
```
Look for the memory section.

---

