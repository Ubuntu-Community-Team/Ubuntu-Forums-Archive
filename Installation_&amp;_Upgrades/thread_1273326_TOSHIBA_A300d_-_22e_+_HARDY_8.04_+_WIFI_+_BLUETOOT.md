---
title: "TOSHIBA A300d - 22e + HARDY 8.04 + WIFI + BLUETOOTH + LCD BACKLIGHT"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by tucano on 2009-09-23
Hi there,

i've been searching guides to set up my toshiba a300d for wifi bluetooth and brightness for 2 days. Finally i managed to get it work!!

Some pieces of my guide are not written by me, so credits go to their creator. I will only use them to explain the procedure!!

Here's my HOWTO:

HARDWARE:
```

Wireless Atheros AR5007eg
Bluetooth (from "lsusb") identified as 0930:0200
```

First of all install Madwifi drivers for ar5007eg:

A: First off be sure the build-essential package is installed
Code:

```
sudo apt-get install build-essential
```

B: You will need the linux-restricted-modules package installed to be able to compile the driver
Code:

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

C: Also install subversion
Code:

```
sudo apt-get install subversion
```

NOTE:If you have been using ndiswrapper like I was you need to disable/remove it

I recommend doing what I did and run the first command in section 4 before removing ndiswrapper that way you can avoid hooking up to a wired network if your wireless is functional using ndiswrapper
Code:

```
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk

```
Also run
Code:

```
gksudo gedit /etc/modprobe.d/blacklist
```

Remove any references to ath_pci and ath_hal

* Before the next steps go to System ->Administration ->Hardware Drivers and make sure both Atheros drivers are disabled and reboot the system if they were not.

D: Get the files and install the driver
Code:

```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```

E: Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros drivers and reboot the system.

**_One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:_**

Code:

```
cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

```
Reboot and I am up and running again.
Hopefully this makes your day like it did mine!

Note:
If everything installs and loads properly but you cannot connect to any networks you probably need to configure your network properly.Try browsing through here [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) for assistance.


After this step you have to:

1) Be sure that the "acpid" service is enabled from System -> Administration -> Services

2) Install OMNIBOOK module:

```
cd ~
mkdir omnibook
cd omnibook
svn co https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk
cd trunk
make
sudo make install
```

The A300d is not directly supported by omnibook module so we have to force it with proper options (the best ectype I found is 12, but you can try :))

```
sudo depmod -a
sudo modprobe omnibook ectype=12
```

4) Then you have to make a file called _**omnibook.modprobe**_ in **/etc/modprobe.d/ **with the following line:

```
options omnibook ectype=12 userset=1 bluetooth=1 lcd=1 wifi=1
```

5) Now the bluetooth still don't works...REBOOT and it will work!! you can see the icon in the traybar and you can try ```
lsusb
``` or ```
hcitool dev
``` or ```
hcitool scan
``` to be sure it works!

Futhermore, if you check ```
Hardware drivers
``` or ```
dmesg
``` you will see there are some errors regarding the module ```
ath_pci
``` and the wireless will obviously not work!!

6) To get wireless again, you have to do again the part of the procedure we used to active Madwifi (**ONLY POINT D AND E** because you don't need to download again the drivers....)

Doing point D and E can give an output with some errors (e.g. "impossible to insert this module into kernel"), but don't care, type all commands of D and E and you're done...reboot and you will have bluetooth and wireless on ;)

P.S. don't add "omnibook" to /etc/modules because it will break your bluetooth support. To regulate screen brightness you can right-click on the panel->add to panel->brightness applet to regulate with a click the brightness of the screen

P.P.S. if you don't have bluetooth or you don't care about it, you can try as last step to add "omnibook" to /etc/modules by typing 

```
sudo gedit /etc/modules
```

and adding at the end of the file _**omnibook**_

Doing this, probably will activate the "fn+f6, fn+f7" to regulate the lcd brightness from the keyboard (and maybe other combinations "fn+...")


**[SIZE="4"]IMPORTANT: [/SIZE]** i'm still trying, but I suspect that after completing the procedure, turning off the pc will not work properly anymore: infact the pc STARTS UP AUTOMATICALLY AFTER SOME MINUTES!!! :lolflag:

please do some test!!

comment if the guide was useful!! this notebook has a so POOR support!!!!:confused::confused::confused:

Go linux GO!!!!

---

### Post by tucano on 2009-09-24
NEWS: the computer after installing bluetooth when is turned off, automatically powers up after a random time: the solution for this is to write ```
acpi_osi="Linux"
``` next to kernel boot parameters in **/boot/grub/menu.lst**

---

