---
title: "HOWTO: get SZ650 webcam working in Ubuntu 7.10"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by arjunrc on 2007-12-21
All due credit to [http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html](http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html)

However, I thought the instructions were very terse. So here are the details:

[LIST]
[*] Get the webcam driver from here: [http://lsb.blogdns.net/files/r5u870-0.10.0.tgz](http://lsb.blogdns.net/files/r5u870-0.10.0.tgz)
[*]  tar xzf r5u870-0.10.0.tgz 
[*] copy [http://www.uuhaus.de/linux/r5u870-0.10.0-vcc7patch](http://www.uuhaus.de/linux/r5u870-0.10.0-vcc7patch) to the directory where the above .tgz was extracted
[*] apply the patch by issuing  patch <r5u870-0.10.0-vcc7patch 
[*] do a make and make install

[*] You now need to manually extract the driver firmware from the Vista version. If you have Vista, you will find R5U870FLx86.sys in the c:\Drivers folder (a sub-dir within it). If you don't have Vista (like me, since I downgraded to XP) you will NOT have the file. Instead download the drivers from [http://support.vaio.sony.co.uk/downloads/info/info.asp?site=voe_en_GB_cons&url=Vaio/Original/SZ6_Drivers.zip](http://support.vaio.sony.co.uk/downloads/info/info.asp?site=voe_en_GB_cons&url=Vaio/Original/SZ6_Drivers.zip)
You will find the file there.

[*] Copy that file to your working directory.
[*] if you don't have guile installed, do a sudo apt-get install guile-1.8
[*] Copy [http://www.uuhaus.de/linux/recode-fw.scm](http://www.uuhaus.de/linux/recode-fw.scm) to the same directory you have the R5U870FLx86.sys file
[*] do a guile recode-fw.scm. This will print a bunch of characters on the screen and create a file called r5u870_183a.fw 
[*] copy r5u870_183a.fw  to /lib/firmware

[*] now reboot
[*] to test, launch skype beta 2.0, go to video, you should now see the camera driver and the camera feed when you click on test video
 
[/LIST]

regds
arjun

---

### Post by msillence on 2008-01-19
There is a new site which is actively supporting the driver:

[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

even works with 2.6.24

Enjoy,
M

---

