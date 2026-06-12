---
title: "Converting Ubuntu to UbuntuCE"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by tomh5480 on 2009-10-13
I ran the following command to convert from Ubuntu to UbuntuCE:

*wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg](http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg) -O- | sudo apt-key add - && wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O- | sudo apt-key add - && sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce*

This is what I get in the terminal window; it's basically telling me that I need to fix some dependencies so that e-sword-installer, dansguardian-gui and encfs-gui will install.  But what do I fix?


-2009-10-13 09:44:48--  [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list)
Resolving ubuntuce.com... 66.40.7.42
Connecting to ubuntuce.com|66.40.7.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 418 [text/plain]
Saving to: `/etc/apt/sources.list.d/ubuntuce.list'

100%[===================================================================================>] 418         --.-K/s   in 0s      

2009-10-13 09:44:48 (26.2 MB/s) - `/etc/apt/sources.list.d/ubuntuce.list' saved [418/418]

Ign [http://ubuntuce.com](http://ubuntuce.com) jaunty_i386/ Release.gpg
Ign [http://ubuntuce.com](http://ubuntuce.com) jaunty_i386/ Translation-en_US                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                      
Ign [http://ubuntuce.com](http://ubuntuce.com) jaunty_i386/ Release                                                                                
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg [189B]                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Get:2 [http://ubuntuce.com](http://ubuntuce.com) jaunty_i386/ Packages [2384B]                                                                     
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release [1019B]                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages [1271B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Fetched 4863B in 3s (1258B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pkgcrosswire_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: e-sword-installer but it is not going to be installed
             Depends: dansguardian-gui but it is not going to be installed
             Depends: encfs-gui but it is not going to be installed
E: Broken packages


Thanks,
TomH

---

### Post by mac9416 on 2009-10-13
From here: [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)


Open System>Administration>Synaptic then...

>  'Broken packages' are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow any further changes to the system until all broken packages have been fixed.
To fix broken packages
[LIST=1]
[*]Choose Edit > Fix Broken Packages from the menu.
[*]Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
[*]Confirm the summary of changes and click Apply.
[/LIST] 

If you prefer the command line:

```
$ sudo apt-get install -f
```

If that appears to fix it, try to install ubuntu-ce again:

```
$ sudo apt-get update && sudo apt-get install ubuntu-ce
```

Hope that helps!

---

### Post by tomh5480 on 2009-10-13
Thanks for the reply.
 
I did that and it updated wine, so I then ran the ubuntuce update line again which produced the same dependencies errors. I re-ran the 'sudo apt-get install -f' line.  The 2nd time nothing changed, and the ubuntuce update still won't go.
 
TomH
 
 
> **mac9416 said:**
> From here: [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)
 
 
Open System>Administration>Synaptic then...
 
 
 
If you prefer the command line:
 
```
$ sudo apt-get install -f
```
 
If that appears to fix it, try to install ubuntu-ce again:
 
```
$ sudo apt-get update && sudo apt-get install ubuntu-ce
```
 
Hope that helps!

---

