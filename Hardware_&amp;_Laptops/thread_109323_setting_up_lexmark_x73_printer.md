---
title: "setting up lexmark x73 printer"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by daniel49 on 2005-12-28
It looked real straight forward but when I tried it, I get the same results this fellow did.

[http://ubuntuforums.org/showthread.php?t=103384&highlight=lexmark+x73](http://ubuntuforums.org/showthread.php?t=103384&highlight=lexmark+x73)

---

### Post by daniel49 on 2006-01-02
well after trying this and that and posting in several forums was about resigned to do my printing in windows but stumbled on the solution today.

When you install the lexmark73 it correctly identifies it and recommends the correct driver the z42.
I also used this driver for the same printer in fedora. So you apply it , a printer icon appears, print a test page, nothing comes out, and it happily tells you everything is cool. Except of course it doesn't work.
Well it turns out instead of selecting the default x73 driver (which it states is the z42 and has selected by default) , one has to scroll up further and you will see an entry called the lexmark_z42. Select that for your driver and then it uses the pre-installed gimp printer and works fine.

So I guess that default entry is just there in case they ever get around to reverse engineering the driver.

---

### Post by daniel49 on 2006-01-04
Bye the way just in case anyone was interested. this is a multi purpose  machine. 
The scanner can also be made to work in Linux by simply copying the firmware file to your linux system from windows , for the x73 it was OSLO31701b2.usb into folder usr/share/sane/gt68xx
then sudo chmod a+r OSLO31701b2.usb int that directory.

open a terminal and type sane-find-scanner
scanimage -L
scaninage >out.pnm
also works fine with gimp.
go to file  then aquire
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

---

### Post by MagicNo14 on 2006-01-06
I selected the Z42 driver for my X73 printer, but if I try to print the testpage it just prints 1 line and then crashes... Any idea's on how to find out what is wrong with it?

---

### Post by MagicNo14 on 2006-01-06
It seems to be working, more or less... The testpage still crashes about 90% of the time for an unknown reason, but I don't intend to print that everyday so I guess I can live with that.

Now about the scanner, I haven't got a windows installation anymore. Could you send me the driver I need to copy? Or perhaps post it somewhere so I can download it? I would be most grateful! :p

---

### Post by manicka on 2006-01-09
[QUOTE=MagicNo14]
Now about the scanner, I haven't got a windows installation anymore. Could you send me the driver I need to copy? Or perhaps post it somewhere so I can download it? I would be most grateful! :p[/QUOTE]

The link is at the bottom of daniel49's post

---

### Post by mudball on 2007-08-19
> **MagicNo14 said:**
> It seems to be working, more or less... The testpage still crashes about 90% of the time for an unknown reason, but I don't intend to print that everyday so I guess I can live with that.

Now about the scanner, I haven't got a windows installation anymore. Could you send me the driver I need to copy? Or perhaps post it somewhere so I can download it? I would be most grateful! :p

e-mail me at [email]arlys.schultz@sbcglobal.net[/email] an i will send you inst cd Ed

---

