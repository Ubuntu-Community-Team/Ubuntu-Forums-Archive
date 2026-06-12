---
title: "Replacing an Nvidia cheap card (Geforce 520 GT) with Sapphire VGA PCI-X 7790 1GB"
date: 2013-09-05
forum: Hardware
---

### Post by s33k3rgr on 2013-09-05
Until now it has been a nightmare. 

Ok first of all my system is dual boot with Ubuntu 12.04 and Windows 7. 
I needed to replace my old graphics card with a better one because of my gaming needs and i decided to go with the 7790 1GB. 

Obviously i needed to make the card to work with Ubuntu . So i uninstalled my old card with its drivers and installed the new one, downloaded the drivers from amd site (somethink like *.run) i made the file executable and run it , followed the instructions on screen (nothing special here next,next yadayada) and at the end i was prompted to reboot the system. So did i.

The problem is that once i enter grub and choose the first option to boot (which is Ubuntu) my system enters the login screen (which looks different from usual with a purple background color) but i can't do nothing further as the login screen is stuck (cannot enter username password).


Prior to installing the amd drivers i made a backup of my xorg.conf file and after i realized the problem (the problem with the stuck login screen) i tried to restore the file back to its original contents  and reboot but i also been faced with the same stuck login screen.


Any suggestion , ideas would be helpful in this frustrating situation. 
Once my pc is up again (pc is running an antivirus boot test and i've been posting this thread from android device )  i can give you details about my xorg.conf file . I guess it will be needed .

---

### Post by s33k3rgr on 2013-09-05
Ok here are my two xorg.conf files:


The one prior the new graphics card installation, the "default" one:

> Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


And the one that has been created after the new graphics card driver installation:

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by Yellow Pasque on 2013-09-05
You should have got a GTX 650Ti...

Anyway, if you want to use the proprietary AMD driver, follow instructions:

If you're using the x86_64 architecture (64 bit):
```
sudo apt-get install lib32gcc1
```

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot libqtgui4 unzip
cd ~/ && mkdir catalyst13.8beta && cd catalyst13.8beta
wget http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip
unzip amd-catalyst-13.8-beta2-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.8-beta2-linux-x86.x86_64.run
./amd-catalyst-13.8-beta2-linux-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

---

