---
title: "HOWTO: canon i250 in Breezy (yes its working!)"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by duan on 2006-02-05
This is what was needed to get my canon i250 printer working on breezy.

I know it looks like a pain, but this printer is cheap and so is its ink so we got what we paid for right?

first of there used to be this requirement that the printer had to be connected to your system and powered up before you boot. I know this is not the unix/linux way but it is simpler than getting to figure out which drivers need to be reloaded/refreshed or whatever, so I just shut down, connected it all up and rebooted whether it was needed or not...)

open up a terminal an make a directory where  you want to save the needed files
```
mkdir ./scratch/i250/  
cd ./scratch/i250/
```

get the driver package:
```
wget http://www.livux.org/otros/canon-i250_2.3_i386.deb
```

get the libtiff3g debian package(this is the file no longer in ubuntu universe):
```
wget http://security.debian.org/pool/updates/main/t/tiff/libtiff3g_3.5.5-7_i386.deb
```
(if you have a normal x86 AMD or Intel pc like me)

if the file is not available, just surf to [http://security.debian.org/pool/updates/main/t/tiff/](http://security.debian.org/pool/updates/main/t/tiff/) and look at the files there, you need the libtiff3g_<version>_<your_architecture>.deb file and download it and place it in the directory where you are working

first install the tiff file:
```
sudo dpkg -i libtiff3g_3.5.5-7_i386.deb
```

then install the printer driver package:
```
sudo dpkg -i canon-i250_2.3_i386.deb
```

(this may fail because it is dependend on some more pacakges, they will be listed and you should be able to install them with apt, like cupsys2. Just make sure to install them all :
(sudo apt-get install cupsys2) etc.

once this is done you can install the actual printer driver:
```
sudo apt-get install canon-i250
```

at this stage you need to restart the cups tool, because it does not know about the new driver. In windows you would have to restart, and it would work here too, but ubuntu is a bit more refined so let's find the cups daemon process, kill it and restart it as root user:
(look for and kill "cupsys" -the first numer in the line of the  process number next to the /usr/sbin/cupsd -F line)
something like this: 
```
ps -ef | grep cups
...
cupsys   22381     1  0 20:26 ?        00:00:01 /usr/sbin/cupsd -F
...
dj@sprinkaan:~$ sudo kill 22381
```

restart cups in the background:
```
sudo /usr/sbin/cupsd -F &
```

you can close the terminal now :-)

now you can clicky-click and get it all done:
system > administration > printing

double click add printer
it sees the canon.. > forward

it should now display your new i250-ver.2.3 driver, just highlight it and click apply.

your printer icon will appear and you can print a test page, if nothing happens it may be that the job is paused, unpause it.

pin up your test page on the refrigirator.

---

### Post by Klaidas on 2006-02-27
WOOT, I did a search and I finally found how to set up my printer!

Reboot, must try it!

---

### Post by Klaidas on 2006-02-27
Dude, it prints!!!! THANKS!!! I thought it was impossible to set up my i250 under linux. :mrgreen: 

You should post this as a how-to \\:D/

---

### Post by duan on 2006-02-27
I don't know how to make a howto here. :-)

But I'm happy your printer works!!

Something else, the turboprint drivers work with a big logo over everything when you want to print, but the headcleaning and alignment stuff works perfectly....

Duan

---

### Post by pracslipkerm on 2006-06-26
I can now print almost 1 page...
The printer seems to stall 5 or 6 lines from the bottom. The light keeps flashing but nothing happens. I sent 2 pages of text to the printer (it is on USB 2.0 port)
Any Ideas would be very much appreciated - I might leave it for the night and see what it's done by the morning. Maybe better to try it on breezy instead of Dapper...
Thanks for the help guys - getting closer!
Cheers 
  Steve :-)

---

### Post by mwob on 2006-07-04
Thanks! The guide only covers i386 distro's though, any advice for me on my 64 bit distro?

Ta

---

### Post by Catfish81 on 2007-03-22
I'm having problems after trying to dpkg the canon file:

> catfish@delta:~/drivers/i250$ sudo dpkg -i canon-i250_2.3_i386.deb 
(Reading database ... 113104 files and directories currently installed.)
Preparing to replace canon-i250 2.3 (using canon-i250_2.3_i386.deb) ...
Unpacking replacement canon-i250 ...
dpkg: dependency problems prevent configuration of canon-i250:
 canon-i250 depends on libglade0; however:
  Package libglade0 is not installed.
 canon-i250 depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 canon-i250 depends on libpng2 (>= 1.0.12); however:
  Package libpng2 is not installed.
 canon-i250 depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
 canon-i250 depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing canon-i250 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 canon-i250
catfish@delta:~/drivers/i250$ ls


I've tried sudo apt-get install libglade0 (etc. etc.) but I get returned errors like:

> catfish@delta:~/drivers/i250$ sudo apt-get install libglade0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  canon-i250: Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
              Depends: libpng2 (>= 1.0.12) but it is not installable
              Depends: libxml1 (>= 1:1.8.14-3) but it is not going to be installed
              Depends: xlibs (> 4.1.0) but it is not installable
  libglade0: Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
             Depends: libxml1 (>= 1:1.8.14-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
catfish@delta:~/drivers/i250$ 


Is there a way to install all of these packages in one hit?

---

### Post by Catfish81 on 2007-03-26
I can't get it to install xlibs or libpng2.

It says:

> catfish@delta:~/downloads/i250$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkb-data
E: Package xlibs has no installation candidate


and

> catfish@delta:~/downloads/i250$ sudo apt-get install libpng2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libpng2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libpng2 has no installation candidate


Where can I get these packages from and how do I install them?
EDIT: I'm using Ubuntu 6.10, this is most likely the cause. Anyone know a work around?

---

### Post by Rich_li_ny on 2007-04-17
I too am having the same problem.    If anyone knows a woking link to this printer driver please drop me a note.

Rich

---

### Post by ubunny on 2008-03-09
I have a canon i250 which works fine under Windohz

followed instructions

used alien to make .deb files
used gnome file manager to install files
added the printer as ppd file 
loaded cups from localhost:631
tried to print test page.  All logs say it finished.  No errors but no printing either
tried uninstalling from cups and reinstalling.  Nothing.

any way to troubleshoot this?  I make the links to the lower libraries as well.

stumped
:confused:

---

