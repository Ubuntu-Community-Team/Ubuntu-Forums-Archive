---
title: "Existing Printer (Canon Pixma iP4950) ceased being recognised"
date: 2017-01-24
forum: Hardware
---

### Post by davethesteam on 2017-01-24
My printer has ceased being recognised by computer (16.04LTS).
Previously worked perfectly but was getting discomboblutade with large .pdf files.
System info says the system is "connected to host".
Tried finding printer - just says printer not installed.
Unable to find it
All connections checked (seem OK).
Have checked and installed cups - terminal states up to date.
Tried using the Canon site but unable to find the driver within the extracted files.
Help please!!!

---

### Post by pdc on 2017-01-24
If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100396602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100396602.html) to the Canon Asia website, you can download the debian package driver that Canon supply; (they also do an rpm and a source code package):

it should come down to you as cnijfilter-ip4900series-3.60-1-deb.tar.gz

assuming you download the package and save it to your Downloads folder, then if you open a terminal, the commands should be: sequentially:

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-ip4900series-3.60-1-deb.tar.gz
cd cnijfilter-ip4900series-3.60-1-deb
sudo ./install.sh[/COLOR]

........ that should create a new entry for you; might be best to delete any existing entries .... if they don't work, so you only have once choice after installing the Canon drivers

________________

some of these older Canon packages need [COLOR="#008000"]libtiff4[/COLOR] and if the install script does not complete; (watch the terminal and read what it says .......);

then get [COLOR="#008000"]libtiff4[/COLOR] from the Debian repositories: [https://packages.debian.org/wheezy/libtiff4](https://packages.debian.org/wheezy/libtiff4)

........... scroll down the page to the bottom ........ if you run 64bit you need [COLOR="#0000FF"]amd64[/COLOR] and if you run 32bit, you need [COLOR="#0000FF"]i386 [/COLOR]

..... probably best to install before starting the Canon driver install to be sure ...... it's a tiny (and safe) file

---

### Post by davethesteam on 2017-01-25
Many thanks indeed pdr.
I now have the printer showing in the printer section of 'Details'.
I have set it as default.
Unfortunately the printer is not printing - the activity light on the front of the printer is on green but not blinking.
There was a comment in the terminal when undertaking your instruction about 'lbadmin' but I did nothing with that.
Thanks in advance for further advice

---

### Post by pdc on 2017-01-25
it was working on 16.04; is that right? 

Ubuntu have a wiki to check through; [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

some of it may look very tricky; but if you attempt to wade through the various bits: .......... things like .......... are  you happy the usb port is all good: ie can you show it works well with another device etc 

If you are in the Midlands, there may well be a linux users group close by so they might help too

---

### Post by davethesteam on 2017-01-25
Hello again

I have been through the items on debugging of printers.
Herewith the full report:


Error: No such file or directory: can't open '/dev/usb/lp1'


david@david-All-Series:~$ sudo usb_printerid /dev/usb/lp1
Error: No such file or directory: can't open '/dev/usb/lp1'
david@david-All-Series:~$ lpinfo -v
lpinfo: cups-deviced failed to execute.
david@david-All-Series:~$ [/CODE]

I can see there is a problem with CUPS and LP1 - what should I do now please?

---

### Post by davethesteam on 2017-01-25
Well, after all the suggestions you gave - which were brilliant, thank you, I was able to go into the printer configuration box (system settings/printers/settings/make and model / change) and after a few seconds was presented with a set of drivers. Changed to appropriate description and Bingo!!
Thanks again for your great help

---

### Post by pdc on 2017-01-25
glad it is working; when I saw the report > pinfo: cups-deviced failed to execute. in the printout you gave; for the command > lpinfo -v, that seemed abnormal; 

not many google hits on it but one here [https://forums.linuxmint.com/viewtopic.php?t=191712](https://forums.linuxmint.com/viewtopic.php?t=191712) covers it ...... cups was not installed; which is shown as ii and instead it was rc ........r meaning removed ...........

can you check with the command > [COLOR="#FF0000"]dpkg -l | grep cups[/COLOR] that the packages seem installed?        ....... paste that command as the vertical line in the middle is a pipe command (ie shift-backslash..)

---

### Post by davethesteam on 2017-01-26
Hi again
Oh dear, there I was thinking it was sorted. An error appeared on the top right hand side of the main menu which then asked for a partial upgrade.
This is the log for partial upgrade:
Jan 25 23:34:37 david-All-Series pkexec[12264]: david: Executing command [USER=root] [TTY=unknown] [CWD=/home/david] [COMMAND=/usr/lib/ubuntu-release-upgrader/do-partial-upgrade --frontend=DistUpgradeViewGtk3]
Jan 25 23:36:30 david-All-Series polkitd(authority=local): Unregistered Authentication Agent for unix-session:c1 (system bus name :1.58, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)

This I did and the problem returned....
This time, in trying to log to:
system settings/printers/connect   I was met with:
"Printing Service not available. Start the service on this computer or connect to another server"
Pressing 'connect'
 error message comes up ' cups failed to connect to server'.

I have tried reloading cups.
I have worked through the 'debugging printer problems' on the Ubuntu Wiki.

All with no effect.
Is there any thing I can do to restore my printer please?

---

### Post by pdc on 2017-01-27
It might be best if a forum moderator moved this thread now to the Install/Upgrades forum; 

as you seem to have issues with what packages are installed; 

maybe when that gets sorted; we can check cups is properly installed

---

### Post by wildmanne39 on 2017-01-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end

You need to start another thread for the other issues we allow only one issue per thread.

If this issue is not solved go back and remove the solved by using thread tools.

For the record never do a partial upgrade it will always break something in your system, they can be caused by the repository's servers having issues and it usually clears up quickly.

Please change the title back to the original, if you need moderator attention their is a report button at the left bottom of the text window click on it and tell us what you need.
Thanks

---

### Post by coffeecat on 2017-01-27
> **pdc said:**
> It might be best if a forum moderator moved this thread now to the Install/Upgrades forum; 

This thread is in the correct sub-forum at the moment, for which the strapline reads:

> Problems getting your hardware to work with Ubuntu? Post your questions here.

The [Installation & Upgrades sub-forum](https://ubuntuforums.org/forumdisplay.php?f=333) is not for help with installing packages or updates - its strapline reads:

> For questions about upgrading and installation of your new Ubuntu OS.

I think this thread is about getting some hardware to work. There appears to be a reference to a partial upgrade in the OP's latest post but this doesn't appear to have been suggested. This needs to be clarified.

---

