---
title: "Nvidia geforce 8600M GT"
date: 2010-03-12
forum: Hardware
---

### Post by Wickednessie on 2010-03-12
I was just wondering how to install the Nvidi geforce 8600M GT driver on ubuntu. I downloaded the driver from Nvidias website but all I got was a .run file, wich my computer can't seem to run. It just opens the file in Gedit and tells me that it can't read it.
Help would be highly apreciated

---

### Post by gladson1976 on 2010-03-12
Open a terminal and goto the folder where you have downloaded the drivers.

Turn off X.org/GDM (Gnome Display Manager):

```
sudo /etc/init.d/gdm stop
```
Run the installer:

```
sudo sh ./Nxxx.run
```

(If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive)

---

### Post by Fafler on 2010-03-12
Why don't you use Ubuntu's own interface for closed source drivers? System -> Administration -> Hardware Drivers. It should download and install it automatically.

---

### Post by nerdy_kid on 2010-03-12
oh great...same card that i have.  good luck

---

