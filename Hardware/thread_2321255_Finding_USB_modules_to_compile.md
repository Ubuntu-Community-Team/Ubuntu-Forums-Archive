---
title: "Finding USB modules to compile"
date: 2016-04-21
forum: Hardware
---

### Post by polishmetal on 2016-04-21
I accidentally removed a bunch of drivers on my laptop with a package software. I need to find the usb drivers source code and compile them in order to back up my files and reboot. 
Does anyone know where I can find the appropriate source code??

---

### Post by ajgreeny on 2016-04-21
Tell us more about what you did as the detail you have given so far (or rather not given) does not give us a lot to go on.

What was the "package software" and what exactly did it remove, and how?

---

### Post by polishmetal on 2016-04-22
I was using synaptic package manager and accidentally managed to uninstall/remove packages and stopped it before it could finish(so i have some stuff left). I've managed to recompile the wifi driver to get internet and need to find a way to recompile the usb modules as modprob/modules doesn't have any directories or modules with usb on my laptop.

---

### Post by ajgreeny on 2016-04-22
You can find the packages that synaptic removed by going to File -> History from the synaptic menu.
Try reinstalling any packages that were removed at that operation.
You could also try reinstalling the appropriate *ubuntu-desktop package to see if that brings in any packages that were removed by accident.

---

