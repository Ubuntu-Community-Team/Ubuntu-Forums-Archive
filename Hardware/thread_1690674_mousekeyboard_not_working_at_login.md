---
title: "mouse/keyboard not working at login"
date: 2011-02-18
forum: Hardware
---

### Post by norden.tom on 2011-02-18
I have a dual boot laptop (windows 7/ ubuntu 10.10) when i boot up ubuntu i get to the login screen and my touch pad and keyboard arent working. if i plug in a usb mouse i can use the mouse but the keyboard is still not responding. 
 
in windows 7 i have no problem with mouse/keyboard or in grub.
 
mouse and keyboard were working yesterday in ubuntu. any ideas?

---

### Post by jerrrys on 2011-02-19
try restarting dbus.  open a terminal and enter '**sudo /etc/init.d/dbus restart**'

more on dbus

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dbus&as_qdr=all&sa=Google+Search&lang=en#866](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dbus&as_qdr=all&sa=Google+Search&lang=en#866)

---

### Post by norden.tom on 2011-02-20
Im still learning ubuntu so i dont even know how to boot to the command line.  when i select ubuntu in grub it automatically starts x.  i have tried to edit the boot menu in grub with "quiet splash text" but the changes i make never save.

---

### Post by jerrrys on 2011-02-20
applications>accessories>terminal  and when you enter your password there will be no visual indication and just copy and paste commands when you can l's and i can get confused

---

### Post by norden.tom on 2011-02-20
i know how to get a terminal up once im logged in.  but i cant even get that far, i get to the login screen and the mouse and keyboard dont work, i tried copying and pasting the password but i cant get all the characters i need
are there some keys i can hold while ubuntu is getting to the login screen to get to a command promt?

---

### Post by jerrrys on 2011-02-21
at boot when grub menu comes up, drop down to 'recovery mode'

---

### Post by norden.tom on 2011-02-21
thanks but recovery mode goes to the same login screen and still no mouse/keyboard

---

