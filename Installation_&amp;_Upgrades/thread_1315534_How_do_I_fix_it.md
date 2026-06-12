---
title: "How do I fix it"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by sunny10 on 2009-11-05
cant update ubuntu 9.10
it repeatedly downloading same updation file
terminal view:
sunny@sunny-laptop:~$ sudo apt-get upgrade
[sudo] password for sunny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  binutils brasero checkbox checkbox-gtk empathy empathy-doc f-spot firefox
  firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support info install-info kerneloops-daemon libbrasero-media0
  libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30
  libpoppler-glib4 libpoppler5 libpython2.6 libusplash0 nvidia-common
  poppler-utils python python-minimal python-ubuntuone-client python2.6
  python2.6-minimal ubuntu-xsplash-artwork ubuntuone-client
  ubuntuone-client-gnome update-manager update-manager-core usplash
  xserver-common xserver-xorg-core xsplash xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support
42 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.9MB of archives.
After this operation, 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
0% [1 libpython2.6 241664/967kB 24%]                         24.4kB/s 16min 53s^Get:2 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
Get:3 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
Get:4 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
1% [4 libpython2.6 253952/967kB 26%]                          63.0kB/s 6min 31s^C
sunny@sunny-laptop:~$ 





&
kernal problem
compaq presario cq60 pc
linux-backports-modules-2.6.31-14-generic N/A
linux-firmware 1.24
plz help me

---

### Post by jjcv on 2009-11-05
> **sunny10 said:**
> 
Get:4 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
1% [4 libpython2.6 253952/967kB 26%]                          63.0kB/s 6min 31s^C
sunny@sunny-laptop:~$ 

I cannot see what the problem is because you did not let apt-get finish to the part where is gives you the error messages.   Can you run apt-get upgrade again but this time paste the last 10 or 15 lines after it finished which should contain the error messages?

---

