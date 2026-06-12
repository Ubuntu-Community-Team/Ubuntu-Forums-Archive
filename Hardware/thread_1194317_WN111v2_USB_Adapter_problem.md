---
title: "WN111v2 USB Adapter problem"
date: 2009-06-22
forum: Hardware
---

### Post by Eduardoo on 2009-06-22
Hi!
I'm new to Ubuntu and since I've installed it I faced some problems, but i managed to solve them, except one: I can't use the  wn111v2 usb adapter. Since i'm a noob, i tried to install the software that came in a cd, by using wine, wich, of course, didn't result. Then, i googled the problem and find several artciles about a "Otus driver" and other ways to use this adapter if, but i don't know how to use it... I only have Ubuntu for a couple of days and i'm very happy with it, but if i can't use the adapter i will have to return to windows...
If could help me, i would be extremely grateful :)

---

### Post by john stiles on 2009-07-15
Hi,

I hope you have managed to get online since you posted. I've just managed to install my WN111 v2 so here's sharing. You need to install the ar9170 linux native driver ref:

[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

In summary:

sudo rm -r /etc/ndiswrapper/*
sudo modprobe -rf ndiswrapper

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz](http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz)
md5sum Compat-Wireless_ar9170_230209.tar.gz

tar xvf Compat-Wireless_ar9170_230209.tar.gz
cd compat-wireless-2009-02-22_AR9170_230209

make
sudo make uninstall
sudo make install

sudo cp ar9170-*.fw /lib/firmware

Reboot. Jaunty automatically adds to network manager applet.
NB. I have backports installed as well but am unsure if this is necessary.

---

### Post by singhs on 2009-07-26
I just install Ubuntu 9.04 today. I was using WN111v2 withi windows and working just find but unable to use the adapter after Ubuntu installation.I am not a computer programmer or expert but have used Ubuntu that was previously indtalled by others. Can you give me step by step on how to install the driver. Do I have to connect wiredly tointernet to follow the instruction?
Thanks

---

### Post by john stiles on 2009-07-29
Yes you require a wired connection to complete the downloads in the instructions. You will need to open a terminal window (application>accessories>terminal) and cut and paste the commands I gave into it.

Reboot and you should have a connection, but not secure. try this command to confirm:

iwconfig wlan0

To enable WPA2 there are excellent instructions here:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

That should result in a working WN111v2 using WPA2, it did for me 

The module and compat wireless instructions link was in German! but there is an official page here.

[http://wireless.kernel.org/en/users/Drivers/ar9170](http://wireless.kernel.org/en/users/Drivers/ar9170)

It details an alternative install, but the one I gave at top actually worked for me.

Good luck

---

### Post by wistrand on 2009-08-02
I also have the exact same problem! Iv'e tried entering the code you suggested but when i rebooted my PC i still couldn't connect to my network.

I also tried using WINE to open the autorun.exe file on my Netgear software-disc. Was a dance on roses 'til the hardware-installation popped up. I got the errormessage "The installation of the client software has failed. Please restart the computer and run the installer again." Even though i also tried that, it didn't work out.

If anyone could help me solve this VERY annoying issue i'd be ******* pooped cuz if this doesn't work out i'll have to go back to windows again! :(

Thanks
Nick

---

