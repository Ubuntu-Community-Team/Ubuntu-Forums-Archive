---
title: "Finished Custom build: ATI problem"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by spyrosebastos on 2009-05-20
Hello all;

I have been using Ubuntu 8.04 on a 2005 dell i386.  Today I finished building my next comp, which was the first build of my own actually for myself.  Anyway, Jaunty-64 installed fine from the CD, and when I start it, everything starts fine up untill the grub loads... however after that, my screen turns black and the only thing that comes up is my Username, then password, then command (terminal) prompt, no GUI at all.

I'm confident the hardware that is giving me the probs is the ATI card.

I've tried:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)   (.pdf intructions)

and read:

[http://ubuntuforums.org/showthread.php?t=1133931&highlight=ATI+Drivers&page=22](http://ubuntuforums.org/showthread.php?t=1133931&highlight=ATI+Drivers&page=22)

These three got me nowhere for their own reasons, that I can explain for anyone if necessary.  Also, doing a clean install of 8.10 doesn't work past the initial install screen from the LiveCD.  It just goes black with a blinking underscore.

Does anyone know or have a link to a site where to find the command to install/unpack the necessary drivers to get the GUI working.  

Oh, last thing, I cannot connect to third party repositories in this "text-only mode"; that i have learned via some commands from the first link posted.  I couldn't reach canonical.

Suggestions?

---

### Post by pro003 on 2009-05-20
in text mode you can edit sources by typing

sudo vi /etc/apt/sources.list

and uncheck third party and what else you got there with # just remover the **#** sign in front of **deb [http://.](http://.)..**

---

### Post by spyrosebastos on 2009-05-22
thanks, but I totally gave up on 9.04 after a few days... isn't worth the hassle for the minor difference over 8.10 IMO

And the reason a clean install of 8.10 wouldn't work because it was a i386 version.  

I Installed clean install of 8.10-64 and it installed fine but when it gets to the login page the mouse and keyboard are completely frozen... no crtl+alt+del, no ctrl+alt+F1. 
I have my BIOS setup to halt boot on any error; it notifies me- the keyboard and mouse are non-existent/undisplayed/unknown.  (The bios wont go farther than this unless I change this option to "Boot regardless of erros").

How can I get into the command prompt to adjust how the OS identifies the keyboard and mouse from the 8.10 login screen?  I can do less w/ 8.10 than w/ the command prompt only of 9.04.

8.04 LTS Live disc will not work, screen just turns white after I select "Install Ubuntu"

---

### Post by pro003 on 2009-05-22
does your hardware supports x64 infrastructure? you've said that you installed x64, thats why I ask you this...

---

### Post by spyrosebastos on 2009-05-23
Well I had spent an hour typing a lengthy response but Ubuntu forums signed me out before I could send it.  So When I signed in it wouldn't let me copy it, great, fantastic.

System:
i7 940 o.c. @ 3.05ghz -3.25ghz running @ 25-30 degrees C
6gb triple channel ram @ 2100mhz
1000 watt power
PNY GeForce 250 - 1024 mb gddr3 - (I returned the ATI 4780 hoping the Nvidia card would be smoother to install; It's not.)
LG BR/DVD reader/writer
2.1 tb harddrive

64-bit works on my mother's computer I just upgraded...

I'll type my source list later, if it is even possible to transcribe it- or will the forums log me out before its done again.

---

### Post by spyrosebastos on 2009-05-23
This is the command-line response to: sudo vi etc/apt/sources.list:

#dev cdrom: [Ubuntu 9.04 _Jaunty Jackalope_-release amd64 (20090420.1)]/  jaunty main restricted                                                                                                                # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to            # newer versions of the distribution                                                                                                                                                                                                          deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted                                deb-src http:// us.archive.ubuntu.com/ubuntu/ jaunty main restricted                                                                                                                                                          ## Major bug fix updates proceed after the final release of the                                     ##distribution.                                                                                                          deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted                      deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted                                                                                                                                           ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu           ## team. Also, please note that software in universe WILL NOT receive any                 ## review or upgrades from the Ubuntu security team                                              deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe                                          deb-src  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe                                    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe                             deb-src  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe                                                                                                                                                    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu           ## team, and may not be under a free licence. please satisfy yourself as to                 ## your rights to use the software. Also, please note that software in                           ## multiverse WILL NOT receive any review or updates from the ubuntu                       ## security team                                                                                                     deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse                                       deb-src   [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse                                deb [http://us.archive.ubuntu.com/ubuntu/jaunty-updates](http://us.archive.ubuntu.com/ubuntu/jaunty-updates) multiverse                            deb-src  [http://us.archive.ubuntu.com/ubuntu/jaunty-updates](http://us.archive.ubuntu.com/ubuntu/jaunty-updates) multiverse                                                                                                                                                   ## Uncomment the following two lines to add software from the "backports"                  ## repository                                                                                                           ## N.B. software from this repository may not have been tested as                              ## extensively as that contained in the main release, although it includes                     ## newer versions of some applications which may provide useful features.                  ## Also, please note that software in backports will not receive any review                    ## or updates from the Ubuntu security team.                                                            # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted univ         erse multiverse                                                                                                         #deb-src  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted     universe multiverse                                                                                                  ## Uncomment the following two lines to add software from Canonical's                        ## 'partner' repository.                                                                                             ## this software is not part of Ubuntu, but is offered by Canonical and the                     ## resective vendors as a service to Ubuntu users.                                                     # deb [http://archive.canonical.com](http://archive.canonical.com) {ubuntu jaunty partner}                                #deb-src http://archive.canonical.com{ubuntu jaunty partner}                                    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted                          deb-src   [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted                  deb http:// security.ubuntu.com/ubuntu jaunty- security universe                    
deb-src  http:// security.ubuntu.com/ubuntu jaunty- security universe      
deb [http://sec](http://sec) [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://sec](http://sec) [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

Trying 8.04-32 before working with 9.04 again.

---

### Post by spyrosebastos on 2009-05-23
wow maybe should have put that in html

---

### Post by pro003 on 2009-05-24
wow gee, you've typed all that? it must have took you hours to do that. well, like you asked I have told you, you 
said non-gui (dos-like environment) came up with no X, offering you to login, well do the login, type your username and pass and it should get you in, and the type 

```
sudo -s
```
and enter again your pass which is also roots pass but only by default. you'll get **root@ubuntu~#** 

then type this:

```
/etc/init.d/networking start
```

it should give you internet access by DHCP protocol, but only if you have a direct internet access from this machine, i.e if you have to create pppoe or vpn the command above won't help.

anyways, if you gain internet access try to update your system by typing:

```
apt-get update && apt-get upgrade
```

click Y to confirm, it will check your configuration and download whatever your system needs to be functional.



if all goes well reboot the system after update

```
sudo shutdown -hr now
```

if you againg get into dos like environment then upgrade didn't help and we take plan b, which is downloading the driver for your card and installing it.

but this we'll try after you try plan A.

p.s. it would be good if you already made it by yourself or maybe totally gave up on ubuntu and installed some other OS, hehehee...

---

### Post by pro003 on 2009-05-24
Ok I'll just write here another step that might help and that is getting the driver and installing it:

Again we are talking about the situation of non-gui mode i.e dos-like mode. you login and then you start the networking with command posted in previos post above and then you download the driver, I assume you'll have 4870 like you said above somewhere.

so, this is what it looks after login:

yourusername@ubuntu~#

we download the driver using wget:

```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run
```

the driver should be downloaded in your home directory.

then we start installing this driver by typing:

```
sudo sh ati-driver*.run
```

it should start to uncompressing and the rest of process is easy, you just hit enter enter until it's done and you're back in non gui mode, then initiate the driver:

```
sudo aticonfig --initiate
```

and then reboot

```
sudo reboot
```

hopefully next you'll see is a full gui mode in your screens snative resolution, and your problem should be solved.

But again, hopefully.

Good luck. ):P

---

### Post by spyrosebastos on 2009-05-26
Thank for your help; sorry about the last two posts, I was pretty frustrated by that point. Unfortunately, I don't think Ubuntu likes this computer very much- 8.04-32/64 can't identify/recognize harddrives, 8.10-32/64 the keyboard mouse bug handicaps the OS... 9.04-32/64 do work though.

For now, Fedora 10 installed smoothly.  I'll probably wait for the next LTS before switching back.

---

### Post by pro003 on 2009-05-26
Fedora 11 (Leonidas) final release should actually come out today on 26th May, I've read that recently, actually I was giving a thought to try it myself...

Good luck.

---

