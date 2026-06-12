---
title: "Canon pixma mx432 is recognized but doesnt work?"
date: 2013-06-25
forum: Hardware
---

### Post by sirboredduh on 2013-06-25
Hello. When I try to add the printer it shows up, but when I try to print a test page or any page, it doesnt seem to work. Thank you in advance

---

### Post by pdc on 2013-06-25
can I suggest you install the drivers that Canon make available for you? 

......if you first go to administration ..printing and delete whatever has been created so far........

for the Canon drivers, go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html)

and when you click download you will get the [COLOR="#008000"]cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

can I suggest some commands to install it? .......if you copy and paste these into a terminal.....use the top line of the terminal.......ie File..Edit and down to paste ...
> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mx430series-3.70-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

that should get it installed for you 

_____________________________________________________________________

to run the scanner component, Canon make a programme available called [COLOR="#0000FF"]ScanGearMP[/COLOR]

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html)

it comes down as [COLOR="#008000"]scangearmp-mx430series-1.90-1-deb.tar.gz[/COLOR]

if you close the terminal; and open it again; and use the commands as above; substituting scangearmp-mx430series-1.90-1-deb.tar.gz !!

to run the programme the command in a terminal is

> [COLOR="#FF0000"]scangearmp[/COLOR]

and you can then create a launcher to launch it ........as suggested here ..

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

ie 

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

and 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

the crucial bit is COMMAND and needs to be scangearmp

---

### Post by sirboredduh on 2013-06-26
> **pdc said:**
> can I suggest you install the drivers that Canon make available for you? 

......if you first go to administration ..printing and delete whatever has been created so far........

for the Canon drivers, go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html)

and when you click download you will get the [COLOR=#008000]cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

can I suggest some commands to install it? .......if you copy and paste these into a terminal.....use the top line of the terminal.......ie File..Edit and down to paste ...








that should get it installed for you 

_____________________________________________________________________

to run the scanner component, Canon make a programme available called [COLOR=#0000FF]ScanGearMP[/COLOR]

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html)

it comes down as [COLOR=#008000]scangearmp-mx430series-1.90-1-deb.tar.gz[/COLOR]

if you close the terminal; and open it again; and use the commands as above; substituting scangearmp-mx430series-1.90-1-deb.tar.gz !!

to run the programme the command in a terminal is



and you can then create a launcher to launch it ........as suggested here ..

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

ie 



and 



the crucial bit is COMMAND and needs to be scangearmp

Thank you very much, Worked like a charm

---

