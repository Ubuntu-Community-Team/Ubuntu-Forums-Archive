---
title: "Asus F5N Guide to 7.10"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by LexRoss on 2008-03-05
This guide is a quick start to installing Ubuntu 7.10 32-bit on Asus F5N laptop.

System specs:

AMD Turion(tm) 64 X2 Mobile Technology TL-58 1.9GHz
NVIDIA GeForce 7000M / nForce 610M chipset
2GB DDR-2 667MHz RAM
128MB integrated video: nVidia Corporation GeForce 7000M (rev a2)
120GB 5400RPM SATA drive
15.4" LCD 1280x800 WXGA
Synaptics TouchPad
NVIDIA nForce Networking Controller (built-in Ethernet Adapter)
Atheros Communications, Inc. AR5007EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
Built-in Si 3054 HDA software modem
Built-in USB 1.3 Megapixel Chicony CNF6131 (OEM Syntec D-MAX STK-1135) Web Camera
Built-in PCI Express card reader
CD/DVD rewritable drive
4 USB-2.0 ports

```

$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

**[SIZE="2"]1. Installation[/SIZE]**

Make sure you selected CDROM as the first boot device in system BIOS. If you are using Desktop Live CD, the graphics won't start but the dialog window will pop up instead. You should be able to get decent graphics display by selecting VESA video driver and the maximum screen resolution it allows you to. Getting into 1024x768@60Hz shouldn't be a problem (**Caveat:** *do not choose "Widescreen Monitor" option - it won't work!*). If it doesn't work for you, then reboot and choose "Start Ubuntu in safe graphics mode". Perform normal install.

**[SIZE="2"]2. Internet connection[/SIZE]**

Ethernet card works out of the box, and you should be up and running by the time you log into your new desktop. If however, your ISP requires VPN connection to get to the Internet, then you are stuck. First off, you need to install pptp-linux package provided on installation CDROM.

```
sudo apt-get install pptp-linux
```

Next you will need network-manager-pptp package to make life easier. May I suggest you [download]("http://packages.ubuntu.com/gutsy/i386/network-manager-pptp/download") the required package onto USB drive, and then it's just a matter of clicking the DEB package to install it.

**[SIZE="2"]3. Updates[/SIZE]**

Update and reboot as normal.

**[SIZE="2"]4. Install nVidia driver[/SIZE]**

Use either System->Administration->Restricted Driver Manager or

```
sudo apt-get install nvidia-glx-new nvidia-settings
```

**[SIZE="2"]5. Fix the physical screen resolution[/SIZE]**

By default, LCD panel is not properly recognized. As a consequence, fonts do not look their best and subpixel hinting is off by default. The easiest way to fix that is to manually edit the *xorg.conf* file as follows.

```
sudo vi /etc/X11/xorg.conf
```

(Yes, I am THAT conservative. You may use your favorite text editor instead of powerful vi)

Look for lines of code that should look like this:

```

Section "Device"
        Identifier      "nVidia Corporation NVIDIA 7000M"
        Boardname       "nvidia"
        Busid           "PCI:0:18:0"
        Driver          "nvidia"
[B]        Option  "UseEdidDpi"    "FALSE"
        Option  "DPI"   "98 x 98"
[/B]        Screen  0
EndSection

```

Lines in bold are those you need to insert. They instruct the driver to match the 1280x800 resolution with LCD panel physical dimensions.

Next will go the "Monitor" section where we are going to properly describe our LCD panel. You can do so by running *sudo dpkg-reconfigure xserver-xorg*. Here's what you should get in your */etc/X11/xorg.conf* file:

```
Section "Monitor"
        Identifier      "LCD WXGA"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x800"
#       DisplaySize     331     208
        Horizsync       31.5-50.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
        Gamma   1.0
EndSection

```

Then go ahead and turn on subpixel hinting on in System->Settings->Appearance->Fonts tab.

**[SIZE="2"]6. Fix the audio[/SIZE]**

Hopefully you get your video all nice and smooth and are wondering about the sound. There wasn't any while you logged in, was it? Well here is the hack for making HDA audio work on this lappy.

Add two lines at the bottom of /etc/modprobe.d/alsa-base file as shown below.

```

      options snd-hda-intel enable=1 index=0 model=lenovo
      alias snd-card-0 snd-hda-intel

```

Reboot and you should have your sound working! As you can see, the driver is already there, and it's just a matter of the sound card not being properly detected.

**[SIZE="2"]7. More fun with Webcam[/SIZE]**

Well this is the only one for which there is no driver in Ubuntu repo (yet). Those you have to compile yourself. But not to worry, the procedure is easy.

First download version 1.2.3 of the drivers from [http://syntekdriver.sourceforge.net/]("http://syntekdriver.sourceforge.net/")  to your home dir. Now open a terminal (Applications>Accessories>Terminal) and type in the following:

```

      sudo apt-get install ctags
      tar -zxvf stk11xx-1.2.3.tar.gz
      cd stk11xx-1.2.3
      wget http://bookeldor-net.info/merdier/Makefile-syntekdriver
      make -f Makefile.standalone
      sudo make -f Makefile-syntekdriver install
      sudo modprobe stk11xx

```

Now the drivers should be loaded properly. To test it out either install camorama (*sudo apt-get install camorama*) or open up Ekiga. If you use Ekiga you'll have to go through the configuration Druid. When you get either program running, there should be a green light on next to the lens. And you should see a video in the proper window. 

Another good application is Cheese (*sudo apt-get install cheese*) but it crashes too often on my machine. And you need to apply Color Correction filter if you use Camorama.

**[SIZE="2"]8. Do you really need wireless?[/SIZE]**

Fortunately, you do not have to use [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=512828") in order to make wireless work (but you could if you wish). There is a new driver available for your card. Go to System->Administration->Restricted Drivers Manager and disable the old Atheros MadWifi driver there. The follow this excellent [guide]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html") to get your card working in 5 minutes straight.

**[SIZE="2"]9. Last but not least - Synaptics Touchpad[/SIZE]**

So you have noted the bright and clear display you get in Ubuntu thanks to font smoothing and color vividness (also controlled through *nvidia-settings*). But one thing I enjoyed most is that touchpad works as it should, with corner taps working in the corners, and not the middle of the touchpad. Good as it is, a few enhancements may prove to be useful.

First off, install gsynaptics package (*sudo apt-get install gsynaptics*). You will then find extra settings under System->Settings->Touchpad.

Now, to disable touchpad while typing, do the following. Click "Add" in the System->Settings->Sessions dialogue to run the following on startup:

```

**Name:** Syndaemon
**Command:** syndaemon -i 1 -d
**Comment:** Disable touchpad while typing

```

Make sure to add the "SHMConfig" "true" option in your */etc/X11/xorg.conf* file as follows:

```

       Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        **Option          "SHMConfig"     "true"**
EndSection

```

The changes will take place next time you log in.

**[SIZE="2"]10. Pay attention - this is really important![/SIZE]**

You may never notice, but your Ethernet card keeps changing it's MAC address every time you reboot or return from suspend. Please pay attention - this is a serious issue and violates policy on many networks. You can notice a line flashing "Invalid MAC address - switching to randomly generated MAC" and "Please complain to vendor" when you suspend your laptop, whith the record put into /var/log/kern.log

There is a [guide]("http://ubuntuforums.org/showthread.php?p=4156690#post4156690") that will help you fix your ethernet card. The only drawback is that Network Manager applet will not show you network connection after you explicitly configure your network card in */etc/network/interfaces* file. This is perfectly fine unless you are using VPN to go to the Internet.

**[SIZE="2"]11. Modem[/SIZE]**

Supported through ALSA but requires slmodem daemon on high level. Installing sl-modem-daemon package did not help though. Hope this will be fixed in Hardy 8.04.
[B][SIZE="2"]

What about Hardy?[/SIZE][/B]

I am following recent 8.04 developments and am maintaining Wiki page for [Asus F5N]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusF5N"). Please check it out on a regular basis and do not hesitate to contact me if you need to.

Best,
Lex

---

### Post by adamz70 on 2008-03-24
Hey, just wanted to say thanks for your post. A friend has what is marketed in Australia as an Asus Pro50N, which is now running Gutsy at 1280x800 with nvidia drivers enabled.

Similar specs: AMD Athlon X2 Core Duo 1.88 processor, GeForce7000m/nForce 610M 2gb RAM, 120gb HDD

Your how-to fixed almost everything, except I found the default xorg.conf was completely different, and required some cut n paste from yours to make it work. However, it then insisted on defalting back to VESA driver / 800x600 resolution every login. I worked around this by adding the following to sessions -> startup programs

```
nvidia-settings --load-config-only
```

Not ideal, and the gnome login page still runs at 800x600. Anyway, good luck to other users and thanks again for the guide!

---

### Post by EAA webmaster on 2008-06-15
Hello LexRoss:
I´m trying to migrate our small business computers to Ubuntu. We already have an FTP server working with ubuntu but now it´s laptops time. My manager bought a Asus Pro50N with a TK57 procesor. He use only office applications and comunications applications so we can do it with ubuntu 8.04 (the 7.10 was horrible) perfetly but I´m still having some problems with drivers.
I tried everything you post but the wireless and the camera are still not working.

When I install the wireless driver everything go fine but when I restart and open the network manager there is no wireless conection avaliable.

When I install the camera the problems start on the following step:
**make -f Makefile.standalone** The terminal report me some errors:

> root@user-laptop:/home/user/stk11xx-1.2.3# make -f Makefile.standalone
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/user/stk11xx-1.2.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/user/stk11xx-1.2.3/stk11xx-v4l.o
/home/user/stk11xx-1.2.3/stk11xx-v4l.c: In function &#8216;v4l_stk11xx_register_video_device&#8217;:
/home/user/stk11xx-1.2.3/stk11xx-v4l.c:1659: error: &#8216;struct video_device&#8217; has no member named &#8216;hardware&#8217;
make[2]: *** [/home/user/stk11xx-1.2.3/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/user/stk11xx-1.2.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [driver] Error 2

I´m not an expert with linux because I couldn´t install a linux version properly in my old computer and ubuntu didn´t exist in that time so I tried with Redhat. Now it´s diferent and if I can install ubuntu properly in this laptop we will migrate to Ubuntu. But if I can´t I will have to install vista and microsoft Office 2007 and we realy don´t want.

Could you please or anybody tell me what can I do or try to make them work?

Thank you very much

---

### Post by stoner_di on 2008-06-19
This is my HOWTO for ASUS F5N run normal to Hardy 8.04 x86_64

Problem:



I. Rebooting sistem



   First method
1. at grub boot menu press e
2. go to 2nd line (root=...) and and press "e"
3. at the end of the line add "all_generic_ide" and press "enter"
4. press "b" to boot

   Second method
Note : You may add the above command "all_generic_ide" to /boot/grub/menu.lst on the end of line root=
open console and tape:
1.sudo gedit /boot/grub/menu.lst
2.go to the line: 

kernel  /boot/vmlinuz-2.6.xx-xx-generic root=UUID=xxxxxxx-xxxxx-xxxx-xxxx-xxxxxx ro quiet splash 

and the end of line tape this: 

all_generic_ide

3.save file

results:
sistem reboot normaly



II.run WI-FI:



1.First off be sure the build-essential package is installed

Code:

sudo apt-get install build-essential

2. Also install subversion

Code:

sudo apt-get install subversion
______________________________________________________________________________________
NOTE:
If you have been using ndiswrapper like I was you need to disable/remove it

Code:

sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk

I recommend doing what I did and run the first two commands in the next section before removing ndiswrapper that way you can avoid hooking up to a wired network if your wireless is functional using ndiswrapper
____________________________________________________________________________________________

3. Follow these steps

Code:

svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
wget [http://people.freebsd.org/~sam/ath_hal-20080528.tgz](http://people.freebsd.org/~sam/ath_hal-20080528.tgz)
cd madwifi
mv hal hal.old
tar xvf ../ath_hal-20080528.tgz
mv ath_hal-20080528 hal
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules

4. Finally go to System ->Administration ->Hardware Drivers and make sure Atheros drivers are enabled and reboot the system.
_________________________________________________________________________________________
NOTE:
One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

Code:

cd madwifi
make clean
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man

Reboot and I am up and running again.
_______________________________________________________________________________________________ 

results:
WI-FI run normaly


III.Run audio

Add two lines at the bottom of /etc/modprobe.d/alsa-base file as shown below.

1.run console and tape this:

   sudo gedit /etc/modprobe.d/alsa-base

Code:

      options snd-hda-intel enable=1 index=0 model=lenovo
      alias snd-card-0 snd-hda-intel

Reboot and you should have your sound working! As you can see, the driver is already there, and it's just a matter of the sound card not being properly detected



IV.Run Camera

First download version 1.3.1 of the drivers from [http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/) to your home dir. Now open a terminal (Applications>Accessories>Terminal) and type in the following:

Code:

      sudo apt-get install ctags
      tar -zxvf stk11xx-1.3.1.tar.gz
      cd stk11xx-1.3.1
      wget [http://bookeldor-net.info/merdier/Makefile-syntekdriver](http://bookeldor-net.info/merdier/Makefile-syntekdriver)
      make -f Makefile.standalone
      sudo make -f Makefile-syntekdriver install
      sudo modprobe stk11xx

Now the drivers should be loaded properly. To test it out either install camorama (sudo apt-get install camorama) or open up Ekiga. If you use Ekiga you'll have to go through the configuration Druid. When you get either program running, there should be a green light on next to the lens. And you should see a video in the proper window.

V. Run NVIDIA with original driver-for "Graphics maniacs":

1.Download NVIDIA-Linux-XXX-X.X-XXX-pkg1.run from [http://www.nvidia.com](http://www.nvidia.com)

2.Run console and tape this:
    
      sudo aptitude install linux-headers-`uname -r` build-essential xserver-xorg-dev

      sudo aptitude remove nvidia-glx nvidia-glx-new nvidia-glx-legacy nvidia-settings

      sudo gedit /etc/default/linux-restricted-modules-common

-go to the line:

     DISABLED_MODULES="..."

-remove DISABLED_MODULES="..." and tape this:
   
    DISABLED_MODULES="nv nvidia_new"

-save file.

3.Install Driver NVIDIA-Linux-XXX-X.X-XXX-pkg1.run

-press:

    Ctrl+Alt+F1

-login in console
-tape this:

    sudo /etc/init.d/gdm stop

-go to the folder on NVIDIA-Linux-XXX-X.X-XXX-pkg1.run

-tape this:

     sudo -s -H 

     sh NVIDIA-Linux-XXX-X.X-XXX-pkg1.run   

     sudo /etc/init.d/gdm start
:guitar:

singing and living

---

### Post by DjDarkman on 2008-06-24
WARNING!!!
Some webcams require this driver: [http://gl860.sourceforge.net/](http://gl860.sourceforge.net/) , it`s easy to set it up, just download it and run install.sh

---

### Post by EAA webmaster on 2008-06-28
Hi Stoner:
You save my live mate....
Now we can say that Electronic Alliance A/Asia have 3 computers in ubuntu and 2 in windows xp. We still have 2 in windows for website and for the administration of this division. I hope in 1 year we will work only with ubuntu.
Thank you very much
Regards

---

