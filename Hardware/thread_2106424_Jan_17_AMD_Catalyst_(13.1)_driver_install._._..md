---
title: "Jan 17 AMD Catalyst (13.1) driver install. . ."
date: 2013-01-19
forum: Hardware
---

### Post by blortuga on 2013-01-19
Since I updated my 12.04 (x64) Ubuntu to 12.10, I ran into the problem where the Catalyst driver doesn't work.
(my ATI card is a Radeon 7700 HD).

The way I got it back and running after my 12.10 upgrade was kind of sketchy - but my options were limited, as my access to a gui (and ability to browse the web and look up answers to questions) was limited. So this is the solution I used, in a nutshell:

*********************************************
sudo apt-get purge fglrx*
sudo add-apt-repository ppa:andrikos/ppa
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get --reinstall install xserver-xorg-video-intel
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates
sudo aticonfig --initial -f
*******************************************

I wasn't willing to risk the 12.11 install, since I had a method that worked, even if it was from the andrikos ppa.

When AMD announced the 1/17 driver (version 13.1) - I was *hoping* it would work with 12.10. IN FACT - since they have a Quetzel wiki page, I think it should be safe to assume, right?
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)

Well: WRONG.

The prep commands apt-get install for cdbs and dh-make result in "no package found for installation" so the installer package can't be built when you run their installer.  The result is a borked system that boots to the terminal. You've got to reinstall ubuntu-desktop (sudo apt-get install ubuntu-desktop) and then the above commands, to get back into running-order.

I don't understand why this has to be so hard; why they can write a driver, but not an installer package.  I don't understand, in particular, why Dell can ship hardware with Ubuntu preinstalled, that packs AMD GPUs, but not contribute to an installer that doesn't soil it's own undergarments. (let alone chipset utilities that can manage to not lose the trackpad during heavy transfers to a USB thumbdrive - but I digress).

---

### Post by bishop9226 on 2013-01-20
This! I just borked my new ubuntu installation because of this new driver.  Thanks for posting how to fix it.

---

### Post by blortuga on 2013-01-22
Y/W. . .

Somehow, I ended up borking my repositories, and couldn't download cdbs (*OR* even run Software Sources) , , , no actionable error messages, Synaptic couldn't even find anything to fix.

So I completely re-installed 12.10 from scratch.

First thing I did was try to re-install the 13.1 driver.

I *STILL* can not get that to work, nor can I add the PPA I listed in the above fix, anymore.
(so . . .  good luck with that, sorry guys).

At least the failure mode now, is that my integrated graphics is being used instead of the ATI card.  

I will probably revert back to 12.04.

---

### Post by blortuga on 2013-01-22
I do not know if I get to mark this as "solved":  


1. I was able to add that ppa, I don't know what the problem was before - it might have been that I set Software Sources to point at a bad server?   In any case - the complete 12.10 reinstall was necessary for ME, because I think I ran into the bug with WINE that caused my sources to become unusable.  I couldn't install the prerequisites. The reinstall did fix this.    

2. I also installed &quot;mesa-utils&quot; and &quot;compizconfig-settings-manager&quot;; and I think that NOT having these installed, may have been the reason why previous installs actually *worked* - - but in my Settings->Details screen, the &quot;Graphics&quot; said &quot;Unkown&quot; even though &quot;fglrxinfo&quot; reported that the driver was installed.  I previously believed that an &quot;Unknown&quot; in that field, meant that the Intel Graphics were being used, because the ATI graphics had failed, and the system had fallen-back. But in THIS case, fglrxinfo was reporting the AMD HD 7700M, even when Settings was saying &quot;Unknown&quot; - so I can't really explain that other than as a bug in the Settings info strings.     

3. I think that I may have built the package FIRST, before I had lib32gcc1 installed, and possibly, reinstalls over that got borked, until I used the --force-overwrite option (below).    

Maybe - maybe not. 
 I think I would have gotten many other errors, if this was the case. 

I RE-TRIED the installation, using the instructions at the LINK in my first post (The ATI Linux Wiki:   [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)).  

Using THIS COMMAND: ```
 sudo dpkg -i --force-overwrite fglrx*.deb 
``` 

I rebooted, and was able to get it to &quot;work&quot;!  

So  - - in summary: (For 12.10 (quantal) (x64) - for MY hardware: Dell Inspiron 7520 with AMD HD 7700M) 
1. Reinstall 12.10 from scratch. 
2. Install mesa-utils and compizconfig-settings-manager. 
3. follow the instructions on that wiki page (including using --force-overwrite).  

This should install the 13.1 catalyst driver successfully.

---

### Post by nortexoid on 2013-01-23
Just dropping in to say that these instructions for installing Catalyst 13.1 worked for me. The only issue I had was that when connected via HDMI, only 1080p would not fill the screen. There is an underscan/overscan slider somewhere in the Catalyst control centre that allows sliding it all the way to the right to have it fill the screen.

Question: How to remove the watermark?

---

### Post by vananematu on 2013-02-20
What worked for me to remove the watermark from 13.1 AMD Catalyst drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Unsupported_Hardware_Watermark](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Unsupported_Hardware_Watermark)

I'm using Ubuntu Studio 12.10 with linux 3.8.0 kernel with AMD Catalyst 13.1 drivers which i installed after instructions found here:
[http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

Though like many i had to replace [B]"fglrx-installer" with "fglrx".

[/B]
After the 13.1 driver install all the Steam for linux games seem to work fine. That's why i updated the original propriatery driver.

I accidentally installed AMD drivers to original 3.5 kernel but i still was able to update the kernel afterwards and remove the watermark.

---

