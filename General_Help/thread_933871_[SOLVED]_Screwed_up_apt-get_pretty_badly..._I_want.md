---
title: "[SOLVED] Screwed up apt-get pretty badly... I want to try to install KDE, but it was"
date: 2008-09-29
forum: General Help
---

### Post by Predator106 on 2008-09-29
weird.

Hey, today I did something stupid (another on the seemingly-endless list :) ). Well after installing KDE on my Xubuntu laptop, I was pleased, I did an apt-get install kde and then booted into kde, all was well, but I realized I had forgotten something in gnome, so when the wizard (which I loved) was up, I went to the virtual terminal and typed in killall -u shaun this way I was hoping the wizard wouldn't save itself as being skipped or anything. So I went back into KDE after doing some stuff, and the wizard isn't there, and it booted into KDE normally.

I don't know how to do anything without that wizard, I'm completely KDE-stupid, being a previous GNOME user...

So I thought removing KDE (completely) would work... nope. I then tried to remove everything KDE related(this is where it all goes downhill). Upon applying and reinstalling KDE, it STILL doesn't show the damn wizard and it remembered everything. I then go into the SpM and try to install kde-4, and then I get an error saying there is a broken dependency, etc. Well, since I removed about 60-80 packages, depending on each other, this causes quite a problem... As I go to install one, it wants to install it's dependency, and it will keep going forever. I was wondering if there was a way to automate this process or something, I wanted it to kind of chain-load down the line.

Well, how can I fix it, and how can I install KDE, what's the best way, I just found out I probably should've done apt-get install kubuntu-desktop......so what about my laptop, just installing the 'kde' package, will that be fine? Should I install the *untu package?

I'm really confused, what is especially misleading, is the laptop runs KDE 3.5, but when I installed this on my computer, the background was different (prolly because of the lack of the wizard). 

I really want KDE, but why is it so confusing, they have the 'kde' package, but they also have like kde-4 , etc. What do I really need?

Also, I have Ubuntu, but with the laptop I had Xubuntu

---

### Post by snova on 2008-09-29
There are two versions of KDE around. There's the venerable KDE 3, and the new KDE 4. KDE 4 is still alpha, and won't come around until Intrepid, so don't use it. I found that out the hard way.

You want the "kde" package, then. The kubuntu-desktop package is a metapackage that just depends on a bunch of other stuff. You don't have to have it, but look into it anyway. It depends on KDE 3 as well. kubuntu-kde4-desktop is similar, but for KDE 4: again, avoid it.

To delete an entire KDE 3 configuration, remove the .kde hidden folder in your home directory.

To rerun the wizard, invoke "kpersonalizer", assuming it's around, which it should be.

---

### Post by cariboo on 2008-09-30
You could also try Synaptic-->Edit-->Fix Broken Packages.

Jim

---

### Post by Predator106 on 2008-09-30
Aw man, instead of reinstalling and all that, I should've just done that :D.

As for the broken packages, it says there are 0 and when I click fix, it just says that it's done right away, like it didn't even do anything.

When I try to install the kubuntu-desktop ('kde' is installed) because I deleted all of the kde applications(every last one), I get this error message.


kubuntu-desktop:
 Depends: kde-guidance but it is not going to be installed
 Recommends: kde-guidance-powermanager but it is not going to be installed


I try to mark what it recommends to install and get this...

kde-guidance-powermanager:
 Depends: kde-guidance but it is not going to be installed


So I try to install kde-guidance

kde-guidance:
 Depends: libpythonize0 but it is not going to be installed


How can I force it to install, heh, as you can see, I really screwed things up.

---

### Post by ukripper on 2008-09-30
> **Predator106 said:**
> Aw man, instead of reinstalling and all that, I should've just done that :D.

As for the broken packages, it says there are 0 and when I click fix, it just says that it's done right away, like it didn't even do anything.

When I try to install the kubuntu-desktop ('kde' is installed) because I deleted all of the kde applications(every last one), I get this error message.


kubuntu-desktop:
 Depends: kde-guidance but it is not going to be installed
 Recommends: kde-guidance-powermanager but it is not going to be installed


I try to mark what it recommends to install and get this...

kde-guidance-powermanager:
 Depends: kde-guidance but it is not going to be installed


So I try to install kde-guidance

kde-guidance:
 Depends: libpythonize0 but it is not going to be installed


How can I force it to install, heh, as you can see, I really screwed things up.

install libpythonize0 first

---

### Post by Predator106 on 2008-09-30
Yeah, same problem

libpythonize0:
 Depends: python-dev but it is not going to be installed


It's like an endless loop, since I unchecked just about everything that was related to KDE....

EDIT: I went through quite a few of these cycles, nothing's going on...

---

### Post by oldos2er on 2008-09-30
Run "kdesu kate /etc/apt/sources.list" in konsole, and check to see if some of your repositories are commented out. Sometimes that's what the error "Depends: [some package] but it is not going to be installed" refers to.

---

### Post by KeyserSoze93 on 2008-09-30
sudo apt-get update
sudo apt-get install -f
sudo apt-get install kubuntu-desktop

?

---

### Post by Predator106 on 2008-09-30
Here's the return:
> 
shaun@Shaun's-Ubuntu:~$ sudo apt-get update
[sudo] password for shaun: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                      
Get:1 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy Release.gpg [189B]                
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Translation-en_US              
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Translation-en_US
Get:2 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates Release.gpg [189B]
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Translation-en_US
Get:3 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security Release.gpg [189B]
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Translation-en_US
Get:4 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed Release.gpg [189B]
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/restricted Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/main Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/universe Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/multiverse Translation-en_US
Get:5 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy Release [65.9kB] 
Get:6 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates Release [58.5kB]
Get:7 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security Release [58.5kB]            
Get:8 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed Release [58.5kB]            
Get:9 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Packages [1178kB]               
Get:10 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Packages [6986B]         
Get:11 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Packages [179kB]         
Get:12 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Sources [1488B]          
Get:13 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Sources [338kB]                
Get:14 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Sources [60.9kB]         
Get:15 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Sources [1323kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Translation-en_US                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release [24.2kB]                        
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:18 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Packages [4293kB]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/universe Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Get:19 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Packages [314kB]       
Get:20 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Packages [6636B] 
Get:21 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Packages [20.1kB]
Get:22 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Sources [908B]   
Get:23 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Sources [90.2kB]       
Get:24 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Sources [2795B]  
Get:25 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Sources [26.4kB]   
Get:26 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Packages [98.4kB]  
Get:27 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Packages [58.7kB]     
Get:28 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Packages [6636B]
Get:29 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Packages [8222B]
Get:30 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Sources [908B]  
Get:31 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Sources [13.7kB]      
Get:32 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Sources [14B]   
Get:33 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Sources [5713B]   
Get:34 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Packages [31.0kB] 
Get:35 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/restricted Packages [7064B]
Get:36 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/main Packages [58.6kB]     
Get:37 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/universe Packages [33.0kB] 
Get:38 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/multiverse Packages [13.0kB]
Get:39 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/restricted Sources [905B]  
Get:40 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/main Sources [13.5kB]      
Get:41 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/universe Sources [7983B]   
Get:42 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-proposed/multiverse Sources [2288B] 
Fetched 8444kB in 34s (242kB/s)                                                
Reading package lists... Done
shaun@Shaun's-Ubuntu:~$ sudo su
root@Shaun's-Ubuntu:/home/shaun# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 python-zopeinterface python-twisted-core libqca2
  libqimageblitz4 scorched3d-data adanaxisgpl-data libglade2-ruby1.8 libgcj-bc
  libgconf2-ruby librdf0 libmono-sqlite1.0-cil libwxgtk2.6-0 libqt4-qt3support
  kdevelop-data libatk1-ruby1.8 glest-data libflac++6 btanks-data python-pyogg
  libxalan110 libglade2-ruby falconseye-data libaccess-bridge-java libexiv2-2
  librasqal0 libpng12-dev python-pyvorbis ruby1.8 libsoprano4 python-editobj
  python-qt3 libvirt0 ruby libfltk1.1 libxen3 libept0 python-bittorrent
  libwxbase2.6-0 ksysguardd-kde4 libcaptury0 python-cerealizer
  libgconf2-ruby1.8 libxul0d libboost-iostreams1.34.1 libxapian15
  sauerbraten-data libglib2-ruby1.8 libqt4-sql libifp4 libcal3d12 debtags
  fping libcairo-ruby1.8 python-tofu libphonon4 libvte0.16-cil libzip1
  libgdk-pixbuf2-ruby1.8 libmozjs0d libconfuse0 fastjar liblua5.1-0
  libkonq5-templates moon-lander-data libgtk2-ruby1.8 libcapseo0
  libqca2-plugin-ossl libraptor1 xaw3dg libxul-common libruby1.8
  libode0debian1 starfighter-data python-reportlab libxerces27
  python-twisted-bin libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Shaun's-Ubuntu:/home/shaun# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kde-guidance but it is not going to be installed
                   Recommends: kde-guidance-powermanager but it is not going to be installed
E: Broken packages
root@Shaun's-Ubuntu:/home/shaun# 


---

### Post by Predator106 on 2008-09-30
As for the source.list file, the problem is... I have added a bunch of things and subsequently commented them out before, so I'm not sure at all what I should be looking for....

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy main restricted multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates universe

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
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security main restricted multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-proposed restricted main universe multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-proposed restricted main universe multiverse #Added by software-properties
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
## Automatix repo
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://parker1.co.uk/apt](http://parker1.co.uk/apt) feisty main
# deb-src [http://parker1.co.uk/apt](http://parker1.co.uk/apt) feisty main
# deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev
# deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ppa.launchpad.net/christer.edwards/ubuntu](http://ppa.launchpad.net/christer.edwards/ubuntu) hardy main

---

### Post by oldos2er on 2008-09-30
If you're running Hardy, you should comment out references to Feisty or other Ubuntu releases. See [http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/](http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/) for a generic Hardy sources.list.

---

### Post by Predator106 on 2008-09-30
Has no effect, same problem, reloaded the package list also.

---

### Post by ukripper on 2008-10-01
Not sure if you have already tried this -

```
sudo apt-get -f install
```

---

### Post by Predator106 on 2008-10-01
Yes, already did, it doesn't do anything, it just says there were 0 upgraded, repaired, etc. Zero for everything. It's almost like it doesn't know that there are broken packages, because synaptic's "fix broken package" button just says it's done in less than a second, not fixing anything or saying anything but that.

EDIT: You know what, I will just do a clean install of Kubuntu, it will be better anyways, since I modified ubuntu so much (poor thing).

---

### Post by ukripper on 2008-10-02
> **Predator106 said:**
> Yes, already did, it doesn't do anything, it just says there were 0 upgraded, repaired, etc. Zero for everything. It's almost like it doesn't know that there are broken packages, because synaptic's "fix broken package" button just says it's done in less than a second, not fixing anything or saying anything but that.

EDIT: You know what, I will just do a clean install of Kubuntu, it will be better anyways, since I modified ubuntu so much (poor thing).

Take backup first of your important data. If you have /home separate that is even better.

---

