---
title: "Media change request during Ubuntu installation"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by martin.klvana on 2007-08-22
Hello,

I have Fujitsu-Siemens AmiloPro V2030 notebook with VIA P4M800Pro motherboard and VIA/S3G Unichrome Pro IGP.

I tried to install Fedora 7 (which I am using on my desktop PC) but failed to set higher than making-me-dizzy 800x600 screen resolution. So I decided to try Ubuntu but I encounter troubles to install the system (ubuntu-7.04-alternate) though I was able to boot live-cd.

During installation of Ubuntu, after about 85 percent is completed, the following notification appears on the screen:

Media change: please insert the disc labeled 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)' in the drive '/cdrom/' and press enter

I do not understand why it request anything. I verified the installation disc by MD5sum and it is OK. Besides I cannot eject CD drive. I googled the message and found that it sometimes happen as post-installation problem and can be easily solved by editing /etc/apt/sources.lst but what about if that problem occurs already during the installation process which is my case.

Any suggestions?
thanks,
martin

---

### Post by martin.klvana on 2007-08-22
...to correct my report - the media change request occurs during "Select and install software" part of the installation. When the message appears I do not know any way to abort the installation so I simply wait for the battery getting empty. Is there another way to abort the installation at that point?

What kind of software is being installed around 85percent of completition? Is the software installation somehow optional - I did not see an option to select which software to install and which not. Perhaps if it is possible to get ubuntu running in a minimum mode then I can install rest of the software afterwards(?)

---

### Post by merlinus on 2007-08-22
Are you connected to the Internet during installation?  If not, it may be looking for the software on a cd.

IIRC, the text-mode Alternate cd has an option for a basic command line installation, and afterwards you can get whatever software you are wanting.

-merlin

---

