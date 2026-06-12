---
title: "Toshiba Satellite A205-S5841"
date: 2008-05-06
forum: Hardware
---

### Post by chocobo333 on 2008-05-06
Hi All,

I'm an Ubuntu newbie but have managed installing Ubuntu 8 (Hardy) on my AMD64 Desktop PC by reading these forums. They're very helpful by the way. 

I just want to find out if any of you have experienced installing Ubuntu on a Toshiba Satellite A205-S5841 or any Toshiba Satellite for that matter? Were there any hardware problems after installing? Did everything work? touchpad, WiFi, Audio, Video etc.?

I have a laptop (Toshiba Satellite A205-S5841) coming soon with Vista installed on in and I want to replace it with Ubuntu.

Hoping for your advice. 

Thanks in advance. Much appreciated!


Chocobo333

---

### Post by Tryfon on 2008-05-06
I've got a Satellite A100-003 and everything worked flawlessly from the first moment, except the bluetooth.
I don't know what's same and what's different in our hardware configuration, but judging from my experience you'll love Ubuntu!

---

### Post by chocobo333 on 2008-05-06
> **Tryfon said:**
> I've got a Satellite A100-003 and everything worked flawlessly from the first moment, except the bluetooth.
I don't know what's same and what's different in our hardware configuration, but judging from my experience you'll love Ubuntu!

Wow! Great! Sounds promising then. :) You're right. I loved Ubuntu the first time it demoed on my desktop. Astounded that everything ran right from the CD and installed perfectly! Can't wait to install Ubuntu on my laptop.  It'll be delivered on Monday. Did you get your bluetooth to work properly though? Searching for a repo for drivers if available. Anyway. :) Thanks! Cheers!

---

### Post by roverton on 2008-05-15
I recently installed Kubuntu 8.04 KDE4 Remix (hardy) on this exact model.  This is the info I dropped into the linux laptop wiki as well.  It took me about 8 hours of searching/configuring post install to get pretty much everything functional but this should cut out the most of it (the awful searching ;)...

Recently installed Kubuntu 8.04 Hardy with KDE4 and there were really only two things I needed to get things up and running on my A205-S5841.

Kernel Version: 2.6.24-16

In order to get the wireless up I had to install a patched version of the madwifi modules (the default tree doesn't support the card, Atheros AR2425) found at
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) (prepatched release source)
reference:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Be sure that the packages build-essential and kernel-headers are installed.
$ tar -xzvf madwifi-nr-r3366+ar5007.tar.gz
$ cd madwifi-nr-r3366+ar5007
$ make
$ sudo make install

edit the file /etc/modules and add:
ath_pci

reboot or modprobe, etc.

Second was the sound. ALSA was installed, version 1.0.16 and sound worked fine except for when the system came up from suspend/hibernate. To fix that...

edit /etc/modprobe.d/alsa-base (as root)
add the line: options snd-hda-intel model=toshiba

Intel graphics worked great right out of the box.

---

### Post by chocobo333 on 2008-05-29
> **roverton said:**
> I recently installed Kubuntu 8.04 KDE4 Remix (hardy) on this exact model.  This is the info I dropped into the linux laptop wiki as well.  It took me about 8 hours of searching/configuring post install to get pretty much everything functional but this should cut out the most of it (the awful searching ;)...

Recently installed Kubuntu 8.04 Hardy with KDE4 and there were really only two things I needed to get things up and running on my A205-S5841.

Kernel Version: 2.6.24-16

In order to get the wireless up I had to install a patched version of the madwifi modules (the default tree doesn't support the card, Atheros AR2425) found at
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) (prepatched release source)
reference:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Be sure that the packages build-essential and kernel-headers are installed.
$ tar -xzvf madwifi-nr-r3366+ar5007.tar.gz
$ cd madwifi-nr-r3366+ar5007
$ make
$ sudo make install

edit the file /etc/modules and add:
ath_pci

reboot or modprobe, etc.

Second was the sound. ALSA was installed, version 1.0.16 and sound worked fine except for when the system came up from suspend/hibernate. To fix that...

edit /etc/modprobe.d/alsa-base (as root)
add the line: options snd-hda-intel model=toshiba

Intel graphics worked great right out of the box.

Sorry for the late reply, been busy at work. I've installed Ubuntu 8 Hardy on my Toshiba Satellite A205-S5841. I had trouble installing Atheros WiFi. Luckily I had drivers for my Speedtouch 330 modem and got my internet going on my laptop and installed madwifi modules as you (roverton) did. It's all good now. :)

---

