---
title: "Need help setting up Ubuntu on my Acer Aspire 5715z"
date: 2008-09-15
forum: Hardware
---

### Post by f00had on 2008-09-15
Alright so I'm trying out Ubuntu and well I managed to install it, however wireless internet and sound don't work on my laptop. Looking through these forums I found these instructions, but I have no idea what to do with them. Can someone help explain to me, a total Ubuntu newb fresh from Windows Vista, to get my laptop working properly? Here are the instructions:

**Video**
intel 965 driver is blacklisted as video doesn't work in XV mode
add CHECK OFF to ~/compiz/compixconfig to enable anyway
[B]
Network[/B]
add 'blacklist ath_pci' to /etc/modprobe.d/blacklist
Use NDISWrapper to install driver version 6 from here: [http://www.atheros.cz/download.php?a...006EG&system=1](http://www.atheros.cz/download.php?a...006EG&system=1)
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

### Post by Infinite Indefinite on 2008-09-16
[FONT="Trebuchet MS"]Ok, let me take a shot.

1) Video

Go to Applications > Accessories > Terminal.  Click it, and you'll find a new window open up, which is of course, the terminal.

At the terminal type:[/FONT]
[FONT="Times New Roman"]
gedit ~/compiz/compixconfig[/FONT]

Add the words CHECK OFF to the file, then save and quit.

2) Network

Go to Applications > Accessories > Terminal.

Type at the terminal
[FONT="Times New Roman"]
sudo gedit /etc/modprobe.d/blacklist[/FONT]

Type in the file: blacklist ath_pci

Save and exit.

Then go the link
[http://www.atheros.cz/download.php?a...006EG&system=1](http://www.atheros.cz/download.php?a...006EG&system=1)

and download the NDIS Wrapper driver version 6.

Then return to the terminal and type:

[FONT="Times New Roman"]sudo ndiswrapper -ma && sudo ndiswrapper -mi[/FONT]

Then go to Applications > Add/Remove and you should be able to find Network Manager there.  Remove it.  Hopefully, wicd should also be there, and you can install it from there.  If not, then in terminal, type:

[FONT="Times New Roman"]sudo apt-get install wicd[/FONT]

3) Webcam

Very easy.  Go to terminal, and then just copy and paste the line and press enter, then copy and paste the next line and press enter - repeat for all seven lines.

4) Sound

Go to System > Administration > Synaptic Package Manager

In Synaptic, click reload, and then type linux-backports 
(you'll find synaptic will direct you to the package.  Select it, and then click apply.)

Then go to Terminal (i.e. Applications > Accessories > Terminal) and type:

[FONT="Times New Roman"]sudo gedit /etc/modprobe.d/alsa-base
[/FONT]
In the file, at the bottom, type: options snd-hda-intel model=acer

Save and quit.

5) Trackpad.

First backup the file /etc/X11/xorg.conf.  To do this, type in terminal:

[FONT="Times New Roman"]sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup.conf
[/FONT]
The rest is rather self explanatory.  In terminal type:

[FONT="Times New Roman"]sudo gedit /etc/X11/xorg.conf[/FONT]

and then just follow the rest of the instructions.  

------------------------------------------------------------------

By the way, how was your experience with Windows Vista and what drove you to get into Ubuntu?

---

### Post by f00had on 2008-09-16
Thank you very much, everything is working now :)

Vista is pretty good, although 2 programs (1 I use often, 1 is an old game I hardly play lol) don't work on it. I'm using Ubuntu now simply out of curiosity, if I like it I might make it my main OS.

---

