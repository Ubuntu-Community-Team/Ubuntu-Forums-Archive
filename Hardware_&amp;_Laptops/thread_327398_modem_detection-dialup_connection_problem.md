---
title: "modem detection-dialup connection problem"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by michie86 on 2006-12-29
hello.

im trying to set up a dialup connection so i can connect to the Internet using ubuntu but i'm encountering problems.  i read some instructions on setting up a dialup connection but i was not succesful. 

i first tried using the pppconfig but when i try sudo pon ispname, i stil can't connect. and when i turn pon off it says that i didn't even had it turned on. :( 

Then i tried configuring using System->Admin->Networking, but when i click autodetect for my modem, it says it could not detect my modem device. so i tried choosing /dev/modem. but when i try to activate the modem, i get an error with "Could not enable interface ppp0. check that the settings are correct for this network and that the computer is corretly connected to it". :( 

but if i try choosing ttsy0 or 1, 2, 3, i can activate the modem but i can connect to the Internet. I think it can't detect my modem. ](*,) 

i badly need to have a dialup connection in ubuntu so i won't have to switch to windows every now and then just for Internet connection. i also need internet connection in the application i'm working on. :( 

any help would be appreciated.. thanks

---

### Post by unisol on 2006-12-29
try this: sudo wvdialconf /etcwvdial.conf and see if wvdial can detect your modem. if not you may have to d/l scanmodem to find your modem. could it be a winmodem?

---

### Post by az on 2006-12-29
What kind of modem do you have?

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by michie86 on 2006-12-29
hello unisol.. i tried sudo wvdialconf /etcwvdial.conf and at the end it said "Sorry, no modem was detected. Is it in use by another program? Did you configure it properly with setserial?"

how do i do the 'd/l scanmodem'? coz when i type it in it says that it isn't a directory.
a winmodem? does that mean a modem w/c can only function in windows? :( 

hi azz.. i'm not sure with my modem coz somebody else bought it and got it installed.. i tried looking at win's ctrl panel and it says SoftV90 Data Fax Voice Modem.. is that it?

---

### Post by michie86 on 2006-12-29
by the way, i'm not angry.. i didn't know that the icon i used in the subject meant 'angry'
but i really need help.. thanks

---

### Post by az on 2006-12-29
> **michie86 said:**
>  SoftV90 Data Fax Voice Modem.. is that it?

It's not a real modem - it's a winmodem (software modem).  See the DialupModemHowto on getting and running scanmodem to determine what driver you need.

The reason it's a pain is because the vendors of that hardware are not very helpful.  Drivers would be written for it if it were possible.

---

### Post by michie86 on 2006-12-30
> **azz said:**
> 
The reason it's a pain is because the vendors of that hardware are not very helpful.

i agree on that.. 

i tried idenifying the chipset (the scanModem wasn't able to identify my modem's chipset, i tried other ways and i think i finally got it) of my modem and then i'll be trying to download the driver for it and so on.. i hope this time it will work.. 

in case there are still problems [which i hope will not happen regarding this matter], i'll inform you..

big thanks to you azz and unisol.. 
i really find this forum very helpful.. :)  
i hope one day i'll be the one giving instead of asking help..

---

### Post by michie86 on 2007-01-07
hello.. up to this point i still can't make my modem work.. scan modem cant detect my modem.. i looked at the numbers printed on the modem itself and its an HSF modem.. i downloaded the driver for HSF of my kernel (2.6.15-23-386) from linuxant, the  i installed it but still no success.. i get "warning:no device detected by HSF driver - HDA modems may require reboot   Note: HDS support not compiled in the driver (requires a 2.16.16 or later kernel)".. then when i try to autodetect the modem for the dialup connection it still can't detect  my modem :( 

please help me, i dont know what to do next :???:  i badly need internet connection on ubuntu.. thanks

---

### Post by chovy on 2007-01-11
i'm am trying to figure out what kind of modem I have. It's plugged in, isn't there a way to do "lspci" or something to figure out it's chipset?

wvdialconf and scanmodem return nothing.

I pulled the modem out, I have a Lucent Actiontec modem...if that helps.

Still hacking around and none of the suggestions in wiki work for my modem.

---

### Post by S P O R K on 2007-03-07
I dragged my old US Robotics external modem out of the junk pile.  Plugged it in and auto-detected no problem.

The easiest solution might be a trip to the electronic's junk shop.

---

### Post by shafi on 2007-03-12
Dear all, I have problem using my modem, i have a Toshiba laptop but the modem is not working, i am using Ubuntu Edgy Eft Gnom,i tried to connect it using wvdial but i couldn't, i dont know what's wrong
my modem is** AC97 Data Fax SoftModem**
when i try
wvdial
i get these errores:
-->WvDial: Internet dialer version 1.56
-->cannot open /dev/ttyS1: input/output error
-->cannot open /dev/ttyS1: input/output error
-->cannot open /dev/ttyS1: input/output error

I also tried /dev/ttyS0, /dev/ttyS2 and S3 and also /dev/Modem

i also could not solve it using scanModem
please help me what to do, thanks alot  :confused:

---

