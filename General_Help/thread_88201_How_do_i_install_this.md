---
title: "How do i install this?"
date: 2005-11-09
forum: General Help
---

### Post by Nicktu on 2005-11-09
How would I go about installing this file?


[http://armagetronad.net/downloads/index.php](http://armagetronad.net/downloads/index.php) I want to install it for ubuntu linux. Please explain which to download and how to run installation. Thanks! :)

---

### Post by Kyral on 2005-11-09
Download the one that says "deb", then open a terminal and go to the directory where you downloaded it and 

```
sudo dpkg -i <nameoffile>
```

---

### Post by Nicktu on 2005-11-09
i have downloaded the deb. Now i am in the terminal what should i write? I'm new please be step by step.

---

### Post by Kyral on 2005-11-09
Where did you download it to?

Also look over my Terminal For Beginners for a tutorial in the Terminal

---

### Post by Nicktu on 2005-11-09
I just did and i didn't understand it, although i like anime. Haha. It's on my desktop.

---

### Post by Kyral on 2005-11-09
```
cd Desktop
```

```
sudo dpkg -i <nameoffile>
```

---

### Post by Nicktu on 2005-11-09
i typed in [HTML]sudo dpkg -i <armagetronad_0.2.7.1-8_i386.deb>[/HTML] and recieved

sytax error near inexpected token 'newline' 


The file appears to be some sort of archive or something? Maybe download the file and try yourself, thanks for your help by the way. Still not sure why it isn't working.


EDIT: i typed what i typed in wrong

---

### Post by Nicktu on 2005-11-09
ok i figured it out, now i recieve this


[HTML]nick@Nick:~/Desktop$ sudo dpkg -i armagetronad_0.2.7.1-8_i386.deb
Password:
Selecting previously deselected package armagetronad.
(Reading database ... 58010 files and directories currently installed.)
Unpacking armagetronad (from armagetronad_0.2.7.1-8_i386.deb) ...
dpkg: dependency problems prevent configuration of armagetronad:
 armagetronad depends on armagetronad-common (= 0.2.7.1-8); however:
  Package armagetronad-common is not installed.
 armagetronad depends on libsdl-image1.2 (>= 1.2.3); however:
  Package libsdl-image1.2 is not installed.
dpkg: error processing armagetronad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 armagetronad
[/HTML]


??

---

### Post by Kyral on 2005-11-09
Okay, go back to the download page and go to the part that says something like "Some things may need common files" or somesuch and download the deb one and install it the same way.

As for the other one..

```
sudo apt-get install libsdl-image1.2
```

---

### Post by Nicktu on 2005-11-09
So go to the maine page an install those files with the code i recieved earlier, now what is this other code for?

---

### Post by Kyral on 2005-11-09
Packages depend on other things. Its complaining that one of the things it depends on isn't installed. That second line installs it :P (At least what its complaining about)

** 				Common 			**

  			  				Some packaging systems require a shared Armagetron Advanced package. 			
  			 					[Linux]("http://prdownloads.sourceforge.net/armagetronad/armagetronad-common_0.2.7.1-8_all.deb?download") (deb) <--- You want this

---

### Post by Nicktu on 2005-11-09
[HTML][COLOR="Blue"]nick@Nick:~/Desktop$ sudo apt-get install libsdl-image1.2[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Package libsdl-image1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsdl-image1.2 has no installation candidate
[COLOR="Blue"]nick@Nick:~/Desktop$ sudo dpkg -i armagetronad_0.2.7.1-8_i386.deb[/COLOR]
(Reading database ... 58078 files and directories currently installed.)
Preparing to replace armagetronad 0.2.7.1-8 (using armagetronad_0.2.7.1-8_i386.deb) ...
Unpacking replacement armagetronad ...
dpkg: dependency problems prevent configuration of armagetronad:
 armagetronad depends on libsdl-image1.2 (>= 1.2.3); however:
  Package libsdl-image1.2 is not installed.
dpkg: error processing armagetronad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 armagetronad
nick@Nick:~/Desktop$

[/HTML]

I did that and now i'm here

---

### Post by Nicktu on 2005-11-09
[COLOR="Blue"]nick@Nick:~/Desktop$ sudo dpkg -i armagetronad-common_0.2.7.1-8_all.deb[/COLOR]
Selecting previously deselected package armagetronad-common.
(Reading database ... 58042 files and directories currently installed.)
Unpacking armagetronad-common (from armagetronad-common_0.2.7.1-8_all.deb) ...
Setting up armagetronad-common (0.2.7.1-8) ...
[COLOR="Blue"]nick@Nick:~/Desktop$ sudo dpkg -i armagetronad_0.2.7.1-8_i386.deb[/COLOR]
(Reading database ... 58078 files and directories currently installed.)
Preparing to replace armagetronad 0.2.7.1-8 (using armagetronad_0.2.7.1-8_i386.deb) ...
Unpacking replacement armagetronad ...
dpkg: dependency problems prevent configuration of armagetronad:
 armagetronad depends on libsdl-image1.2 (>= 1.2.3); however:
  Package libsdl-image1.2 is not installed.
dpkg: error processing armagetronad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 armagetronad[COLOR="Blue"]
nick@Nick:~/Desktop$ sudo apt-get install libsdl-image1.2[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Package libsdl-image1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsdl-image1.2 has no installation candidate
nick@Nick:~/Desktop$ sudo dpkg -i armagetronad_0.2.7.1-8_i386.deb
(Reading database ... 58078 files and directories currently installed.)
Preparing to replace armagetronad 0.2.7.1-8 (using armagetronad_0.2.7.1-8_i386.deb) ...
Unpacking replacement armagetronad ...
dpkg: dependency problems prevent configuration of armagetronad:
 armagetronad depends on libsdl-image1.2 (>= 1.2.3); however:
  Package libsdl-image1.2 is not installed.
dpkg: error processing armagetronad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 armagetronad
nick@Nick:~/Desktop$





I did that and now i'm here


Edit: sorry double post

---

### Post by Kyral on 2005-11-09
Do you have Universe and Multiverse open?

If you don't

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Nicktu on 2005-11-09
I did what it told me to. Would me being in the terminal or root terminal make a difference?


The instructions just made me open up what seemed to be a text file and overwrite it with the new text, is this correct?

---

### Post by Kyral on 2005-11-09
For the Sources.list you need to sudo the command (put sudo before it)

And then yes, just replace it (Make SURE you use Breezy if you are on Breezy and Hoary if you are using Hoary)

---

### Post by Nicktu on 2005-11-09
I am in hoary, I used hoary (5.04)


Anyway, now what?

---

### Post by Kyral on 2005-11-09
Did you copy over the Hoary one (It says "Hoary" in it) :P

---

### Post by Nicktu on 2005-11-09
Yeah, and I clicked Save.

---

### Post by Kyral on 2005-11-09
now

```
sudo apt-get update && sudo apt-get upgrade
``` 
Updates your list of available packages and also checks for updates

Then try to use the earlier apt-get command

---

### Post by Nicktu on 2005-11-09
[COLOR="Blue"]root@Nick:/home/nick # sudo apt-get update && sudo apt-get upgrade[/COLOR]
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [26.2kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [75.3kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release [11.3kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages [490kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [17.1kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [50.1kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources [7121B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources [175kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages [2169kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources [857kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [88.4kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources [48.4kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages [18.6kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources [5509B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages [11.5kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages [26.3kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages [1536B]
Fetched 4118kB in 14s (277kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  armagetronad: Depends: libsdl-image1.2 (>= 1.2.3) but it is not installed
E: Unmet dependencies. Try using -f.
[COLOR="Blue"]root@Nick:/home/nick #  sudo apt-get install libsdl-image1.2[/COLOR]
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libsdl-image1.2
0 upgraded, 1 newly installed, 0 to remove and 126 not upgraded.
1 not fully installed or removed.
Need to get 25.0kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe libsdl-image1.2 1.2.3-6 [25.0kB]
Fetched 25.0kB in 0s (43.8kB/s)

Preconfiguring packages ...
Selecting previously deselected package libsdl-image1.2.
(Reading database ... 58078 files and directories currently installed.)
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.3-6_i386.deb) ...
Setting up libsdl-image1.2 (1.2.3-6) ...

Setting up armagetronad (0.2.7.1-8) ...

root@Nick:/home/nick #



Seemed like it was sucessful, now what?

---

### Post by Kyral on 2005-11-09
Do a

```
killall gnome-panel
``` to refresh the GNOME Menus and see if its there

---

### Post by Nicktu on 2005-11-09
I'm not quite sure where I should be looking for it. I refreshed, and i don't see it anywhere. Should i run the sudo -i <filename> again for the main file? Or?

---

### Post by Kyral on 2005-11-09
Time to learn about the cool thing about the terminal.

Open it up (its okay to be the normal user) and start typing the first few letters of the program and hit TAB. If its a unique enough string (and its the name of a program) it will autocomplete

---

