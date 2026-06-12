---
title: "sagem f@st 800 e2t and Tiscali"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by gseviour on 2005-05-01
I maged to install ubuntu a couple of days and most things seem to work properly except for my internet connection.

I've downloaded the latest eagle_usb driver and followed  these instructions
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230) (I have g++ installed as well as the kernel headers).

startadsl does not get me a connection and running eaglectrl -w fails to synchronise the modem.

Anyway i'm not even sure playing around with compiling drivers and stuff is the way to go seeing how ubuntu is aimed at beginners.

Please, please, please can someone point me in the right direction.

Cheers

---

### Post by themelvin on 2005-05-01
To set up adsl you need to do that:

dpkg -l pppoeconf

and then

sudo pppoeconf

It worked with me.

---

### Post by gseviour on 2005-05-04
pppoeconfig reports something like
"sorry I scanned 2 interface cannopt connect to
Access Concentrator" (I cant remember the exact message)

I've also tried reinstalling ubunto and then installing the eagle-usb driver through that gui based package manager (cant remember the name but I can find it on the menu) - it brought up a gui based configuration wizard but unfortunately I lost the wizard due to the power cord getting knocked out when I was switching the modems usb cable between computers - i then had to follow some instructions before the gui based package manager would work again and after that I was taken through a text based wizard. Both wizards have not been seen since - even after i used the gui package manager to remove and then reinstall the driver. Eck!  ](*,)  :-({|= 

Anyway I still hope to get the modem working and if that fails then I'll consider buying a router (which I'd really like to avoid 'cos itd be cheating and I've already gone through the process of buying a serial modem when I found out my used-to-be-expensive modem card was a lousy winmodem)

---

### Post by gseviour on 2005-05-06
firstly, thanks to themelvin for the information regarding pppoeconf - i'm sure its part of the answer but unfortunately something is still not quite right with my configuration.

Is there anyone out there who can give me some more pointers?

Cheers

---

### Post by zxc on 2005-05-13
I know this may sound stupid but you need to get the .deb versions.

I've sucessfully installed the drivers but it was basically I found someone in the ubuntu channel who directed me through every stage and every problem so I couldn't say how to do it.

I was trying to fiddle around with compiling my own thingys, but don't bother. You need to find the .deb online (online debian repositiories?) as your synaptic won't work (as you have no internet). Then you need to put them on your ubuntu partition. I reccomend you ask around it the #ubuntu irc channel for someone to help you install it.

Oh and btw i thinks it's:

Eaglectrl -d  not Eaglectrl -w
and Sudo Startadsl.


Also you can use Eaglestat to see the status of your modem.

---

