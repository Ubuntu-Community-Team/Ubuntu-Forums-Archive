---
title: "hardy heron x86_64; b43 not working on HP Pavilion dv6636nr"
date: 2008-04-28
forum: Hardware
---

### Post by makobu on 2008-04-28
Hello;
I have a HP Pavilion dv6636nr notebook on which i have installed Ubuntu Hardy Heron 8.04 x86_64 RC. My wiereless card however does not work. Here are the specifics;

$ lspci -- 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
$ lspci -n -- 03:00.0 0280: 14e4:4311 (rev 02)

i installed b43-fwcutter and rebooted. After loging in;

-> The b43 module was not leaded ($ lsmod | grep b43 yielded no results)
-> After manually loading it ($ sudo modprobe b43 ) the module apeared in the loaded modules list, but the light was still orange, but disturbing was that tail -f /var/log/messeges said nothing about the module being loaded, and nothing appeared on there when i slid the wiereless  switch on and off
--> dmesg has no mention of b43 either

---

### Post by tayroni on 2008-04-28
You can consider using ndiswrapper. It's a very better way to make your wireless work on linux

To do that: 

1 ) sudo apt-get install ndiswrapper-utils-1.9 ndisgtk zip unzip


2 ) Add the lines

blacklist b43
blacklist b43legacy
blacklist b44

to the very end of /etc/modprobe.d/blacklist

3 ) Reboot

4 ) Download windows driver of your board

[http://ftp.us.dell.com/network/R151517.EXE]("http://ftp.us.dell.com/network/R151517.EXE")

5 ) Unzip it

unzip -a R151517.EXE

and type these commands ON DIRECTORY THAT CONTAINS bcmwl5.inf

sudo ndiswrapper -i <driver>.inf
sudo ndiswrapper -l

You should see "Driver installed, Hardware present"

6 ) Load driver during boot

Type now

sudo ndiswrapper -ma

and add the lines

ndiswrapper
ssb

to the end of /etc/modules.

7 ) Create new file /etc/init.d/ndiswrapper

sudo gedit /etc/init.d/ndiswrapper

with these lines

#/bin/bash

rmmod ohci-hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci-hcd

save, exit and type on console

sudo chmod a+x /etc/init.d/ndiswrapper
sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper

8 ) Reboot

---

### Post by makobu on 2008-05-02
This worked perfectly!

---

### Post by umlauf on 2008-05-03
I have a HP Pavillion dv6258se and it worked for me too on Hardy x86. Thanks a lot, tayroni!

---

### Post by Celso Marques on 2008-05-09
Hi guys!
This tip works fine for me too!!:popcorn:

Thanks a lot!

HP Pavilion DV6625us AMD 64 X2 TL-58 1.9Ghz + Broadcom BCM94311MCG

---

