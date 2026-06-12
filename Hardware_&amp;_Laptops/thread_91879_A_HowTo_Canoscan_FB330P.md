---
title: "A HowTo: Canoscan FB330P"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by Bigglez on 2005-11-18
HOW TO GET YOUR CANOSCAN FB330P TO SCAN
=======================================
Greetings, this is a hasty howto. I hope it helps you!
I used Kubuntu 5.04 to do this. It may work on Ubuntu (I should hope...) and it should work on all versions of both.

(NOTE: All commands and lines with quotes should be entered without the quotes.)

(Warning:I did use kynaptic to install "sane-extra" but I think that was a waste of time.)

The canon_pp driver supports all these scanners:
CanoScan FB320P 
CanoScan FB620P
CanoScan FB330P
CanoScan FB630P
CanoScan N340P
CanoScan N640P
CanoScan N640P ex
It comes in the sane-backend 1.0.15 package.

Make sure you are root before you test your CanoScan. It will NOT work as a normal user. I usually open a terminal and type "sudo -s" to be root for as long as I like. 

There is nothing you need to 'run' or 'refresh' to get SANE to work. The main app is "scanimage". If it does not detect your scanner then check your configurations.

1. View /etc/canon_pp.conf and make sure it looks okay, check for parport0. Do a "dmesg | grep port" and look for parport0 too.
If you see parport1 for example, then your canon_pp.conf should reflect that (I guess).

2. Edit /etc/sane.d/dll.conf ensure "net" and "canon_pp" are not remarked, remove the # in front of them. You can put a # in front of all the others if you want (I did).
* Hint: If you cannot seem to edit a file when you are root then open another terminal and "sudo kwrite somefile" will work.

3. Now enter "scanimage -L" (as root). You should see:
```
device `canon_pp:parport0' is a CANON FB330P flatbed scanner
device `net:localhost:canon_pp:parport0' is a CANON FB330P flatbed scanner
```

It should be working at this point. Ensure you did steps 1&2 properly. If this fails, there are some tips at end of this doc.

Steps to scan as normal user
============================
1. Edit /etc/saned.conf and put "localhost" at the end.

2. Put this line in /etc/inetd.conf
"sane-port stream tcp nowait root.root /usr/sbin/saned saned"

3. Open /etc/services and search for "sane". Insert a new row under that and add:
"sane-port 6566/tcp # SANE network scanner daemon"
(Get the tabs right)
Delete the original row, the one starting with "sane")
Save.

4. restart inetd with "/etc/init.d/inetd restart"

5. Test by "saned -d" - you should only see errors to the effect of "couldn't bind" - never mind, that's cool.

6. Open a normal-user account and: 
"scanimage -L"
Should detect the scanner.

USEAGE TIPS:
============
Kooka crashes all the time. I have given up.
I use the command-line now. 
"scanimage -h" Will give you options, at the end are canon-specific options.
Full-page, good quality colour:
"scanimage --mode Color --depth 12 -x 216mm -y 297mm > test1"
Will put the scan into 'test1' (It's a PNM image type - whatever that is), but I assume conversion is easy with "convert")

Stuck tips:
======
If you are still stuck:
man sane
man saned
man sane-canon_pp
[http://www.linuxprinting.org/download/digitalimage/Scanning-as-Normal-User-on-Wierd-Scanner-Mini-HOWTO.txt](http://www.linuxprinting.org/download/digitalimage/Scanning-as-Normal-User-on-Wierd-Scanner-Mini-HOWTO.txt) (Very old info, but I used some of it.)
Sane website.
Are what I used to get this working.

Well, that's all folks
d : )

---

### Post by kr0n1x on 2007-10-16
i haven't "inetd" service...

can anyone update this "how-to" for feisty? thanks

---

### Post by maphew on 2007-12-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/173393](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/173393) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **kr0n1x said:**
> i haven't "inetd" service...

can anyone update this "how-to" for feisty? thanks

It's a lot easier to get xsane to recognize the scanner now, though I can only get mine to work in grey scale for some reason I've yet to determine (Bug #173393). All I had to do was steps 1 & 2 and then run xsane as root. To get the scanner to work for a normal user simply `chmod 777' the parallel port (there may be a security issue with this, but for my home system I'm not concerned).

sudo chmod 777 /dev/parport0

---

### Post by kr0n1x on 2007-12-09
when i launch xsane as normal user, it remains "searching devices"... and stay as is.

with root, it works after some seconds..

---

### Post by maphew on 2007-12-12
even after chmod'ing parport0 it doesn't work? hmmm. This is just a guess but perhaps the user needs to have the "use scanners" user privilige checked under System > Users & Groups > [username]

There is this related message, but I didn't try the solution propsed there: [http://ubuntuforums.org/showpost.php?p=1194786&postcount=8](http://ubuntuforums.org/showpost.php?p=1194786&postcount=8)

---

### Post by kr0n1x on 2007-12-12
permissions in groups seems correct :(

---

