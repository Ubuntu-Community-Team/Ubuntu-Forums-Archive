---
title: "Removing unnecessary processes"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by withoutme on 2005-09-03
I am a Linux newbie. I have Ubuntu 5.04 installed on my really really old laptop. I did the server installation. My computer is still slow. I would like to know if there are any unnecessary process that I can kill - during boot, after boot, in the background etc etc. Here are my spec..

Hardware: 
Toshiba Tecra 550CDT
266Mhx Pentium MMX
96Mb Ram
4GB HD

SOftware:
Ubuntu 5.04 Server installation with
XFCE4
firefox
Gaim

I still havent figured out to make my wireless work, but I want to speed up things first.. Any help please. Things like
1. How to indentify unnecessary processes
2. At boot time, in background.
Thank you again

---

### Post by weekend warrior on 2005-09-04
To speed up your laptop more you may want to try Fluxbox instead of XFCE. For services, there's a package called "bum" (search in Synaptic) Boot-Up Manager, that will list them and allow you to easily deactivate/activate them so as to figure out which ones are necessary or not for your tasks.

---

### Post by withoutme on 2005-09-04
kewl.. i will give it a try .. thank you

---

### Post by withoutme on 2005-09-06
Hey, I tried to install BUM by downloading the .deb package from the website. However I got the following dependency errors:
sudo dpkg -i gksu_1.3.4-1_i386.deb
Selecting previously deselected package gksu.
(Reading database ... 27908 files and directories currently installed.)
Unpacking gksu (from gksu_1.3.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 gksu depends on libgksu1.2-0 (>= 1.3.3); however:
  Package libgksu1.2-0 is not installed.
 gksu depends on libgksuui1.0-1; however:
  Package libgksuui1.0-1 is not installed.
 gksu depends on libglib2.0-0 (>= 2.8.0); however:
  Version of libglib2.0-0 on system is 2.6.3-1.
 gksu depends on libgnome-keyring0 (>= 0.4.3); however:
  Version of libgnome-keyring0 on system is 0.4.2-0ubuntu1.
 gksu depends on libpango1.0-0 (>= 1.8.2); however:
  Version of libpango1.0-0 on system is 1.8.1-0ubuntu2.
dpkg: error processing gksu (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gksu

So I tried to download the gksu form debian ftp site and tried to do a dpkg on it and still got dependency errors. SO I thot I should try 'apt-get install bum". I still got dependeency errors with gksu. And more dependency erros if I tried to install gksu with apt-get install gksu:
vj@alexis:~/Downloads/Firefox$ sudo apt-get install bum
Reading package lists... Done
Building dependency tree... Done
bum is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bum: Depends: libgtk2-perl but it is not going to be installed
       Depends: libgnome2-perl but it is not going to be installed
       Depends: libglib-perl but it is not going to be installed
  gksu: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to be installed
        Depends: libgksu1.2-0 (>= 1.3.3) but it is not going to be installed
        Depends: libgksuui1.0-1 but it is not installable
        Depends: libglib2.0-0 (>= 2.8.0) but 2.6.3-1 is to be installed
        Depends: libgnome-keyring0 (>= 0.4.3) but 0.4.2-0ubuntu1 is to be instal led
        Depends: libpango1.0-0 (>= 1.8.2) but 1.8.1-0ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
AND
vj@alexis:~/Downloads/Firefox$ sudo apt-get -f install bum
Reading package lists... Done
Building dependency tree... Done
bum is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bum: Depends: libgtk2-perl but it is not going to be installed
       Depends: libgnome2-perl but it is not going to be installed
       Depends: libglib-perl but it is not going to be installed
  gksu: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to be installed
        Depends: libgksu1.2-0 (>= 1.3.3) but it is not going to be installed
        Depends: libgksuui1.0-1 but it is not installable
        Depends: libglib2.0-0 (>= 2.8.0) but 2.6.3-1 is to be installed
        Depends: libgnome-keyring0 (>= 0.4.3) but 0.4.2-0ubuntu1 is to be installed
        Depends: libpango1.0-0 (>= 1.8.2) but 1.8.1-0ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I even tried the apt-get install -f option with no result. Help please




Are you sure BUM will work in XFCE?

---

### Post by weekend warrior on 2005-09-06
Yes I'm sure BUM will work in XFCE. In fact I'm in XFCE right now and have it running. What website are you referring to? What version of BUM did you download? I have 1.3.2-1

When you use ubuntu, you don't need to go to any websites looking around for files. That's for Windows. You can and should download ubuntu packages easily through Synaptic; not website debian packages. 

What's happening is that the version of BUM you've downloaded is probably a newer version (I suspect 1.3.3 right?) and failing to find newer versions of packages that you have. Look carefully at the dependency messages and you'll see dpkg telling you this: ie "depends on version  2.3.5-1 however version 2.3.2 installed". 

Basically, what you downloaded is for Debian unstable "Sid" and ubuntu "Breezy" but that's not what you're using, hence the problems. Open Synaptic and it will probably tell you that you have 1 broken package. Use the "Search" button and type "bum" without quotes, then right click "Mark for Removal". Then click "Apply". You can just trash the .deb file you downloaded.

Now, try again - but do it the right way. Just open Synaptic and hit the "Reload" button. Then click the "Search" button and type "bum" without the quotes. This is the one from the official ubuntu repositories. Right click and "Mark for Installation". Then hit the "Apply" button and Synaptic should do the rest.



Edit: clarifications

---

### Post by withoutme on 2005-09-06
I removed everything by s*sudo apt-get remove bum gksu* 
This removed everything. No more dependency errors. Then I did
sudo apt-get install bum, and it gave
vj@alexis:~$ sudo apt-get install bum
Reading package lists... Done
Building dependency tree... Done
Package bum is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bum has no installation candidate

What happened to bum?

---

### Post by weekend warrior on 2005-09-06
Is the universe repository currently enabled on your system? Synaptic allows you to easily check which repositories you have activated - click "Settings", "Repositories". The package is in the universe and should be available to you if the repository is enabled.

[http://search.belnet.be/packages/ubuntu/ubuntu/pool/universe/b/bum/](http://search.belnet.be/packages/ubuntu/ubuntu/pool/universe/b/bum/)

---

### Post by withoutme on 2005-09-06
I think it is enabled. Here is my soures.list
# ubuntu repository, must not be commented
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

#backports repository
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

In my synaptic when i searched for bum, it came up, but said it could not be installed as it had become obsolete etc etc etc

---

### Post by weekend warrior on 2005-09-07
That's odd. First off, disable the backports repositories; you only want to deal with normal repos right now. Did you make sure to "Reload" Synaptic? Is there anything listed as broken, to install/upgrade, to remove? What is the version number of the bum package showing up in Synaptic now, 1.3.2-1?  

It sounds like the newer, incompatible bum package you tried to install is still around locally. In Synaptic, select bum again, but don't mark it - just select. Now go up to the menu "Package" then "Force Version". Is the option available? If so what do you see? Which versions? (Don't try and force it for now, just look to see what's there).

If the incompatible one is there, that may be causing the problem and you'll need to get rid of it locally, then reload Synaptic and try again. If you can't find it, look in /var/cache/apt/archives.

If there *aren't* two versions, then I'm a bit stumped tbh :-k These are the dependencies and version numbers on my system so you can compare what you have now. 

sysv-rc, 2.86-5ubunut6
perl, 5.8.4-6ubuntu1
libgtk2-perl, 1:1.061-1ubuntu1
libgnome2-perl, 1.020-1
libglib2-perl, 1:1.061-1
liblocale-gettext-perl, 1.01-17

Also check if you maybe have "file-rc" installed. This conflicts with BUM.



Good for you for being patient btw. This obviously isn't how installing new software normally goes. Something like this normally takes 20 seconds. When correct procedure is followed that's how it should go.

---

