---
title: "Regarding updates"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Yashpal1985 on 2009-06-02
Hey can any one give the latest **Sources.list** for ubuntu 8.10 for i386 ...i think my source.list has become obsolete....its no more updating my system??? guys please reply ASAP...its damn URGENT... :( :( :(

---

### Post by MichaelSammels on 2009-06-02
```
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

Here you go, hope this helps. :)

---

### Post by MichaelSammels on 2009-06-02
However, also try:

```
sudo apt-get update
```

---

### Post by Yashpal1985 on 2009-06-02
i tried apt-get update

but it follows by this::

[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# apt-get update Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all Release.gpg
Ign [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Translation-en_US                          
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                
Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all Release                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Ign [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Packages                         
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
99% [Waiting for headers]^Cated.com intrepid/main Packages
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# 
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# vim /etc/apt/sources.list
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# apt-get update 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US                                                                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                                                                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                                                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages         
Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all Release.gpg     
Ign [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Translation-en_US                
Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all Release                               
Ign [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Packages 
Hit [http://apt.wakoopa.com](http://apt.wakoopa.com) all/main Packages
99% [Waiting for headers]^C:   



And stops eventually

---

### Post by MichaelSammels on 2009-06-02
Did you try the sources.list I posted?

---

### Post by Yashpal1985 on 2009-06-02
i will try them right now...thnks

---

### Post by MichaelSammels on 2009-06-02
Once you replace your sources with mine, be sure to run:

```
sudo apt-get update
```

Any problems, post the results here. :)

---

### Post by Yashpal1985 on 2009-06-02
can u tell me how to replace the sources.list with yours??

---

### Post by MichaelSammels on 2009-06-02
Open Terminal:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Yashpal1985 on 2009-06-02
I replaced my sources.list with yours but.....


i am getting this error::

[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by MichaelSammels on 2009-06-02
Run this:

```
sudo killall apt-get
sudo killall aptitude
sudo killall dpkg
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Yashpal1985 on 2009-06-02
Tried your command but this is the output::




[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# export http_proxy=http://yashpal.si:789456@192.168.10.2:3128
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# sudo killall apt-get
apt-get: no process killed
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# sudo killall aptitude
aptitude: no process killed
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# sudo killall dpkg
dpkg: no process killed
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# sudo dpkg --configure -a
[email]root@sk-yshpal-si:/home/DIRECTI/yashpal.si[/email]# sudo apt-get update
0% [Waiting for headers] [Waiting for headers]

---

### Post by MichaelSammels on 2009-06-02
Are you running some form of Proxy Server (such as SquidGuard/DansGuardian) or Firewall Software (such as ufw, iptables or FireStarter)?

---

### Post by Yashpal1985 on 2009-06-02
Yes i am accessing from a proxy server.... is there any issue regarding that?

---

### Post by MichaelSammels on 2009-06-02
Perhaps the proxy server is blocking aptitude. Disable your proxy server and try again. If it works, make sure you setup your proxy settings in:

System -> Preferences -> Network Proxy

And select it for system wide, but try disabling it first. :)

---

### Post by Yashpal1985 on 2009-06-02
thanks for your help.....

---

