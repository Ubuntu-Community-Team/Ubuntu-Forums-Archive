---
title: "Wireless network card help !!"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by utech on 2005-12-16
i am a very very very very... very.... beginer in linux i only know comands like ls,cd,cat,chmod 0777,./run and 2 or 3 things more....i have a dell inspiron 5100 and a wireless card ( Motorola - BCM4306 802.11b/g wireless lan card ) and i dont know how to install the card :( PLZ HELP ME and SORRY MY ENGLISH :( I AM FROM PUERTO RICO :D and i have only 14 years so be pacient :D


Bye....

---

### Post by Lambert on 2005-12-16
1. Plug in the card and go to system>administration>networking. Does the card show in the list? If yes try to configure and activate. If no then you need to install a driver.

2. I believe that is a broadcom chipset so more then likely it won't be in your list and you need to use an app called ndiswrapper which basically makes the windows driver work for wireless devices in linux. There's a link in my signature for ndiswrapper with instructions on how to install the drivers.

---

### Post by utech on 2005-12-16
shit ! man :( i do something wrong :( or i dont know :s


i install the Windows wireless drivers and then i put the cd of my motorola card and they are a file  called autorun.inf and get that file and put to install and them the program say instaled :D but my wireless card have 2 ligths 1 say POWER and the other say LINK and the 2 are offf :(  ...

i dont understand so much the english of the link that you have in you signature but i understand your english :D plz tell me what i need to do :S when i install the program ...

bye

---

### Post by Lambert on 2005-12-16
I will start with assumption that you got ndiswrapper installed. And my instructions are from command line.

copy your drivers from the cd to your home folder on your hard driver. Make sure you copy all files in the xp driver folder. .sys .inf .bin 

change to this directory

```
sudo ndiswrapper -i filename.inf
``` (of course replace filename with the name of the .inf file)

then this command

```
sudo ndiswrapper -l 
```(that's a lower case L)

you should get output similar to this.

Installed ndis drivers:
bcmwl5 driver present, hardware present
then run this command

```
sudo depmod -a
``` 
then

```
sudo modprobe ndiswrapper
``` 
now go into system>administration>networking and try to configure your card

if everything works run this command so driver loads at boot.

```
sudo ndiswrapper -m
``` 
hope this is clear

try to search the internet for instructions on ndiswrapper in your native language.

---

### Post by utech on 2005-12-16
0k man i installed the Windows wireless drivers (  ndiswrapper ) then i put my CD ( COMPACK DISK  xD ) then i get all the files ALL!!! and put it in /home/utech/Desktop/Tarjetas ... they are a file called autorun.inf i go to system/adminitration> Windoes wireless drivers then they say me INSTALL NEW DRIVER i click it then i go to /home/utech/Desktop/Tarjetas where they are al the files of the CD ( COMPACK DISK ) and choose autorun.inf and then say correctly instale ( or someting like that but say installed) the i go to the root terminal and type the comand : sudo ndiswrapper -i autorun.inf
but they say this :(

Installed ndis drivers:
autorun invalid driver!
 
SHIT MAN! PLZ HELP ME ! :D I DONT WANT TO GO TO WINDOWS BECAUSE SUCKS!!!

---

### Post by Lambert on 2005-12-16
autorun.inf does not sound like a correct driver. should be something like bcmwl5.inf

---

### Post by utech on 2005-12-17
Man !! Thanks Thanks Thanks Its Works!!!
Man !! Thanks Thanks Thanks Its Works!!!
Man !! Thanks Thanks Thanks Its Works!!!
Man !! Thanks Thanks Thanks Its Works!!!


Thanks :d

---

