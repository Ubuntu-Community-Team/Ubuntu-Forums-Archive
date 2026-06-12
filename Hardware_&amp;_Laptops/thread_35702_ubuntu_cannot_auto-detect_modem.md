---
title: "ubuntu cannot auto-detect modem"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by snairofilac on 2005-05-19
i have ubuntu installed with a PCTel HSP MicroModem 56.
 
i added a modem control to the desktop panel and configured it but it would not activate the connection, and no dialing noise or modem noise at all.
 
ubuntu device manager finds and accurately identifies the modem.
 
i configured pppconfig to contain the username and password given me by my ISP, and to create myself as a dialer.
 
pppd from console gives me an error:
Warning:  section [dialerdefaults] does not exist in wvdial.conf
Can't open /dev/modem : no such file
 
pon gives no error, poff gives error:
/usr/bin/poff: no pppd is running.  None stopped.
 
I see that wvdialconf will create a wvdial.conf file automatically?
is this what i need to do?
 
thanks

---

### Post by jasmuz on 2005-05-19
[QUOTE=snairofilac]i have ubuntu installed with a PCTel HSP MicroModem 56.
 
i added a modem control to the desktop panel and configured it but it would not activate the connection, and no dialing noise or modem noise at all.
 
ubuntu device manager finds and accurately identifies the modem.
 
i configured pppconfig to contain the username and password given me by my ISP, and to create myself as a dialer.
 
pppd from console gives me an error:
Warning:  section [dialerdefaults] does not exist in wvdial.conf
Can't open /dev/modem : no such file
 
pon gives no error, poff gives error:
/usr/bin/poff: no pppd is running.  None stopped.
 
I see that wvdialconf will create a wvdial.conf file automatically?
is this what i need to do?
 
thanks[/QUOTE]
 First of all PCTel HSP MicroModem 56 is a Winmodem!, its not a real modem.
Visit [www.linmodems.org](www.linmodems.org) to read about that.
Of course the Ubuntu device manager finds it, because it uses a DMA and IRQ area in your pc (being listed dosent necesarily mean compatibility).

Read the documentation about winmodems to see if you can find some nice way to make it work, if not....i recommend an external modem.

---

### Post by snairofilac on 2005-05-20
[http://www.linmodems.org/](http://www.linmodems.org/)

appears to be just what i needed.  i am currently downloading a PCTel Driver .gz and will burn and try installation on the landlocked computer tomorrow

arg proprietary difficulties

thanx for help

---

### Post by snairofilac on 2005-05-20
does this device exist?

external modem
proven Lincompatibility record
intelligent indicator troubleshooting lights
$30 shippable this week



is USB the way to go with external modems?

---

### Post by snairofilac on 2005-05-21
it appears i will soon be purchasing a real modem.  I have tried to configure three win-modems and have been unsuccessful.

Anyone recommend a trusty model of external modem for compatibility with Ubu?

---

### Post by benson on 2005-06-23
I have problems too with winmodems. I might consider buying one if cash permits. :(

My friends says, 3COM US Robotics 56K External modem. will this do? it's quite expensive. Would someone suggest  a cheaper one?

Thanks!

---

