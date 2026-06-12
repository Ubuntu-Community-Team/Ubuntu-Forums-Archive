---
title: "Please help at apt-get"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by pajoohesh on 2009-01-24
[COLOR="Blue"]hello ubuntufolks,

There is a serious problem with apt that I have encountered and I can not do anything for it except re-installation.

when during the 'apt-get install' internet connection is lost dpkg terminates with an error on several package. there is no way to solve this problem. by removing some packages by 'dpkg -r' I managed to run 'dpkg --configure -a' correctly but I still can not do any 'apt-get install'. 

I tried 'apt-get build-dep' on one of the packages that had error and unfortunately, now more packages have error with dpkg and I can not run 'dpkg --configure -a'.  

Now the faulty packages are:m4, gettext, dvipng, texlive-base-bin-doc,texlive-latex-base

I really appreciate any help as this problem with apt is very sad and is not good for ubuntu. if there is no solution I am ready for reinstalling but please write me something to avoid these kinds of problems in the future.[/COLOR]

---

### Post by mikewhatever on 2009-01-24
Can you please post the full error message you get when trying to install stuff. Simply run apt-get install and then copy/paste the text here.

---

### Post by pajoohesh on 2009-01-24
```
[COLOR="Blue"]amir@Simulator:~$ sudo apt-get install
[sudo] password for amir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up m4 (1.4.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing No apport report written because the error message indicates its a followup error from a previous failure.
                                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       cdbs (--configure):
 dependency problems - leaving unconfigured
Setting up dvipng (1.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing dvipng (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-base-bin-doc (2007.dfsg.2-3ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-latex-base-doc (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-latex-base-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 m4
 autoconf
 automake1.7
 intltool
 cdbs
 dvipng
 texlive-base-bin-doc
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
amir@Simulator:~$ 
[/COLOR]
```

[COLOR="Blue"]Thanks for your attention,[/COLOR]

---

### Post by oldos2er on 2009-01-24
What happens if you run

 ```
sudo dpkg --configure -a
```

---

### Post by mikewhatever on 2009-01-24
It looks like apt-get wants to configure a bunch of packages, but can't because it runs into dependency problems. You may want to try the <sudo apt-get install -f> command to install the required dependencies. If you get more errors, with whatever commands, post them here as in the post above.

---

### Post by pajoohesh on 2009-01-25
[COLOR="Blue"]> What happens if you run

sudo dpkg --configure -a
[/COLOR]
```
amir@Simulator:~$ sudo dpkg --configure -a
[sudo] password for amir: 
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing cdbs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 autoconf
 automake1.7
 intltool
 cdbs
amir@Simulator:~$ 

```

[COLOR="Blue"]> It looks like apt-get wants to configure a bunch of packages, but can't because it runs into dependency problems. You may want to try the <sudo apt-get install -f> command to install the required dependencies. If you get more errors, with whatever commands, post them here as in the post above.[/COLOR]
```
amir@Simulator:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up m4 (1.4.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing No apport report written because the error message indicates its a followup error from a previous failure.
                                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     cdbs (--configure):
 dependency problems - leaving unconfigured
Setting up dvipng (1.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing dvipng (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-base-bin-doc (2007.dfsg.2-3ubuntu1) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-latex-base-doc (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-latex-base-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 m4
 autoconf
 automake1.7
 intltool
 cdbs
 dvipng
 texlive-base-bin-doc
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
amir@Simulator:~$ 
```

[COLOR="Blue"]'sudo apt-get update'  runs without any problem.

'sudo apt-get upgrade'[/COLOR]
```
amir@Simulator:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up m4 (1.4.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing No apport report written because the error message indicates its a followup error from a previous failure.
                                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       cdbs (--configure):
 dependency problems - leaving unconfigured
Setting up dvipng (1.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing dvipng (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-base-bin-doc (2007.dfsg.2-3ubuntu1) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-latex-base-doc (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-latex-base-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 m4
 autoconf
 automake1.7
 intltool
 cdbs
 dvipng
 texlive-base-bin-doc
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
amir@Simulator:~$ 
```

[COLOR="Blue"]> sudo dpkg -r m4[/COLOR]

```
amir@Simulator:~$ sudo dpkg -r m4
[sudo] password for amir: 
(Reading database ... 135512 files and directories currently installed.)
Removing m4 ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 m4
amir@Simulator:~$ 

```

[COLOR="Blue"]sudo dpkg -s autoconf[/COLOR]

```
amir@Simulator:~$ sudo dpkg -s autoconf
Package: autoconf
Status: install ok unpacked
```

[COLOR="Blue"]sudo dpkg -s m4[/COLOR]
```
amir@Simulator:~$ sudo dpkg -s m4
Package: m4
Status: deinstall ok half-configured
```

[COLOR="Blue"]sudo dpkg -s intltool[/COLOR]

```
amir@Simulator:~$ sudo dpkg -s intltool
Package: intltool
Status: install ok unpacked
```

[COLOR="Blue"]if you need any more information please tell me.

thank you very much.[/COLOR]

---

### Post by pajoohesh on 2009-01-25
[COLOR="Blue"]no solution folks?

no problem. but please tell me what can i do to avoid this kind of problems in the future. this is second time that i should reinstall and it is not good.

[/COLOR]

---

### Post by oldos2er on 2009-01-25
Can you please post the output of

 ```
cat /etc/apt/sources.list
``` ?

---

### Post by pajoohesh on 2009-01-26
[COLOR="Blue"]> **oldos2er said:**
> Can you please post the output of

 ```
cat /etc/apt/sources.list
``` ?

```
amir@Simulator:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ir.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ir.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
amir@Simulator:~$ 
```[/COLOR]

---

### Post by pajoohesh on 2009-01-28
[COLOR="Blue"]Really no solution guys? 

It is strange.[/COLOR]

---

### Post by avtolle on 2009-01-28
Just to clarify; your problem arose when, doing an installation of several packages, your internet connection was lost? Due to that, there are the various problems you have posted about, and others have tried to help you with. 

If I'm correct about the internet connection being lost as being the core of your problem, in the future update/upgrade via a wired connection and not wireless to reduce the chances of loss of network connection.

---

### Post by pajoohesh on 2009-01-28
> Just to clarify; your problem arose when, doing an installation of several packages, your internet connection was lost? Due to that, there are the various problems you have posted about, and others have tried to help you with.

[COLOR="Blue"]I am not sure about that. I conclude the internet connection must have been lost as I was away from the computer and also I do not have any idea about other reasons.[/COLOR]

> **avtolle said:**
> 
If I'm correct about the internet connection being lost as being the core of your problem, in the future update/upgrade via a wired connection and not wireless to reduce the chances of loss of network connection.

[COLOR="Blue"]sorry, but you are trying to tell me that losing internet connection and subsequently breaking apt-get and therefore an out of work ubuntu is reasonable?

I am not sure actually.[/COLOR]

---

### Post by oldos2er on 2009-01-28
Your sources.list looks ok.

 Have you tried running
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update && sudo apt-get safe-upgrade
```

---

### Post by avtolle on 2009-01-28
What I was trying to say is that if indeed the internet connection was lost during the installation process, it is rational to assume that a needed dependency was not fully downloaded and thus, without the dependency there for configuration, the error messages you received are reasonable. That said, have you tried to clean out  /var/apt/cache by removing the packages that had downloaded, and then trying it again?

---

### Post by avtolle on 2009-01-28
Sorry; /var/cache/apt is where you want to look, I believe.

Edit: with more particularity, /var/cache/apt/partial

---

### Post by vpsville on 2009-01-28
Have you tried:

sudo apt-get -f

?

---

### Post by avtolle on 2009-01-28
> **vpsville said:**
> Have you tried:

sudo apt-get -f

?
From earlier posts, it appears the OP has tried that without success.

---

### Post by pajoohesh on 2009-01-28
> **oldos2er said:**
> Your sources.list looks ok.

 Have you tried running
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update && sudo apt-get safe-upgrade
```

[COLOR="Blue"]up to 'sudo apt-get update' there is no problem. There is no apt-get safe-upgrade instead I used 'sudo Aptitude safe-upgrade'[/COLOR]

```
amir@Simulator:~$ sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  linux-headers-2.6.27-11{a} linux-headers-2.6.27-11-generic{a} linux-image-2.6.27-11-generic{a} linux-restricted-modules-2.6.27-11-generic{a} 
The following packages will be upgraded:
  at-spi ca-certificates-java libatspi1.0-0 libpulse-browse0 libpulse0 libpulsecore5 linux-generic linux-headers-generic linux-image-generic 
  linux-libc-dev linux-restricted-modules-common linux-restricted-modules-generic pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf 
  pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-pyatspi ufw 
The following partially installed packages will be configured:
  autoconf automake1.7 cdbs dvipng intltool m4 texi2html texlive-base-bin-doc texlive-latex-base-doc 
20 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.4MB of archives. After unpacking 166MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-11-generic 2.6.27-11.25 [23.1MB]
Get:2 http://us.archive.ubuntu.com intrepid-updates/restricted linux-restricted-modules-common 2.6.27-11.16 [10.4kB]                                         
Get:3 http://us.archive.ubuntu.com intrepid-updates/restricted linux-restricted-modules-2.6.27-11-generic 2.6.27-11.16 [765kB]                               
Get:4 http://us.archive.ubuntu.com intrepid-updates/main ufw 0.23.3 [43.5kB]                                                                                 
Get:5 http://us.archive.ubuntu.com intrepid-updates/main python-pyatspi 1.24.0-0ubuntu3.8.10.1 [44.1kB]                                                      
Get:6 http://us.archive.ubuntu.com intrepid-updates/main libatspi1.0-0 1.24.0-0ubuntu3.8.10.1 [166kB]                                                        
Get:7 http://us.archive.ubuntu.com intrepid-updates/main at-spi 1.24.0-0ubuntu3.8.10.1 [116kB]                                                               
Get:8 http://us.archive.ubuntu.com intrepid-updates/main ca-certificates-java 20080712ubuntu4 [98.6kB]                                                       
Get:9 http://us.archive.ubuntu.com intrepid-updates/main libpulse0 0.9.10-2ubuntu9.3 [168kB]                                                                 
Get:10 http://us.archive.ubuntu.com intrepid-updates/main libpulse-browse0 0.9.10-2ubuntu9.3 [27.7kB]                                                        
Get:11 http://us.archive.ubuntu.com intrepid-updates/main libpulsecore5 0.9.10-2ubuntu9.3 [216kB]                                                            
Get:12 http://us.archive.ubuntu.com intrepid-updates/restricted linux-generic 2.6.27.11.14 [2904B]                                                           
Get:13 http://us.archive.ubuntu.com intrepid-updates/main linux-image-generic 2.6.27.11.14 [2888B]                                                           
Get:14 http://us.archive.ubuntu.com intrepid-updates/restricted linux-restricted-modules-generic 2.6.27.11.14 [2908B]                                        
Get:15 http://us.archive.ubuntu.com intrepid-updates/main linux-headers-2.6.27-11 2.6.27-11.25 [5783kB]                                                      
Get:16 http://us.archive.ubuntu.com intrepid-updates/main linux-headers-2.6.27-11-generic 2.6.27-11.25 [652kB]                                               
Get:17 http://us.archive.ubuntu.com intrepid-updates/main linux-headers-generic 2.6.27.11.14 [2880B]                                                         
Get:18 http://us.archive.ubuntu.com intrepid-updates/main linux-libc-dev 2.6.27-11.25 [664kB]                                                                
Get:19 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio 0.9.10-2ubuntu9.3 [339kB]                                                               
Get:20 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio-esound-compat 0.9.10-2ubuntu9.3 [31.3kB]                                                
Get:21 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio-module-gconf 0.9.10-2ubuntu9.3 [10.9kB]                                                 
Get:22 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio-module-hal 0.9.10-2ubuntu9.3 [17.4kB]                                                   
Get:23 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio-utils 0.9.10-2ubuntu9.3 [156kB]                                                         
Get:24 http://us.archive.ubuntu.com intrepid-updates/main pulseaudio-module-x11 0.9.10-2ubuntu9.3 [19.1kB]                                                   
Fetched 32.4MB in 13min57s (38.7kB/s)                                                                                                                        
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.27-11-generic.
(Reading database ... 144901 files and directories currently installed.)
Unpacking linux-image-2.6.27-11-generic (from .../linux-image-2.6.27-11-generic_2.6.27-11.25_amd64.deb) ...
Done.
Preparing to replace linux-restricted-modules-common 2.6.27-9.13 (using .../linux-restricted-modules-common_2.6.27-11.16_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Selecting previously deselected package linux-restricted-modules-2.6.27-11-generic.
Unpacking linux-restricted-modules-2.6.27-11-generic (from .../linux-restricted-modules-2.6.27-11-generic_2.6.27-11.16_amd64.deb) ...
Preparing to replace ufw 0.23.2 (using .../archives/ufw_0.23.3_all.deb) ...
Unpacking replacement ufw ...
Preparing to replace python-pyatspi 1.24.0-0ubuntu3 (using .../python-pyatspi_1.24.0-0ubuntu3.8.10.1_all.deb) ...
Unpacking replacement python-pyatspi ...
Preparing to replace libatspi1.0-0 1.24.0-0ubuntu3 (using .../libatspi1.0-0_1.24.0-0ubuntu3.8.10.1_amd64.deb) ...
Unpacking replacement libatspi1.0-0 ...
Preparing to replace at-spi 1.24.0-0ubuntu3 (using .../at-spi_1.24.0-0ubuntu3.8.10.1_amd64.deb) ...
Unpacking replacement at-spi ...
Preparing to replace ca-certificates-java 20080712ubuntu3 (using .../ca-certificates-java_20080712ubuntu4_all.deb) ...
Unpacking replacement ca-certificates-java ...
Preparing to replace libpulse0 0.9.10-2ubuntu9.2 (using .../libpulse0_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse-browse0 0.9.10-2ubuntu9.2 (using .../libpulse-browse0_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement libpulse-browse0 ...
Preparing to replace libpulsecore5 0.9.10-2ubuntu9.2 (using .../libpulsecore5_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement libpulsecore5 ...
Preparing to replace linux-generic 2.6.27.9.13 (using .../linux-generic_2.6.27.11.14_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.27.9.13 (using .../linux-image-generic_2.6.27.11.14_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Preparing to replace linux-restricted-modules-generic 2.6.27.9.13 (using .../linux-restricted-modules-generic_2.6.27.11.14_amd64.deb) ...
Unpacking replacement linux-restricted-modules-generic ...
Selecting previously deselected package linux-headers-2.6.27-11.
Unpacking linux-headers-2.6.27-11 (from .../linux-headers-2.6.27-11_2.6.27-11.25_all.deb) ...
Selecting previously deselected package linux-headers-2.6.27-11-generic.
Unpacking linux-headers-2.6.27-11-generic (from .../linux-headers-2.6.27-11-generic_2.6.27-11.25_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.27.9.13 (using .../linux-headers-generic_2.6.27.11.14_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.27-9.19 (using .../linux-libc-dev_2.6.27-11.25_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace pulseaudio 0.9.10-2ubuntu9.2 (using .../pulseaudio_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-esound-compat 0.9.10-2ubuntu9.2 (using .../pulseaudio-esound-compat_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio-esound-compat ...
Preparing to replace pulseaudio-module-gconf 0.9.10-2ubuntu9.2 (using .../pulseaudio-module-gconf_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-hal 0.9.10-2ubuntu9.2 (using .../pulseaudio-module-hal_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio-module-hal ...
Preparing to replace pulseaudio-utils 0.9.10-2ubuntu9.2 (using .../pulseaudio-utils_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio-module-x11 0.9.10-2ubuntu9.2 (using .../pulseaudio-module-x11_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Processing triggers for man-db ...
Setting up m4 (1.4.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing cdbs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up dvipng (1.11-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing dvipng (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texi2html (1.78-1) ...
No apport report written because MaxReports is reached already
                                                              install-info: No dir file specified; try --help for more information.
dpkg: error processing texi2html (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-base-bin-doc (2007.dfsg.2-3ubuntu1) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up texlive-latex-base-doc (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
install-info: No dir file specified; try --help for more information.
dpkg: error processing texlive-latex-base-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.27-11-generic (2.6.27-11.25) ...
No apport report written because MaxReports is reached already
                                                              Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-9-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic                                                                                       
 *  fglrx (8.543)...                                                                                                                                         fglrx (8.543): Installing module.
..........
......
                                                                                                                                                      [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-restricted-modules-common (2.6.27-11.16) ...

Setting up linux-restricted-modules-2.6.27-11-generic (2.6.27-11.16) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic

Setting up ufw (0.23.3) ...
Installing new version of config file /etc/init.d/ufw ...

Setting up libatspi1.0-0 (1.24.0-0ubuntu3.8.10.1) ...

Setting up at-spi (1.24.0-0ubuntu3.8.10.1) ...

Setting up python-pyatspi (1.24.0-0ubuntu3.8.10.1) ...

Setting up ca-certificates-java (20080712ubuntu4) ...
Installing new version of config file /etc/ca-certificates/update.d/jks-keystore ...

Setting up libpulse0 (0.9.10-2ubuntu9.3) ...

Setting up libpulse-browse0 (0.9.10-2ubuntu9.3) ...

Setting up libpulsecore5 (0.9.10-2ubuntu9.3) ...

Setting up linux-image-generic (2.6.27.11.14) ...
Setting up linux-restricted-modules-generic (2.6.27.11.14) ...
Setting up linux-generic (2.6.27.11.14) ...
Setting up linux-headers-2.6.27-11 (2.6.27-11.25) ...
Setting up linux-headers-2.6.27-11-generic (2.6.27-11.25) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic                                                                                       
 *  fglrx (8.543)...                                                                                                                                         fglrx (8.543): Already installed on this kernel.
                                                                                                                                                      [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.27.11.14) ...
Setting up linux-libc-dev (2.6.27-11.25) ...
Setting up pulseaudio (0.9.10-2ubuntu9.3) ...

Setting up pulseaudio-esound-compat (0.9.10-2ubuntu9.3) ...
Setting up pulseaudio-module-gconf (0.9.10-2ubuntu9.3) ...
Setting up pulseaudio-module-hal (0.9.10-2ubuntu9.3) ...
Setting up pulseaudio-utils (0.9.10-2ubuntu9.3) ...
Setting up pulseaudio-module-x11 (0.9.10-2ubuntu9.3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 m4
 autoconf
 automake1.7
 intltool
 cdbs
 dvipng
 texi2html
 texlive-base-bin-doc
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake1.7:
 automake1.7 depends on autoconf (>= 2.54); however:
  Package autoconf is not configured yet.
dpkg: error processing automake1.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of intltool:
 intltool depends on automake1.7 | automaken; however:
  Package automake1.7 is not configured yet.
  Package automaken is not installed.
  Package automake1.7 which provides automaken is not configured yet.
dpkg: error processing intltool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdbs:
 cdbs depends on intltool; however:
  Package intltool is not configured yet.
dpkg: error processing cdbs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 autoconf
 automake1.7
 intltool
 cdbs
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 0 updates [-20].
amir@Simulator:~$
```

> What I was trying to say is that if indeed the internet connection was lost during the installation process, it is rational to assume that a needed dependency was not fully downloaded and thus, without the dependency there for configuration, the error messages you received are reasonable. That said, have you tried to clean out /var/apt/cache by removing the packages that had downloaded, and then trying it again?

[COLOR="Blue"]Thanks for your response. isn't there a way to tell apt-get or aptitude to not start installation before all the packages are received successfully to avoid dependency problems?

Also, the /var/cache/apt/archives/partial is empty now as i have cleaned them in 'sudo apt-get clean'.

Thanks for your responses.
[/COLOR]

---

### Post by shundi on 2009-01-29
Interesting...I'm having the same problem and have tried all of the above without any success...

---

### Post by pajoohesh on 2009-01-29
[COLOR="Blue"]unfortunately ubuntu suffers from this problem. I have also looked much more threads but found no way. however somewhere recommended using -s or --dry-run to avoid from package dependency problems but I am not sure how much it will work.

and maybe another way to have all the packages and then doing installation is using --download-only option. [/COLOR]

---

### Post by hoogland on 2009-04-16
I got around the problem by removing all referenced files of the partially installed package as follows:


cd /var/lib/dpkg/info

sudo rm m4* (in case of m4 failing to install properly)

sudo apt-get install -f

---

### Post by peakshysteria on 2009-04-17
This may seem simple, and I'm not sure it will work or that it relates to your problem, but have you tried marking *all updates* in Synaptic and applying it there? This was the solution for me with a similar problem. Mythread; [http://ubuntuforums.org/showthread.php?t=1127560](http://ubuntuforums.org/showthread.php?t=1127560)

---

