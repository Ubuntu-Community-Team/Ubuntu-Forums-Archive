---
title: "system info"
date: 2008-11-23
forum: General Help
---

### Post by groknet on 2008-11-23
Hello
How can i get system info in ubuntu 8.10
eg to display what graphics card the computer has,
network cards etc...?

Greeting grok sweden

---

### Post by Ryadt on 2008-11-23
You can use ```
lshw
```
or install this app```
sudo apt-get install hardinfo
```

---

### Post by ITAndrew on 2008-11-23
Can install sysinfo

sudo apt-get install sysinfo

CPU info can be found at /proc/cpuinfo

Or genericly would be the gnome-system-monitor I.g. System > Administration > System Monitor.

---

### Post by bigbrovar on 2008-11-23
ifi u want some really detailed infor about your system u could also try **dmidecode**
but u have to install it first
```
sudo apt-get install dmidecode
```
then open a terminal and just run dmidecode

if you want the out put displayed in a text file run ```
sudo dmidecode > myhardware
```

the go to your home directory and you would see a text file named myhardware which contains everything there is to know about you hardware.

---

### Post by groknet on 2008-11-23
Tx  :KS

---

### Post by Ryadt on 2008-11-23
Mark your thread as solved please.

---

### Post by mmck on 2009-02-11
thanks...

---

