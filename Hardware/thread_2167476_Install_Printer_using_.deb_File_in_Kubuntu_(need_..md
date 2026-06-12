---
title: "Install Printer using .deb File in Kubuntu (need .ppd file?)"
date: 2013-08-13
forum: Hardware
---

### Post by Feathers McGraw on 2013-08-13
Hi all,

I've recently converted my girlfriend's mum to Kubuntu (13.04), and she's getting on well with it. However, I'm having issues adding her printer in KDE. If I crack this, I think she'll be happy using Linux full-time :popcorn:.

The printer is an Epson XP-405. By following instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=2091976"), I downloaded the .deb installer from the Epson website, which installed without any error messages.

When I go to add the printer using System Settings --> Printers --> "Click here to add a new printer", the printer shows up in the list of network printers (and again if there's a wired connection). However, when I click on it and proceed I am prompted to choose from a list of models (not including the Epson XP-405), or to manually select a .ppd file.

Where do I get the .ppd file? Did the .deb installer create one and stash it somewhere? If so, where? If not, do I have to create one?

Thanks,

Feathers

---

### Post by Yellow Pasque on 2013-08-13
Look in /opt. You can check where the .deb put it using dpkg -c:
```
dpkg -c <.deb name>
```
For example:
```
dpkg -c epson-inkjet-printer-201201w_1.0.0-1lsb3.2_amd64.deb
```
returns  the full list of files, including:
```
drwxr-xr-x root/root         0 2012-05-23 00:23 ./opt/epson-inkjet-printer-201201w/ppds/
drwxr-xr-x root/root         0 2012-05-23 00:23 ./opt/epson-inkjet-printer-201201w/ppds/Epson/
-rw-r--r-- root/root     39941 2012-05-23 00:23 ./opt/epson-inkjet-printer-201201w/ppds/Epson/Epson-XP-302_303_305_306_Series-epson-driver.ppd.gz
-rw-r--r-- root/root     39940 2012-05-23 00:23 ./opt/epson-inkjet-printer-201201w/ppds/Epson/Epson-XP-402_403_405_406_Series-epson-driver.ppd.gz
```

---

### Post by Feathers McGraw on 2013-08-14
Thanks, that's really useful!

I know it it's strange but I've never actually used dpkg from a terminal before,  I've always just double clicked the file in a file manager. I take it that does something like "dpkg -i {.deb package}"?

I love this forum, it's so easy to learn new things. Just for anyone else who stumbles across this thread, here's a "cheat sheet" for dpkg: [http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php](http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php)

I'll try that tonight.

Thanks again,

Feathers

---

