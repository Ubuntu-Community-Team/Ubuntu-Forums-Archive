---
title: "I NEED HELP Error w/  dhcdbd
 network-manager
 network-manager-gno
dpkg: error pro"
date: 2008-09-18
forum: General Help
---

### Post by morissette on 2008-09-18
Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome





```
root@morissette:/home/morissette# sudo aptitude install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@morissette:/home/morissette# sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  gimp-gnomevfs libgimp2.0 tomboy 
The following packages have been kept back:
  gimp gimp-data gimp-python 
The following partially installed packages will be configured:
  dhcdbd network-manager network-manager-gnome 
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up dhcdbd (2.0-5ubuntu1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                            invoke-rc.d: initscript dhcdbd, action "start" failed.
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up dhcdbd (2.0-5ubuntu1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                            invoke-rc.d: initscript dhcdbd, action "start" failed.
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
root@morissette:/home/morissette# sudo dpkg --configure -a
Setting up dhcdbd (2.0-5ubuntu1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                            invoke-rc.d: initscript dhcdbd, action "start" failed.
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome
root@morissette:/home/morissette# sudo apt-get install --reinstall hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/339kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 124704 files and directories currently installed.)
Preparing to replace hal 0.5.9.1-6ubuntu5 (using .../hal_0.5.9.1-6ubuntu5_i386.deb) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
Unpacking replacement hal ...
Setting up dhcdbd (2.0-5ubuntu1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                            invoke-rc.d: initscript dhcdbd, action "start" failed.
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up hal (0.5.9.1-6ubuntu5) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 

Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@morissette:/home/morissette# sudo -s
root@morissette:/home/morissette# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@morissette:/home/morissette# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 tomboy
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dhcdbd (2.0-5ubuntu1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                            invoke-rc.d: initscript dhcdbd, action "start" failed.
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dhcdbd
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@morissette:/home/morissette# sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

```

---

### Post by pytheas22 on 2008-09-18
Try running:
```

sudo apt-get remove --purge dhcdbd
sudo apt-get remove --purge network-manager
sudo apt-get remove --purge network-manager-gnome
sudo apt-get install network-manager-gnome
```

Does that give you different results?  If not, what does:
```

sudo aptitude install network-manager-gnome
```

do?

---

