---
title: "Canon IRC3880 driver for ubuntu"
date: 2011-05-30
forum: Hardware
---

### Post by ilcontegis on 2011-05-30
Dear all

I desperately need to make this printer work on my laptop.
I have a DELL latitude E6320 with Ubuntu 11.04 64bit. 
I cannot find a proper driver. The only one I have found is on a japanese website and is only for 32bit [here]("http://cweb.canon.jp/drv-upd/lasershot/linux/lipslxlinux.html").
But when I try to install it I get error
```
matteo@matteo-dell:~/Downloads$ sudo dpkg -i --force-architecture ./cndrvcups-common_2.20-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cndrvcups-common:i386.
(Reading database ... 153661 files and directories currently installed.)
Unpacking cndrvcups-common:i386 (from .../cndrvcups-common_2.20-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cndrvcups-common:i386:
 cndrvcups-common:i386 depends on libatk1.0-0 (>= 1.7.2).
 cndrvcups-common:i386 depends on libc6 (>= 2.3.2.ds1-21).
 cndrvcups-common:i386 depends on libglade2-0 (>= 1:2.4.2-2).
 cndrvcups-common:i386 depends on libglib2.0-0 (>= 2.6.0).
 cndrvcups-common:i386 depends on libgtk2.0-0 (>= 2.6.0).
 cndrvcups-common:i386 depends on libpango1.0-0 (>= 1.8.1).
 cndrvcups-common:i386 depends on libxml2 (>= 2.6.16).
 cndrvcups-common:i386 depends on zlib1g (>= 1:1.2.1).
 cndrvcups-common:i386 depends on cupsys | cups.
 cndrvcups-common:i386 depends on gs-esp.
 cndrvcups-common:i386 depends on libcups2 | libcupsys2 (>= 1.1.23).
dpkg: error processing cndrvcups-common:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-common:i386

```

Could you please help me? 
Thanks!

---

### Post by prshah on 2011-05-31
> **ilcontegis said:**
> I cannot find a proper driver. The only one I have found is on a japanese website and is only for 32bit [here]("http://cweb.canon.jp/drv-upd/lasershot/linux/lipslxlinux.html").

There's two things you can try:

a) There is a 64-bit rpm available. You can use a program called "alien" (it's in the repos) to convert the rpm to a deb for use in Ubuntu. It's not foolproof, but it usually gets the job done.

b) Extract the archives you have downloaded. Look for a .PPD file. You can use this in CUPS (Common Unix Printer System) to install your printer.

To use the PPD in CUPS, open the browser on your Ubuntu system. In the address bar, type ```
http://localhost:631
``` to open the CUPS (Common Unix Printing System) page.

If at any point CUPS asks for a username and password, give the username and password of any sudo capable user on the system.

On the CUPS main page, choose the "Administration" tab. Then choose "Add printer". From the options, choose as suitable for your printer.

Give the printer a name, and fill in whatever other information you feel relevant. Continue. 

In the next screen, you can provide a .PPD file if you have it available on the driver disk. If you have a PPD file, enter it's location and choose "Add printer".

Set your default options as suitable to you, including paper sizes, tray options, etc. 

Now your printer should be working fine. Please try a test page, and post back here if you have any problems.

---

### Post by ilcontegis on 2011-05-31
First of all thank you for your answer.
I converted the driver with alien as suggested and I have successfully installed it.
I configured the printer. I can see the ink levels, but the printer only prints the following message:
**** Unable to open the initial device, quitting.

I have never seen such error and I can't understand its meaning.
I hope you know what to do next.

I also have another problem I could install only 1 of the two packages provided on the japanese website.
The other gives me the following error, and I cannot remove the package that is already installed

```

matteo@matteo-dell:~/Desktop$ dpkg -i cndrvcups-common_2.20-2_amd64.deb 
dpkg: error: requested operation requires superuser privilege
matteo@matteo-dell:~/Desktop$ sudo dpkg -i cndrvcups-common_2.20-2_amd64.deb 
dpkg: error processing cndrvcups-common_2.20-2_amd64.deb (--install):
 cndrvcups-common: 2.20-2 (Multi-Arch: no) is not co-installable with cndrvcups-common:i386 2.20-1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 cndrvcups-common_2.20-2_amd64.deb
matteo@matteo-dell:~/Desktop$ sudo apt-get remove cndrvcups-
cndrvcups-common  cndrvcups-lips4   cndrvcups-lipslx  
matteo@matteo-dell:~/Desktop$ sudo apt-get remove cndrvcups-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'cndrvcups-common' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


Thank you for your time
Regards

---

### Post by ilcontegis on 2011-06-19
up anyone?
I need it for work pls....Or I must go back to windows -.-

---

### Post by rennradl on 2011-06-21
I had trouble installing the driver for our IR3345  (cndrvcups-common,   cndrvcups-ufr2-uk). The solution was to convert the 64bit rpm with alien AND to have thi i386 libs installed. Some Canon drivers are still partly 32bit (i.e. do a sudo apt-get install ia32-libs)

---

### Post by ilcontegis on 2011-06-21
> **rennradl said:**
> I had trouble installing the driver for our IR3345  (cndrvcups-common,   cndrvcups-ufr2-uk). The solution was to convert the 64bit rpm with alien AND to have thi i386 libs installed. Some Canon drivers are still partly 32bit (i.e. do a sudo apt-get install ia32-libs)
Thanks for posting, however this is what I already did (and already explained in the previous post). The problem is still there.

---

### Post by ClashTheBunny on 2011-08-09
Any luck with this?  I'm struggling with the exact same issue.

---

### Post by ClashTheBunny on 2011-08-09
Oops, spoke too soon, this worked:

```
sudo dpkg -P cndrvcups-ufr2-uk:i386
sudo dpkg -P cndrvcups-common:i386
```

Then ```
dpkg -i *deb
``` in the alien output directory.

---

