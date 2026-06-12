---
title: "Printer Paused - Won't Resume"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by skjantzen on 2006-01-06
I unplugged my USB printer (HP Deskjet 5740 which has been working fine up till today) so that I could install some hardware (new DVD burner) and forgot to plug it back in. In the meantime family members sent a bunch of stuff to the printer. In the upper right corner of the screen is the printer icon with a red exclamation point. Mouseover says HP-Deskjet-5740-Paused. If I click on it, I see the jobs but it won't let me cancel any of them. Reboot does nothing. Unplugging and plugging printer, nothing. Tried to use System-->Administration-->Printing to delete printer and reinstall but I can't delete the current printer. It also says it is paused. I click on Resume and it doesn't do anything.


Scott

---

### Post by skjantzen on 2006-01-07
[QUOTE=skjantzen]I unplugged my USB printer (HP Deskjet 5740 which has been working fine up till today) so that I could install some hardware (new DVD burner) and forgot to plug it back in. In the meantime family members sent a bunch of stuff to the printer. In the upper right corner of the screen is the printer icon with a red exclamation point. Mouseover says HP-Deskjet-5740-Paused. If I click on it, I see the jobs but it won't let me cancel any of them. Reboot does nothing. Unplugging and plugging printer, nothing. Tried to use System-->Administration-->Printing to delete printer and reinstall but I can't delete the current printer. It also says it is paused. I click on Resume and it doesn't do anything.
[/QUOTE]

[Later...next day...]

I've continued to work on this problem and can't figure it out. I've tried several command line options. 
$ sudo lpc
lpc>
...10 minutes later, still nothing happening....

Thought maybe if I switch to su, that might help...
# lprm
Password for root on 192.168.1.100?
Password for root on 192.168.1.100?
lprm: Unable to cancel job(s)!

When asked for "Password for root..." I entered the same password as I did to get su. I also tried my regular sudo password but still nothing. Eventually I just pressed "enter" and then  got the last line.

What gives?

Should I uninstall cups and anything else having to do with printing and start again? Do I reinstall Ubuntu? Is it broken?

Scott

---

### Post by imranj on 2006-01-07
Did u try installing, hmm, as a new printer again?


[QUOTE=skjantzen][Later...next day...]

I've continued to work on this problem and can't figure it out. I've tried several command line options. 
$ sudo lpc
lpc>
...10 minutes later, still nothing happening....

Thought maybe if I switch to su, that might help...
# lprm
Password for root on 192.168.1.100?
Password for root on 192.168.1.100?
lprm: Unable to cancel job(s)!

When asked for "Password for root..." I entered the same password as I did to get su. I also tried my regular sudo password but still nothing. Eventually I just pressed "enter" and then  got the last line.

What gives?

Should I uninstall cups and anything else having to do with printing and start again? Do I reinstall Ubuntu? Is it broken?

Scott[/QUOTE]

---

### Post by skjantzen on 2006-01-07
I did try to install as a new printer via System --> Admin --> Printing. Won't let me delete the old one or install a new one. 

SJ

---

### Post by gosh on 2006-01-07
How about System -> Administration -> Services and then stopping and restarting CUPS?

---

### Post by skjantzen on 2006-01-07
Tried stopping then restarting cups. Didnt' help. Stopped cups a second time and then went to System --> Administration --> Printing but then it says that it can't find the cups server (No kidding). Started cups again. Went back to System --> Administration --> Printing and tried to delete printer and create new printer. Still won't let me.

SJ

---

### Post by Amon_Re on 2006-01-07
[QUOTE=skjantzen]Tried stopping then restarting cups. Didnt' help. Stopped cups a second time and then went to System --> Administration --> Printing but then it says that it can't find the cups server (No kidding). Started cups again. Went back to System --> Administration --> Printing and tried to delete printer and create new printer. Still won't let me.

SJ[/QUOTE]

You can manually remove the printer the following way:

sudo nano /etc/cups/printers.conf

Example printers.conf:
```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed Jan  4 07:35:40 2006
<DefaultPrinter LaserJet-5P>
Info LaserJet-5P
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```

By deleting the <printer></printer> section you effectively remove the printer.
Stop cups, edit the file (make a backup first just in case) and start cups again.

---

### Post by skjantzen on 2006-01-07
I used Synaptic Package Manager to uninstall all packages related to cups. I then rebooted the computer and used Synaptic to reinstall cupsys, foomatic, gnome-cups-manager, hpijs, and ijs gimpprint (and all associated packages). Again rebooted. Then went to System--> Administration--> Printing and now get the error: "The Cups Server could not be contacted." When I go to System--> Administration--> Services, cupsys is checked off. I deslected it and then started it again, then went back to printing and still get the same error mesage that the cups server could not be contacted.

Any suggestions?

SJ

---

### Post by Amon_Re on 2006-01-07
[QUOTE=skjantzen]I used Synaptic Package Manager to uninstall all packages related to cups. I then rebooted the computer and used Synaptic to reinstall cupsys, foomatic, gnome-cups-manager, hpijs, and ijs gimpprint (and all associated packages). Again rebooted. Then went to System--> Administration--> Printing and now get the error: "The Cups Server could not be contacted." When I go to System--> Administration--> Services, cupsys is checked off. I deslected it and then started it again, then went back to printing and still get the same error mesage that the cups server could not be contacted.

Any suggestions?

SJ[/QUOTE]

Did you stop cups prior to removing it? You might have a stale deamon running on the port cups uses (631 iirc), if this is the case, a simple reboot solves it (or going to the console & killing the task).

To check (and or kill it from the console):

**sudo ps ax | grep "cups"**

This should give you something like this:

```
 9808 ?        Ss     0:08 gnome-cups-icon --sm-client-id default3
10483 ?        SNs    0:17 /usr/sbin/cupsd -F
29444 pts/0    S+     0:00 grep cups
```

To kill it:
**kill -9 10483**

Substitute the number with the one from your result, or simply reboot

---

### Post by skjantzen on 2006-01-07
I tried what you suggested, but when I do "sudo nano /etc/cups/printers.conf" the file is empty. How do I stop and start cups from the command line. I tried the following but no luck.

scott@aragorn:~$ sudo service cups stop
sudo: service: command not found
scott@aragorn:~$ sudo service cups restart
sudo: service: command not found

[QUOTE=Amon_Re]You can manually remove the printer the following way:

sudo nano /etc/cups/printers.conf

Example printers.conf:
```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed Jan  4 07:35:40 2006
<DefaultPrinter LaserJet-5P>
Info LaserJet-5P
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```

By deleting the <printer></printer> section you effectively remove the printer.
Stop cups, edit the file (make a backup first just in case) and start cups again.[/QUOTE]

---

### Post by Amon_Re on 2006-01-07
[QUOTE=skjantzen]I tried what you suggested, but when I do "sudo nano /etc/cups/printers.conf" the file is empty. How do I stop and start cups from the command line. I tried the following but no luck.

scott@aragorn:~$ sudo service cups stop
sudo: service: command not found
scott@aragorn:~$ sudo service cups restart
sudo: service: command not found[/QUOTE]

sudo /etc/init.d/cupsys stop
sudo /etc/init.d/cupsys start

---

### Post by skjantzen on 2006-01-08
[QUOTE=Amon_Re]sudo /etc/init.d/cupsys stop
sudo /etc/init.d/cupsys start[/QUOTE]

I tried stopping and restarting cups, seemed to be successful, but still can't access System--> Administration --> Printing. Still says it can't find the cups server.

$ sudo /etc/init.d/cupsys stop
 * Stopping Common Unix Printing System: cupsd                           [ ok ]
$ sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                           [ ok ]

Anything else I can try. I'm ready to reinstall Ubuntu.

SJ

---

### Post by Amon_Re on 2006-01-08
[QUOTE=skjantzen]I tried stopping and restarting cups, seemed to be successful, but still can't access System--> Administration --> Printing. Still says it can't find the cups server.

$ sudo /etc/init.d/cupsys stop
 * Stopping Common Unix Printing System: cupsd                           [ ok ]
$ sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                           [ ok ]

Anything else I can try. I'm ready to reinstall Ubuntu.

SJ[/QUOTE]

Try opening the cups interface in firefox, address: [http://localhost:631](http://localhost:631)
Also, see the logs in /var/log, and perform **sudo /etc/init.d/cupsys status**

---

### Post by casfindad on 2006-01-10
Hi,

I was having the same problems as you. I had my printers working for one happy day, then everything hit the fan when I tried to network them last night. Printer was paused and no amount of cajoling could get it to print. A restart may have been associated with the problem. I think I solved it for my system, and I hope this helps you:

First I removed the paused print jobs and then the paused printer via System>Administration>Printing.

After googling "linux printer paused" and reading some other forums, I decided to remove cupsys via the following:

```
sudo apt-get remove --purge cupsys
```

The resulting messages:

```

Reading package lists... Done
Building dependency tree... Done
Package cups is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
casey@SagamoreHill:~$ sudo apt-get remove --purge cupsys
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  bluez-cups* cupsys* cupsys-driver-gimpprint* cupsys-driver-gimpprint-data*
  hplip-base* hplip-data* ubuntu-desktop*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 28.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124934 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing bluez-cups ...
Removing cupsys-driver-gimpprint ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Purging configuration files for cupsys-driver-gimpprint ...
Removing cupsys-driver-gimpprint-data ...
Removing hplip-base ...
 * Stopping HP Linux Printing and Imaging System                         [ ok ]
Purging configuration files for hplip-base ...
Removing hplip-data ...
Removing cupsys ...
 * Stopping Common Unix Printing System: cupsd                           [ ok ]
Purging configuration files for cupsys ...
dpkg - warning: while removing cupsys, directory `/var/run/cups' not empty so not removed.
```

I then typed:

```
ls /etc/cups
```

to get

```
classes.conf  client.conf  cupsd.conf.O  pstoraster.convs
```

This confirmed that my cupsd.conf file was removed.

I then re-installed cupsys with 

```
sudo apt-get install cupsys
```

Resulting message:

```
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  cupsys-driver-gimpprint foomatic-bin xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf hplip
The following NEW packages will be installed:
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8963kB of archives.
After unpacking 16.3MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/main cupsys 1.1.23-10ubuntu4 [8963kB]
Fetched 8963kB in 45s (197kB/s)

Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 123498 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.1.23-10ubuntu4_i386.deb) ...
Setting up cupsys (1.1.23-10ubuntu4) ...
 * Starting Common Unix Printing System: cupsd                           [ ok ]


```

I checked /etc/cups and found

```
certs         cupsd-browsing.conf  interfaces  pdftops.conf  pstoraster.convs
classes.conf  cupsd.conf           mime.convs  ppd           raw.convs
client.conf   cupsd.conf.O         mime.types  ppds.dat      raw.types
```

So now I had a brand spankin' new cupsd.conf.

I re-installed my printer with System>Administration>Printing and voila! I was able to print a test page. I then opened up a text document and was able to print that as well. And there was much rejoicing...

You'll notice that my purge removed some packages that were not replaced in my installation of cupsys. After reading the package notes for the missing packages in Synaptic, I decided to re-install cupsys-gimpprint-driver (and -data) and hplip-base (and -data). I'll let you know if this screws things up.

Who says printer setup in Linux is tough? :rolleyes: 

I still don't have any luck getting my iMac running OSX to see the new printer though. :???:

---

### Post by Tripmonkey_uk on 2006-01-17
Cheers for the info!
Doesn't work with an Epson R300 though unfortunatly :(

***EDIT***
After checking [http://localhost:631/]("http://localhost:631/") I found this:
Description: Stylus-Photo-R300
Location:
Printer State: stopped, accepting jobs.
"Unable to open USB device "usb://EPSON/Stylus%20Photo%20R300": No such device"
Device URI: usb://EPSON/Stylus%20Photo%20R300

The strage thing is that the printer worked straight after a clean install of Ubuntu. Printed a test page fine & didn't start to pause until I tried to print from Gimp?
I'm completely new at this, so if any one could help me out i'd be grateful.. Thanx!

***2nd EDIT***
Ok! after searching about the forums, I stumbled across this to change my permissions..
sudo chmod a+rw /dev/usb/lp0
Printed test page fine so I just need to do a restart & see if the settings hold.

***3rd EDIT***
[_This_]("http://www.ubuntuforums.org/showthread.php?t=118550") is what I found out.
If u've already got print jobs on pause then this should also start them printing straight away.
Hope it helps

---

### Post by ElaneFreuyh on 2007-09-28
I'l add my observations to this - it may be of use to someone

in short - printing over USB works - printing over network does not.

i have 2 printers installed - 
HP laserjet 2100M (over network)
HP photosmart C3100 ( USB cable)

both using hpijs driver. (have tried other available drivers - exactly the same problem)

heres the output from the cups system log after a failed print attempt

E [28/Sep/2007:09:28:09 +0100] cupsdReadClient: 9 IPP Read Error!
E [28/Sep/2007:09:28:53 +0100] [Job 10] No %%BoundingBox: comment in header!
E [28/Sep/2007:09:28:53 +0100] [Job 10] Unable to locate printer 'http'!
E [28/Sep/2007:09:28:53 +0100] PID 6246 (/usr/lib/cups/backend/socket) stopped with status 4!
E [28/Sep/2007:09:29:39 +0100] Resume-Printer: Unauthorized
E [28/Sep/2007:09:30:00 +0100] [Job 11] No %%BoundingBox: comment in header!
E [28/Sep/2007:09:30:00 +0100] PID 6490 (/usr/lib/cups/backend/socket) stopped with status 4!
E [28/Sep/2007:09:30:00 +0100] [Job 11] Unable to locate printer 'http'!
E [28/Sep/2007:09:30:03 +0100] PID 6489 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!

/----------------this section repeats every 5 seconds --------------------
E [28/Sep/2007:09:32:16 +0100] cupsdAuthorize: Local authentication certificate not found!
E [28/Sep/2007:09:32:16 +0100] cupsdAuthorize: Local authentication certificate not found!
E [28/Sep/2007:09:32:16 +0100] cupsdAuthorize: Local authentication certificate not found!
E [28/Sep/2007:09:32:16 +0100] cupsdAuthorize: Local authentication certificate not found!
---------------------------------------------------------------------------------------------/

hope thats of some help

---

