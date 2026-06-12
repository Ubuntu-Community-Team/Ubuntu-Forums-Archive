---
title: "kppp not working properly in Kubuntu 5.04"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by mortram on 2005-04-20
I've got a USB Best Data 56K modem that I've set up successfully in Fedora, and I *thought* I had set it up successfully in Kubuntu (had to compile the drivers as I can't seem to find the packages for the USB slmodem, and the standard packages don't work).  The modem connects properly, but kppp says 'wait: CONNECT' even though it's received a successful CONNECT message from the server, and just sits there forever.  wvdial will also connect, but that seems to spit NO CARRIER in an infinite loop.  Possibly something to do with the "resolve.conf" warning message when launching kppp?

Even stranger, setting up the modem in Ubuntu (not Kubuntu) seems to connect fine in the using the network preferences, but none of the included applications can connect to anything.


thanks to anyone who has a tip!

---

### Post by mortram on 2005-05-03
to anyone else who might find the solution useful:

all I had to do to fix this was to remove "auth" from /etc/ppp/options



I'm now, however, trying to get ppp to work (unsuccessfully so far) in Ubuntu.  KDE was pretty neat for a day-or-so but I don't think I remember even Win95 crashing as often.  I'll revisit the desktop again sometime...

like, tomorrow, when I give up on getting my modem to work in Ubuntu :)

---

### Post by ludi on 2005-05-03
[QUOTE=mortram]to anyone else who might find the solution useful:

all I had to do to fix this was to remove "auth" from /etc/ppp/options



I'm now, however, trying to get ppp to work (unsuccessfully so far) in Ubuntu.  KDE was pretty neat for a day-or-so but I don't think I remember even Win95 crashing as often.  I'll revisit the desktop again sometime...

like, tomorrow, when I give up on getting my modem to work in Ubuntu :)[/QUOTE]
noauth is the correct.
Follow the Ubuntu wiki for the ppp stuff...
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

---

### Post by ludi on 2005-05-03
[QUOTE=mortram]I've got a USB Best Data 56K modem that I've set up successfully in Fedora, and I *thought* I had set it up successfully in Kubuntu (had to compile the drivers as I can't seem to find the packages for the USB slmodem, and the standard packages don't work).  The modem connects properly, but kppp says 'wait: CONNECT' even though it's received a successful CONNECT message from the server, and just sits there forever.  wvdial will also connect, but that seems to spit NO CARRIER in an infinite loop.  Possibly something to do with the "resolve.conf" warning message when launching kppp?

Even stranger, setting up the modem in Ubuntu (not Kubuntu) seems to connect fine in the using the network preferences, but none of the included applications can connect to anything.


thanks to anyone who has a tip![/QUOTE]
Have you tried the Ubuntu how-to?
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

---

### Post by mortram on 2005-05-03
I had no luck following the wiki instructions.  My Gnome apps still aren't finding the internet connection.

---

### Post by ludi on 2005-05-03
Have you tried pon? It didn't work?
This can be a hardware problem (I've had one).
What's the problem?

---

