---
title: "updated to 8.10 and have no video drivers"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by LuckyLuck on 2009-03-12
hi< Nowice talk>>>

I updated from 8.04 to 8.10 thorough update manager...

after restarting system is not detecting VIDEO CARD...

I have laptop VAIO pcg-z1rmp
everything was cool before update to 8.10

-------------------------------------
but now i have small 
screen 8inch cross with 800x600 resolution
WITH BLACK 2inch frame AROUND(nice but) 

 should be
screen 14inch cross with 1400x... resolution...
---------------------------------------------

when I go to 
system->Administration->Hardware Drivers - IS NOTHING THERE

I TRYED
sudo dpkg-reconfigure xserver-xorg

BUT IS NOT WORKING TO...

i tryed
sudo displayconfig-gtk

BUT IS SAYING ME
sudo: displayconfig-gtk: command not found

what can i do

HELP ME PLEASE?

---

### Post by Neo_The_User on 2009-03-12
if you had no video drivers, you'd be in command line right now.

do glxinfo in the terminal and post the entire thing here.

---

### Post by LuckyLuck on 2009-03-12
i put

$ glxinfo

and get back:
-------------

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

-------------

everythin was working nice before updating to 8.10

there was drivers....

---

### Post by IsmailBhai on 2009-03-12
ubuntu 8.10 gives alot of video problems.  the solution is to get a good xorg file. if you didnt save your xorg before updating, try to find someone with the same video card and screen resolution.  you can add the modes yourself in xorg and restart.

---

### Post by LuckyLuck on 2009-03-12
you can add the modes yourself in 
xorg
-----

can you direct me how, please
any hint
what is 
xorg...

sorry but Im no terminal femiliar...
in terminal i just know to put password when is asking-)))

and I will try to go to your link- THANK YOU VERY MUCH...

---

### Post by LuckyLuck on 2009-03-13
is done!!!

i,m not sure how...

I tryed few command from internet but was snowing is stuck on 2nd-3rd step of 6...

but when I restarted my resolution is back OK!-)

now looks so huge-) because i had only 8inch srean and I was feeling like lookind behind someone shouldere on his computer...

NOW WORKS!

sorry but i,m not sute how...

just need to restart after some commands of intaling new Xorg file...
even when was showing that instalation FAILD...

thank you anyway-)))

I wanted to go for openSUSE or MINT... to fix problem ...but is OK now...

and by the way i foun web how to fix the same problem...

[http://www.linuxquestions.org/questions/linux-hardware-18/installing-ati-9550-driver-ubuntu-8.10-intrepid-708370/](http://www.linuxquestions.org/questions/linux-hardware-18/installing-ati-9550-driver-ubuntu-8.10-intrepid-708370/)

GOOD LUCK-)))

---

### Post by LuckyLuck on 2009-03-13
IT WAS MY FIRST POST

and I'm not sure how to 
MARK QUESTION AS RESOLWED
should be in options on top- but I can not see...

any tip?

THX

OR WHICH POST ICON TO CHOSE TO MARK AS RESOLVED...

---

### Post by LuckyLuck on 2009-03-14
I think I FOUND The PROBLEM!!!

MY CARD STARTED TO BE regcognised and work properly
after I removed- UNISTSLLED from
Application->
Add Remowe
+++++++++++++++++++++++++++++++++

''ATI Catalyst Control Center''

+++++++++++++++++++++++++++++++
and RESTARTED system...

DO NOT INSTAL IT BACK
----------------------

IT WILL FREAK OUT SYSTEM AGAIN,
 AND WILL NOT SEE YOUR VIDEO CARD AGAIN

Good LUCK-)

---

