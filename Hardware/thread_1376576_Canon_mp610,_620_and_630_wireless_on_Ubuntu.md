---
title: "Canon mp610, 620 and 630 wireless on Ubuntu"
date: 2010-01-09
forum: Hardware
---

### Post by Gladeines on 2010-01-09
I needed to install my canon mp620 printer and didnt find good drivers
 so by combining some post from different forums i got a sollution for my problem
 [http://ubuntuforums.org/showthread.php?t=1305248&highlight=canon+printer](http://ubuntuforums.org/showthread.php?t=1305248&highlight=canon+printer)
 [http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)
 

 i hope to help others out with the same problem
 a funny fact: i succeeded with this after only 3 days experience with linux
 so if your down, keep your head op and try again.
 

 
[LIST=1]
[*]install cups, libcups2,     libcups2-dev en build-essential
[/LIST]
 

 ```
        apt-get install cups libcups2 libcups2-dev build-essential
```
     Download the package cups-bjnp-0.5.4.gz-tar
     from [http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/)
     create a folder named printerdrivers in root of your account
     dpkg the package in that map
     you may delete the original package
 

     execute this in the terminal
 

```
 sudo su (give the root password)
             cd printerdrivers/cups-bjnp-0.5.4/
             ./configure && make && sudo make install

```     Download the original printerdrivers from the canon site
 *    cnijfilter-common_2.80-1_i386.deb*
 *    cnijfilter-mp610series_2.80-1_i386.deb*
 

     copy them to the folder printerdrivers
  2.    execute this in the terminal
 

```
dpkg -x cnijfilter-common_2.80-1_i386.deb common
             dpkg --control cnijfilter-common_2.80-1_i386.deb
             chmod 777 common
             chmod 777 DEBIAN
             gedit /DEBIAN/control

```     find l the words libcupsys2 in the document that opens and replace it with libcups2
     save the file and close gedit
     
     navigate to the folder printer
     and cut the folder DEBIAN and past it into the folder common
     then execute this in the terminal
 

```
cd common
             chmod 755 DEBIAN
             cd ..
             chmod 755 common
             dpkg -b common cnijfilter-common_2.80-1_i386.deb
             rm -rf common

```     execute the second step also for the onther printerdriver  
     in my case: *cnijfilter-mp610series_2.80-1_i386.deb*
 but sustitute “common” with “mp610series” wherever it appears above.
 

 

 

 
[LIST=1]
[*]Install the     drivers by executing this in the terminal
[/LIST]
 

```
 sudo dpkg -i cnijfilter-common_2.80-1_i386.deb

sudo dpkg -i cnijfilter-mp610series_2.80-1_i386.deb

```
[LIST=1]
[*]Then download     this files from [http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)
[/LIST]
         canonmp620-630en.ppd
        cifmp610.conf
 

     also copy them into the folder printerdrivers
     and execute this in the terminal
 

```
cp canonmp620-630en.ppd /usr/share/ppd/
             cp cifmp610.conf /usr/lib/bjlib/
             /etc/init.d/cups restart

```     navigate to [http://localhost:631]("http://localhost:631/") in your browser
     click on administration
     click on add printer
     when your printer is found select it
     click on continue
     you may enter the place of your printer
     klik on continue
     search for canonmp620-630 or canonmp610 in the list
     select it and click on continue
     set your default options and set them
 

 the last step lets ubuntu know that these drivers are good
 so execute this in the terminal
 

```
sudo chown -hR root /urs/lib/cups/filter
         sudo chown -hR root /urs/lib/cups/backend
         sudo chgrp -hR root /urs/lib/cups/filter
         sudo chgrp -hR root /urs/lib/cups/backend

```

---

### Post by dirtyhabanero on 2010-08-06
This worked for you? I'm having a good amount of difficulty, but I'm marching on...

Just wanted to ask you about altering the second driver, you were a little unclear...did you mean to replace the word "common" with "mp610series" wherever it came up in the control file? or simply change the libcupsys2 bit? Thanks...

I haven't booted into windows for about 2 weeks now! The ride has been good.

---

### Post by uriela on 2010-11-26
Thanks for all the good information. I was a bit leery when I saw that the .deb files were for a 386 computer, when I am running an AMD64 one. Not to be deterred I went through the steps and - sure enough - the install failed @ my laptop's architecture. :(

---

