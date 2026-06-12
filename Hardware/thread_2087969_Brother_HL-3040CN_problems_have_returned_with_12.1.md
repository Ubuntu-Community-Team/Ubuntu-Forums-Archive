---
title: "Brother HL-3040CN problems have returned with 12.10"
date: 2012-11-25
forum: Hardware
---

### Post by baybe1111 on 2012-11-25
[http://ubuntuforums.org/showthread.php?t=1602075&page=3](http://ubuntuforums.org/showthread.php?t=1602075&page=3) has many solutions to problems with this printer, however with 12.10 new problems have arisen.
I have tried all the solutions in the above post and the printer does not print. Network printing works fine for windows PC's as well as for Ubuntu 10.10 laptops and desktops sharing the printer, but one desktop running 12.10 will not work over network or USB connection. It is the only 12.10 machine.
The closest I can get is seeing the green data led on the printer flash when I send a test print to it over USB, but nothing else happens.
I provide free IT access for students, so don't have much money, so replacing the printer is not an option right now, as much as I'd like to because this Brother printer has always been a great big headache in Linux.
Any suggestions would be appreciated.

---

### Post by pdc on 2012-11-25
can we ask you what the command

> sudo dpkg -l | grep Brother

gives, if you copy and paste into a terminal: 

can you tell us if you are using 32bit or 64bit; 

the thread that you cite

[http://ubuntuforums.org/showthread.php?t=1602075](http://ubuntuforums.org/showthread.php?t=1602075)

gives post #6 as being successful, and the last entry (a month ago) that this works on 12.10 ...............

---

### Post by baybe1111 on 2012-12-03
Thank you for your reply.
I will update the referenced thread also.
I finally got this to work doing something very unscientific. 
After doing everything on [http://ubuntuforums.org/showthread.php?t=1602075&page=3](http://ubuntuforums.org/showthread.php?t=1602075&page=3) 
I went to Synaptic and searched for anything containing Brother
Installed all the packages.
Sent a test page, and Bingo- it works.
Not sure what did it, but one of those packages did.

Hope this helps someone who is unfortunate enough to own a Brother printer.

---

