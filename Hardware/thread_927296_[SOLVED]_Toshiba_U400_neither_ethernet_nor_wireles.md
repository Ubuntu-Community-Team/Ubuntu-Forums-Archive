---
title: "[SOLVED] Toshiba U400 neither ethernet nor wireless networking"
date: 2008-09-22
forum: Hardware
---

### Post by ubuntergeist on 2008-09-22
hello,

I've recently bought a Toshiba u400 :
Core 2 duo 1.86 Ghz
2 GB RAM
200 GB HDD
Marvel Yukon 88E8040 ethernet controller
Atheros AR9281 wireless controller

Everything works perfectly with the exception of the ;ost important part : Networking. I have no network connection at all, the network manager only displays ppp connection (my v92 modem seems to have been detected)
I think that my ethernet and wireless controllers are supported by Ubuntu Hardy (I installed version 8.04.1).
I was told there was a bug in some drivers that causes a hardware conflict, there's a solution on the internet but it requires installing kernel source packages, modifying a source file and recompiling a Ubuntu kernel, as I don't have access to the internet I can't apply it.

can someone please tell me how I could carry out the process using another PC or using windows (download the necessary packages in once then transfer them on my pc to apply the procedure)
My pc works under vista 64 (I have Virtualbox on it with Hardy installed) but it's helluva an OS, Ubuntu is way more powerful and runs much more smoothly even with my live USB.

thank you,

---

### Post by dAF2000 on 2008-09-23
My Toshiba U400-136 worked (lan and wireless) when I installed the latest 8.10 alpha. Couldn't get it working with 8.04 either.

---

### Post by ubuntergeist on 2008-09-23
> **dAF2000 said:**
> My Toshiba U400-136 worked (lan and wireless) when I installed the latest 8.10 alpha. Couldn't get it working with 8.04 either.

I need a secure and stable OS. Intrepid is still in alpha stage.

I'm going to try Linux Mint (they provide proprietary drivers, may be it'll work) but to tell the truth I don't like their environment and their tools very much, I ant to stick to ubuntu. Is it possible to install Ubuntu Gnome on Mint after removing all desktop environments ? I mean via command line apt.

thank you,

---

### Post by estamand on 2008-09-23
The U400 (according to specs) have a Marvell Yukon network card.  Did you use the 8.04.1 installer by chance?

As for the wireless try this (Found on Toshiba linux website [http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm](http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm))

 	

sudo modprobe -r iwl4965

cd /etc/modprobe.d/
touch iwl4965
edit iwl4965

In the file enter the following
alias wlan0  iwl4965
options  iwl4965 disable_hw_scan=1

modprobe  iwl4965
ifconfig wlan0 up

---

### Post by ubuntergeist on 2008-09-23
> **estamand said:**
> The U400 (according to specs) have a Marvell Yukon network card.  Did you use the 8.04.1 installer by chance?

As for the wireless try this (Found on Toshiba linux website [http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm](http://linux.toshiba-dme.co.jp/linux/eng/installinfo.htm))

 	

sudo modprobe -r iwl4965

cd /etc/modprobe.d/
touch iwl4965
edit iwl4965

In the file enter the following
alias wlan0  iwl4965
options  iwl4965 disable_hw_scan=1

modprobe  iwl4965
ifconfig wlan0 up


Yes I'm using Hardy 8.04.1 actually I just picked up the latest stable version. Why ? is there a bug in this one ?

Thanks a lot for your help, I'm trying this right now to see if it works.

---

### Post by estamand on 2008-09-23
I remember there being a bug with 8.04 initial release where a NIC driver (either Realtek or Mavell) was causing the system to hang on boot.  But that was resolved with 8.04.1.

---

### Post by ubuntergeist on 2008-09-23
hi,
Estamand I've tried your solution but it didn't work. The system doesn't look to detect my network and wireless chips.
I've attached two files containing lspci and lsmod output if somebody could take a look at them.

BTW, I've also tried Linux Mint but it didn't work either.

I bought this laptop specifically because on [http://www.linux-laptop.net](http://www.linux-laptop.net) they said it is mostly ubuntu compatible with only a few issues concerning hardware (bluetooth that needs to be worked out).

I am disappointed on two counts : I can't run my favorite distro properly and the proprietary system is one of the worst I've ever used (Vista64 is unstable, buggy and miserably slow).

If I have to do some command line stuff, could someone please tell me how I could download Debian packages (namely Kernel-source and its dependencies like gcc & libs) without having ubuntu (or maybe from a virtual machine running ubuntu) so that I can install madwifi source driver or at least use NDIS Wrapper ?

thanks a lot.

---

### Post by estamand on 2008-09-23
I made a mistake.  You don't have an Intel Wireless card.  Your computer has a Atheros Wireless card.  I found this: [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

It might help you.

---

### Post by ubuntergeist on 2008-09-23
> **estamand said:**
> I made a mistake.  You don't have an Intel Wireless card.  Your computer has a Atheros Wireless card.  I found this: [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

It might help you.

Actually I had a little doubt when I read the module name but I continued anyway.

Thanks again, I have installed the script on a Virtualbox-run ubuntu system and got the deb package but I don't know how it will fare on a natively-run system.

Hopefully it will work.

---

### Post by ubuntergeist on 2008-09-23
I have finally solved the problem (at least for wireless networking). I have used the solution suggested in this [thread]("http://ubuntuforums.org/showthread.php?t=874097").
I have just downloaded and run the script in a virtualbox-run ubuntu system, saved the deb package output then installed it on the natively-run ubuntu system (a usb keypen). I had to use modprobe to load the module to avoid rebooting the system and I got my connection.

Thanks a lot to all of you who helped me.

bye

---

