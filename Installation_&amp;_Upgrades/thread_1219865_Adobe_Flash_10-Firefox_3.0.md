---
title: "Adobe Flash 10-Firefox 3.0"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Dylan Bartlett on 2009-07-22
Im having trouble upgrading to adobe flash 10. i downloaded the .deb from adobe and it says it installed successfully. Now if i type about:plugins into the address bar it says that my default flash player is shockwave 9.0 r159.

**Shockwave Flash**

 File name:  libflashplayer.so 
Shockwave Flash 9.0 r159

---

### Post by kc4mts on 2009-07-23
The following is assuming that you are using a 32 bit version of Ubuntu. (Adobe does not have a 64 bit version of flash available on their site). If the former is true then you need to go into Synaptic Package Manager and search for Adobe-flashplugin. Right click on that file and mark it for complete removal. When it has finished go to [http://www.adobe.com/go/getflash](http://www.adobe.com/go/getflash) and select the package for your system (if you are using Ubuntu, that would usually be the .deb package). I would recommend installing instead of saving as Gdebi does a very good job and is fast. You do also have the option to save the file but installation is not as easy ( usually has to be done through terminal).

:!:Disclaimer....make sure of what system you have before trying any of this. If you have a 64 bit pc and Ubuntu 64 bit version then none of this may apply.

Alan

---

### Post by masux594 on 2009-07-23
Heve u seen [this thread]("http://ubuntuforums.org/showthread.php?t=1193567")? Try to search a little bit before post =P

Sysc, A

---

