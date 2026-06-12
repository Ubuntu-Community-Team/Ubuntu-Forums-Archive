---
title: "Update Manager Problem"
date: 2008-08-21
forum: General Help
---

### Post by TheMixtureMedia on 2008-08-21
Hi there my updatemanager crashed on me it will not look for new updates and I can not check the software source. I can not even upgrade to 8.10 update manager just goes away any idea??

---

### Post by hermes0710 on 2008-08-21
Can you post the output of the command "sudo apt-get update" (terminal) ?

---

### Post by dannyboy79 on 2008-08-21
> **TheMixtureMedia said:**
> Hi there my updatemanager crashed on me it will not look for new updates and I can not check the software source. I can not even upgrade to 8.10 update manager just goes away any idea??

you can check the software source by issuing this command

```
gksudo gedit /etc/apt/sources.list
```

I use aptitude instead of apt-get because when you install apps with aptitude it will remember what dependencies were installed with it, then when you go to remove that app, it will remove those extra dependencies that aren't needed where apt-get just leaves them if you do sudo apt-get remove app. Just an FYI

---

### Post by TheMixtureMedia on 2008-08-21
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release.gpg [189B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release.gpg [189B] 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                         
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports Release [44.0kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed Release [58.5kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Packages [56.0kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Packages [14B]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Packages [38.3kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Packages [6763B]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/main Sources [8785B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/restricted Sources [14B]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/universe Sources [10.5kB]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-backports/multiverse Sources [2594B]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Packages [7074B]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Packages [69.2kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Packages [13.0kB]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Packages [19.7kB]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/restricted Sources [896B]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main Sources [25.4kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/multiverse Sources [2291B]
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/universe Sources [6338B]
Fetched 370kB in 2s (155kB/s)                       
Reading package lists... Done



# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties

---

### Post by TheMixtureMedia on 2008-08-21
Anyone have any ideas??

---

### Post by TheMixtureMedia on 2008-08-21
Can anyone help me I posted the information you asked me to...

---

### Post by TheMixtureMedia on 2008-08-22
why does no one want to help me with this???

---

### Post by phoenix49 on 2008-08-22
Have you tried

sudo apt-get upgrade

?

---

### Post by TheMixtureMedia on 2008-08-22
But I can not still get my update manager or upgrade to 8.10 to work but this is what it says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-restricted-modules-2.6.24-21-generic linux-restricted-modules-common
  nvidia-glx
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132054 files and directories currently installed.)
Preparing to replace linux-restricted-modules-common 2.6.24.14-21.47 (using .../linux-restricted-modules-common_2.6.24.14-21.48_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Preparing to replace linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47 (using .../linux-restricted-modules-2.6.24-21-generic_2.6.24.14-21.48_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.24-21-generic ...
Preparing to replace nvidia-glx 1:96.43.05+2.6.24.14-21.47 (using .../nvidia-glx_1%3a96.43.05+2.6.24.14-21.48_i386.deb) ...
Unpacking replacement nvidia-glx ...
Setting up linux-restricted-modules-common (2.6.24.14-21.48) ...

Setting up linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.48) ...

Setting up nvidia-glx (1:96.43.05+2.6.24.14-21.48) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by dannyboy79 on 2008-08-22
so you're saying that the update manager GUI isn't working? I am not sure what to tell about that. If you want to upgrade to 8.10, that command would be 

sudo aptitude -s dist-upgrade
and that will simulate what would happen if you ran that command. If what pops up is tons of stuff, then it may be safe to assume that you'll be upgrading to 8.10, so then you would run the command again without the -s, the -s stands for simulate what would happen. Look into using aptitude instead of apt-get. you can goggle as to why and you'll soon be using aptitude before apt-get, IF you can figure out you're update manager GUI problem that is. 

WHat exactly happens when you go to system, administration, update manager?

And what happens if you started it through the terminal by issuing

gksudo /usr/bin/update-manager

does anything else show up in the terminal after you run that command like errors or what not?

---

### Post by TheMixtureMedia on 2008-08-22
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 43, in <module>
    gtk.init_check()
RuntimeError: could not open display

this is what happends :-(

---

### Post by Aenima99x on 2008-08-22
Try the following commands in a terminal

```
sudo apt-get install python2.5
```
```
sudo apt-get install python-gnome2
```
```
sudo apt-get install python-software-properties
```

---

### Post by dannyboy79 on 2008-08-22
wait, are you even using a Window Manager? Whenever I see things like "can not open display" that means there's no window manager. Like right now I am tied into my home computer through ssh. In the terminal I can type in gksudo gedit /etc/fstab and it returns:
(gksudo:11255): Gtk-WARNING **: cannot open display:

You must be using a Window Manager like Gnome but something is definitely messed up. Follow what Aenima99x is saying and hopefully that fixes it.

---

