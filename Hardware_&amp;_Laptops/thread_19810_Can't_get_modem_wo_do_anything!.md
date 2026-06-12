---
title: "Can't get modem wo do anything!"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by kelean on 2005-03-13
Hi, my cable modem died so i hoooked up my external modem ran pppconfig.  WWhen i try to to use modem with pon nothing happens.  It  is frustrating seeing i had to hook up my old computer with windows on it.  Pllease help, thank you.

---

### Post by az on 2005-03-13
sudo pon
sudo plog

Post the output here.

---

### Post by kelean on 2005-03-14
[QUOTE=azz]sudo pon
sudo plog

Post the output here.[/QUOTE]
 Thanks for the reply azz.  After sudo pon and sudo plog I got nothing.  All it did was give me was a new line in the consol. 

I reformated my hard drive and installed yoper again.  I really like Ubuntu but tith the moden and no sound I have had enough.  I will look at ubuntu down the road but for now I prefer to have sound and my dial up working.

---

### Post by brousch on 2005-03-14
Since you are going from ethernet to modem, you may be having a routing problem.

sudo gedit /etc/ppp/peers/<name of your modem connection>
Add "replacedefaultroute" (without the quotes) in the middle somewhere.
Save the file and try to connect.

I see you are in the same city as I am, so let me know if you need help!

---

### Post by az on 2005-03-14
[QUOTE=kelean]Hi, my cable modem died so i hoooked up my external modem ran pppconfig.  WWhen i try to to use modem with pon nothing happens.  It  is frustrating seeing i had to hook up my old computer with windows on it.  Pllease help, thank you.[/QUOTE]


It would seem you did not configure the ppp connection properly with pppconfig

Try sudo pppconfig again and save your settings.  Make a connection named mprovider, otherwise, do 
sudo pon <connection name>

---

