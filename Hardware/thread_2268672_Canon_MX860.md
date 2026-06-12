---
title: "Canon MX860"
date: 2015-03-10
forum: Hardware
---

### Post by Heavenly_Abyss on 2015-03-10
```
miguel-glide@Glide:~$ find mx860.ppd
find: `mx860.ppd': No such file or directory
miguel-glide@Glide:~$ sudo /usr/sbin/lpadmin -p canonmx860 -P canonmx860.ppd -v cnijnet:/XX-XX-XX-XX-XX-XX  -E
lpadmin: Unable to open PPD file "canonmx860.ppd" - No such file or directory


```

So, how do I go by installing this? Yes, I have followed instructions on installing for Canon mx printers.

---

### Post by nerdtron on 2015-03-10
The second command did not work because the mx860.ppd file is not on the current directory. Where is this file located?

I'm guessing it is in your Downloads folder? Then you have to go in your downloads folder before executing your command.
```
 cd ~/Downloads
ls
sudo /usr/sbin/lpadmin -p canonmx860 -P canonmx860.ppd -v cnijnet:/XX-XX-XX-XX-XX-XX  -E

```

---

### Post by Heavenly_Abyss on 2015-03-10
It isn't in my Downloads folder and I have looked there. I have tried that command as well.

---

### Post by nerdtron on 2015-03-10
> **Heavenly_Abyss said:**
> It isn't in my Downloads folder and I have looked there. I have tried that command as well.

Where is the file then? did you not download or copy the file mx860.ppd?

Unless you know where the file is, none of your commands or command i have given will work.

---

### Post by Heavenly_Abyss on 2015-03-10
Well, according to the instruction I was suppose to already have downloaded that file by following it, but I don't think that I have the file at all.

Update: I found out a workaround by plugging directly to the computer though that doesn't make it wireless. Still am able to print though.

---

### Post by pdc on 2015-03-10
Hi there heavenly abyss;

........so you need the drivers for the MX860 series from Canon; I see it is a 2009 model; 

if I was guiding someone; I would suggest they go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100187702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100187702.html) and download [SIZE=4][COLOR="#008000"]cnijfilter-mx860series-3.10-1-i386-deb.tar.gz[/COLOR][/SIZE]
__________________

.........a couple of things I notice about that

1) it is an i386 driver; ..................... so you are just running a 32bit Ubuntu, is that right?

2) it is a version 3.10 driver; and any Canon driver < 4.0 needs [COLOR="#0000FF"]libtiff4[/COLOR]         ......... ubuntu removed it last year ........ but one can get it easily from the Debian repositories [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and the 32bit version of [COLOR="#0000FF"]libtiff4[/COLOR] is 17 down the list 

________________

to check what Canon drivers are actually installed, if you copy this command ```
dpkg -l | grep cnijfilter
``` and paste it into a terminal; and if you could share the result with us here? ............ we could perhaps comment to on how to get all going

---

### Post by Heavenly_Abyss on 2015-03-12
> **pdc said:**
> Hi there heavenly abyss;

........so you need the drivers for the MX860 series from Canon; I see it is a 2009 model; 

if I was guiding someone; I would suggest they go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100187702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100187702.html) and download [SIZE=4][COLOR=#008000]cnijfilter-mx860series-3.10-1-i386-deb.tar.gz[/COLOR][/SIZE]
__________________

.........a couple of things I notice about that

1) it is an i386 driver; ..................... so you are just running a 32bit Ubuntu, is that right?

2) it is a version 3.10 driver; and any Canon driver < 4.0 needs [COLOR=#0000FF]libtiff4[/COLOR]         ......... ubuntu removed it last year ........ but one can get it easily from the Debian repositories [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and the 32bit version of [COLOR=#0000FF]libtiff4[/COLOR] is 17 down the list 

________________

to check what Canon drivers are actually installed, if you copy this command ```
dpkg -l | grep cnijfilter
``` and paste it into a terminal; and if you could share the result with us here? ............ we could perhaps comment to on how to get all going

Actually, I think I should change the title as the printer I am trying to get to work is MX472, but linux tutorials implies that I need to use the MX860 driver to work with Canon MX printers in Linux. That is exactly why the title is as it is now. The printer is already working at this point though I can't get it wireless. I already have that file, and applied that file by followings instruction used in linux tutorials on how to get Canon MX printers working in linux. It seems that I have to use the MX470 series drivers instead. And yes, it is Ubuntu 32-bit version. 

Here's the outcome after applying terminal command - 
```
ii  cnijfilter-common                          4.10-1                               i386         IJ Printer Driver for Linux.
ii  cnijfilter-mx470series                     4.10-1                               i386         IJ Printer Driver for Linux.
ii  cnijfilter-mx860series                     3.90-76~ubuntu14.04.1                i386         IJ Printer Driver for Linux.
```

Now that the printer is working thorough USB, I duplicated a printer setting, and changed URL to ipp:\\192.168.1.1XX, but no success.

Update: I managed to get the printer working through wireless method not long after I edited this post. I am getting a error icon with a "!" though.

---

### Post by pdc on 2015-03-13
gosh; ...........I am curious what "tutorials" you have been reading as the MX470series seems to be a 2014 model; and it uses a 4.1 driver so no need for libtiff4

to set up a printer; one needs:

1) establish a connection
2) install the drivers
3) register the ppd file with the print spooler

...........so for 1) to get it connected wirelessly, here is a guide from Canon UK [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mx474_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mx474_printer_wireless_connection_setup/) for anyone who comes afterwards

---

### Post by pdc on 2015-03-13
gosh; ...........I am curious what "tutorials" you have been reading as the MX470series seems to be a 2014 model; and why use MX870 drivers as Canon supply a 470 driver; and the 470 uses a 4.1 driver so no need for libtiff4

to set up a printer; one needs:

1) establish a connection
2) install the drivers
3) register the ppd file with the print spooler

...........so for 1) to get it connected wirelessly, here is a guide from Canon UK [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mx474_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mx474_printer_wireless_connection_setup/) for anyone who comes afterwards; you feel it is all good now 

2) seems like the printer drivers from Canon; are installed; 

3) printer registration ............ if you want to delete an existing registration the command ```
sudo /usr/sbin/lpadmin -x MX470USB
``` should do it ........if the printer is called MX470USB in your system

........then one could run the install script again............. which should be inside the directory [COLOR="#0000CD"]cnijfilter-mx470series-4.10-1-deb[/COLOR] and it will not need to install the drivers, but it will find the printer with its wireless connection; if that connection is good; and will then re-register it and .. it should be fine

---

