---
title: "hELP ME OUT PLEASE"
date: 2008-06-17
forum: Hardware
---

### Post by aviborse on 2008-06-17
Hi ALl,

First of all.......i m absolutely new to linux...and ubuntu in specific..
was fed up with vista...:( hence decided to change to linux....while surfing i got yo know ubuntu is good..hence installed it on my latop...and im very happy with it...wireless working,my nvidia working ...good looks and compatibility minus...virus as in microsoft os.....now problem lies in my experimentive attitude...while reading a forum...i got something i tried it out ..now i m not able to update my laptop with the update manager.....given below are the details ...plz help me out,...thx in advance..

forum thread folllowed
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

LAPTOP

cOMPAQ PRESARIO 6608AU
AMD TURION X 2
NVIDIA
1GB RAM
160 GB HARD DISK

_**UPDATE MANAGER DESCRIPTION COPY**_

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/Release.gpg](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/Release.gpg)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_IN.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_IN.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_IN.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


**_This is what i had changed.............._**
command given in the terminal was

**_ sudo apt-get update_**
**_ sudo apt-get update_**
_**wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -**_
**_gksu ntfs-config_**
**_gksu ntfs-config_**
_**gksu gedit /etc/apt/sources.list**_



# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all

---

### Post by NikoC on 2008-06-18
What if you do the following in a terminal:

sudo gedit /etc/apt/sources.list

Delete the last 3 lines (flomertens,ntfs)
Save the file, close it and then:

sudo apt-get update
sudo apt-get upgrade

Edit: Perhaps I should elaborate a little bit more on all these commands. Ubuntu uses so called repositories from which you can download and install extra software (call it a free online download service) via Synaptic. The list of servers is stored in the file sources.list. However, there are also non-supported packages for which you have to add the location, i.e. server name, to the sources.list. So the 'sudo  gedit /etc/apt/sources.list' let's you edit this list (sudo means that you do this as a super user, super user do). 'apt-get update' refreshes the package list and retrieves the package names from the server(s) you just added. 'apt-get upgrade' actually installs those packages. Via Synaptic the same things happen but via a GUI.
Well I'm not really an expert myself, but this is how I understand things ;)

---

### Post by aviborse on 2008-06-18
Thanks a million,.......that problem does not exsits anymore..

---

### Post by aviborse on 2008-06-18
Is experimenting with my os ...a good idea...cause i constantly do it!
one more question...what is a kernel?...and how does it effect my working...recently chked out this link [http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html..it](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html..it) shows my kernel is old...what happens if i upgarde it?

---

### Post by NikoC on 2008-06-18
Well again, I'm not really a 'techie',

But as far as I understand the kernel is the central component of the computer system, it makes the link between hardware (cpu, memory, ...) and applications. So as new hardware keeps emerging the kernel needs updating and also further developing.

In ubuntu if a new kernel is released via the repositories, your update manager will ask you to install it for you. I, myself, however choose to manually update my system via the terminal method:
sudo apt-get update
sudo apt-get upgrade

To know your kernel version you can type uname -r in a terminal. Often different distributions (Ubuntu, Suse, etc.) include different kernel releases at different times.

If you like to mess around with your system (which is the best way of learning things imo), make sure you always make backups of your essential documents. That's the way I learned and still am learning things.

Have fun exploring!

Cheers.

---

### Post by aviborse on 2008-06-18
Thanks for the advice......i m eager to learn more....hence i applied it..
now my kernel is 2.6.25.7...with ubuntu 8.04...but my wireless card not working ,....also sound card is not functional all my music is off.feel so boring.can anybody help me? screen resolution has also dropped to 800x600.
how can i enable the desktop effects

---

### Post by master_kernel on 2008-06-18
Your sound is probably due to intel HD audio not enabled in your xconfig.
For your wireless card you might want to do a search in the master kernel thread.
As for your video, just install Envy-NG and install the nVidia driver.

Also, it'd be great if you could try out the new kernelcheck beta (check out the kernelcheck reference in my signature)! Don't forget to uninstall the old one first though.

MK

---

### Post by soccerboy on 2008-06-18
the reason your sound is not working is because 2.6.25 is a development kernel.  It is not completed yet.  The stable releases are even for the last version.  You should normally not try new kernels until you upgrade your os to the latest version.  You can, if you are adventurous, try new development stuff in a virtual environment or on another installation to keep your main working installation safe.  also, ntfs-3g has been stable for a while and ntfs support in ubuntu is next to (if not) flawless now.

---

### Post by aviborse on 2008-06-18
thx for the suggestion.My wlan is working well now. Surfing thru wireless card is now fun.as for sound i m working out A  solution.I was trying to be adventurous..hence installed kernel 2.6.25.7......as for my OS it is ubuntu 8.04.Isnt this the latest version? forgive me of i mm wrong .I m a bit new to this environment. but wanting to learn .....

---

### Post by aviborse on 2008-06-20
I lost my  w mireless connection again....had to format my laptop again.
Somehow the same steps(as in [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)) are working out for me .........i tried thrice the same procedure. Doesnt seem to work. Here's what i get

Laptop
Compaq Presario 6608AU
AMD Turion
1GB ram
160 GB hard disk.

avi@avi-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1b:24:86:db:c0
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network DISABLED
description: Wireless interface
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan1
version: 02
serial: 00:1a:73:92:4a:15
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



avi@avi-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1b:24:86:db:c0
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network DISABLED
description: Wireless interface
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan1
version: 02
serial: 00:1a:73:92:4a:15
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

avi@avi-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Please guide me!!!!!!!!
Thanks in advance.

---

### Post by aviborse on 2008-07-05
I have installed Kopete.......but there seems to be a problem where ever somebody pings me i get a chat window............wen i accept that chat window my laptop restarts........can u please explain why is this happening!!!!!!!!

---

