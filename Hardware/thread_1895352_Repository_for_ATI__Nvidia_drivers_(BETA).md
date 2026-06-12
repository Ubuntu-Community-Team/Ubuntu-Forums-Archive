---
title: "Repository for ATI / Nvidia drivers (BETA) ?"
date: 2011-12-14
forum: Hardware
---

### Post by Dlambert on 2011-12-14
This doesn't really pertain to gaming in theory. But it's motivation does.

I would like to know if there is a repository for Ubuntu that had the latest beta builds of the Catalyst or Nvidia drivers? Sure ubuntu has jockey, but those drivers are "old" and don't offer the same performance as the more recent ones. I have a Radeon HD 6950 and would like the most performance for gaming. So is there a repository available with the latest drivers built for Ubuntu? I ask because manually install the drivers (Nvidia) have become a pain with unity and Gnome3. Thank you!


P.S Would it be that hard to set one up? If it doesn't exist.

---

### Post by bluexrider on 2011-12-14
> **Dlambert said:**
> This doesn't really pertain to gaming in theory. But it's motivation does.

I would like to know if there is a repository for Ubuntu that had the latest beta builds of the Catalyst or Nvidia drivers? Sure ubuntu has jockey, but those drivers are "old" and don't offer the same performance as the more recent ones. I have a Radeon HD 6950 and would like the most performance for gaming. So is there a repository available with the latest drivers built for Ubuntu? I ask because manually install the drivers (Nvidia) have become a pain with unity and Gnome3. Thank you!


P.S Would it be that hard to set one up? If it doesn't exist.

I don't think you will find proprietary drivers in PPA

---

### Post by WienerWuerstel on 2011-12-14
If you want the newest proprietary Nvidia Drivers then just add [this]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") PPA to your System. 
The newest AMD/ATI Drivers are in the Ubuntu "proposed" Repos as there didn't seem to be a stable PPA that provides the (newest) fglrx Drivers.

---

### Post by Dlambert on 2011-12-14
> **WienerWuerstel said:**
> If you want the newest proprietary Nvidia Drivers then just add [this]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") PPA to your System. 
The newest AMD/ATI Drivers are in the Ubuntu "proposed" Repos as there didn't seem to be a stable PPA that provides the (newest) fglrx Drivers.

And where might that repo be found? :) Thank you! And I know it couldn't be found in an official repo, I was just curious.

---

### Post by bluexrider on 2011-12-14
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) YOUR_UBUNTU_VERSION_HERE main  

deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) YOUR_UBUNTU_VERSION_HERE main



[FONT=monospace]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates[/FONT] 

[FONT=monospace]sudo apt-get update[/FONT] [FONT=monospace]

sudo apt-get install fglrx[/FONT]

---

### Post by Dlambert on 2011-12-14
> **WienerWuerstel said:**
> If you want the newest proprietary Nvidia Drivers then just add [this]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") PPA to your System. 
The newest AMD/ATI Drivers are in the Ubuntu "proposed" Repos as there didn't seem to be a stable PPA that provides the (newest) fglrx Drivers.

I Love that PPA you gave me! My hat to those guys!

---

### Post by Dlambert on 2011-12-14
> **bluexrider said:**
> deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) YOUR_UBUNTU_VERSION_HERE main  

deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) YOUR_UBUNTU_VERSION_HERE main



[FONT=monospace]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates[/FONT] 

[FONT=monospace]sudo apt-get update[/FONT] [FONT=monospace]

sudo apt-get install fglrx[/FONT]

Thank you again!

---

### Post by linuxman94 on 2011-12-14
Currently the fglrx driver in the ubuntu-x ppa is not the newest driver available.  So that ppa won't do much good.  

The easiest way to install the proprietary drivers, if you want the latest ones, is to build the packages using the amd installer.

```
sudo sh ./filename_here.run --buildpkg
sudo apt-get purge fglrx*
sudo dpkg -i *.deb
```

---

### Post by bluexrider on 2011-12-14
well, there ya go. with everything said and done you are on you way.

please mark this 

(SOLVED)

---

### Post by Dlambert on 2011-12-15
> **linuxman94 said:**
> Currently the fglrx driver in the ubuntu-x ppa is not the newest driver available.  So that ppa won't do much good.  

The easiest way to install the proprietary drivers, if you want the latest ones, is to build the packages using the amd installer.

```
sudo sh ./filename_here.run --buildpkg
sudo apt-get purge fglrx*
sudo dpkg -i *.deb
```


Thank you!!!! :KS :KS :KS :KS :KS

---

### Post by bluexrider on 2011-12-15
we do what we do when we can do it

---

