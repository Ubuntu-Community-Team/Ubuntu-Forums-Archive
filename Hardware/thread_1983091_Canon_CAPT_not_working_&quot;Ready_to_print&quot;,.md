---
title: "Canon CAPT not working &quot;Ready to print&quot;, job registers as complete yet nothing prints"
date: 2012-05-19
forum: Hardware
---

### Post by thecopy on 2012-05-19
As the title says, my jobs registers as completed but nothing gets printed!

I have an LBP6300dn. The drivers i am using is compiled for amd64.

If i run 
[PHP]sudo captstatusui -P LBP6300dn[/PHP]

It reports "Ready to print". But nothing gets printed!

I have googled this matter for three days and each time i've gotten a little further - but right now i am stuck. Please help me!

---

### Post by thecopy on 2012-05-20
Please respond - i can also clean my printer through the captstatusui. It will print a clean-page.

---

### Post by Sivella on 2012-05-21
Hello,

> I have an LBP6300dn. The drivers i am using is compiled for amd64.
Where this driver downloading from, which version # ?
Could you tell us the main steps of the installation procedure you have followed ?
Thanks.

---

### Post by thecopy on 2012-05-21
> **Sivella said:**
> Hello,


Where this driver downloading from, which version # ?
Could you tell us the main steps of the installation procedure you have followed ?
Thanks.

It is v2.20

I used this script
[https://github.com/raducotescu/CanonCAPTdriver](https://github.com/raducotescu/CanonCAPTdriver)

---

### Post by Sivella on 2012-05-22
OK, but this script is quite "old" now, and as far as I know it is not updated since Ubuntu 11.04. There are some issues with 12.04 which are not managed by the script.

The CAPT driver v2.20 is OK. If you have succeed to install the 2 packages cndrvcups-common (first) and cndrvcups-capt without any error message you could keep it.

Here is a way to install your LBP6300n :
It could seem a bit hard, but don't worry, and come back if you have any question.

Firts, in :   System Settings --> Printing
Remove any printer(s).

If you have run the script, remove the auto-start for daemon ccpd created by the script :
> sudo update-rc.d -f ccpd remove1) Create the following directories/file if they are missing:
> sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon                      2) In 12.04 there is a new way to manage multiarch, and it doesn't comply with Canon CAPT driver. So you have to install "by hand" the 11.10 (onieric)  ia32-libs package. Take care the ia32-libs package in the 12.04 depots is a dummy/transition, it doesn't work.[INDENT]Install the dependences needed :
lib32asound2,
lib32ffi6,
lib32bz2-1.0,
lib32gcc1,
lib32stdc++6,
lib32z1,
lib32ncurses5,
lib32ncursesw5,
libc6-i386,
You can use the 12.04 version they work...
[/INDENT][INDENT]Download and install the ia32-libs package
[http://packages.ubuntu.com/oneiric/ia32-libs](http://packages.ubuntu.com/oneiric/ia32-libs)

Now you must lock this version to avoid update...
> echo "ia32-libs hold" | sudo dpkg --set-selections[/INDENT]3)   Register the printer:
> sudo /usr/sbin/lpadmin -p LBP6300 -m CNCUPSLBP6300CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E                      4) Register the printer with ccpd daemon:
> sudo /usr/sbin/ccpdadmin -p LBP6300 -o /dev/usb/lp0                      5)   Start ccpd daemon:
> sudo /etc/init.d/ccpd start                      6) Test install:
> captstatusui -P LBP6300                      will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.
Try to print something.

In   System Settings --> Printing   set your LBP6300 as default (right click on LBP6300 icon)
Probably on next boot, a "new" LBP6300-2 will appear. Don't worry about that and ignore it (the default is LBP-6300).  

If it works well, I will explain you how to  manage automatically ccpd daemon.

Good luck.

---

### Post by thecopy on 2012-05-25
> **Sivella said:**
> 
*--*
If it works well, I will explain you how to  manage automatically ccpd daemon.

Good luck.

Thank you for the response, but still it just shows up as completed but nothing gets printed. See attached screenshot

EDIT: I found this in /var/log/cups/error_log:

> 
erik@workstationubuntu:~$ cat /var/log/cups/error_log | grep "21170"
I [26/May/2012:00:02:13 +0200] [Job 59] Started filter /usr/lib/cups/filter/pstocapt3 (PID 21170)
D [26/May/2012:00:02:14 +0200] PID 21170 (/usr/lib/cups/filter/pstocapt3) did not catch or ignore signal 13.


---

### Post by Sivella on 2012-05-26
OK, we will try to cancel and restart a new install with the Canon drivers  from the PPA mickael-gruz.

1) Remove the 2 printers LBP6300 and LBP6300-2 (System settings --> Printing)

2) Purge the Canon drivers:[INDENT]> sudo apt-get purge cndrvcups*[/INDENT]3) Download and install transitional package "gs-esp" :[INDENT][http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)

[/INDENT]4) Download and install from the PPA depot the 2 packages :[INDENT][https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")

[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")

Install first cndrvcups-common.[/INDENT]5) Restart cups :[INDENT]> sudo service cups restart[/INDENT]Then go back to my previous post ---> 3)   Register the printer:

Hope it will works ...

---

### Post by thecopy on 2012-05-26
> **Sivella said:**
> Hope it will works ...

It did! Thank you very much Sivella! I use the printer often and it's expremely nice to be able to print directly from Ubuntu and not having to dual boot into Windows!

Why did the gs-esp package make it work?

---

### Post by Sivella on 2012-05-27
Very good news :cool:

> Why did the gs-esp package make it work?     This dummy package gives compatibility between the old gs-esp (used by Canon) and ghostscript (the new one) used by Ubuntu. So during drivers installation, they "think" Ubuntu used gs-esp ...

So now here is the way to "auto-manage" ccpd daemon.
see my post#6 [http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

It will work :D

---

### Post by Sivella on 2012-06-06
Hello thecopy,

Due to a new cups update, it seems that usblp module is now blacklisted (like it was with 11.10).
So the printer is not mounted in /dev/usb.

The solution is to cancel this blacklist.

Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf

Comment (#) the line : blacklist usblp
Here is my file :
> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp                      

---

### Post by jmgc on 2012-10-22
Sorry to revive the thread. Just wanted to thank Sivella for the excellent tutorial and state that it also works for my LBP3300.

Thank you so much, Sivella.

---

### Post by GoldIsCold on 2013-02-09
Hi, after rich history of installing drivers for my LBP2900 I have trouble with step #3 of the fifth post:
> sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

in responce of it i have:
> lpadmin: &#1055;&#1086;&#1073;&#1077;&#1076;&#1072;
which means
lpadmin: Success
and on the next step
> LBP2900 can't find in CUPS Spooler Entry!!
Have i something wrong with cups?
lpstat works the same way:
> lpstat -l
lpstat: &#1055;&#1086;&#1073;&#1077;&#1076;&#1072;


---

### Post by pdc on 2013-02-10
welcome to the forums

if you go here

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

.......the ubuntu howto....they recommend 

> sudo /usr/sbin/lpadmin -p LBP**** -m CNCUPSLBP5000CAPTK.ppd -v [COLOR="Red"]ccp://localhost:59787 -E[/COLOR]

(instead of the older [COLOR="Magenta"]ccp:/var/ccpd/fifo0 -E[/COLOR] ........where  you need to ensure that you have fifo directories created .........etc)

I saw reference that where folks followed posts by Sivella on hot to install......that he too has adopted the ccp://localhost:59787 -E method

I can only hope you are using 32bit ubuntu, as life does seem simpler that way

---

### Post by GoldIsCold on 2013-02-17
Thanks. Everything fine but printing have not happened yet).
And in /var/log/cups/error_log i can see this:
> E [17/Feb/2013:23:08:50 +0400] UbuntuLike: File "/usr/lib/cups/filter/texttopdf" has insecure permissions (0100777/uid=0/gid=0).
E [17/Feb/2013:23:08:50 +0400] [Job 18] Unable to start filter "texttopdf" - Success.
E [17/Feb/2013:23:08:50 +0400] [Job 18] Stopping job because the scheduler could not execute a filter.
Something wrong with users or groups?

PS 
777 was made by myself.
UbuntuLike is printer name.

---

### Post by pdc on 2013-02-17
the guide for installing the CAPT driver probably assumes a pretty standard setup;

I think you are concealing some differences in your setup; as compared to a basic install; 

(such as I have!!)

.......so help us understand......... what tweaks have you done to your setup?

> File "/usr/lib/cups/filter/texttopdf" has insecure permissions (0100777/uid=0/gid=0).

> 777 was made by myself.

---

### Post by GoldIsCold on 2013-02-17
Well, to be honest, i made nearly all different things from many sources in addition to this one.
But here is log entry before > sudo chmod -R 777 /usr/lib/cups/filter
> E [17/Feb/2013:22:46:28 +0400] UbuntuLike: Directory "/usr/lib/cups/filter" has insecure permissions (040755/uid=1000/gid=1000).
E [17/Feb/2013:22:46:28 +0400] [Job 15] Unable to start filter "texttopdf" - Success.
E [17/Feb/2013:22:46:28 +0400] [Job 15] Stopping job because the scheduler could not execute a filter.
E [17/Feb/2013:22:51:29 +0400] [Job 15] Stopping unresponsive job!

And i found this in the same log
> E [17/Feb/2013:23:32:47 +0400] Unknown directive SystemGroup on line 3 of /etc/cups/cupsd.conf.


---

