---
title: "Driver Installation Problem with Package Manager"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by coucoucbm on 2009-05-01
Hi every body,

I was a windows user until recently after I converted to linux (Much safer :-)) so I'm new in the Linux field and just starting using Ubuntu8.10.

I was trying to install a driver for a printer from Brother web site (see link: [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-8500](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-8500))
After I downloaded the deb package I double clicked on it and I though installation will be easy. but it did not go through. 

1-I have tried to run the installation command from the terminal as they say in this page/step4 ([http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)) but I got this error message:
[COLOR="Red"]
dpkg: operation requires read/write access to dpkg status area[/COLOR]

2-I tried the same command with sudo, but I got:

[COLOR="Red"]dpkg: error processing mfc8500lpr-1.1.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc8500lpr-1.1.2-1.i386.deb[/COLOR]

since then the Package Manager has a stop sign with this error notice:
[COLOR="Red"]An error occured, please run Package manager from the right-click menu or apt-get in a terminal to see what is wrong. the error message was:'unknown Error:"<Type'exceptions.SystemError'>'(E:The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.)'This usually means that your installed packages have unmet dependencies
[/COLOR]


I assume this an easy problem (at least I hope so) but I can not figure out if my driver is corrupted or is it a location problem.

Please help.
Thanks in advance.

---

### Post by zigga15 on 2009-05-01
> **coucoucbm said:**
> Hi every body,

I was a windows user until recently after I converted to linux (Much safer :-)) so I'm new in the Linux field and just starting using Ubuntu8.10.

I was trying to install a driver for a printer from Brother web site (see link: [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-8500](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-8500))
After I downloaded the deb package I double clicked on it and I though installation will be easy. but it did not go through. 

1-I have tried to run the installation command from the terminal as they say in this page/step4 ([http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)) but I got this error message:
[COLOR="Red"]
dpkg: operation requires read/write access to dpkg status area[/COLOR]

2-I tried the same command with sudo, but I got:

[COLOR="Red"]dpkg: error processing mfc8500lpr-1.1.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc8500lpr-1.1.2-1.i386.deb[/COLOR]

since then the Package Manager has a stop sign with this error notice:
[COLOR="Red"]An error occured, please run Package manager from the right-click menu or apt-get in a terminal to see what is wrong. the error message was:'unknown Error:"<Type'exceptions.SystemError'>'(E:The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.)'This usually means that your installed packages have unmet dependencies
[/COLOR]


I assume this an easy problem (at least I hope so) but I can not figure out if my driver is corrupted or is it a location problem.

Please help.
Thanks in advance.

First of all nice work on converting to linux -- ha ha...

First of all - go to synaptic package manager click edit > fix broken packages.

See if that helps, otherwise use

dpkg -i -f --configure
from the folder you are installing into.

Then to get the drivers working I suggest you follow the instructions more carefully. Installing stuff with synaptic is easy, but when you have wrappers and dependencies it can get a bit tricky.

I am awake for about 3 more minutes - gotta wake up in a few hours to drop gf at airport :(

---

### Post by coucoucbm on 2009-05-01
HI Thanx for you help and I hope you slept enough.

Synaptic shows and error message when it stats then shuts off.
[COLOR="Red"]E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
[/COLOR]


I tried to do the sudo installation from the folder as follow but did not work:

[COLOR="Red"]
mohamed@mohamed-laptop:~$ cd /home/mohamed/Desktop/Appplications
mohamed@mohamed-laptop:~/Desktop/Appplications$ sudo dpkg -i  --force-all  --force-architecture mfc8500lpr-1.1.2-1.i386.deb
(Reading database ... 140009 files and directories currently installed.)
Preparing to replace mfc8500lpr 1.1.2-1 (using mfc8500lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8500lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr-1.1.2-1.i386.deb
mohamed@mohamed-laptop:~/Desktop/Appplications$[/COLOR] 

Any thoughts?

---

### Post by zigga15 on 2009-05-01
sudo apt-get autoclean

or

sudo apt-get dist-upgrade --fix-missing

keep googling for "fixing broken packages" 

Also, I wouldn't reset why this is not fixed. I "half installed" creative's attempt to create linux drivers. My computer died pretty hard.

Pretty bad that synaptic died --- their install system must be pretty sketchy. Make sure u follow the instructions down to the letter in the future - then at least you know they are to blame.

---

### Post by coucoucbm on 2009-05-02
thx for replying. this is what the two commands gave me:

mohamed@mohamed-laptop:~$ sudo apt-get autoclean
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del firefox-3.0 3.0.8+nobinonly-0ubuntu0.8.10.2 [887kB]
Del libxine1-gnome 1.1.15-0ubuntu3.2 [15.1kB]
Del firefox-3.0-gnome-support 3.0.9+nobinonly-0ubuntu0.8.10.1 [84.4kB]
Del firefox-3.0-branding 3.0.9+nobinonly-0ubuntu0.8.10.1 [202kB]
Del libxine1-bin 1.1.15-0ubuntu3.2 [1344kB]
Del clamav-freshclam 0.94.dfsg.2-1ubuntu0.2 [254kB]
Del libcupsimage2 1.3.9-2ubuntu9 [51.7kB]
Del clamav 0.94.dfsg.2-1ubuntu0.1 [233kB]
Del libxine1-console 1.1.15-0ubuntu3.2 [61.4kB]
Del cups-client 1.3.9-2ubuntu9 [115kB]
Del firefox-3.0 3.0.9+nobinonly-0ubuntu0.8.10.1 [887kB]
Del firefox-3.0-branding 3.0.8+nobinonly-0ubuntu0.8.10.2 [202kB]
Del clamav-freshclam 0.94.dfsg.2-1ubuntu0.1 [254kB]
Del libpq5 8.3.6-0ubuntu8.10 [290kB]
Del firefox-3.0-gnome-support 3.0.8+nobinonly-0ubuntu0.8.10.2 [84.4kB]
Del clamav-base 0.94.dfsg.2-1ubuntu0.1 [19.5MB]
Del firefox 3.0.9+nobinonly-0ubuntu0.8.10.1 [69.0kB]
Del cups-common 1.3.9-2ubuntu9 [1163kB]
Del libcups2 1.3.9-2ubuntu9 [170kB]
Del clamav-base 0.94.dfsg.2-1ubuntu0.2 [19.5MB]
Del cups 1.3.9-2ubuntu9 [2139kB]
Del xulrunner-1.9-gnome-support 1.9.0.8+nobinonly-0ubuntu0.8.10.1 [39.4kB]
Del firefox-gnome-support 3.0.8+nobinonly-0ubuntu0.8.10.2 [68.8kB]
Del firefox-gnome-support 3.0.9+nobinonly-0ubuntu0.8.10.1 [68.9kB]
Del libxine1-x 1.1.15-0ubuntu3.2 [212kB]
Del xulrunner-1.9-gnome-support 1.9.0.9+nobinonly-0ubuntu0.8.10.1 [39.4kB]
Del libxine1 1.1.15-0ubuntu3.2 [1304B]
Del libxine1-ffmpeg 1.1.15-0ubuntu3.2 [393kB]
Del tzdata 2009d-0ubuntu0.8.10 [674kB]
Del wine 1.1.18~winehq0~ubuntu~8.10-0ubuntu1 [8238kB]
Del clamav 0.94.dfsg.2-1ubuntu0.2 [233kB]
Del xulrunner-1.9 1.9.0.8+nobinonly-0ubuntu0.8.10.1 [7543kB]
Del cups-bsd 1.3.9-2ubuntu9 [36.2kB]
Del firefox 3.0.8+nobinonly-0ubuntu0.8.10.2 [68.9kB]
Del libxine1-misc-plugins 1.1.15-0ubuntu3.2 [931kB]
Del wine 1.1.19~winehq0~ubuntu~8.10-0ubuntu1 [8284kB]
Del libclamav5 0.94.dfsg.2-1ubuntu0.2 [525kB]
Del xulrunner-1.9 1.9.0.9+nobinonly-0ubuntu0.8.10.1 [7547kB]
Del libclamav5 0.94.dfsg.2-1ubuntu0.1 [524kB]
mohamed@mohamed-laptop:~$ sudo apt-get dist-upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
mohamed@mohamed-laptop:~$ 


obviouisly it did not work. so I will keep searching, THX again.

cheers

---

### Post by coucoucbm on 2009-05-02
I tried to restart from the beginning and redo the installation properly as they say in this page [http://solutions.brother.com/linux/e...ion_prn1a.html](http://solutions.brother.com/linux/e...ion_prn1a.html)
but I was not able to get step2 done because I need to have ia32-libs or lib32stdc++ installed. I tried that and got this message

mohamed@mohamed-laptop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
mohamed@mohamed-laptop:~$



It seems like my original installation error is messing all the process!

---

### Post by Partyboi2 on 2009-05-02
> **coucoucbm said:**
> I tried to restart from the beginning and redo the installation properly as they say in this page [http://solutions.brother.com/linux/e...ion_prn1a.html](http://solutions.brother.com/linux/e...ion_prn1a.html)
but I was not able to get step2 done because I need to have ia32-libs or lib32stdc++ installed. I tried that and got this message

mohamed@mohamed-laptop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
mohamed@mohamed-laptop:~$



It seems like my original installation error is messing all the process!
Hi, open a terminal and type or paste
```
sudo dpkg --remove --force-remove-reinstreq mfc8500lpr
```
and see if that clears it up.

---

### Post by pastalavista on 2009-05-02
I searched though synaptic (I was bored) and believe I found your package. It's in a package called 'brother-lpr-drivers-laser1'

---

### Post by coucoucbm on 2009-05-02
> **Partyboi2 said:**
> Hi, open a terminal and type or paste
```
sudo dpkg --remove --force-remove-reinstreq mfc8500lpr
```
and see if that clears it up.

Hi thx for replying. I tried it and this what came out:

mohamed@mohamed-laptop:~$ sudo dpkg --remove --force-remove-reinstreq mfc8500lprdpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 140008 files and directories currently installed.)
Removing mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8500lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr
mohamed@mohamed-laptop:~$ 

any suggestion?

---

### Post by coucoucbm on 2009-05-02
> **pastalavista said:**
> I searched though synaptic (I was bored) and believe I found your package. It's in a package called 'brother-lpr-drivers-laser1'

Thx. I'm not able to get access to synaptic. Synaptic shows and error message when it starts then shuts off.
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

:-((

---

### Post by pastalavista on 2009-05-02
> **coucoucbm said:**
> Thx. I'm not able to get access to synaptic. Synaptic shows and error message when it starts then shuts off.
OK then, try this
```
sudo aptitude reinstall synaptic
```
and if you can't fix synaptic
```
sudo apt-get install brother-lpr-drivers-laser1
```

A broken package manager is worse than a broken package :P:lolflag:

---

### Post by coucoucbm on 2009-05-02
> **pastalavista said:**
> OK then, try this
```
sudo aptitude reinstall synaptic
```
and if you can't fix synaptic
```
sudo apt-get install brother-lpr-drivers-laser1
```

A broken package manager is worse than a broken package :P:lolflag:

this is what I got:

mohamed@mohamed-laptop:~$ sudo aptitude reinstall synaptic
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  synaptic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 12 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the mfc8500lpr package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the mfc8500lpr package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
mohamed@mohamed-laptop:~$ sudo apt-get install brother-lpr-drivers-laser1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
mohamed@mohamed-laptop:~$

---

### Post by Partyboi2 on 2009-05-03
The problem is with the mfc8500lpr package not synaptic so reinstalling synaptic will probably not fix the problem.
Open a terminal and try this:
```
sudo mv /var/lib/dpkg/info/mfc8500lpr.postrm /var/lib/dpkg/info/mfc8500lpr.postrm.broke
``````
sudo apt-get --purge remove mfc8500lpr
```you should get an output like this:
```
The following packages will be REMOVED:
  mfc8500lpr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 209660 files and directories currently installed.)
Removing mfc8500lpr ...
dpkg - warning: while removing mfc8500lpr, directory `/usr/local' not empty so not removed.

```But the package should have been removed and synaptic should be working again. :)

---

### Post by coucoucbm on 2009-05-03
> **Partyboi2 said:**
> The problem is with the mfc8500lpr package not synaptic so reinstalling synaptic will probably not fix the problem.
Open a terminal and try this:
```
sudo mv /var/lib/dpkg/info/mfc8500lpr.postrm /var/lib/dpkg/info/mfc8500lpr.postrm.broke
``````
sudo apt-get --purge remove mfc8500lpr
```you should get an output like this:
```
The following packages will be REMOVED:
  mfc8500lpr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 209660 files and directories currently installed.)
Removing mfc8500lpr ...
dpkg - warning: while removing mfc8500lpr, directory `/usr/local' not empty so not removed.

```But the package should have been removed and synaptic should be working again. :)


thanks for following up with me on this. I tried what you said and this the output:
mohamed@mohamed-laptop:~$ sudo mv /var/lib/dpkg/info/mfc8500lpr.postrm /var/lib/dpkg/info/mfc8500lpr.postrm.broke
[sudo] password for mohamed: 
mohamed@mohamed-laptop:~$ sudo mv /var/lib/dpkg/info/mfc8500lpr.postrm /var/lib/dpkg/info/mfc8500lpr.postrm.broke
mv: cannot stat `/var/lib/dpkg/info/mfc8500lpr.postrm': No such file or directory
mohamed@mohamed-laptop:~$ sudo apt-get --purge remove mfc8500lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
mohamed@mohamed-laptop:~$ 

I have checked on that same folder /var/lib/dpkg/info/ and there is 5 files:
mfc8500lpr.conffiles
mfc8500lpr.list
mfc8500lpr.postinst
mfc8500lpr.postrm.broke
mfc8500lpr.prerm

????????

---

### Post by coucoucbm on 2009-05-03
HI Guys, I think I'm close to accomplish some thing here, Just need some more help. Any body can tell me how to delete this file 
/var/lib/dpkg/info/mfc8500lpr.postrm

According to this thread (presents exactly the same problem) deleting this file is the solution
[http://ubuntuforums.org/showpost.php?p=1475222&postcount=8](http://ubuntuforums.org/showpost.php?p=1475222&postcount=8)

in the same thread another user had suggested to comment out the command line in that file (mfc8500lpr.postrm) which I tried but I was not able to save it since it needs special root permissions.

any advice???

---

### Post by pastalavista on 2009-05-03
Use sudo to get permission

```
sudo nano /var/lib/dpkg/info/mfc8500lpr.postrm
```

then just add # to the beginning of the command line

---

### Post by coucoucbm on 2009-05-03
:):):)Many Thanks to you Pastalavista.

Actually I was able to log in the terminal as Root and run the command
sudo dpkg --remove --force-remove-reinstreq mfc8500lpr 
without commenting out the command line in the mfc8500lpr 

the result came exactly as what I got after I implemented your command:

mohamed@mohamed-laptop:~$ sudo nano /var/lib/dpkg/info/mfc8500lpr.postrm
[sudo] password for mohamed: 
mohamed@mohamed-laptop:~$ sudo dpkg --remove --force-remove-reinstreq mfc8500lpr 
dpkg - warning: ignoring request to remove mfc8500lpr which isn't installed.
mohamed@mohamed-laptop:~$ 

I was able then to open synaptic and the problem seems to be solved.
the file is still there but package manager is back to work
Thank you again for your precious help.
Best Regards:):):):)

---

