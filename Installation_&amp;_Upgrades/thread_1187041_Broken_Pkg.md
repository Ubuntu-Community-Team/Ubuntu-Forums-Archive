---
title: "Broken Pkg ?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by lotusalive on 2009-06-14
Weell, did not expect it, but while installing libkdcraw7 from Synaptic Pkg Mgr, it has hung itself without fully installing, with the following reason:

E: /var/cache/apt/archives/libkdcraw7_4%3a4.2.2-0ubuntu2_i386.deb: trying to overwrite `/usr/share/kde4/apps/libkdcraw/profiles/adobergb.icm', which is also in package libkdcraw5


libdkcraw5 and libkdcraw-dev will NOT uninstall.  libkdcraw7 will NOT install, _AND_ will NOT Unmark, much less uninstall !  Update in Terminal produces same result, and Update Mgr is also hung because of it.

When I ask the Broken Filter to Repair libkdcraw7, it replies it has Successfully Removed Dependencies, yet the 'hang' still exists...

As a result of this, I cannot Uninstall the 4 packages that are 'local or obsolete' until this is fixed, and suspect I can't install anything... :(

All ideas welcome !

The Broken Dependencies Pkgs are 'Darkroom,' and 'libdvdcss2,' and with libkdcraw7 not installing or unmarking, these broken packages remain that way...  

Installing all Missing Recommends under Custom Filters fixed the libdcraw7 problem, by unmarking it, and also uninstalled 'darkroom,' Synaptic Pkg Mgr no longer hung.  YET: libdvdcss2 is still 'Broken' status under Custom Filter...

---

### Post by gradinaruvasile on 2009-06-14
Try 

sudo apt-get install -f

in a terminal

---

### Post by lotusalive on 2009-06-14
That command could not do it when I tried it with a hung Synaptic and Update Mgr !  Command did work, post 'hang,' and freed up 56.9MB disk space removing what is no longer needed !  Thx !

Still do not know what to think of Broken Pkg libdvdcss2.  Have not pursued it, but none of my dvd's work in Jaunty.

---

### Post by gradinaruvasile on 2009-06-14
> **lotusalive said:**
> That command could not do it when I tried it with a hung Synaptic !

You must quit synaptic. Then run this command at the terminal. Only 1 package management tool is allowed at 1 time be it synapic, apt whatever.
Please do that and post the output from the terminal.

---

### Post by lotusalive on 2009-06-14
This is my sys now:

sol@sol-desktop:~$ sudo apt-get upgrade
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  brasero glade-3 glade-gnome-3 gnome-settings-daemon-dev libbrasero-media0
  libgladeui-1-9
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2719kB of archives.
After this operation, 709kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libbrasero-media0 2.26.1-0ubuntu1 [196kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main brasero 2.26.1-0ubuntu1 [1540kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libgladeui-1-9 3.6.3-0ubuntu1 [439kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main glade-gnome-3 3.6.3-0ubuntu1 [31.6kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main glade-3 3.6.3-0ubuntu1 [491kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main gnome-settings-daemon-dev 2.26.1-0ubuntu2 [22.3kB]
Fetched 2719kB in 20s (133kB/s)                                                
(Reading database ... 229627 files and directories currently installed.)
Preparing to replace libbrasero-media0 2.26.0-0ubuntu3 (using .../libbrasero-media0_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement libbrasero-media0 ...
Preparing to replace brasero 2.26.0-0ubuntu3 (using .../brasero_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement brasero ...
Preparing to replace libgladeui-1-9 3.6.1-0ubuntu1 (using .../libgladeui-1-9_3.6.3-0ubuntu1_i386.deb) ...
Unpacking replacement libgladeui-1-9 ...
Preparing to replace glade-gnome-3 3.6.1-0ubuntu1 (using .../glade-gnome-3_3.6.3-0ubuntu1_i386.deb) ...
Unpacking replacement glade-gnome-3 ...
Preparing to replace glade-3 3.6.1-0ubuntu1 (using .../glade-3_3.6.3-0ubuntu1_i386.deb) ...
Unpacking replacement glade-3 ...
Preparing to replace gnome-settings-daemon-dev 2.26.0-0ubuntu4 (using .../gnome-settings-daemon-dev_2.26.1-0ubuntu2_i386.deb) ...
Unpacking replacement gnome-settings-daemon-dev ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up libbrasero-media0 (2.26.1-0ubuntu1) ...

Setting up brasero (2.26.1-0ubuntu1) ...

Setting up libgladeui-1-9 (3.6.3-0ubuntu1) ...

Setting up glade-3 (3.6.3-0ubuntu1) ...

Setting up glade-gnome-3 (3.6.3-0ubuntu1) ...
Setting up gnome-settings-daemon-dev (2.26.1-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
sol@sol-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Packages
Reading package lists... Done
sol@sol-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sol@sol-desktop:~$

All recommendations appreciated !  Thanks gradinaruvasile !

---

