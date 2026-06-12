---
title: "Problems with Nvidia driver"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by DK Ubun on 2009-05-27
I'm running a dual boot with the latest version of Ubuntu and Windows XP. Yesterday after i had to reboot, the resolution was changed to 800*600 (I normally use 1680*1050). I had been using the driver from the add/remove package, i got some advice from a fellow Linux user, he told me to try and use EnvyNG. i uninstalled the driver from the package, and installed it via EnvyNG, when i did i got the message, "Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 322, in driverMenu
    self.driverPage(driver)
  File "interface.py", line 216, in driverPage
    candidateLen.append(len(details['candidate']))
TypeError: object of type 'NoneType' has no len()" 

Thanks in advance.

---

### Post by Cillys on 2009-05-27
Do you have more than 2GB of Ram ...??? if so drop it down to 2GB or less ...  Nvidia will not work .. PERIOD! if you have more than that ... little unknown fact ....

---

### Post by madverb on 2009-05-27
Not a fact at all. That is a massive load of crap.
The reason it is an unknown "fact" is because it's a lie.

---

### Post by 73ckn797 on 2009-05-27
> **Cillys said:**
> Do you have more than 2GB of Ram ...??? if so drop it down to 2GB or less ...  Nvidia will not work .. PERIOD! if you have more than that ... little unknown fact ....


Nvidia + 6GiB RAM works perfectly for me.

---

