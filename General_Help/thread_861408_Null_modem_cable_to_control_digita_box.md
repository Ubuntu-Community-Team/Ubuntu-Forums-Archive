---
title: "Null modem cable to control digita box"
date: 2008-07-16
forum: General Help
---

### Post by Green_Star on 2008-07-16
I would like to know if it is possible to control my digital satellite box(Viewsat ultra) with Ubuntu using Null modem cable. Basically I need to change the channel, change the volume, turn on/off the device etc. So that I can record tv using mythtv. IR blaster is another option but I want to buy blaster only if i can not use null modem cable/serial port. 

(Box has RS-232 port and I guess I have null modem cable I am not sure whether the serial cable and null modem cable are two different cables or not but I have the cable which i got when i bought the receiver)

Thanks in advance.

---

### Post by cariboo on 2008-07-16
It looks like you will have to go with the ir blaster, as the only thing I can find is this:

[http://ubuntuforums.org/archive/index.php/t-541674.html](http://ubuntuforums.org/archive/index.php/t-541674.html)

THis thread is more about uploading firmware using minicom.

Jim

---

### Post by Green_Star on 2008-07-16
> **cariboo907 said:**
> It looks like you will have to go with the ir blaster, as the only thing I can find is this:

[http://ubuntuforums.org/archive/index.php/t-541674.html](http://ubuntuforums.org/archive/index.php/t-541674.html)

THis thread is more about uploading firmware using minicom.

Jim

Thanks man, I saw above link when I was searching for a solution. The official firmware releases are not much frequent, so I can live with USB upgrade. I do not want to spend much on Blaster, but any way what is the cheapest one I can at local store?

---

### Post by markbuntu on 2008-07-16
I'm sure there is some kind of basic terminal program around so you can talk to your sattelite box which is probably what you need.

A null modem cable is wired different than a regular serial rs232 cable. It switches a couple of wires, rts and dts I think. It was a long time ago when I last fooled  around with that stuff so I may be wrong but the diffference is that it allows you to connect 2 RS232 serial ports together without any intervening hardware.

Have you tried the Terminal Server Client?

---

### Post by Green_Star on 2008-07-18
> **markbuntu said:**
> I'm sure there is some kind of basic terminal program around so you can talk to your sattelite box which is probably what you need.

A null modem cable is wired different than a regular serial rs232 cable. It switches a couple of wires, rts and dts I think. It was a long time ago when I last fooled  around with that stuff so I may be wrong but the diffference is that it allows you to connect 2 RS232 serial ports together without any intervening hardware.

Have you tried the Terminal Server Client?

Thanks man, could you please tell me what is Terminal Server Client? How can I use it?

---

### Post by danwood76 on 2008-07-18
> **markbuntu said:**
> 
A null modem cable is wired different than a regular serial rs232 cable. It switches a couple of wires, rts and dts I think. It was a long time ago when I last fooled  around with that stuff so I may be wrong but the diffference is that it allows you to connect 2 RS232 serial ports together without any intervening hardware.


Its the Rx and Tx lines that are switched to allow 2 bus masters to communicate with each other.

I doubt you are able to control that box over RS232 if it isnt documented anywhere.
Normal RS232 protocols are generally hardware specific and without a documented protocol you dont have much of a chance.

You dont need to spend much money to build a linux IR transmitter, LIRC is a great piece of software for this and the hardware is very simple to build.
[http://www.lirc.org/html/install.html](http://www.lirc.org/html/install.html)
You can probably even buy a reciever/transmitter on ebay or the like.

---

### Post by Green_Star on 2008-07-18
> **danwood76 said:**
> Its the Rx and Tx lines that are switched to allow 2 bus masters to communicate with each other.

I doubt you are able to control that box over RS232 if it isnt documented anywhere.
Normal RS232 protocols are generally hardware specific and without a documented protocol you dont have much of a chance.

You dont need to spend much money to build a linux IR transmitter, LIRC is a great piece of software for this and the hardware is very simple to build.
[http://www.lirc.org/html/install.html](http://www.lirc.org/html/install.html)
You can probably even buy a reciever/transmitter on ebay or the like.


That is very helpful. So controlling with RS232 is more complicated. And I am not that handy to build a IR transmitter. I searched in ebay, it is not expensive but shipping killing the price, almost more than the product price. If you find any cheaper ones (if it includes receiver and transmitter that would be great) please let me know.

Another question, which one is good IR transmitter? USB or serial? And which one is more hard to configure?

---

