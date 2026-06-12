---
title: "Windows printing through CUPS"
date: 2010-09-01
forum: Hardware
---

### Post by freelyx on 2010-09-01
Hey guys,

I'm trying to get an HP Designjet 500 to print through a windows machine. The linux box it's connected to prints beautify but unfortunately I cannot find the right driver for the Windows machine. 

Does anybody have any suggestions as to what type of driver to use? I've tried connecting to HP and using the drivers provided by them to no avail...

---

### Post by elperrillo on 2010-09-26
You are taking the wrong approach. If you use CUPS as your print server and then you have to find he drivers and install them manually for each machine then you are going to waste a looooooot of time. CUPS has every driver you can possibly imagine, you just have to get those divers to work with Windows through Samba. If you do then you can just go to the server, right click on the printer, click on connect and it will get the drivers from the CUPS server. For that you have follow a few steps, but after that every new printer that you install in your server will be a breeze, no more looking for drivers. Follow this guide, it is the only one that has worked for me so far.

[http://geekyprojects.com/ubuntu/getting-windows-printer-drivers-from-cups/](http://geekyprojects.com/ubuntu/getting-windows-printer-drivers-from-cups/)

---

