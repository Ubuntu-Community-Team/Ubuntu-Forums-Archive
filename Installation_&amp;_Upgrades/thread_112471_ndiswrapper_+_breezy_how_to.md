---
title: "ndiswrapper + breezy? how to?"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by crixtiano on 2006-01-04
Hi, I'm a Ubuntu's user since Warty version.

I have used ndiswrapper for wireless internet connection for warty and hoary version. But Yesterday I have installed Breezy version and I can't install ndiswrapper.

I have tried to install ndiswrapper mannually first, like I always did in warty an hoary versions. But to install manually I need the kernel sources to compile ndiswrapper.

The problem is I can't find kernel sources from Breezy Install CD. 

So, I did the plan B: install ndiswrapper with apt, and I did:

$ sudo apt-get install ndiswrapper
$ sudo ndiswrapper -i mrv8ka51.inf
$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper

The 4th link it didnt work. modprobe tell me it can't find ndiswrapper module.

So, how to install ndiswrapper in breezy version?

---

### Post by katu on 2006-01-04
I don't know if this will help, but the package for ndiswrapper is called 
**ndiswrapper-utils** and not ndiswrapper. therefore point 1. should give you an error that the package is not found. 
try installing:
```

sudo apt-get install ndiswrapper-utils

```

and see what it says. then if it still crashes try posting the output of:
```

ndiswrapper -l

```

cheers,
Katu

---

### Post by crixtiano on 2006-01-04
I did it and doesn't work

---

### Post by katu on 2006-01-04
If you don't post the error messages here it will be near impossible to help you. Please post here the output of these commands:
```

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i mrv8ka51.inf
sudo ndiswrapper -m
sudo ndiswrapper -l
sudo modprobe ndiswrapper

```

Katu

---

### Post by az on 2006-01-04
[QUOTE=crixtiano]I did it and doesn't work[/QUOTE]
What do you mean.  The kernel module is already in your running kernel and the utility is on the install cd.  It is cached on your harddrive diring the install.  Install ndiswrapper-utils should work fine.

Now, if your windows driver no longer works, it is probably because ndiswrapper is developer using the most current driver.  The one that come with your card may be too old for the version of ndiswrapper that is shipped with breezy.  Try looking on the manufacturer's site for a newer version of the windows driver.  You can also check the wiki, there is a link to the ndiswrapper wiki where they list the proper windows drivers.

---

### Post by n00b13 on 2006-01-04
Hi,

I installed breezy badger for the first time last night.

I used mandrake for about 5 hours last year until when rebooting, my harddrive died. 

I have tried to get ndiswrapper to work, but to no avail

sorry for the long post, but i hope somebody can help me....

tristan@tristan-linux:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tristan@tristan-linux:~$ sudo ndiswrapper -i tnet1130.inf
Installing tnet1130
cp: cannot stat `tnet1130.inf': No such file or directory
tristan@tristan-linux:~$ sudo ndiswrapper -i TNET1130.inf
tnet1130 is already installed. Use -e to remove it
tristan@tristan-linux:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
tristan@tristan-linux:~$ sudo ndiswrapper -l
Installed ndis drivers:
tnet1130        invalid driver!
tristan@tristan-linux:~$ sudo ndiswrapper -e
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
tristan@tristan-linux:~$ sudo ndiswrapper -e tnet1130.inf
Driver tnet1130.inf is not installed. Use -l to list installed drivers
tristan@tristan-linux:~$ sudo ndiswrapper -l
Installed ndis drivers:
tnet1130        invalid driver!
tristan@tristan-linux:~$ sudo ndiswrapper -l
Installed ndis drivers:
tnet1130        invalid driver!
tristan@tristan-linux:~$ sudo ndiswrapper -e tnet1130.inf
Driver tnet1130.inf is not installed. Use -l to list installed drivers
tristan@tristan-linux:~$ sudo ndiswrapper -e TNET1130.inf
Driver TNET1130.inf is not installed. Use -l to list installed drivers
tristan@tristan-linux:~$ sudo ndiswrapper -l
Installed ndis drivers:
tnet1130        invalid driver!
tristan@tristan-linux:~$ sudo ndiswrapper -i /tmp/winxp/TNET1130.INF
tnet1130 is already installed. Use -e to remove it
tristan@tristan-linux:~$ sudo ndiswrapper -e tnet1130
tristan@tristan-linux:~$ sudo ndiswrapper -l
No drivers installed
tristan@tristan-linux:~$ sudo ndiswrapper -i /tmp/winxp/TNET1130.INF
Installing tnet1130
cp: cannot stat `/tmp/winxp/TNET1130.INF': No such file or directory
tristan@tristan-linux:~$ sudo ndiswrapper -i tmp/winxp/TNET1130.INF
tnet1130 is already installed. Use -e to remove it
tristan@tristan-linux:~$ sudo ndiswrapper -l
Installed ndis drivers:
tnet1130        invalid driver!
tristan@tristan-linux:~$ sudo ndiswrapper -e tnet1130
tristan@tristan-linux:~$ sudo ndiswrapper -l
No drivers installed
tristan@tristan-linux:~$ sudo ndiswrapper -i tmp/winxp/TNET1130.INF
Installing tnet1130
cp: cannot stat `tmp/winxp/TNET1130.INF': No such file or directory
tristan@tristan-linux:~$ sudo ndiswrapper -e tnet1130


EDIT:

wopps, i just found out that linux is case sensitive, silly me

path was /tmp/WinXP/tnet1130.inf

-30 e-cred points

---

### Post by az on 2006-01-04
So, is it working?

If not, then the driver is too old.  Try to find a more recent version of the wornows driver for your card.  You may also be using the wrong driver for your card.  Often the  windows driver comes with more than one .inf file.

See the ndiswrapper wiki.  Google ndiswrapper wiki and look at the listed cards.  See what drivers work with them and where to download them.

Edit:  Here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

