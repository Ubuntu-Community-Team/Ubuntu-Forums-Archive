---
title: "Plz need Help with my graphics Drivers(or Direct X)"
date: 2011-02-16
forum: Hardware
---

### Post by A_Gamer on 2011-02-16
Firstly, I would like to kiss the foreheads of the makers and developers of this fantabulous OS, but since I'm a newbie to this OS,  I will need some of ur help along the way...

This OS has revived two of my brothers' dead Windows XP-based Intel Classmates.

Secondly, I installed (light)ubuntu 10.04 on two of my brothers' Intel classmate since support from Intel is dead and unusable...
Anyways is there any way to install and use direct X 9.0 on them?
I installed crossover since I can't seem to get wine to install on google chrome???
CS 1.6 is slow as hell because it's using open GL which is very slow and unsupported on the GMA 915 built-in graphics chip...

Both of them are fully operational and gaming capable( I tested CS 1.6 on XP and had 25 fps+) doesn't sound like much, but this is great for it's specs:
Intel Celeron M 900 Mhz codenamed "Little Endian"
Intel 82801FB\ICH6M Chipset
Intel GMA 915 Integrated 8 MB shared Memory!(I also need a driver for this,pls)
Intel Value NAND SSD 2GB (as a HDD)
Max Resolution: 800x480...

Plz I'm in dire need of help! 
Thanks in advance...

---

### Post by clhsharky on 2011-02-16
A_Gamer

Welcome to UF.

Ubuntu is not a free windows. 
Ubuntu is also a modern OS with compositing unlike legacy XP, comparison ?
> Anyways is there any way to install and use direct X 9.0 on them?
direct X belongs to Windows

Window games is best played in windows.
Of course Id never go on Internet with Windows.


Sharky

---

### Post by A_Gamer on 2011-02-16
> **clhsharky said:**
> A_Gamer

Welcome to UF.

Ubuntu is not a free windows. 
Ubuntu is also a modern OS with compositing unlike legacy XP, comparison ?

direct X belongs to Windows

Window games is best played in windows.
Of course Id never go on Internet with Windows.


Sharky

Well, here's ur answer:
[http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)
And secondly, I CANNOT, and I repeat I CANNOT install any windows version(s) on them!

---

### Post by A_Gamer on 2011-02-17
Bump :(

---

### Post by A_Gamer on 2011-02-17
Plz I need urgent help on this; Direct X games doesn't want to work and open gl is too slow for this chipset...
I don't know how to compile the Intel drivers and can somebody do it for me plz(or at least help me install it)
I have only around 70 MB of free HDD space, so I cannot install any large packages(running lubuntu 10.04)
Extra info:
Most of the packages aren't installed in the software manager
I have wine already installed
glxgears report 290 FPS on 800x480

ANY KIND HELP would be appreciated; thanks!

---

### Post by eriktheblu on 2011-02-17
> **A_Gamer said:**
> Firstly, I would like to kiss the foreheads of the makers and developers of this fantabulous OSThat's a lot of foreheads

> I installed crossover since I can't seem to get wine to install on google chrome???
Very confused. Are you trying to 
A: Run Chrome on Ubuntu using Wine
B: Download Wine using Chrome and install Wine on Ubuntu or
C: Trying to install Wine on Chrome OS

For A, use the Linux native Chrome rather than the Windows version. For B, Wine is available in the software center. C, I don't think is practical or desirable.

> CS 1.6 is slow as hell because it's using open GL which is very slow and unsupported on the GMA 915 built-in graphics chip...You're trying to run a kerosene through a gasoline engine. Even if you get it to work, the results won't be perfect. There are open alternatives to CS (assuming you mean Adobe) available; I suggest you consider those.

---

### Post by A_Gamer on 2011-02-17
> **eriktheblu said:**
> That's a lot of foreheads


Very confused. Are you trying to 
A: Run Chrome on Ubuntu using Wine
B: Download Wine using Chrome and install Wine on Ubuntu or
C: Trying to install Wine on Chrome OS

For A, use the Linux native Chrome rather than the Windows version. For B, Wine is available in the software center. C, I don't think is practical or desirable.

You're trying to run a kerosene through a gasoline engine. Even if you get it to work, the results won't be perfect. There are open alternatives to CS (assuming you mean Adobe) available; I suggest you consider those.

hhhhhhhhh
No I meant that I wanted to play Counter Strike 1.6(not CS 1.6)
Or to improve it's performance, cuz Opengl produces -15 FPS, and Direct X produces 25+ FPS(Tried on XP before it was heavily abused by viruses)
I'm running lubuntu 10.04 with a lot of packages missing to save space, but I installed Wine & Mesa GL utilites( Warning: 75 MB of free SSD space left)
I just want to play Direct X games on ubuntu, because I can't get Windows to install(tried Windows 98 SE-Windows 2000-Windows XP & XP lite-Windows Embedded standard 7-Windows 7 lite-Windows Vista lite), ut with no avail :(

---

### Post by sydbat on 2011-02-17
> **A_Gamer said:**
> Well, here's ur answer:
[http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)
And secondly, I CANNOT, and I repeat I CANNOT install any windows version(s) on them!WOW! A link to a Russian site that has a "download" from Mediafire for a 'nowhere-near-official' DirectX installer.

Let me tell you a couple of things:

1) In order to do anything this site states, you have to have "their" version of WINE installed, which brings us to...

2) **THIS IS A SITE THAT WILL (most likely) INSTALL MALWARE ON YOUR COMPUTER!** Sure, it can only do damage to whatever WINE **THEY** want you to install, but I imagine that it has other tricks up its sleeve.

If you are so sure you can run games on the hardware you mention in your OP, then either get a legit version of WinXP to perform a re-install, or use the OFFICIAL repositories to download applications in Ubuntu. 

As mentioned by clhsharky, this is not a free version of Windows. You DO NOT go searching the Internet for applications to install.

Now, if you want more information about WINE, visit these 2 links...

[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by A_Gamer on 2011-02-17
> **sydbat said:**
> WOW! A link to a Russian site that has a "download" from Mediafire for a 'nowhere-near-official' DirectX installer.

Let me tell you a couple of things:

1) In order to do anything this site states, you have to have "their" version of WINE installed, which brings us to...

2) **THIS IS A SITE THAT WILL (most likely) INSTALL MALWARE ON YOUR COMPUTER!** Sure, it can only do damage to whatever WINE **THEY** want you to install, but I imagine that it has other tricks up its sleeve.

If you are so sure you can run games on the hardware you mention in your OP, then either get a legit version of WinXP to perform a re-install, or use the OFFICIAL repositories to download applications in Ubuntu. 

As mentioned by clhsharky, this is not a free version of Windows. You DO NOT go searching the Internet for applications to install.

Now, if you want more information about WINE, visit these 2 links...

[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Well, thank u; instead of wasting my time with these bastards...
I cannot install any windows cuz the internal Storage drive is an Intel Value NAND SSD connected through a USB port somehow!!?
Anyways, I will try to install winetricks(how does it work?,oh well, I guess I will try)....
I just want to play Direct x Games, and when I try to open Age of Empires 2, It shows an error related to direct draw...

---

### Post by Stephann on 2011-02-17
Hiya A_Gamer,

Pretty much what they said.  You say you 'can't' install Windows on the computer; why not?  It sounds like it's a laptop (given the graphics chipset you mention); if you flip it upside down, is there a sticker with a windows code?  If so, you're in business.  Install windows, and play windows games on it.  If not?  You can probably buy a (legit) windows XP powered computer at a garage sale or on craigslist for $50, and transfer that license over (or simply use that machine.)

---

### Post by Stephann on 2011-02-17
> **A_Gamer said:**
> Well, thank u; instead of wasting my time with these bastards...
I cannot install any windows cuz the internal Storage drive is an Intel Value NAND SSD connected through a USB port somehow!!?
Anyways, I will try to install winetricks(how does it work?,oh well, I guess I will try)....
I just want to play Direct x Games, and when I try to open Age of Empires 2, It shows an error related to direct draw...

I see you replied, before I posted.  I don't have any experience with that  particular machine.  Frankly, it sounds like you're trying to use it for  a purpose it's not really intended; it'd be like hacking a Linksys  router and trying to play quake on it.  Novel, but not really useful.  I  stand behind the $50 machine advice; older games will run nicely on a gigahertz processor machine, something you can find for very low cost.

---

### Post by A_Gamer on 2011-02-17
> **Stephann said:**
> I see you replied, before I posted.  I don't have any experience with that  particular machine.  Frankly, it sounds like you're trying to use it for  a purpose it's not really intended; it'd be like hacking a Linksys  router and trying to play quake on it.  Novel, but not really useful.  I  stand behind the $50 machine advice; older games will run nicely on a gigahertz processor machine, something you can find for very low cost.

Sorry guys; I'm really on a tight budget here and I'm in debt...
I just need a way to play these games that's it..
There is a way and I know it, the only problem is that I don't know how to(Btw, I installed wine tricks and wine itself, now what?)

One more thing; I cleaned the temporary "cache"(if that's what u  guys call it) with the sudo apt-get clean command(It worked but I need more space cuz I installed Google chrome)...

---

