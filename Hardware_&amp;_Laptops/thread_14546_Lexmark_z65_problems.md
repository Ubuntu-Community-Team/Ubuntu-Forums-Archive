---
title: "Lexmark z65 problems"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by yarook on 2005-02-08
Hi
As you may have guessed, I have troubles getting my Lexmark Z65 printer to work.
Here is what I have tried untill now:
- downloaded the CUPS driver from [http://www.lexmark.com](http://www.lexmark.com)
- executed the install-script using sh script-name -keep
- installed the rpm packages usig alien and dpkg
On other distros I have used(Mandrake, Fedora) I have managed to get the printer working after install trough the cups web-interface. In ubuntu however, I can not log in due to security reasons(anyone knows how to bypass this restriction?), and the Gnome-cups manager just does not support Z65.
Thanks in advance
Petar

---

### Post by yarook on 2005-02-08
Problem solved.
The trick was in enabling the root acces for CUPS web interface with:
[I]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart[/I]
Petar

---

### Post by nicky75 on 2005-02-24
[QUOTE=yarook]Problem solved.
The trick was in enabling the root acces for CUPS web interface with:
[I]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart[/I]
Petar[/QUOTE]

Hello I have installed tcl/tk dev using synaptic and then i downloaded CJLZ65LE-CUPS-1.0-1 from lexmark, but then i try: sh lexmarkz65-CUPS-1.0-1.gz.sh command I have this output:

Verifying archive integrity...OK
Uncompressing Lexmark Printer Driver............
./install: line 15: ./xlexinstall: No such file or directory
The program returned an error code (127)

Can you help me? :roll:

---

### Post by yarook on 2005-07-18
[QUOTE=nicky75]Hello I have installed tcl/tk dev using synaptic and then i downloaded CJLZ65LE-CUPS-1.0-1 from lexmark, but then i try: sh lexmarkz65-CUPS-1.0-1.gz.sh command I have this output:

Verifying archive integrity...OK
Uncompressing Lexmark Printer Driver............
./install: line 15: ./xlexinstall: No such file or directory
The program returned an error code (127)

Can you help me? :roll:[/QUOTE]

Hi!
Following instructions worked for me:
[QUOTE]
 After you untar the CJLZ65LE-CUPS-1.0-1.TAR.GZ file type this command:
sh lexmarkz65-CUPS-1.0-1.gz.sh -keep
Ignore the error warnings when you encounter them. On the same directory(where you launched the sh command) you will find an 'installer' directory. Enter the 'installer' directory(cd installer) and there you will find 2 rpm files. 
[QUOTE]

Now this is when the article goes on about installing rpm files. However, since Ubuntu uses deb packages , you need a way to convert rpm  to deb packages.
The tool that does that is called alien and you should be able to install it with synaptic or in shell through following command:
    sudo apt-get install alien

After that you convert the packages with following shell commands...
    alien -d z65llpddk-2.0-2.i386.rpm
    alien -d lexmarkz65-CUPS-1.0-1.i386.rpm

... and install them in a similar way:
    alien -i z65llpddk_2.0-3_i386.deb
    alien -i lexmarkz65-cups_1.0-2_i386.deb

Hope this helps and next time I'll try to answer a bit sooner  ;-)

---

### Post by black hole sun on 2005-07-18
[QUOTE=yarook]Hi!
Following instructions worked for me:
 After you untar the CJLZ65LE-CUPS-1.0-1.TAR.GZ file type this command:
sh lexmarkz65-CUPS-1.0-1.gz.sh -keep
Ignore the error warnings when you encounter them. On the same directory(where you launched the sh command) you will find an 'installer' directory. Enter the 'installer' directory(cd installer) and there you will find 2 rpm files. 

Now this is when the article goes on about installing rpm files. However, since Ubuntu uses deb packages , you need a way to convert rpm  to deb packages.
The tool that does that is called alien and you should be able to install it with synaptic or in shell through following command:
    sudo apt-get install alien

After that you convert the packages with following shell commands...
    alien -d z65llpddk-2.0-2.i386.rpm
    alien -d lexmarkz65-CUPS-1.0-1.i386.rpm

... and install them in a similar way:
    alien -i z65llpddk_2.0-3_i386.deb
    alien -i lexmarkz65-cups_1.0-2_i386.deb

Hope this helps and next time I'll try to answer a bit sooner  ;-)[/QUOTE]
 Dude! 5 months later! I bet he's already forgotten about this thread / board :D

---

### Post by yarook on 2005-07-19
[QUOTE=black hole sun]Dude! 5 months later! I bet he's already forgotten about this thread / board :D[/QUOTE]

Dude! Since my previous posts clearly were not detailed enough I have made an update for anyone else with the same problem.
 He/she however has not only managed to solve his/hers printing problems but has also written a tutorial, as you can see from following link:
[http://www.ubuntuitalia.it/index.php?option=com_content&task=view&id=71&Itemid=40](http://www.ubuntuitalia.it/index.php?option=com_content&task=view&id=71&Itemid=40)

---

### Post by Jani97 on 2007-09-07
Hi All,

Thanks for the great guide. For being the newbie that i am at linux and ubuntu i found that with this guide i managed to install my Lexmark Z65 on Feisty Fawn even though Lexmark doesn't have any debinan/ubuntu specific driver.

I found, though, that some information, which i found to be necesary for the newbie was missing from this guide so i'll have a crack at adding this information to this guide.

First get the CJLZ65LE-CUPS-1.0-1.TAR.GZ file from the Lexmark site, in a console write:

 wget [http://www.downloaddelivery.com/srfilecache/CJLZ65LE-CUPS-1.0-1.TAR.GZ](http://www.downloaddelivery.com/srfilecache/CJLZ65LE-CUPS-1.0-1.TAR.GZ)


After having downloaded the file, unpack it:

tar -xf CJLZ65LE-CUPS-1.0-1.TAR.GZ 

After you untar the CJLZ65LE-CUPS-1.0-1.TAR.GZ file type this command:
sh lexmarkz65-CUPS-1.0-1.gz.sh -keep

Ignore the error warnings when you encounter them. On the same directory(where you launched the sh command) you will find an 'installer' directory. Enter the 'installer' directory (cd installer) and there you will find 2 rpm files.

Since Ubuntu uses deb packages , you need a way to convert rpm to deb packages.
The tool that does that is called alien and you should be able to install it with synaptic or in shell through following command:
sudo apt-get install alien

After that you convert the packages with following shell commands...
alien -d z65llpddk-2.0-2.i386.rpm
alien -d lexmarkz65-CUPS-1.0-1.i386.rpm

... and install them in a similar way:
alien -i z65llpddk_2.0-3_i386.deb
alien -i lexmarkz65-cups_1.0-2_i386.deb

restart CUPS daemon:

    sudo /etc/rc2.d/S19cupsys restart

and

    sudo /etc/init.d/cupsys restart

After having run the two previous alien commands ppd file to install the printer are located in the following directory:

/usr/share/cups/model

it's Lexmark-Z65-lxz65cj-cups.ppd.gz

Before you carry on, be sure to connect the printer to the computer (USB connector).

You do not need to pack this gz file up. The "Printer" program in the X menu /System/Administration will unpack and install the files.  

When you run the program you will have to choose your printer when it detects it, "Local or identified printer"/'"Use a detected printer:" (My printer was for some reason identified twice, first as Lexmark Z65 (Lexmark Z65 USB1) and Lexmark Lexmark Z65 (Lexmark Printer). I don't know why but i installed both using the driver that was earlier installed and when using the first one Lexmark_Z65_USB1 it printed out fine.

For installing choose the desired printer, click forward, click on the button "install driver" open the ppt.gz file in /usr/share/cups/model, select the file  and click "open". The driver will be installed but if you get the message that the driver is already installed you will find it under supplier Lexmark. The drivers name is Z65 v1.0-1. When you have selected/installed the driver click "forward" and the printer will be installed.

restart CUPS daemon:

    sudo /etc/rc2.d/S19cupsys restart

Accessing the CUPS web base configuration page:
If you wish to use the CUPS web based configuration page open 

[http://localhost:631/admin](http://localhost:631/admin) 

and your user account.


If you can not open it it's probably becouse you need to enabe the root access for CUPS web interface by doing the following:

sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart


Yet again, thanks to everyone for writing down these solutions. I have only gathered the information for what i had to do in order to get my printer working :D

---

### Post by grischan on 2008-04-02
hi folks,

i killed my mother's windows installation and installed ubuntu 7.10. as you may already think there was no printing with lexmark z65.

following your instruction first seemed to solve my problem, because it helped me to the ppd file. unfortunately there is still no printing. i attach the /var/log/cups/error.log and hope there is someone who could provide any help.

i also looked for an already filed ubuntu bug, but couldn't find one that seemed to fit. but i'm bloody new to this.

---

