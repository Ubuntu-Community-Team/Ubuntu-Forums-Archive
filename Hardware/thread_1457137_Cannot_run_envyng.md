---
title: "Cannot run envyng"
date: 2010-04-18
forum: Hardware
---

### Post by hqt on 2010-04-18
I'm a new user of Ubuntu. I have a computer with Geforce 7300GT, when I use envyng, the messenger appear, and I press 1 to istall NVIDIVA card graphic, but the propram say that there is a problem, that is: 
 
Traceback (most recent call last):
File "interface.py", line 432, in <module>
a.mainMenu()
File "interface.py", line 295, in mainMenu
a.driverMenu('nvidia')
File "interface.py", line 322, in driverMenu
self.driverPage(driver)
File "interface.py", line 216, in driverPage
candidateLen.append(len(details['candidate']))
TypeError: object of type 'NoneType' has no len()
 
who can help me please :( 
thanks for all :)

---

### Post by hqt on 2010-04-18
I think my system is missing some libraries, and who can tell me, how can I down those missing libraries, please :)
thanks for all

---

### Post by Mark Phelps on 2010-04-18
Think you may be out of luck as the developer of EnvyNG has dropped support for it.

---

