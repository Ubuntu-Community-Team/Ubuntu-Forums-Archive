---
title: "upgrade failed but update manager does not offer upgrade any more"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by barnskybeat on 2009-01-04
I recently tried to upgrade from 8.04 to 8.10 (network upgrade). The upgrade was interrupted at an early stage (download of packages) due to a network outage. 

Later I wanted repeat/re-start the upgrade but now the Upgrade Manager does not offer the upgrade any more.

Any help?

---

### Post by Pumalite on 2009-01-04
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by barnskybeat on 2009-01-05
Tried it to no avail. upgrade still not offered:
here are the details,any other idea?


dirk@dirk-laptop:~$ sudo dpkg --configure -a
[sudo] password for dirk: 
dirk@dirk-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk-vnc-1.0-0 obex-data-server python-pyatspi python-brlapi libavahi-ui0
  libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dirk@dirk-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Reading package lists... Done
dirk@dirk-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dirk@dirk-laptop:~$

---

### Post by albinootje on 2009-01-05
> **barnskybeat said:**
> Tried it to no avail. upgrade still not offered:

Can you start with the upgrade-manager again ?
```

$ update-manager -h
Usage: update-manager [options]

Options:
  -h, --help            show this help message and exit
  -V, --version         Show version and exit
  -c, --check-dist-upgrades
                        Check if a new distribution release is available
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Upgrade using the latest proposed version of the
                        release upgrader
  --dist-upgrade        Try to run a dist-upgrade

```
And post your /etc/apt/sources.list here please.

---

### Post by barnskybeat on 2009-01-06
sorry , but I am pretty new to linux and this command line stuff. when entering the commands into the terminal window I get nothing but error messages...

anyhow. here's my sources list:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://kh.archive.ubuntu.com/ubuntu/](http://kh.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://kh.archive.ubuntu.com/ubuntu/](http://kh.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

---

### Post by albinootje on 2009-01-06
OK. Can you post the output of the following in a terminal :
```

uname -a
lsb_release -a

```
And run this :
```

sudo apt-get update
gksu update-manager --dist-upgrade

```
And report back whether that starts to continue with the upgrade or not.

---

### Post by Pumalite on 2009-01-06
There are many ways to upgrade. Now that you are fully apdated and that apt-get seems OK:; you could give a try to the official method:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You can also use the Alternate CD Method which is included in the above link.

---

### Post by barnskybeat on 2009-01-06
Here the output:
ddirk@dirk-laptop:~$ uname -a
Linux dirk-laptop 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux
dirk@dirk-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
dirk@dirk-laptop:~$ sudo apt-get update
[sudo] password for dirk: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US           
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports Release.gpg         
Ign [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Translation-en_US       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release [24.2kB]                         
Ign [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                    
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/main Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources                 
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/restricted Packages 
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/universe Packages   
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/multiverse Packages 
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/main Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/restricted Sources  
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Fetched 1B in 5s (0B/s)
Reading package lists... Done
dirk@dirk-laptop:~$ gksu update-manager --dist-upgrade
gksu: unrecognized option `--dist-upgrade'
GKsu version 2.0.0

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
dirk@dirk-laptop:~$

---

### Post by barnskybeat on 2009-01-06
and this one:

dirk@dirk-laptop:~$ sudo apt-get --dist-upgrade
E: Sense dist is not understood, try true or false.
dirk@dirk-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dirk@dirk-laptop:~$

---

### Post by Pumalite on 2009-01-06
sudo apt-get dist-upgrade
(remove '--' in front of dist)

---

### Post by barnskybeat on 2009-01-06
did that already in line three above. here again the result:
dirk@dirk-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dirk@dirk-laptop:~

---

### Post by barnskybeat on 2009-01-06
alternate CD method also does not work, i.e. mounting iso file as cdrom0 on desktop

---

### Post by albinootje on 2009-01-06
> **barnskybeat said:**
> 
dirk@dirk-laptop:~$ gksu update-manager --dist-upgrade
gksu: unrecognized option `--dist-upgrade'
GKsu version 2.0.0

Usage: gksu [-u <user>] [options] <command>


Sorry to see this :(
Since you wrote that your dist-upgrade was interrupted.. can you try this please :
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo update-manager --dist-upgrade

```

---

### Post by barnskybeat on 2009-01-07
you are a star, upgrade just started running!

---

