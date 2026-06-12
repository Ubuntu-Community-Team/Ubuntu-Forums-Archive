---
title: "NVIDA Driver issue"
date: 2010-03-07
forum: Hardware
---

### Post by Chris Chandler on 2010-03-07
Yesterday I encountered a frustrating issue.  I turned the computer on in the morning and there were some automatic updates that needed to be loaded.  I ran the updates and then left the computer alone until after lunchtime.  I restarted and things started being problematic.  On startup, the video driver can't be initiated:

> NVIDIA(0): Failed to initialize the NVIDIA grapic device PCI:2:0:0
Screen(s) found but none have usable configuration And it says to please check the system log for additional error.  I can also choose to startup in low-graphics mode, which is what I've been having to do.

The log holds the following EE:

> xf86 Close console KDE SET MODE failed:  Bad file descriptor
This also holds true for VT_Getmode and VT_Getstate

So the NVDIA driver is acting screwy and synaptic won't accept the newest driver.  I had been using 185, and tried to get 190 and 195 to work, to no avail.

Synaptic cannot bring the newest driver up and running.  The following error occurs here:
> E: /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_amd64.deb: subprocess new pre-installation script returned error exit status I followed several guides yesterday and last night to try and find a similar issue, but all solutions have been ending in error.  This morning I attempted to use the PPA from this site:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

I followed the directions on the site to add it to the software sources (no problem) and then go to fetch updates and get the following information:

> sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages            
  404  Not Found
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US
Get:1 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Fetched 1B in 6s (0B/s)                                                        
W: Failed to fetch [http://ppa.launchpad.net/nvidida-vdpau/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/nvidida-vdpau/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Now I can walk through that site and go to the correct file, because the typed URL is "nvidida" not "nvidia", but I don't know what to do from there.  So:

1.  Why in the world would my video driver be failing?  Things were running smoothly until yesterday's update?  What do I need to do to fix this?
2.  If the PPA is a possible solution, what do I need to do with the Packages.gz from the launchpad site?

I'm running a quad core AMD 64 Phenom 9850 with 6 gigs of RAM, with Karmic AMD64 (Kernel 2.6.31-20-generic, GNOME 2.28.21).  Please help!

---

### Post by josemuniznyc on 2010-03-23
* BUMP *

I myself am having a similar problem, though it only started today. I ran update manager and on restart the NVIDA module would not load.

Here are the relevant lines (I think) from the kernel log:

Mar 23 21:39:40 Husserl kernel: [   15.012926] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 21 (level, low) -> IRQ 21
Mar 23 21:39:40 Husserl kernel: [   15.012935] nvidia: probe of 0000:00:03.5 failed with error -1
Mar 23 21:39:40 Husserl kernel: [   15.013219] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 20
Mar 23 21:39:40 Husserl kernel: [   15.013221] nvidia 0000:03:00.0: PCI INT A -> Link[LGPU] -> GSI 20 (level, low) -> IRQ 20
Mar 23 21:39:40 Husserl kernel: [   15.013226] nvidia 0000:03:00.0: setting latency timer to 64

---

### Post by davidpbrown on 2010-04-04
I think I have the same problem but I understand it even less.

I wondered it was the graphics card packing in but now hope it can be just a driver issue. It's only affecting the high resolution - everything continues as low resolution ok, except for a couple of odd occasions, when it's cut out back to the login screen.

The graphics screws up very early into the boot though, immediately after the Dell splash, before substantial software is loaded.. the grub prompt even is corrupted. If this is different problem let me know but the errors look the same.

Out of ideas, I photographed the errors to catch them. I've not spent time reading the logs it offers, as I'm hoping it's a known issue with a simple solution.

Rather odd is that booting with another Ubuntu version from disk the problem remains and affects the graphics for the initial startup of that. Messed up by vertical lines of different colour - 3rd element of the pic below

[IMG]http://www.davidpbrown.co.uk/offsite/1.jpg[/IMG]

---

### Post by davidpbrown on 2010-04-04
The NVidia X Server Settings suggests "You do not appear to be using the NVIDIA X Driver." It suggests editing the X config file and restarting the X server.

However, running nvidia-xconfig as root throws me out back to the login screen. So maybe that's where the issue is found??

---

### Post by davidpbrown on 2010-04-04
Ok - it's fixed for me but I don't know how! If it was running nvidia-xconfig as root throwing me back to the login screen, then it's not obvious that was an intended correction.

Here's hoping it's just that and not a temperamental hardware problem.

---

