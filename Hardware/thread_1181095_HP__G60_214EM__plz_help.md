---
title: ":: HP  G60 214EM :: plz help ::"
date: 2009-06-07
forum: Hardware
---

### Post by riQeh on 2009-06-07
Hey forum..

I just bought a new laptop Hewlett Packard G60 214EM. Comes with Vista.

Now i never used linux before, but have an interest to get away from microsoft, so would love to use ubuntu.

So far so good..

A download and install went well.. EASY infact.. now i have a perfect dual boot laptop. Exactly what i want.. now the tricky bit.

Everything seems to be working in ubuntu, sound, graphics etc..

Everything except my wireless adapter. Now this is a built in wireless adapter, and i have no idea how to get the name of it (to download the driver)

Anyone know...
(a) the name of my built in wireless adapter?
(b) already have the driver which they can supply me?
(c) tell me it won't ever work and i need to buy an external wireless adapter (if so, which one do they recommend that will fit into the limited slots on my laptop, and that is compliant with ubuntu)

Thanks in advance techhies...

---

### Post by avilella on 2009-06-07
Can you open a terminal and do an:

lspci

Do you find a line with the word "Atheros"?

Here is an installation report for this laptop:
[https://wiki.ubuntu.com/LaptopTestingTeam/G60-125NR](https://wiki.ubuntu.com/LaptopTestingTeam/G60-125NR)

> **riQeh said:**
> Hey forum..

I just bought a new laptop Hewlett Packard G60 214EM. Comes with Vista.

Now i never used linux before, but have an interest to get away from microsoft, so would love to use ubuntu.

So far so good..

A download and install went well.. EASY infact.. now i have a perfect dual boot laptop. Exactly what i want.. now the tricky bit.

Everything seems to be working in ubuntu, sound, graphics etc..

Everything except my wireless adapter. Now this is a built in wireless adapter, and i have no idea how to get the name of it (to download the driver)

Anyone know...
(a) the name of my built in wireless adapter?
(b) already have the driver which they can supply me?
(c) tell me it won't ever work and i need to buy an external wireless adapter (if so, which one do they recommend that will fit into the limited slots on my laptop, and that is compliant with ubuntu)

Thanks in advance techhies...

---

### Post by overdrank on 2009-06-08
Hi and welcome, to add to avilella I have a G-60 and you can activate the driver located under system, administration, hardware drivers.

---

### Post by riQeh on 2009-06-08
[FONT=Verdana][SIZE=3]ok.. strange happenings..

The wireless card works!! kinda worked on its own. This increases my faith in ubuntu. except the computer is running very VERY slowly. inside firefox the refresh rate is awful. When i scroll down in a browser the page refreshes on line at a time, very slowly.. is this a problem with my video card driver??
[/SIZE][/FONT]

---

### Post by overdrank on 2009-06-08
> **riQeh said:**
> [FONT=Verdana][SIZE=3]ok.. strange happenings..

The wireless card works!! kinda worked on its own. This increases my faith in ubuntu. except the computer is running very VERY slowly. inside firefox the refresh rate is awful. When i scroll down in a browser the page refreshes on line at a time, very slowly.. is this a problem with my video card driver??
[/SIZE][/FONT]

You will need to install the graphics drivers from the same location I mentioned earlier. System, administration, hardware drivers.

---

### Post by riQeh on 2009-06-08
ok..

i go System>Administration>HardwareDrivers. i get a pop-up telling me that propriety drivers are being used to make this system work.

Alternate Atheros madwifi is currently in use. Whether i use this or not my wireless card does not work anymore, and there is no options for video display. Please help..

---

### Post by overdrank on 2009-06-08
> **riQeh said:**
> ok..

i go System>Administration>HardwareDrivers. i get a pop-up telling me that propriety drivers are being used to make this system work.

Alternate Atheros madwifi is currently in use. Whether i use this or not my wireless card does not work anymore, and there is no options for video display. Please help..

Ok can you post the output of the command lspci in the terminal located under applications, accessories, terminal. You can copy and paste.
And which version of Ubuntu are you using? This can be found under system, about Ubuntu.

---

### Post by riQeh on 2009-06-08
Ubuntu 9.04 - the Jaunty Jackalope - released in April 2009.


riqeh@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
riqeh@ubuntu:~$ 


thanks for this..

---

### Post by overdrank on 2009-06-08
Ok you have almost the exact same setup as mine. If you will try and update your system in the terminal.
You can use the command ```
sudo apt-get update && sudo apt-get upgrade
```
Then you should be given the drivers located under system, administration, hardware drivers. 
If you wish you may manually install the nvidia drivers but lets try the first option. :)
Edit you may have to disable the wireless drivers and enable them again after reboot.

---

### Post by riQeh on 2009-06-08
riqeh@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for riqeh: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_GB          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_GB                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_GB              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_GB                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources                
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg                         
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_GB              
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_GB          
  Unable to connect to packages.freecontrib.org http:
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources              
Reading package lists... Done
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
riqeh@ubuntu:~$ 

should i try again??? :$

---

### Post by overdrank on 2009-06-08
If you are using Jaunty 9.04 then why are the Dapper repos showing?
Did you upgrade from Dapper 6.06?
Could you please post the output of the command ```
cat /etc/apt/sources.list

```

---

### Post by yaroto98 on 2009-06-08
What I had to do is go to
system->software sources
select all the sources available throughout the tabs (third party included). there's a place (i don't remember where) where you can change your repo server. run a "select best server" to find the one with the fastest ping. pick that server and run

```
sudo apt-get update && sudo apt-get upgrade
```

but cat that sources.list too.

---

### Post by riQeh on 2009-06-08
riqeh@ubuntu:~$ cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
riqeh@ubuntu:~$ 

??? illegal packages ???

---

### Post by overdrank on 2009-06-08
Is that the whole content of the output?
You would not be running Jaunty 9.04 then. 
This maybe why you do not see the hardware drivers located under administration.
Under system, about Ubuntu what release are you using?

---

### Post by riQeh on 2009-06-08
nope i'm definately using Jaunty 9.04. infact the first time i told u that was a copy and paste from System>About ubuntu

should i reinstall? or do u have a copy of source.list

please help..

---

### Post by overdrank on 2009-06-08
> **riQeh said:**
> nope i'm definately using Jaunty 9.04. infact the first time i told u that was a copy and paste from System>About ubuntu

should i reinstall? or do u have a copy of source.list

please help..

If you like you may use a copy of my sources list
Edit before you try please check one more command  ```
lsb_release -a
```

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```
You will need to edit your sources list with this command ```
gksu gedit /etc/apt/sources.list
```
And replace your list with the copy I posted. The save the file. Then use the update command earlier given. I hope this helps as it time for me to retire to sleep. I will hang around as long as I can.

---

### Post by davidaspey on 2009-06-19
i have a g60 214em all i had to do was update the system, then activate the nvidia 180 driver and reboot. thats all.! 

no need to use the madwifi etc . all hardware works perfectly, webcam etc.

ive tried both flavours of ubuntu x86 and x86_64 with no issues.

\\:D/

---

### Post by overdrank on 2009-06-19
> **davidaspey said:**
> i have a g60 214em all i had to do was update the system, then activate the nvidia 180 driver and reboot. thats all.! 

no need to use the madwifi etc . all hardware works perfectly, webcam etc.

ive tried both flavours of ubuntu x86 and x86_64 with no issues.

\\:D/

Welcome, and great everything works for you. But as you can see riQeh has some issues with the sources list. :)

---

### Post by riQeh on 2009-06-21
Ok..

First things first.. Thank you to both repliers. Your effort has been gratefully recieved.

i'm currently updating UBUNTU as per instructions.. could someone please elaborate on the 
then activate the nvidia 180 driver

instruction.

cheers..

---

