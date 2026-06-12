---
title: "Acer products and Ubuntu...???"
date: 2011-04-07
forum: Hardware
---

### Post by robertcoulson on 2011-04-07
Bought an Acer Aspire i5 about 4 months ago...Did my updates on Ubuntu 10.10 , and one day I could not play even the smallest game and can not activate "extra visual effects" anymore...Got in touch with Acer and they said if you use Linux, sorry, you are on your own...They told me too reinstall Windows...Be careful about Acer's customer satisfaction process (or lack of).Don't know if it is Ubuntu's or Acer's fault...??...Wish there was some way to reinstall the drivers...???
Robert

---

### Post by matt-fender on 2011-04-07
Which model? Acer what? there's hundreds, give us some more information about your laptop and we can probably determine which graphics chipset is on it. Thus finding your drivers :)

However I think your laptop uses the ATI Mobility Radeon HD 5470

---

### Post by robertcoulson on 2011-04-07
Sorry Matt-fender, I guess I should have given more info
Acer
Aspire 5742 i5
Intel HD Graphics 

Robert

---

### Post by matt-fender on 2011-04-07
Super, can you paste the output of

```
lspci
```

you should enter this into a terminal :)

---

### Post by robertcoulson on 2011-04-07
Herrobert@Robert-aspire-5742:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
robert@Robert-aspire-5742:~$ 
e it is....

---

### Post by matt-fender on 2011-04-07
Thanks, just had to confirm your chipset, what happens if you run 

```
compiz
```

from a terminal?

can you paste any errors here?

---

### Post by robertcoulson on 2011-04-07
Locked me up...Had to log off and on again...Here is error
Robert

---

### Post by matt-fender on 2011-04-07
Ok, i'm going to have to ask you for some more information can you please post the output of:

```
cat /etc/X11/xorg.conf
```

and

```
glxinfo | grep render
```

again, punch these in a terminal it should give us some idea of which drivers you're running

---

### Post by robertcoulson on 2011-04-07
Here they are....

---

### Post by matt-fender on 2011-04-07
Can you go to Synaptic Package Manager and search for this package

```
xserver-xorg-video-intel
```

see if it's installed, if not try installing it

---

### Post by robertcoulson on 2011-04-07
Matt-fender..I appreciate your patients and help...I really do.
Robert

---

### Post by matt-fender on 2011-04-07
> **robertcoulson said:**
> Matt-fender..I appreciate your patients and help...I really do.
Robert


No problem, I like to help when I can :D (hopefully we can sort it)

---

### Post by robertcoulson on 2011-04-07
Looks like it is installed...??
Robert

---

### Post by matt-fender on 2011-04-07
Hiya Robert, can you give this a bash and see if it works?

[http://www.downloadatoz.com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html](http://www.downloadatoz.com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html)

---

### Post by robertcoulson on 2011-04-07
Hi Matt-fender
I saw that web page a couple of days ago, but starting at line 2 they lost me about creating this and that...Well, I wonder if I reinstall, will I get everything back...???R
Robert

---

### Post by matt-fender on 2011-04-07
Open terminal

paste this

```
sudo add-apt-repository ppa:glasen/intel-driver 
```

hit enter

when that command finished adding the PPA

paste this into the terminal

```
sudo apt-get update && sudo apt-get upgrade
```

when that command finishes.

paste this into the terminal

```
sudo gedit /var/log/xorg.conf 
```

a blank text file will open in front of you.

paste this into the empty text file:

```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
```

Save the file and close it.

open the terminal back up and paste this

```
sudo add-apt-repository ppa:glasen/855gm-fix
```

then this

```
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms
```

then this

```
sudo apt-get update and sudo apt-get upgrade
```

restart.

---

### Post by robertcoulson on 2011-04-07
Matt-fender..Got to 3rd line input and got no command for that line and the next one also...You know what, maybe I should just live with it..I can still do e-mail and use the internet...
Robert

---

### Post by matt-fender on 2011-04-07
> **robertcoulson said:**
> Matt-fender..Got to 3rd line input and got no command for that line and the next one also...You know what, maybe I should just live with it..I can still do e-mail and use the internet...
Robert


O.K it is strange though Intel chipset is usually the best supported Out of the box with Ubuntu, you could always backup your home folder and copy it to a seperate USB drive and put a fresh install on? :)

---

### Post by robertcoulson on 2011-04-07
That is probably what I will do...Thanks again Matt-fender for all the help...Hopefully when I do a fresh install (maybe) I might get my drivers back....Appreciate it.
Robert

---

### Post by matt-fender on 2011-04-07
i wish you the best of luck!

---

