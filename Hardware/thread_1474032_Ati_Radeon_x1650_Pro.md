---
title: "Ati Radeon x1650 Pro"
date: 2010-05-05
forum: Hardware
---

### Post by Angelic on 2010-05-05
Hi all,

As the title suggests, I have an Ati Radeon x1650 Pro. Ubuntu picks up the card just fine, only problem is no 3D acceleration, so no fancy effects :( (And just a slow computer in general, even without effects).

Anyone got any idea how to get this thing working? I've tried several things (a lot of the Ati/Radeon related packages in the software manager) and nothing works. Ati CCP won't recognise the card. Also tried installing the driver from the Ati site, simply won't install.

What should I do?

---

### Post by jrichter on 2010-05-15
I have the same card and problem.  Any luck?

---

### Post by Confused Computer User on 2010-05-16
Same problem on my ATI Radeon X1600.

I tried this:
> **Chrisco66 said:**
> Try this, it worked for me.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

The effects still don't work BUT the slowness is gone. so one step in the right direction

---

### Post by sandu.lulu on 2010-06-21
i have the same issue with the same hardware..

isn't there some sort of a fix?

---

### Post by Mark Phelps on 2010-06-21
Basically -- NO.  That hardware was relegated to "legacy" status over a year ago by AMD/ATI such that there are no fglrx drivers that will work with it anymore.

The only drivers that will work are the open source drivers.

If you want details on tweaking, though, you should go to the Phoronix forums.  They do a LOT of work with the open source drivers.

---

### Post by Yellow Pasque on 2010-06-21
Make sure you remove any failed install attempts of the proprietary driver and reinstall the appropriate packages: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by calinorg on 2010-07-21
Try this:
1. open terminal
2. type this (enter your password when asked):
```
sudo echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```
3. reboot, and enjoy

(taken from [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by chaale on 2010-07-27
> **calinorg said:**
> Try this:
1. open terminal
2. type this (enter your password when asked):
```
sudo echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```3. reboot, and enjoy

(taken from [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Here's what the console return :

```
bash: /etc/modprobe.d/radeon-kms.conf: Permission denied
```(didn't even asked for admin password).

So I believed the file access is restricted, but :

```
bash: /etc/modprobe.d/radeon-kms.conf: Permission denied
sudo ls -l /etc/modprobe.d/radeon-kms.conf
[sudo] password for :
ls: cannot access /etc/modprobe.d/radeon-kms.conf: No such file or directory
```I'm actually running with display drivers for radeon from fglrx package from package manager udated to current version. Still glitchy. I guess the RV535 isn't supported.

I also tried what's writen after on the Wiki for KMS.

I noticed I had no xorg.conf file. I created it like on the wiki, but for Radeon. I also edited the Grub.

No changes. Well it crashed video card display on restart, I had to fix it with the BootCD Restore utility.

FYI, I'm actually running Ubuntu Studio (Lucid) with Linux 2.6.32 and Gnome 2.30.2.

I also have ATI (Sapphire) Radeon x1650 pro (RV535).

I'm new on Linux, but nifty, and can't find a way to fix it.

---

### Post by InsaneNoob on 2010-11-12
I did a fresh install of 10.10 x64 and i had the nice fancy graphics and compiz working fine.. 

But for some reason, if you put this card into a system with ubuntu already installed prior to having the card, it will be detected but wont enable the fancy graphics

---

