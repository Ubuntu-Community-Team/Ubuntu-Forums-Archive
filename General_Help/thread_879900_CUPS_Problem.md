---
title: "CUPS Problem"
date: 2008-08-04
forum: General Help
---

### Post by benste on 2008-08-04
Hy all,
I tried to rename / change some of the printer description in the last days,
but iwasn't bale to do it because of an errror message which is similar to that one which I got now when I tried to print something on my local printer
(connected via printserver - usb)

I'll post a screenshot

---

### Post by benste on 2008-08-04
Cups asks the password of localhost is it similar to my normal one or what password is it?

it doesn't accept my normal password


edit:
tested local webserver mysql password - worked !!!

WHY does cups use my MySQL Password???

edit two,
but if i want to go to the next register card it asks the password again and again - please help me, I have to print something!!

---

### Post by benste on 2008-08-04
if I start the cups control as root (included gksudo into the launcher) it works fine

the problem for printing was that cups deactivated the printer internaly.
Now it works but I'm not shure whether this is a bug in the launcher of ubuntu

can someone check if he uses is as root or normal user please thx

---

### Post by LowSky on 2008-08-04
log into cups from [This Link]("localhost:631").
see if it still given you the same issues

---

### Post by benste on 2008-08-04
lol there it asks username and password - doesn't acept my user name + pswd

seems to be that cups is only accesable via root on my computer

---

