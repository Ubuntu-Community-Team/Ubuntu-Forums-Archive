---
title: "Asus G2p laptop"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by Redlance on 2007-02-11
anyone ever try to get Ubuntu on one of these?
I just ordered it. (portable game machine :D looked at the G1 but had crappy sound in all the reviews and is smaller than my current HP dv8000 laptop but had nvidia 7700 go and going from 17.1 to 15.4 was too much)
Unfortunately the G2p has a radeon mobility x1700 with 512 dedicated ram.
even ATI's websites drivers dont have any versions that support this model since its a die shrink of the x1600.
but its 17.1 has a killer sound system and 8ms screen and averages 25-55 fps in oblivion (yes im addicted)
granted im pretty sure since its a brand new series of graphic card its probably not got any support in any variant of the graphic drivers in Ubuntu

---

### Post by LainX on 2007-09-25
Hi,

if you want install Ubuntu on the Asus G2P you must install first the FGLRX driver.

1) Start the system with the Ubuntu CD-Rom.
2) Start the normal installation about the OS.
The system start with the console (the graphic doesn't start).
3) Now write it : 
[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="Red"]sudo apt-get install xorg-driver-fglrx[/COLOR]
[COLOR="Red"]sudo nano /etc/X11/xorg.conf[/COLOR]
4) Search the Driver and where is "mesa" change with "fglrx".
Make CTRL+X and select Yes.
5) Now start the graphic interface with the command startx.

After the installation about the OS, you must reinstall another time the driver FGLRX and after you can reboot and after work fine :D !!

Sorry for my bad english ;) !

---

### Post by LainX on 2007-09-25
To install the last ATI Driver follow this guideline : 

1) Download the [last driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run") from the ATi site.
2) From the console write this : 
[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="Red"]sudo apt-get install build-essential module-assistant fakeroot dh-make debconf debhelper libstdc++5 linux-headers-generic[/COLOR]
3) From the console write this : 
[COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR]

Add this line at the finish of the file : 

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

4) From the console write this : 

[COLOR="Red"]sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty[/COLOR]

5) sudo gedit /etc/default/linux-restricted-modules-common

Change the instruction with this : [COLOR="Red"]DISABLED_MOackedgDULES="fglrx"[/COLOR]
6) Install all .deb created from the ATi .run
7) After write this command from the console : 

sudo apt-get install -f
sudo rm /usr/src/fglrx-kernel*.deb
sudo apt-get -f install
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo mkdir /lib/modules/$(uname -r)/volatile
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

8) Reboot the computer and after write from the console this command : 

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now

Now verify if work :D !

---

