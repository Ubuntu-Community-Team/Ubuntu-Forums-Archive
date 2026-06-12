---
title: "Trouble installing kubuntu on HP  Pavilion dv 4000"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by sunch1ld on 2007-07-17
Hi, I have downloaded kubutu 7.04 i386. I boot the live cd to intall the operating system. I select the option to install the operating system using graphic interface. When the graphic start the screen is white. My screen is an lcd 1280x800. My labtop is an HP Pavilion dv 4000. What I have to do see the graphical interface? I have tried also with the  safe mode but the result is that nothing start. Thanks

---

### Post by omair.majid on 2007-08-29
I can confirm. I am having the same problem on my pavillion dv4394. ( with an ATI mobility radeon x700 )

Dapper used to run ok. wanting to do some KDE4 development, i tried installing feisty. I got the Kubuntu boot up screen, but then instead of the login screen/desktop, i got a white screen. The same thing happened in safe graphics mode.

---

### Post by omair.majid on 2007-08-30
I got kubuntu fiesty working today with my ati mobility radeon x700 so i thought i would share my thoughts. I knew I had dapper working so i did a dapper install and upgraded to edgy and then fiesty. on restarting my computer after upgrading to fiesty, X refused to start. Since i knew that my Xorg.conf file was not wrong, i thought the problem must be the driver. Xorg wont start with vesa either. Then i found that Xorg offered the fglrx - ati open source drivers. so i changed to that and it started working fine.

in summary, you probably want to switch to the fglrx drivers instead of vesa or ati.

after you boot up and get the white screen, switch to a console by using ctrl+shift+f1. open up /etc/X11/xorg.conf (as root) and in the Device section replace the Driver, "ati" or "vesa" with "fglrx" and it should work. good luck!

---

