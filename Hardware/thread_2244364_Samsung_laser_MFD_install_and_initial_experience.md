---
title: "Samsung laser MFD install and initial experience"
date: 2014-09-15
forum: Hardware
---

### Post by kurt18947 on 2014-09-15
Note to mods: If you wish to move this to a more appropriate formum, please do.

In the spirit of letting the community know about Linux friendly  hardware, this is a review of Samsung's SL-M2870FW. This model is being being superceded by a newer model so bargains can be found in the U.S. I got mine from neweggbusiness.com for $89.99. I'm not going to go discuss specs, those can be found easily.

Samsung makes available a universal installer which includes bash scripts to install & uninstall and also the binaries. There is no source code available to my knowledge. The installer is very much like Brother's installer. The difference is that Brother downloads the driver from their website, Samsung bundles the driver with the installer. I did find that if I downloaded the software onto the target machine, execute flags were properly set.  If I copied to a flash drive then onto another machine, I had to set the execute flags on the install*.sh and uninstall*.sh files. The install only takes a few seconds for both printer and scanner. I opened a terminal, navigated to the folder containing the extracted Samsung files and typed 

```
sudo bash install.sh. 
```

I had to press 'enter' several times to read through and agree to the lengthy license. It's easy to press 'enter' one too many times and abort the process.

The first install was using a plain jane fresh install of Ubuntu Gnome 64 bit. It worked perfectly, printer and scanner were both recognized and duplex printing was pretty easy to implement. Ubuntu Gnome bundles system-config-printer which I prefer to choose the connection type, enter the I.P. address etc. I did not try connecting via wireless directly to the printer. The only connection is wired ethernet. I set a static I.P. and turned off the printer's wireless which is on by default. I print wirelessly via a wireless router which has been reliable. This machine includes a web server and I think its security is better than the older Brother MFC-7820 it replaced. There is a means to limit the number of tries to log onto the machine after which anyone has to wait a few minutes before trying again. These numbers can be set.

The only problem I've found so far is with trying to scan from a machine that already has Brother scanner driver installed. I have two installs that have/had Brother drivers installed and two installs that did not have any scanner drivers installed.  One is the fresh Ubuntu Gnome 14.04  install and one that has been running 14.04 since before 14.04 was released. I was not able to get xsane, simple scan or gscan2pdf to see the Samsung scanner if the Brother scanner driver was present. The two installs that didn't have a prior scanner installed recognized the Samsung scanner and worked. I have licensed vuescan which did see the Samsung scanner on all machines. I tried sane-find-scanner but that seems to look only for USB or parallel port machines. It didn't find the Samsung scanner. I'm sure it would be possible to be able to scan using SANE on the partitions with Brother software but I haven't taken the time and don't have the need.

The executive summary is that IMO Samsung multifunction machines are viable choices for Ubuntu and its close relatives. I hope you find this useful and will try to answer any questions.

---

