---
title: "HP DeskJet Ink Advantage 3776"
date: 2017-06-26
forum: Hardware
---

### Post by victorh2007 on 2017-06-26
I am new in the world of Linux.
I have installed Ubuntu Gnome 17.04 on my PC and I want to buy a new printer.

What do you think of HP DeskJet Ink Advantage 3776? Is it compatible with Ubuntu? Does is have a functional driver for both print and scan functions?

Thanks in advance for any help!

---

### Post by kc1di on 2017-06-26
according to HP that model is fully supported with hplip drivers and should work great. 
Most HP printers are well supported in Linux.  Here is the[ page ]("http://hplipopensource.com/hplip-web/recommended.html")to their support page that list all there models that are supported in linux.

---

### Post by kc1di on 2017-06-26
Hello victorh2007  and welcome to Ubuntu,
According to HP that model is fully supported with hplip drivers and should work great. 
Most HP printers are well supported in Linux.  Here is the[ page ]("http://hplipopensource.com/hplip-web/recommended.html")to their support page that list all there models that are supported in linux.

---

### Post by pdc on 2017-06-26
so 17.04 comes with hplip 3.16.11 

and the 3776 needs at least 3.16.8 so what is on 17.04 is fine; I guess you will use a wireless setup; you should be able to use the LCD screen on the HP to connect to your router; some report problems; so one can do a usb connect first; and curiously the wireless gets going after that step; 

________________________

almost as an aside ......................

17.04 offers air-print support [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-Driver-Less-Print](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-Driver-Less-Print) and     [https://support.apple.com/en-us/HT201311](https://support.apple.com/en-us/HT201311) so for some HP devices, they provide this integration

the 3776 isn't on the airprint list, but a few are [https://support.apple.com/en-us/HT201311](https://support.apple.com/en-us/HT201311)

---

### Post by kc1di on 2017-06-26
one thing you may wish to do is install hplip-gui it's in the repository and it is a hp gui for the printer and has a few or controls. 
you can install it in a terminal this way```
sudo apt-get install hplip-gui
```
you can then install the printer by doing a search in application menu for hptoobox.  
good luck.

---

