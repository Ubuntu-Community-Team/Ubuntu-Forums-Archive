---
title: "First Time Using NDISWRAPPER for Broadcom 1350"
date: 2008-12-07
forum: Hardware
---

### Post by PressureWave on 2008-12-07
its been a long day, ive had to load windows xp and Ubuntu 8.10 on my Dell Inspiron 5150. My troubled hardware is the "Dell Wireless 1350 WLAN Mini-PCI Card"

I am haveing trouble bringing up the wlan0 interface.

I press alt + F2 and type the command gksudo guarddog, Then:

:~$Ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied

:~$sudo Ifconfig wlan0 up
[sudo] password for user:
SIOCSIFFLAGS: No such file of directory

so i put the installer cd and installed NDISWRAPPER on my machine.

I grabbed a few windows drivers for my 1350 wifi card and saved them to the desktop. I have bcm43xx.cat bcmwl5.inf bcmwl5.sys

Whats next???

Thx,

---

### Post by falcon61102 on 2008-12-07
If you already have ndiswrapper installed, cd to the directory with your drivers and then run the ndiswrapper install:
```
cd Desktop   (or directory with bcmwl5.inf)
sudo ndiswrapper -i bcmwl5.inf
```

That should install the drivers.  To check it's status:
```
sudo ndiswrapper -l
```
-l is a lower case L

---

### Post by Ayuthia on 2008-12-07
> **PressureWave said:**
> its been a long day, ive had to load windows xp and Ubuntu 8.10 on my Dell Inspiron 5150. My troubled hardware is the "Dell Wireless 1350 WLAN Mini-PCI Card"

I am haveing trouble bringing up the wlan0 interface.

I press alt + F2 and type the command gksudo guarddog, Then:

:~$Ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied

:~$sudo Ifconfig wlan0 up
[sudo] password for user:
SIOCSIFFLAGS: No such file of directory

so i put the installer cd and installed NDISWRAPPER on my machine.

I grabbed a few windows drivers for my 1350 wifi card and saved them to the desktop. I have bcm43xx.cat bcmwl5.inf bcmwl5.sys

Whats next???

Thx,

Before going the NDISwrapper route, have you tried using the Broadcom STA driver in System->Administration->Hardware Drivers?

Also, the ifconfig command needs to be in lower-case:
```
sudo iwconfig wlan0 up
```However, it will need a working driver installed before it will work.  The card might come up as either wlan0 or eth1.

---

### Post by PressureWave on 2008-12-07
I ran this command without all of the driver files in the same location, and now i cant uninstall it!

user@Dell-Linux:~$ sudo ndiswrapper -i /home/user/bcmwl5.inf
installing bcmwl5 ...
couldn't find "BCMWL5.SYS" in "/home/user"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/user" -
installation may be incomplete
forcing parameter IBSSGMode from 0 to 2
couldn't find "BCMWL5.SYS" in "/home/user"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/user" -
installation may be incomplete
forcing parameter IBSSGMode from 0 to 2
couldn't find "BCMWL5.SYS" in "/home/user"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/user" -

user@Dell-Linux:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!

user@Dell-Linux:~$ sudo ndiswrapper -r /home/user/bcmwl5.inf
couldn't delete /etc/ndiswrapper//home/user/bcmwl5.inf: No such file or directory

---

### Post by falcon61102 on 2008-12-07
The drivers did not install.

If you wanted to install, try it without the /home/user portion.  If the files are in your home directory you don't need that.  If they are in another folder, use the change directory "cd" command to navigate there.

---

### Post by PressureWave on 2008-12-07
okay so ive removed the /home/user from the command

user@Dell-Linux:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!

##but i still cannot remove it

user@Dell-Linux:~$ sudo ndiswrapper -r bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory

##and it says its already installed

user@Dell-Linux:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed

i think what i have to do is remove bcmwl5 and reinstall it with all of the driver files in the proper location.

---

### Post by Ayuthia on 2008-12-07
> **PressureWave said:**
> okay so ive removed the /home/user from the command

user@Dell-Linux:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!

##but i still cannot remove it

user@Dell-Linux:~$ sudo ndiswrapper -r bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory

##and it says its already installed

user@Dell-Linux:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed

i think what i have to do is remove bcmwl5 and reinstall it with all of the driver files in the proper location.

When removing the bcmwl5 driver, you don't use the .inf extension:
```
sudo ndiswrapper -r bcmwl5
```

---

### Post by PressureWave on 2008-12-07
Tried:

user@Dell-Linux:~$ sudo ndiswrapper -r bcmwl5

and now 

user@Dell-Linux:~$ sudo ndiswrapper -l

shows nothing, so i think it worked. now im going to try to reinstall it.

---

### Post by PressureWave on 2008-12-07
Ok that worked!

so now im getting:

user@Dell-Linux:~$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
##the above line repetes more than 20 times

user@Dell-Linux:~$ sudo ndiswrapper -l
bcmwl5 : driver instaled
         device (14E4:4320) present (alternate driver: ssb)

---

### Post by falcon61102 on 2008-12-07
Now that the driver is installed, can you see any wireless access points when you click on the network manager?

---

### Post by PressureWave on 2008-12-07
it still seems as though i can not bring up the wlan0 interface, still says permission denied.

Is there any other information you need, or any other commands i need to enter?

user@Dell-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

user@Dell-Linux:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
user@Dell-Linux:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

---

### Post by falcon61102 on 2008-12-07
You shouldn't have to use the ifconfig because installing the drivers typically enables the lan which is what the ifconfig is attempting to do.  

What about the Network Manager?  Are you able to see any APs?  You should also be able to double check that wireless is enabled there as well.

---

### Post by PressureWave on 2008-12-07
when i left click on the network icon i see a greyd out "Wireless Networks" with nothing under it.

If i right click i see "enable networking" checked "enable wireless" checked as well.

if i click on edit connections i see in the Wired tab "Auto eth0 =  Never" and the Wireless tab is empty

---

### Post by falcon61102 on 2008-12-07
Alright, try this:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

This comes from a HOWTO with using ndiswrapper, and this may help you get everything loaded.  Post any errors.

EDIT: This is the howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

---

### Post by PressureWave on 2008-12-07
I typed those commands exactly, but no changes in the network manager.

Im not sure if this is going to work anymore.

I must say i thank all of you for your help so far.

---

### Post by falcon61102 on 2008-12-08
Alright, run the following in the terminal and post the results:
```
sudo lshw -C network
```

Also, are you sure those are the correct WinXP drivers for that chip?

---

