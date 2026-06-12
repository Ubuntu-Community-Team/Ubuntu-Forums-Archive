---
title: "Nvidia card, things gone bad"
date: 2009-03-17
forum: Hardware
---

### Post by hhappak on 2009-03-17
Well, I am not an expert in Linux and thats probably why things gone bad. I tried to install the 180.22 nvidia driver for my 8600GT card from the Nvidia website. It didnt work... I got a black screen with a message to tell me that no video card was detected and that I have to recofigure the resolution settings. Once logged, all compiz effects are down and the nvidia settings give me an error message that I am not using an X-driver. now I tried to install the restricted driver back, but the same black screen with the error message appear, and when I reopened the restricted drivers, it told me that another version of the driver is in use. I did remove the drivers for nvidia in hope that I can reinstall the restricted drivers back...But now I cant even find any restricted drivers :S Plz help me fix this mess and return back to what things were.

---

### Post by Claus7 on 2009-03-17
Hello,

if your screen resolution goes down the command you should use is:

sudo dpkg-reconfigure -phigh xserver-xorg

Regards!

---

### Post by hhappak on 2009-03-17
Thanx, but the problem goes beyond that now. The system does not recognise my card, niether does nvidia settings. Also there are no drivers in the restricted drivers for me anymore which I cant really explain how it happened :S

---

### Post by Claus7 on 2009-03-17
Hello,

does this link help you?
[http://ubuntuforums.org/archive/index.php/t-1056531.html](http://ubuntuforums.org/archive/index.php/t-1056531.html)

Regards!

---

### Post by hhappak on 2009-03-17
From bad to worse :S Thanx for the link, it describes exactly my problem. But something must have gone bad during the procedure, and now I cant even log to Ubuntu. I just get stuck at a black screen. Is there anyway I can even log using command lines only so that I can fix things back up?

---

### Post by Claus7 on 2009-03-17
Hello,

can you see grub menu and choose to enter in recovery mode? 
Also I do not remember if you can fix anything from ubuntu cd. I hope that you have a backup of your system. In case you do not, I would go to live cd, mount an external hdd and move all my data there. 
Also if you are able to have access to a terminal the command startx would not be a bad idea. Other than that I think that you are not many steps away from reinstalling. This is all I can tell you.

Good luck,
Regards!

---

### Post by hhappak on 2009-03-18
Thanx alot for the help I really appreciate it. I finally managed to get my system back up, and with the graphic card accelerated. The only problem left now is that compiz wont allow me to set the effects to extra. It keep giving me an error message "Desktop effects could not be enabled". I wonder if the graphic card is really accelerated now, but nvidia settings is responding correctly though.

---

### Post by Claus7 on 2009-03-18
Hello,

you are welcome. What I would suggest you is:
i)to post exactly the errors you have so as to be able to help you more efficiently. Now, with the last error you get, just a little search revealed this:
[http://ubuntuforums.org/showthread.php?t=582207](http://ubuntuforums.org/showthread.php?t=582207)
it is a long thread so you should have a lot of reading.

ii) it would be nice to explain the steps that you took to solve your problems. That way others that faced or might face the same or similar problem will be able to find a descent solution. 

Glad that things are working nicely,
Regards!

---

