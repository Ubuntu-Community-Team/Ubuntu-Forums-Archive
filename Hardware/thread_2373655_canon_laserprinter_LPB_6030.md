---
title: "canon laserprinter LPB 6030"
date: 2017-10-08
forum: Hardware
---

### Post by ya-paulle on 2017-10-08
I have a canon laserprinter LPB 6030, conected via USB. Installed ubuntu17.10beta2. The printer was recognized by the system, but if I want to print something i get the message Printer cannot be started. But the printer is connected and switched on. Don't know how to get the printer working.

---

### Post by gurdenite on 2017-10-08
This might help

[https://askubuntu.com/questions/725130/trying-to-get-a-canon-lbp6030w-to-work](https://askubuntu.com/questions/725130/trying-to-get-a-canon-lbp6030w-to-work)

---

### Post by pdc on 2017-10-08
so Canon supply a linux driver for this LBP6030; they updated it 21st July 2017

you get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html) and if you click to SAVE, it should come down into your Downloads folder as [COLOR="#0000FF"]linux-UFRIILT-drv-v140_uken.tar.gz[/COLOR]

you need to open a terminal; hold down the control and alt and t buttons together to do that ....... and to paste into the terminal, right-click at the text prompt (flashing sign) in the terminal; and look for PASTE in the menu that appears ...............

If you copy each command from below; line by line; paste into the terminal; hit the ENTER key after each paste ........

```
cd Downloads
```
```
tar -xzvf linux-UFRIILT-drv-v140_uken.tar.gz
```
```
cd linux-UFRIILT-drv-v140_uken
```

and this final command will run the install script: it may ask you some questions; so look for those; and it will ask for your sudo password at some stage: so have that ready
```
./install.sh
```

_______
to get a driver working, there are usually 2 steps:
1) install drivers
2) register the printer in lpadmin

............ with the install script, both are done for you and the printer should work after this; 

PS if you delete any existing icon from your PRINTERS folder before you start the above: get rid of any that don't work; DELETE by right-click on the icon and select DELETE ..

---

### Post by ya-paulle on 2017-10-09
Thank you pdc, printer is now working. 
But it was not
cd linux-UFRIILT-drv-v140_uken
it was 
cd linux-UFRIILT-drv-v140-uken

Otherwise thank you for your great help.:P

---

### Post by pdc on 2017-10-09
thank you; you did very well to get all that sorted; my apologies; so that must have been a formatting error where the person preparing the webpage added an "underscore": ....    I just copied what they said the file name was from the website ... never had that one before!! Glad the printer is working well now

---

