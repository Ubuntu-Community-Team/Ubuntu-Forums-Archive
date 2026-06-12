---
title: "gnome-cups-manager problem"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by svanac on 2005-05-17
hello, 

I want to setup printer HP PSC-2110.
# gnome-cups-manager
 
-(gnome-cups-manager:8903): WARNING **: failed request with status 1280

What's  wrong?

I have installed HPOJ!

---

### Post by harryc on 2005-05-17
Just change the /etc/cups/cupsd.conf and set the daemon user to root: Put "User root" in the file. Then restart cupsys.

---

### Post by David Haas on 2005-05-17
Hi svanac--Here is how I, and I think most other Ubuntu users, install their printers. First, make sure that the cupsys and foomatic packages are installed--check in Synaptic for this (System>Administration>Synaptic Package Manager). Then go to the printer GUI (System>Administration>Printing). Here, click on "New Printer" and select your printer. Then click on PPD file and click through the directories to locate the PPD file for your printer. It's located at /usr/share/cups/model/foomatic-ppds/HP, and the PPD file is HP-PSC_2110-hpijs.ppd.gz. I recently purchased an HP Deskjet 5740 and installed it this way in a few minutes. It works great.
David

---

### Post by svanac on 2005-05-18
When I want go to printer GUI, then show error message:

The CUPS server could not be contacted.

---

### Post by David Haas on 2005-05-18
The Cups server is cupsd and is in the sbin directory (/usr/sbin). So, you can check to see whether it's installed. If it's there and not being found (contacted), or if it's not there, then you could reinstall all the cupsys packages in Synaptic Package Manager, except for the BSD package.
David

---

### Post by harryc on 2005-05-18
Is cupsd running?

```
 ps aux | grep cupsd
```

Here's a valid result - 

harryc@ubuntu:~$ ps aux | grep cupsd
cupsys    9343  0.0  0.3   5592  1672 ?        SNs  13:50   0:14 /usr/sbin/cupsd

---

### Post by svanac on 2005-05-19
Yes, it's running 

baglov@pingvinar:~$ ps aux | grep cupsd
baglov    8987  0.0  0.0   3200   752 pts/0    R+   12:43   0:00 grep cupsd

---

### Post by harryc on 2005-05-19
Try uninstalling/reinstalling  gnome-cups-man and/or the latest version.

---

### Post by svanac on 2005-05-19
[QUOTE=harryc]Try uninstalling/reinstalling  gnome-cups-man and/or the latest version.[/QUOTE]
 and then I want restart cupsys

    baglov@pingvinar:~$ /etc/init.d/cupsys restart
     * Restarting Common Unix Printing System: cupsd
    cupsd: Child exited with status 13!

---

### Post by harryc on 2005-05-19
It should load and run when you boot. Try rebooting.

---

### Post by svanac on 2005-05-19
I'm try this and It's still doesn't work.

This may be a serious problem ](*,)

---

### Post by trash on 2005-05-19
I am having exactly the same problem here... I did have cups working as a print server but then switched the printer to another machine, edited the files and now the gnome print manager won't open, saying cups server can't be reached.. i have double checked all edits to files and still no go.
I will try reinstalling next.

I wish the cups people would start working on making cups MORE user friendly, yes I know there are people who say the documentation is great and it is but it is still WAY too heavy for the average user. They have a really great web interface which would be easy to build in lots of popup help and simplified information...  I don't understand why the default setting isn't a simple local printer setup, since for most users and newbs this would be the case and then people can edit once they get a feel and understanding for it.

---

### Post by jebe on 2005-05-19
hi,

with this printer you should use the hp printer software:

[http://hpinkjet.sourceforge.net/install.php#HPLIP](http://hpinkjet.sourceforge.net/install.php#HPLIP)

i got it working with kanotix but not yet with ubunut. (but hplip packages is apt-getable)

if you have more luck let met know

maybe usefull: [http://www.ubuntuforums.org/showthread.php?t=30063](http://www.ubuntuforums.org/showthread.php?t=30063)

jebe

---

### Post by nemesa on 2005-07-19
svanac: I had the same problem, but now i solve it.

First of all:
"
Yes, it's running

baglov@pingvinar:~$ ps aux | grep cupsd
baglov 8987 0.0 0.0 3200 752 pts/0 R+ 12:43 0:00 grep cupsd
"

no it isn't running. It's just the grep process, what you have started.

Try to reinstall the "libslp1" package with synaptic.
Then:
cd /etc/init.d/
sudo ./cupsys restart

---

### Post by trash on 2005-07-19
[QUOTE=nemesa]svanac: I had the same problem, but now i solve it.

First of all:
"
Yes, it's running

baglov@pingvinar:~$ ps aux | grep cupsd
baglov 8987 0.0 0.0 3200 752 pts/0 R+ 12:43 0:00 grep cupsd
"

no it isn't running. It's just the grep process, what you have started.

Try to reinstall the "libslp1" package with synaptic.
Then:
cd /etc/init.d/
sudo ./cupsys restart[/QUOTE]

I figured i'd give it a try too since nothing else is working, wouldn't let me reinstall 'libslp1' so i removed it along with cupsys, cupsys-driver-gimpprint, cupsys-driver-gimpprint-data and ubuntu-desktop and then reinstalled them all but still i'm getting cups cannot be contacted when i try to open the print manager.:(

---

### Post by taygan on 2005-09-07
DId you ever figure this out??  I'vew got an HP895 which is supposed to be a great linux printer, but I keep getting the 1280 error as well..  I need to restatr cups every time a add/remove a printer.

---

### Post by perlmonger on 2005-09-14
[QUOTE=harryc]Is cupsd running?

```
 ps aux | grep cupsd
```

Here's a valid result - 

harryc@ubuntu:~$ ps aux | grep cupsd
cupsys    9343  0.0  0.3   5592  1672 ?        SNs  13:50   0:14 /usr/sbin/cupsd[/QUOTE]
 I'm having trouble deciding if cups is installed correctly on my Kubuntu 5.04 system since I cannot print or configure the cups server. I get an error message that says cups server not running when I try to restart it from the gui. If I enter at the command line /etc/init.d/cupsys restart or /etc/init.d/cupsys start I get -su: cupsys: command not found.

Here's the result of ps -Al | grep cupsd 
5 S     7  7222     1  0  76   0 -  1724 -      ?        00:00:00 cupsd

and heres ps aux | grep cupsd
lp        7222  0.0  1.0   6896  2808 ?        Ss   11:05   0:00 /usr/sbin/cupsd
root      7556  0.0  0.1   1596   480 pts/1    S+   19:11   0:00 grep cupsd

I think all the packages are installed but I cannot log in at [http://localhost:631/](http://localhost:631/) to do any admin tasks. I tried the user account and the root account. Doesn't cups run as root? I installed the printer through the control center --> peripherals --> printers --> add printer wizard and it seemed to go ok but when I try to print a test page nothing happens.

Can someone help me figure out if cups server is running or not? I'm trying to install a local printer.

---

