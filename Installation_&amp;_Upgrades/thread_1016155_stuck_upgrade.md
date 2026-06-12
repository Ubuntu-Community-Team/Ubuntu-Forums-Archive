---
title: "stuck upgrade"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by paul cooke on 2008-12-19
distribution upgrade is stuck almost 1 minute from end of installing upgrades, just before cleaning up.

last message shown is:
Starting ivman: manager.c.1387 (do_startup_configure) Directory /etc/ivman will be used for configuration files

apparently there was an error message earlier about adduser and some new user called ivman, but that error has scrolled up and is lost

how can I cleanly kick the upgrader onto the cleaning up and finishing off

oh, that didn't work... ctrl C has killed off the distribution upgrader completely.

---

### Post by paul cooke on 2008-12-19
opened a terminal and tried the following:

```
paulc@broken-drum:~$ sudo apt-get clean
[sudo] password for paulc: 
paulc@broken-drum:~$ sudo dpkg --configure -a
Setting up ivman (0.6.14-3ubuntu1) ...
Starting ivman: manager.c:1387 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
dpkg: error processing ivman (--configure):
 subprocess post-installation script killed by signal (Interrupt) (that was me kicking it)
Errors were encountered while processing:
 ivman
paulc@broken-drum:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libitext-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ivman (0.6.14-3ubuntu1) ...
Starting ivman: manager.c:1387 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
dpkg: error processing ivman (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 ivman
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
paulc@broken-drum:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg                     
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB       
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy Release                                 
Ign http://archive.canonical.com hardy/partner Translation-en_GB               
Hit http://gb.archive.ubuntu.com hardy-updates Release                         
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.canonical.com hardy Release                                 
Hit http://gb.archive.ubuntu.com hardy/main Sources                            
Hit http://gb.archive.ubuntu.com hardy/restricted Sources                      
Hit http://gb.archive.ubuntu.com hardy/universe Sources    
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy Release.gpg             
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://archive.ubuntu.com hardy/main Translation-en_GB
Hit http://archive.ubuntu.com hardy/restricted Translation-en_GB
Hit http://archive.ubuntu.com hardy-backports Release.gpg
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_GB
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-backports Release
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Reading package lists... Done
paulc@broken-drum:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  k3b xmms-wma
The following packages will be upgraded:
  ubuntu-docs
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 3520kB of archives.
After this operation, 19.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com hardy-updates/main ubuntu-docs 8.06.1 [3520kB]
Fetched 3520kB in 3s (1141kB/s)       
(Reading database ... 359742 files and directories currently installed.)
Preparing to replace ubuntu-docs 6.06.2 (using .../ubuntu-docs_8.06.1_all.deb) ...
Unpacking replacement ubuntu-docs ...
Setting up ivman (0.6.14-3ubuntu1) ...
Starting ivman: manager.c:1387 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
```

basically, it's frozen trying to start ivman... and from what I've googled, ivman is pretty important... how the bleep do I get past this as I daren't reboot this box at the moment

---

### Post by cariboo on 2008-12-19
If you run in a terminal:

```
sudo apt-get purge ivman
```

You should be able to finish your upgrade, if you need ivman you can always reinstall it after the upgrades are done.

Jim

---

### Post by paul cooke on 2008-12-19
OK, that gave the following:

```
paulc@broken-drum:~$ sudo apt-get purge ivman
[sudo] password for paulc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libitext-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ivman*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 291kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 360803 files and directories currently installed.)
Removing ivman ...
Stopping ivman: ivman.
Stopping ivman: ivman.
Purging configuration files for ivman ...
```

I'm now going for the reboot... fingers crossed...

---

### Post by paul cooke on 2008-12-19
OK, I'm back... I have a shiny system... usb pen drive automounts

Quick question. How can I recover the disk space consumed by the files downloaded for the upgrade? They're still there, but I don't know where they were put and synaptic has no change in disk space when I click the "delete cached package files" button

---

### Post by Ublis on 2008-12-19
You could try running "sudo apt-get clean" or "sudo apt-get autoclean" in a terminal. Not sure if they do the same thing as the button in synaptic.

---

