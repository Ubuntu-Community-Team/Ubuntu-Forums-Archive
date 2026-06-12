---
title: "How I can deal with   ndiswrapper"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-02
please how i can use the ndiswrapper to use the windows drivers on ubuntu ?

---

### Post by ajmorris on 2008-04-02
hi there,
first get the windows drivers executable file.
then do the following:
```
1) cabextract file.exe
2) ndiswrapper -i driver.inf
3) ndiswrapper -l  (to check it is installed)
4) sudo depmod -a
5) sudo modprobe ndiswrapper

```

then, sudo iwconfig should show your wireless interface (or the wireless applet on the gnome taskbar will also show networks)

AJ

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-02
sorry i am new user for the ubuntu ,, what about the file path , how the ndiswrapper detect it ?

---

### Post by ajmorris on 2008-04-02
i dont quite understand what you mean? which file path? If you mean the file path of the driver once ndiswrapper installs it, the files are copied to a system directory for ndiswrapper to use...

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-02
my friend i have windows drivers and want to install it on the ubuntu by ndiswrapper, also i do not know how to check the drivers if it installed on ubuntu or not , i am new user for ubuntu and want some guide for that to move from windows to ubuntu

---

### Post by ian_33 on 2008-04-02
This worked for me:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper+kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper+kevdog)

---

