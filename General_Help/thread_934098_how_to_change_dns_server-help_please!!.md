---
title: "how to change dns server-help please!!"
date: 2008-09-30
forum: General Help
---

### Post by clownzy on 2008-09-30
Hello there,
Im new to ubuntu so any help will be very much appreciated.Im trying to change my dns settings to opendns.
However when I go to a new teminal window and type:
gksudo network-adminIt says: unable to lookup session information.
The DNS tabs do come on but you can't modify or insert anything!
It asks me to enter my password and I do so I presume that gives me root access!
Thanks for any suggestions...

---

### Post by kpkeerthi on 2008-09-30
[https://www.opendns.com/homenetwork/start/device/ubuntu](https://www.opendns.com/homenetwork/start/device/ubuntu)
[http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/](http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/)

---

### Post by hyper_ch on 2008-09-30
edit your /etc/resolv.conf file or - IMHO better - set your modem/router to use the opendns server.

---

### Post by clownzy on 2008-10-07
Thanks to all for your answers.I now manage to change the dns server settings to opndns.Howver when I retsart the computer it goes back to the original settings.I have tried all the instructions about what to type in so they are saved but doesnt seem to work,says command not found.I have also tried modifying eth0 to another name but still no..
Im unable to change the settings through the router as the company i use for broadband won't let me!GRRRRR
Any other ideas?>....Im not that technical but im trying!
Thanks

---

### Post by kpkeerthi on 2008-10-07
Check out the first link in my last post. It has instructions for it.

---

