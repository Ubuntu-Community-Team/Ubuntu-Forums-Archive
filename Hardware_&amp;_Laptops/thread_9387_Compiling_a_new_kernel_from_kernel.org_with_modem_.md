---
title: "Compiling a new kernel from kernel.org with modem patch."
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by charleyramm on 2004-12-28
I have a USB adsl modem, which does not work with ubunutu. I believe i have found a kernel patch that would let me use it, but the patch only applies to the Mandrake 10 kernel, or the standard kernel.org kernel.
 What i intend to do first, is compile a normal kernel.org kernel for my machine and make sure it all works ok. After which, i will try to add the adsl modem stuff. 

This is the information I have found so far. 
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=186990](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=186990)

My modem is labeled as a Vitelcom product, and the logo of my ISP, STA is printed on the top. The ubuntu device manager shows it as a conexant modem. I will get more details on it soon. Right now it is plugged in to a windows xp machine, so that i can connect to the internet. 

 I hope that if i can get this to work, the information here will be of use to other people who are having trouble with this modem.  Wish me luck!

This is what mine looks like.  (excuse my mess!:D)
[http://charleyramm.no-ip.org/dsci0175.jpg](http://charleyramm.no-ip.org/dsci0175.jpg)
Server seems borked. Will fix this soon. 

 from lsusb
Vendor id is 0x0572
Product id is 0xcb00

---

### Post by charleyramm on 2004-12-28
The things i have determined i must do.

Get linux-2.6.6 sources and unzip
#wget [http://kernel.org/pub/](http://kernel.org/pub/) whatever
#tar -xjf linux-2.6.6.tar.bz
#cd linux-2.6.6


Get and apply patch for conexant access runner adsl stuff
#wget [http://www.zullinux.it/linux/patch-2.6.6_20040517_accessrunner.gz](http://www.zullinux.it/linux/patch-2.6.6_20040517_accessrunner.gz)
#gunzip -c parch-2.6.6_20040517_accessrunner.gz | patch -p1


Build and install kernel as usual 
(Any bets on how long this takes with a 266 pentiumII?)

Find out how I setup an adsl connection with linux, when everything is functioning as it should.
How do i tell when everything is functioning as it should be?

---

### Post by charleyramm on 2004-12-28
I am going to try patching the standard ubuntu kernel, There was a change to speedtch.c around version 2.6.9 of the kernel.org version, but i think the speedtch.c of 2.6.8.1 is the same as 2.6.6.
 The Debian.src.changelog shows no changes to speedtch.c either.  I am just waiting for it to compile now. Hopefully it will be done by morning. 

This is my current list of tasks i've worked out:

```

>sudo apt-get install essential-build-tools
>sudo apt-get install linux-source-2.6.8.1
>sudo apt-get install ncurses5-dev

>mkdir /home/you/build
>cd /home/you/build

>wget http://www.zullinux.it/linux/patch-2.6.6_20040517_accessrunner.gz

>tar -xjf /usr/src/linux-source-2.6.8.1.tar.bz2
>cd linux-source-2.6.8.1

>gunzip -c /home/you/build/patch-2.6.6_20040517_accessrunner.gz | patch -p1

>make menuconfig 
then set the following options like this (M is for module)

1) Go to the section  Device Driver -> Networking Support -> Networking Options -> ....

    <M> Asynchronous Transfer Mode (ATM) (EXPERIMENTAL)
    <M> Classical IP over ATM (EXPERIMENTAL)
    [*] Do NOT send ICMP if no neighbour (EXPERIMENTAL)
    <M> LAN Emulation (LANE) support (EXPERIMENTAL)
    <M> Multi-Protocol Over ATM (MPOA) support (EXPERIMENTAL)
    <M> RFC1483/2684 Bridged protocols
    [*] Per-VC IP filter kludge


2) Then Go to section  Device Driver -> USB Support ->
    <M> Support for USB
    <M> Alcatel Speedtouch USB support (NEW) (near the bottom)

Save and exit menuconfig.

#make  

go cure the common cold or something

#sudo make install

Find out what make install has done.  The new kernel should be in /boot. You probably need to add the new kernel to my /boot/grub/menu.lst Make a new menu entry for the new kernel, so you dont get stuck with an unbootable system. 

```

---

### Post by Johnny Ears on 2005-01-06
Hi, I've got an Alcatel speedtouch usb modem & it does not work either..  however I'm a newbie (as I'm sure are others) & whilst the stuff you've written looks lovely... i don't understand what i need to do.. could someone be kind enough to write me a speedtouch for noobs help page? 

Many thanks guys

---

