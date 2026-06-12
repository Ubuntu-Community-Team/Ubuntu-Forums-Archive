---
title: "[SOLVED] AMD SB600 and Raid 0"
date: 2008-07-23
forum: Hardware
---

### Post by D4rkn3ss on 2008-07-23
Hello to all,

I have a problem in making ubuntu (latest version) working on a raid 0 setup.
In bios level the raid works correctly but when i try to install ubuntu it "breaks" the raid configuration and ask me to install the operating system on one of the two HDD's.

Here is my system's hardware:
AMD Phenom 9600
Gigabyte GA-MA 790FX-DQ6
North Bridge: AMD 790FX 
South Bridge: AMD SB600 
Realtek 8111B/8168B chip (10/100/1000 Mbit) 
2GB RAM
GeCube Ati HD 3780 512mb


I suppose some drivers has to be installed during setup in order for the linux installation to detect the raid configuration correctly. 
Could you help(with simple steps as i am new to the linux world)?
Also is there a problem with any other hardware of the computer that i should know?

---

### Post by D4rkn3ss on 2008-07-23
OK i found a solution to my problem.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

