---
title: "Need help with Gateway laptop"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by jrobbins88 on 2007-04-24
Recently I bought a gateway laptop, but loathed Windows Vista, so I decided to switch to Ubuntu; but silly me, I didn't dual boot it and transfer all the hardware and support over to Ubuntu.

The model number is ML3706, or .. W340UI. I don't know which is the correct one, since there are two labels omn the bottom of the laptop.

I like the interface of Ubuntu, and all I really want from my laptop is to go online and do some writing with a word processor or something.

All I really want is my internal wireless to work, as well as my sound. Then I'm good!

Any help would be greatly appreciated!

---

### Post by jrobbins88 on 2007-04-24
Bump ..

---

### Post by deeproot on 2007-04-24
It looks like you are using this wifi card:

6008015R - Integrated 802.11/g WLAN (FRU)
GemTek Specifications
106971, 6008015R
Manufacturer Gemtek
Model BCM4318E 11G WMIB-158G21A20 USA
Features BroadRange technology
Form Factor Type IIIB MiniPCI
Host interface 32-bit miniPCI

Manufacturer Lite On
Model WN2300L
Chipset Realtek RTL 8185L
RF Realtek RTL 8225
Standard IEEE802.11b, IEEE802.11g, IEEE802.11i
Bus Interface MiniPCI Card,Type 3 B


Does fiesty say its using any restricted drivers when you get into gnome? If so which ones?
Try opening a terminal and typing "sudo lspci" and what it shows.
and maybe "iwconfig"

You can always try [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

I'm no pro but I wanna try to help

Deeproot

---

### Post by jrobbins88 on 2007-04-24
I don't really know much of anything. 

I have the ubuntu-6.06.1-desktop-i386.iso installed on my laptop, but it just boots up, and pretty much .. that's it.

I'm not sure if it's the Feisty version or not, but it's not detecting any of my internal hardware, i.e: sound driver, wifi driver, etc.

I'll try what you suggested, but more help would be greatly appreciated. :)

And yes, it says it's using restricted hardware ..

---

### Post by andrew_howlett on 2007-04-24
Jr:

Use the forum search function for gateway wireless, you will find many entries, for instance:

[http://ubuntuforums.org/showthread.php?t=210958&page=4](http://ubuntuforums.org/showthread.php?t=210958&page=4)

andrew.

---

### Post by deeproot on 2007-04-24
if you are running 6.06 then you are running a pretty old version of Ubuntu.  Laptop hardware has become more easily detected and used with newer versions of Ubuntu. I would recommend getting the newest version, Feisty Fawn 7.04, and installing that. Chances are most if not all of your devices will just work out of the box.  I have a gateway also and with 7.04 all my devices worked by default.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

get desktop edition 7.04 for standard personal computer.

And from there we can start fresh with current software

Deep

---

### Post by dracflamloc on 2007-05-06
Just an FYI this laptop still doesnt get sound or wireless with 7.04. I'm stuck

---

### Post by rkrisher on 2007-10-16
Your motherboard should be the same as my gateway MT3705.  Check on the label under the RAM for a part# 40GAB1230-C200.  Try the below link where I posted instructions for the wireless and sound.

[http://ubuntuforums.org/showthread.php?p=3524207](http://ubuntuforums.org/showthread.php?p=3524207)

Ubuntu and Debian are related so the steps should still be the same.

---

