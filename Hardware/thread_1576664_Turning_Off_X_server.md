---
title: "Turning Off X server"
date: 2010-09-17
forum: Hardware
---

### Post by jncocontrol on 2010-09-17
How do i turn off the Nvidia X server, Cause i would like to update my Video card, and the Driver on the hardware Jockey is out of date. Any help would be appreciated.

---

### Post by endotherm on 2010-09-17
hit ctrl + alt + F1
login to the virtual terminal, adn enter'
```
sudo service gdm stop
```
then use ps to confirm that x and gdm are stopped.

---

### Post by jncocontrol on 2010-09-19
I did that, And it brought me to a black prompt screen. Do i do the "sudo sh <directory here>/<name of the file here>" command?

---

### Post by endotherm on 2010-09-20
> **jncocontrol said:**
> I did that, And it brought me to a black prompt screen. Do i do the "sudo sh <directory here>/<name of the file here>" command?
yep.

---

