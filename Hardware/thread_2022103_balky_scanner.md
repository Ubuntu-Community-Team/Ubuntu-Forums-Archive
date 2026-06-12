---
title: "balky scanner"
date: 2012-07-10
forum: Hardware
---

### Post by Lloydb39 on 2012-07-10
Didn't get a solution for this in general help and decided it might belong in hardware: Epson 4490 scanner won't work on a Dell running version 11.10. SANE sees the scanner but iscan can't. Read all I could and determined it might require editing the usb section of the  epson.conf file. Two problems: The computer I own says I'm not the owner and can't edit the file and I'm afraid to edit a conf file for fearing of crashing the whole machine.
Another impediment. Much of the lit on this talks about doing stuff "as root." None of it (that I could find) tells you how to be as root.
Anyone who can guide me out of this morass would be my favorite person of the day.

---

### Post by howefield on 2012-07-10
To open/edit epson.conf use.. (I'm assuming the path to your epson.conf, but if it is different then substitute as required).

```
gksudo gedit /etc/sane.d/epson.conf
```

Type in your password, edit and save.

You probably want to backup the file beforehand in case of error.

```
sudo cp /etc/sane.d/epson.conf /etc/sane.d/epson.conf.old
```

---

