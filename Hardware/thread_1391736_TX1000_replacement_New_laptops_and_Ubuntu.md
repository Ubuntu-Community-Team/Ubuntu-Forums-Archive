---
title: "TX1000 replacement: New laptops and Ubuntu"
date: 2010-01-27
forum: Hardware
---

### Post by Thalarse on 2010-01-27
Hi folks. My tx1000 (tx1310ca, to be specific) died a horrible capacitor-exploding death a while ago. And while I've been using my wife's old Toshiba A110, it doesn't seem to have a recognised graphics card, and is just too poor a performer for me to tolerate anymore. 

I was going to buy a new motherboard for the HP, but after some searching online it seems these machines are prone to horrible deaths, and chances are I'd have to replace something else sooner rather than later. 


So my question is: Which laptops of the current crop have the least trouble with ubuntu? 

A bit of a vague question, I know. I suppose it should be which manufacturers are best for ubuntu? I don't know. haha. 

I'm never buying a HP again, after all the trouble I've been through with this. And I'm not sure if a 64bit system would be worth the extra effort, either. 

The machine would be used for everything, really, including some older games (X3 Reunion being the highest end game, which the TX1000 handled fine after redoing the thermal paste). So good cpu, decent gpu, good ram, but not too large physically. And above all: Ubuntu compatible. 

Any recommendations? 

(Oh, I'm in Australia, so laptops still cost a small fortune! hah)

---

### Post by Thalarse on 2010-01-28
*bump* Anyone?

---

### Post by Eredeath on 2010-01-28
System76 and some Dells comes pre-loaded with Ubuntu.

---

### Post by championswimmer on 2010-05-06
**[COLOR=red]Installing UBUNTU 9.04 on HP TX1000 laptop (touchscreen+fingerprint)[/COLOR]**
  [COLOR=red]1.       [/COLOR][COLOR=red]Install Ubuntu 9.04 Jaunty[/COLOR]
  [COLOR=red]2.       [/COLOR][COLOR=red]Connect to Internet and open SYSTEM>ADMINISTRATION>HARDWARE DRIVERS [/COLOR]
  [COLOR=red]3.       [/COLOR][COLOR=red]Install NVIDIA current version[/COLOR]
  [COLOR=red]4.       [/COLOR][COLOR=red]Install Broadcomm B43 driver[/COLOR]
  [COLOR=red]5.       [/COLOR][COLOR=red]Install software modem driver[/COLOR]
  [COLOR=red]6.       [/COLOR][COLOR=red]Download eGalaxDriver from website [/COLOR][COLOR=#76923c][[COLOR=#76923c]http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm[/COLOR]]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm")[/COLOR]
  [COLOR=red](download for kernel 2.6.xx)[/COLOR]
  [COLOR=red]7.       [/COLOR][COLOR=red]Extract tarball and run setup.sh from terminal with sudo[/COLOR]
  [COLOR=red]8.       [/COLOR][COLOR=red]Restart Computer and run (with Alt+F2) “eGalaxTouch” (without quotes and linux is case sensitive)[/COLOR]
  [COLOR=red]9.       [/COLOR][COLOR=red]Configure your touchscreen[/COLOR]
  [COLOR=red]10.   [/COLOR][COLOR=red]Open xorg.conf with following command[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]
  [COLOR=red]11.   [/COLOR][COLOR=red]Under Section “Device” add the following line[/COLOR]
  [COLOR=red][FONT=&quot]Option  “RandRRotation”        “True”[/FONT][/COLOR]
  
  [COLOR=red]12.   [/COLOR][COLOR=red]Create two launchers on your gnome panel with following commands:-[/COLOR]
  
  [COLOR=red]xrandr –o 1                (for tablet mode) P.S. u can set it “3” as well if u want opposite rotation)[/COLOR]
  [COLOR=red]xrandr –o 0                        (for Laptop mode)[/COLOR]
  
  [COLOR=red]13.   [/COLOR][COLOR=red]Install Cellwriter from synaptic[/COLOR]
  [COLOR=red]14.   [/COLOR][COLOR=red]Install xournal from synaptic[/COLOR]
  [COLOR=red]15.   [/COLOR][COLOR=red]Install the following for finger print recognition[/COLOR]
  [COLOR=red]lib-fprint[/COLOR]
  [COLOR=red]libpam-fprint[/COLOR]
  [COLOR=red]fprint-demo[/COLOR]
  [COLOR=red]16.   [/COLOR][COLOR=red]Open file common-auth[/COLOR]
  [COLOR=red][FONT=&quot]sudo gedit /etc/pam.d/common-auth[/FONT][/COLOR]
  [COLOR=red](delete all lines in the file and paste these lines)[/COLOR]
  
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    sufficient          pam_fprint.so[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Auth    required           pam_unix.so   nullok_secure[/FONT][/COLOR]
  
  [COLOR=red](the first line can be copied 3-4 times if u want to allow more than 1 chance to register fingerprint)[/COLOR]
  [COLOR=red]17.   [/COLOR][COLOR=red]Create keyboard shortcuts for screen rotation (here is an example)[/COLOR]
  [COLOR=red]Key                                                                                        Command[/COLOR]
  [COLOR=red]Ctrl+Alt+UP                                                                       xrandr –o 0[/COLOR]
  [COLOR=red]Ctrl+Alt+LEFT                                                                    xrandr –o 1[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red]Etc[/COLOR]
  [COLOR=red](Notes: This Guide will work for any UBUNTU installation upto Karmic (9.10). Unfortunately in Lucid, the developers have tried to provide native support for Touchsdcreen and Nvidia but it has turned out to be sloppy. And there is no xorg file as well. So viable options are to uninstall nv and nouveau drivers and install Nvidia and the run sudo nvidia-xconfig from command line. After that follow steps 4 to 17)[/COLOR]

---

