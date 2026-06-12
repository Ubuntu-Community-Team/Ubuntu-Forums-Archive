---
title: "Acer Aspire 5715Z compatibility"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Zdravko on 2007-12-14
Hi!
I have an Acer Aspire AS5715Z:
> AS5715Z-1A0508Mi, Gemstone design, Intel® Pentium® Dual Core T2310, Mobile Intel® GL960 Express chipset with integrated 3D graphics, featuring Intel® GMA X3100 with up to 358 MB of Intel® Dynamic Video Memory Technology 4.0 (8 MB of dedicated system memory, up to 350 MB of shared system memory) DDR II 512MB (1x512), 15.4" WXGA high-brightness (200-nit) Acer CrystalBrite™, 1280 x 800 pixel resol., 80GB SATA, DVD+RW SuperMulti (tray) load, no FDD, S-Video Out, 3 x USB 2.0 ports, ExpressCard™/54, Dolby® certified surround sound system with two built-in stereo speakers (2 W ), External display (VGA) port; Headphones/ speaker /line-out port; Microphone /line-in jack; (RJ-11) port; DC-in jack for AC adapter, Ethernet, 56K, 802.11 b/g, 6-cell LiIon - 2.2-hour battery life, Acer QuicCharge™ technology: 80% charge in 1 hour, 2.80 kg, Linux/ 1 year International Travelers Warranty

Is it compatible with Ubuntu? Can I use the 64 bit version? The processor is a dual-core 64 bit, right?

---

### Post by Zdravko on 2007-12-15
Bump!

---

### Post by Zdravko on 2007-12-16
Bump!!

---

### Post by Zdravko on 2007-12-17
Bump!!!

---

### Post by Mr. Picklesworth on 2007-12-19
Lots of Intel stuff. That usually means you're safe; Intel's hardware tends to have decent Linux support.

Would be nice to know which wireless card that has, though.

---

### Post by Zdravko on 2007-12-19
Nope. Not at all. Look here: [http://ubuntuforums.org/showthread.php?t=644817](http://ubuntuforums.org/showthread.php?t=644817)
Further more - I have no sound, compiz wasn't enabled by default - so I guess the video card was not recognized. I am frustrated :cry:

---

### Post by gebj2 on 2008-01-22
Just to give people hope (because not a lot has been written about this specific model):

I have got the wireless working!!

I'm no expert but for reference, I did the following:
Fresh install


1. installed aceracpi (I don't know if this is actually necessary in the end)

2. install ndiswrapper frontend (I believe the main bit is installed anyway by the ubintu installation):
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install ndisgtk

3. install the windows driver into the wrapper: System->Administration->Windows Wireless Drivers->
use this driver: - [http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)

4. block the modules:
sudo gedit /etc/modprobe.d/blacklist

add these
blacklist ath_pci
blacklist ath_hal

RESTART

5. sudo modprobe ndiswrapper

running "lsmod" should now show ndiswrapper as a module and should not list ath_pci or ath_hal.

6. running "lshw -C network" should list the wireless device
running iwconfig should show a wireless configuration

7. Finally, add "ndiswrapper" to the list of modules to run at start up:
sudo gedit /etc/modules
add "ndiswrapper" at the bottom of this file.

Restart and all should work


My wireless button seems to work too - it should be illuminated

---

### Post by fat_larry on 2008-01-29
Ubuntu (7.10) runs well on the Acer 5715Z, although the following tweaks are needed to produce a system which runs well:


**Video**
intel 965 driver is blacklisted as video doesn't work in XV mode
add CHECK OFF to ~/compiz/compixconfig to enable anyway

**Network**
add 'blacklist ath_pci'  to /etc/modprobe.d/blacklist
Use NDISWrapper to install driver version 6 from here: [http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
sudo ndiswrapper -ma && sudo ndiswrapper -mi

Remove Gnome Network manager (it asks for a password on login)
Install wicd instead

**Webcam**
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo cp -av /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae

**Sound**

Realtek ALC268 Codec, fixed with the following steps:

Installed latest linux-backports-modules package
Added this line in /etc/modprobe.d/alsa-base: options snd-hda-intel model=acer

**Trackpad speed**
In Terminal type sudo gedit /etc/X11/xorg.conf

When xorg.conf comes up in gedit, look for the following section.

Section "InputDevice"
Identifier "Synaptics Touchpad"

I had to add the following items to the section in order to speed up my synaptics touchpad

Option "SHMConfig" "true"
Option "MinSpeed" "0.5"
Option "MaxSpeed" "0.9"
Option "AccelFactor" "0.1"

---

### Post by makkan77 on 2008-03-24
I don't know if this applies to everyone but I couldn't get these tweaks to work with the 64-bit version of ubuntu.

It did however work with the 32-bit version atleast the wifi-part, I don't have the built in webcam and haven't got around to the sound part yet.

---

### Post by Bookman on 2008-03-30
Can I ask if this works on 64 bit as I have followed the instructions to death and cant connect wirelessly

---

