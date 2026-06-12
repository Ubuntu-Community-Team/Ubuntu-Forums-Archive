---
title: "HOW TO FIX BCM 4313 chipset &amp; 4312 chipset ubuntu 10.10  kernel 2.6.35-24 and prior!!"
date: 2010-12-27
forum: Hardware
---

### Post by soad6 on 2010-12-27
FIXED!! FIXES ISSUES WITH BCM 4313 & 4312 if you run Ubuntu 10.10 and are on 2.6.35-24 gen

if you updated to kernel 2.6.35.-24 gen
please revert to any version prior to this...
then uninstall the bcmwl-kernel-source package
and install the b43-fwcutter package
and install the firmware-b43-lpphy-installer package
then reboot.
confirmed by 5 ppl this works.

command as follows below

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo reboot
...
if this doesn't work for you please let me know... also if this works
with anything other then these two chipsets please let me know... thanx

---

### Post by PatchesTheCaveman on 2010-12-29
Better not to upgrade to 2.6.35-24 till they fix it.  The bcmwl driver works a lot better than the b43 driver for most people.

---

### Post by mrkrinkle2 on 2011-01-03
Hi soad6

I booted up into 2.6.35-22-generic (Ubuntu 11.04) after it didn't work (in the current 2.6.35-24-generic) and tried your instructions.

I got the following when I tried the install line;

sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-lpphy-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  diffstat module-assistant quilt linux-headers-2.6.35-22 debconf-utils linux-headers-2.6.35-22-generic dkms kernel-package
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Seems like it does not like my card?

Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)

System is a HP-Mini-110-310.

Any Clues?

---

### Post by andrek on 2011-01-03
I suggest you to upgrade to natty (although it's still in alpha stage). I'm using 2.6.37-11-generic @ Ubuntu 11.04 Natty Narwhal and the STA Broadcom driver (bcmwl-kernel-source) works without any problem.

---

### Post by mrkrinkle2 on 2011-01-03
Hi andrek

According to SYSTEM > ABOUT UBUNTO, I AM using Natty Narwhal (11.04) but it has kernel 2.6.35-24-generic.

How can I get the kernel 2.6.37-11-generic?

---

### Post by soad6 on 2011-01-04
your not in the right kernel... and this will only fix if your card worked before you upgraded to new kernel if you lost signal... sorry if not, then not sure ill look into it more... sorry been busy with school lately so i dont always check forums everyday

---

### Post by mrkrinkle2 on 2011-01-04
It's a new computer and it's never worked properly yet.

It was on kernel 2.6.35-22 when I first installed and then it updated to 2.6.35-24.

:confused:

---

### Post by soad6 on 2011-01-04
hmm you could try removing what i said and and the bcmwl source ones and install the STA ones... idk if that would work but it should

---

### Post by igortude on 2011-03-01
> **soad6 said:**
> fixed!! Fixes issues with bcm 4313 & 4312 if you run ubuntu 10.10 and are on 2.6.35-24 gen

if you updated to kernel 2.6.35.-24 gen
please revert to any version prior to this...
Then uninstall the bcmwl-kernel-source package
and install the b43-fwcutter package
and install the firmware-b43-lpphy-installer package
then reboot.
Confirmed by 5 ppl this works.

Command as follows below

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo reboot
...
If this doesn't work for you please let me know... Also if this works
with anything other then these two chipsets please let me know... Thanx



thank you buddy!
It works!

---

### Post by JMGesling on 2011-03-04
I tried what's listed in this thread, since I am having similar problems. Up until a few days ago, my wireless card (BCM 4318 ) was working like a charm. Then, it up and quit. I've tried ndiswrapper, all the b43 installers (including lp-phy), and none will install correctly. running lspci shows that the computer can see that my wireless card is there, but it won't recognize it or install new drivers. I am this close to re-installing Ubuntu, but I'd like to try and get it fixed before coming to that. 

I thought maybe it was the update to a higher kernel version, so I installed 2.6.35-22 and took out all the later versions (-27, -25). Still no luck. 

Anything you can suggest would be awesome. If you need more info, just holler and I'll copy and paste what you want as best as I can. I am still a bit of a noob to Linux and Ubuntu, but I learn quick.

---

### Post by ikm on 2011-09-07
Hello I do not speak English very well .. I will thank you if you do not write abbreviations ... going to the problem .. I also have a BCM4313 wireless card, but I can not receive traffic when I use kismet package ASAS ... use ubuntu 11.04
 Kernel: 6.2.38-8-generic

 I also tried to activate the monitor mode with airmon-ng (mon0)
 kismet output:
 NOTICE: Disabling channel hopping, no enabled sources are Able to change channel.
 Source 0 (WIFI): Enabling monitor mode for interface mon0 b43 source channel 6 ...
 FATAL: Failed to Set Channel 6 16: Device or resource busy
 Done.

 running kismet with wlan0, run properly, but does not appear any network.

 thank you very much, and please excuse the grammatical errors

---

### Post by www.rzr.online.fr on 2011-10-18
Have you tested this device along kernel's b43 opensource driver ? 

It looks it's unsupported for now ... but said there are pple on it 

[http://rzr.online.fr/q/broadcom](http://rzr.online.fr/q/broadcom)

---

### Post by vishal1121 on 2013-04-27
this is wat i got

sudo apt-get remove bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 cryptsetup
  libecryptfs0 reiserfsprogs rdate bogl-bterm ecryptfs-utils libdebconfclient0
  dmraid
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,589kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 282150 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.6
root@bt:~/Desktop# sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-lpphy-installer

---

