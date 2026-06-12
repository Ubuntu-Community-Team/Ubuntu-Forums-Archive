---
title: "Laptop overheats and works very slow on 12.04"
date: 2012-04-27
forum: Hardware
---

### Post by babell00 on 2012-04-27
I just installed a new Ubuntu 12.04 64-bit on my Dell 1558. I don't know way but it works very very slow, compare to fedora or windows 7. For instance opening terminal, or new tab in firefox takes about 5s or more or changing a tab about 10s.
And also overheats, after 10min of work my laptop turn off it self, which never happened before.

If anyone have any suggestion what can be wrong, please let my know.

Kind Regards,
babell00

---

### Post by c2tarun on 2012-04-27
> **babell00 said:**
> I just installed a new Ubuntu 12.04 64-bit on my Dell 1558. I don't know way but it works very very slow, compare to fedora or windows 7. For instance opening terminal, or new tab in firefox takes about 5s or more or changing a tab about 10s.
And also overheats, after 10min of work my laptop turn off it self, which never happened before.
 
If anyone have any suggestion what can be wrong, please let my know.
 
Kind Regards,
babell00
 
 
This is unusual, I also upgraded to 12.04 64-bit yesterday and I was not facing any such problem, Infact I find 12.04's graphics more smooth and its giving me better performances than other releases. I have DELL laptop too.
 
Can you please share your laptop configurations?

---

### Post by babell00 on 2012-04-27
Hi!

Cpu: CPU 2.26-GHz Intel Core i5-430m
RAM: 4GB
Graphics Card: 512MB - ATI Mobility Radeon HD 4570

thanks

---

### Post by c2tarun on 2012-04-27
> **babell00 said:**
> Hi!
 
Cpu: CPU 2.26-GHz Intel Core i5-430m
RAM: 4GB
Graphics Card: 512MB - ATI Mobility Radeon HD 4570
 
thanks
 
 
Come on that is one hell of a PC, it can't be slow or heat up, mine is (i3 + 3GB ram and 1 GB graphic card) :(
I think you should call dell guys and ask them to change the heat sink, and also try to keep your laptop over some hard surface and then use, if possible get a cooling pad. :)

---

### Post by Onesimus on 2012-04-27
As it is a Dell Laptop you may want to install i8kutils, to stop it overheating

I have uploaded a script that may be helpful.  You will need to extract it, and then run the script as root
```
sudo bash ./setup-i8k.sh
```

Hope this helps.

---

### Post by c2tarun on 2012-04-27
> **Onesimus said:**
> As it is a Dell Laptop you may want to install i8kutils, to stop it overheating

 
I got to try that :) sounds interesting.

---

### Post by babell00 on 2012-04-27
> **Onesimus said:**
> As it is a Dell Laptop you may want to install i8kutils, to stop it overheating

I have uploaded a script that may be helpful.  You will need to extract it, and then run the script as root
```
sudo bash ./setup-i8k.sh
```Hope this helps.



I will try it when i get back home

cheers

---

### Post by zdeuyo on 2012-04-27
> **babell00 said:**
> I will try it when i get back home

cheers

Hello,

This happened to me as well. Make sure you upgrade everything, not only what shows in Update Manager.

sudo apt-get update

then

sudo apt-get upgrade

this solved my problem.

See if this works.

---

