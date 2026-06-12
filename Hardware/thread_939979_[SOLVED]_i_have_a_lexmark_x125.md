---
title: "[SOLVED] i have a lexmark x125"
date: 2008-10-06
forum: Hardware
---

### Post by 1467 on 2008-10-06
i have a lexmark x125 do you have any idea how to set it up i know i need to get the drivers for it but where do i get them ?

plz help 

thank you

---

### Post by nixscripter on 2008-10-06
It's a bit out of date, but try this:

[http://ubuntuforums.org/showthread.php?t=230496](http://ubuntuforums.org/showthread.php?t=230496)

---

### Post by 1467 on 2008-10-08
thank you vary much

---

### Post by hroos on 2009-08-19
I have problem with my Lexmark X125 and tried to install. [COLOR=lime]Look at my comments below[/COLOR]:
 
Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

[B]cd Desktop
mkdir prndriver
cd prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd drv_x125
cd src
make (ignore warnings you may see here)
sudo make install

sudo /etc/init.d/cupsys restart[/B]
**[COLOR=lime]**** cupsys doesn't exist in this directory; error: command not found[/COLOR]**

**** ADDED FOR UBUNTU DAPPER 6.06 
**** DAPPER users also type in the following commands. BREEZY users can skip this. ****

[
 
 
quote=nixscripter;5919012]It's a bit out of date, but try this:
 
[http://ubuntuforums.org/showthread.php?t=230496](http://ubuntuforums.org/showthread.php?t=230496)[/quote]

---

