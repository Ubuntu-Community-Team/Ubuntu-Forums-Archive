---
title: "Sierra 580 aircard (PCMCIA) ...How?"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by geoffphuket on 2007-06-23
How do I get my PCMCIA  Sierra 580 air card working on my new  Acer Aspire 5052ANWXMi Laptop ?

I have the latest download of Ubuntu live 7.04

I also have no sound, but I guess this is another huge problem to overcome :(

Please reply in small words...I'm new to this! :D

Cheers in advance,

 geoffphuket

---

### Post by geoffphuket on 2007-06-23
No replies, so I guess I'm back to Windows XP again ! ....At least everything works with no hassel :D

---

### Post by Gerrit Bijlsma on 2007-11-30
Hi. 
Don't go back to windows xp (yet)
I have my aircard 580 working well (although it is sometimes difficult to get a connection)
Sierra wireless has an install script that you can download but......

I am not an expert but I am starting to like Ubuntu
I did the following:
find the correct /dev/ttyUSBX device by using ls -l /dev/ttyU*
it should give you a list of two devices; /dev/ttyUSB0 and /dev/ttyUSB1
If you have more /dev/ttyUSB devices you will have to unplug your aircard 580 and see what devices dissapear.

Than you can use either Gnome ppp or do a manual network configuraton trough the network icon on the top left hand corner of your screen.
select /dev/ttyUSB0 (in my case) as modem type in "evdo@catevdo.com) as user, no password and #777 and dial number 
That will configure /etc/pppd/peers/ppp0 correctly
use the same icon to connect to ppp0 via modem
or 
use the command line pppd call ppp0

this should get you on-line
It works on both Ubuntu and Kubuntu 7.04 feisty and 7.10 gusty 

Good luck,

Gerrit (from Phuket)

---

