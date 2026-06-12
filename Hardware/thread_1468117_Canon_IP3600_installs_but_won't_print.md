---
title: "Canon IP3600 installs but won't print"
date: 2010-05-01
forum: Hardware
---

### Post by Bryan55 on 2010-05-01
Hi
I have just got a IP3600 printer. When I plugged it into my PC ubuntu recognized it straight away and installed "cups-drivers-gutenprint 5.2.4.0ubuntu2"

However when I try to print the test page, or anything els, I get a message saying "processing" the light on the printer flashes twice then the message changes to "idle- finished page 1..." but nothing has been printed.
I have tried the "troubleshooting" but it comes up with nothing

I have done a search on this forum and found only stuff related to installing canon's own drivers which I will probable have to try if I can not fix this.


My set up info:
9.10 64bit
raid1

Thanks for any help.
Bryan.

PS I have checked that the printer actually works on my old windoze pc.

---

### Post by monkeychild on 2010-05-04
Hi,
I have just sorted mine this instant.
I did it by:-

Open Terminal and type
sudo apt-get install cups libcups2 libcups2-dev build-essentials
sudo /etc/init.d/cups restart (just incase)

Downloaded the drivers from cannons website 
[http://software.canon-europe.com/software/0031336.asp?model=](http://software.canon-europe.com/software/0031336.asp?model=)

Extracted the files

cd into the directory then in terminal (as deb installer kept failing it????)
sudo dpkg -i cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i cnijfilter-ip3600series_3.00-1_i386.deb

powered on the printer and et voila 

Hope that helps, as I spent ages getting this working :)

---

### Post by Bryan55 on 2010-05-06
Hi Monkeychild.
[COLOR=Black]
Thanks for the help.[/COLOR]

I tried what you suggested but I got this at the first step

bryan@Bydand:~$ sudo apt-get install cups libcups2 libcups2-dev build-essentials[sudo] password for bryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
libcups2 is already the newest version.
[COLOR=Red]E: Couldn't find package build-essentials[/COLOR]
[COLOR=Black]
I carried on but with no success.

Bryan
[/COLOR]

---

### Post by Bryan55 on 2010-05-11
Hi.

I found that you need to delete the none functioning printer from the system before the new drivers will come into effect.

Bryan.

---

### Post by johanbove on 2011-07-01
Today is a good day. Not sure what happened, but the printer drivers "kicked-in". The printer is working fine now.

My original post:

> Hi, i'm having troubles getting this printer to work on 11.04, having a similar problem as described in the original post of this thread. The printer seems to install just fine, yet doesn't want to print.

I tried installing the driver packages but am getting stuck at missing dependencies.

Do you know if there's a way to cleanly uninstall all printer drivers? To start over, let's say to not have to re-install the OS.

I mean, where do printer drivers actually go once you install them?
On Windows this was pretty simple to find out, yet I find this on Linux extremely difficult since it looks like drivers are saved anywhere...

---

