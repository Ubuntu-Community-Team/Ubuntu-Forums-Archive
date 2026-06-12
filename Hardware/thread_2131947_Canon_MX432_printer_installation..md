---
title: "Canon MX432 printer installation."
date: 2013-04-03
forum: Hardware
---

### Post by texasjim37 on 2013-04-03
Hi,
I am having a problem with the installation of a Canon MX432 Photo/printer.  I am using Verizon FIOS as my internet host.  I can not find this printer on the printer list when trying to install.  Anyone have any suggestions?
Thanks,
Jim

---

### Post by pdc on 2013-04-03
go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html)

download MX430 series [COLOR="#0000FF"]IJ Printer Driver Ver. 3.70 for Linux (debian Packagearchive[/COLOR]) .......it comes down as [COLOR="#008000"]cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

save as file

**Leave your printer off initially**,*[COLOR="#DDA0DD"] till the terminal says to turn it on[/COLOR]* ....

copy and paste these commands into a terminal: commands are

>  [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mx430series-3.70-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

that should get you going 

then go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html)  for ScanGearMP and install along the lines described above

run it by

> [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal and make a launcher for repeated use.........google how to .......

---

### Post by texasjim37 on 2013-06-12
Thank you ...

---

### Post by texasjim37 on 2013-06-12
Thank you Problem Sovled
Jim ):P

---

