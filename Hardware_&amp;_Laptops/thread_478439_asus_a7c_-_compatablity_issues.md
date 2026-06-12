---
title: "asus a7c - compatablity issues"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by viruzeno on 2007-06-19
**This post could be related to an Ubuntu bug filed at**: [https://wiki.ubuntu.com/A7Jc](https://wiki.ubuntu.com/A7Jc) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The install cd boots, fine then dumps out with an error "cant find screen attatched".

the laptops specs are:

CPU: Intel core2duo T5600 (1.83)
LCD: 17" WXGA+
LAN: Realtek RTL818/8111 Gigabit NIC (NDIS 6.0)
WLAN: Intel 3945ABG
VIDEO: ATI MOBILITY RADEON X1450

EXTRAS:-
CARD READER: RICOH
TV CARD: AVERMEDIA M10D MINIPCI HYBRID DVBT
WEB CAM: UNKNOWN (but it's a 1.3mp if that helps)

i mainly want to know if i can install unbuntu as i love it, but i made the move to a laptop and i cant stand windows vista's memory consumption and general crap'nes. if you need any more infomation please let me know, i am good with computers but not with hardware drivers etc... (i only know how to use them for basic programing, games, and other noob activitys)

thanking you in advance for any help you can offer.

---

### Post by viruzeno on 2007-06-20
ok i am able to start to install ubuntu with the altanate CD, however it it freezing while trying to install "vwdial". i am going to try turning off my modem in the BIOS, other then that i think that it may install, (minus the dirvers i assume)

---

### Post by viruzeno on 2007-06-22
i have solved the issue, 

to install ubuntu you need to download the alternate disk, then choose the advanced booting options.

you will need to add 

```
boot: install vga=771 noapic nolapic
```

to the end of the install path, then once you have loaded, you need to run the following to get the ATI drivers working

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

then reboot and you should have graphics, now you can install all the other drivers, oh yay.

---

### Post by Dmit on 2007-07-23
Thank you very much for the hint! Although I'm having one more strange problem: my Realtek ethernet adapter is detected, but not working. 

The notebook model and hardware is exactly as yours, the system detects RTL8111/8169B chip at boot stage, but it does not even recognize if the cable is plugged in or not (always showing something like eth0 link is down).

Did you ever had such a problem with your installation?

---

### Post by Cappy on 2007-07-23
Hi, please don't use "vga=771", use "nosplash" instead. Otherwise you get a crash when you shutdown Ubuntu.

---

### Post by Dmit on 2007-07-23
I used vga=711 option when booting from alternate install CD and the installation went OK. Now I have Ubuntu installed, it shows splash correctly, but I can't proceed any further, because my realtek ethernet card does not recognize ethernet media. I have tried several different cables and different switches with no success at all. Windows works fine.

---

### Post by Cappy on 2007-07-23
Unless you screen shuts off (or gives frequency out of range) you don't need the "vga=771" or "nosplash" at all, you just need the "noapic nolapic" part, and that works on the normal Live CD also.

Ethernet:
[http://ubuntuforums.org/showthread.php?t=500924](http://ubuntuforums.org/showthread.php?t=500924)
Will be the solution as long as you didn't uninstall Windows. If that doesn't help try searching on "RTL8111" on the forums from the main page.

---

### Post by Dmit on 2007-07-23
Thank you very much!

I realized, what actually the problem was. The option "wake-on-lan" is enabled on my system, but I usually switch between OS'es by doing hybernate, not complete shutdown. So the "wake-on-lan" switch simply does not work when hybernating. After full Vistal shutdown it worked fine under linux.

Anyway, how stupid it was... Thanx!!

---

### Post by danap on 2008-01-28
Hello,

I have the same laptop...

Configuring the webcam: Syntek DC-1125  -  "174f:a311"

  Before start the installation, install the linux-header-XXXXXXXX, gcc and camorama, gqcam, VLC or another software.

           wget [http://ufpr.dl.sourceforge.net/sourceforge/syntekdriver/stk11xx-1.2.3.tar.gz](http://ufpr.dl.sourceforge.net/sourceforge/syntekdriver/stk11xx-1.2.3.tar.gz)

           tar -xzvf stk11xx-1.2.3.tar.gz

           cd stk11xx-1.2.3

           wget [http://bookeldor-net.info/merdier/Makefile-syntekdriver](http://bookeldor-net.info/merdier/Makefile-syntekdriver)

           make -f Makefile-syntekdriver

           sudo make -f Makefile-syntekdriver install

           sudo modprobe stk11xx

---

