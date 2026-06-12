---
title: "Compatible Drivers For ATI X3870X2"
date: 2009-04-23
forum: Hardware
---

### Post by thebigschwag on 2009-04-23
greetings to yall....
Im new to ubuntu, and have a good question to ask...
I got the desktop version of 9.04 and love it so far
I tryed allot and even read up on sites but not a starit answer
some say this and some say that, even ATI says theyr work on ubuntu
anuways

I have a HIS Radeon x3870 X2 1GB GDDR3 - H387X2F1GNP

is this card compatible?
I rad some place saying no and some saying yes and *rolls eyes*
I tryed activating the driver, but after a reboot it crashed badly, leaving some vertical lines on the top

Full PC Spec
CPU: AMD Athlon 64 X2 6400+ / 3.2 GHz prosessor - Model: ADX6400CZWOF
MotherBoard: MSI K9A Platinum - hovedkort - ATX - 580X CrossFire
VidCard: HIS Radeon x3870 X2 1GB GDDR3 - Model: H387X2F1GNP
RAM: Corsair XMS2 Xtreme Performance TwinX  Matched - Model: TWIN2X2048-6400C4

I know the motherboard is CRAP... Im praying for my computer to die soon so I can buy new parts *grinz*

So what Im asking is...
is there a driver that would make my videocard fully work?
and if so, would you please wright a stupids guide how to do it? LOL I ot basic knowledge but aint that good yet


hope some can shine abit light on my situation
sorry for typos and whatnot
thanks
-tbs-

---

### Post by thebigschwag on 2009-04-25
guess I figured out how to build a package in the terminal....
but when it starts to install it asks me to incert the "Ubuntu 9.04_Jaunty Jakalope_-Release i386(20090420.1)
so I tryed burning the SAME iso I used and poped it into my cd rom, but it still asks me for it...
what have I done wrong?

I do hope someone that could help me

---

### Post by StuartN on 2009-04-25
> **thebigschwag said:**
> guess I figured out how to build a package in the terminal....

You should not have trouble with this card. It is listed as supported by the ATI Catalyst 9.4 driver and that should be automatically installed with Ubuntu 9.04.

See [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37) for more information about installation etc.

---

### Post by thebigschwag on 2009-09-08
call me a dunce...
been some time since I tryed bothering with ubuntu, since my videocard dont wanna be acepted and I have big dificultys trying to figure that videocard issue out.
Since activating the driver thats restricted frizzle my screen with wierd graphic buggs.

reason why I want to use ubuntu is pritty much that I only do office stuff and some chating and video and music, and ubuntu is nicer and faster than windows in my opinion.

but I would like to get the ATI driver fully operating in ubuntu, and if theres anyone here thats willing to lend me a hand in fixing my videocard issue I would be greatfull.

some of you say "go here and read" and give me a link to Ati's guide.
well I tryed it like 50 times now, and Im beginnig to feel  I reinstalled ubuntu more than windows >_<

I would like for some people that know what to do to give me a correct way of installing and activating the ATI drivers. like a step by step intructions.
Im gonna reinstall ubunu if theres some stuff I have messed up that will interfere with the correct way of doing this

Like
1:
2:
3:
4:
and so on.
yes I need it in with a spoon, Im not a total linux guru like most of you are.
but I do hope some will help me out here.


I have upgraded my pc since the last time, but still the same videocard...
MotherBoard: ASUS M4A79T Deluxe - hovedkort - ATX - AMD 790FX
CPU: AMD Black Edition AMD Phenom II X4 955 / 3.2 GHz Prosessor
RAM: Corsair XMS3 DHX minne - 4 GB ( 4 x 2 GB ) - DIMM 240-pin - DDR3
VideoCard: HIS Radeon HD 3870X2 - grafikkadapter - 2 GPU'er - Radeon HD 3870 - 1 GB

thanks...
-thebigschwag-

---

### Post by StuartN on 2009-09-08
> **thebigschwag said:**
> I would like to get the ATI driver fully operating in ubuntu

What do you mean by "fully operating"?

If the restricted driver does not work, then don't install it again, but what would it add anyway? If you want to install the older Radeon driver then use an older Ubuntu, like 8.10 or earlier.

---

### Post by thebigschwag on 2009-09-08
what I mean is that the videodriver isnt activated, if I do activate it ubuntu gets graphical issues, so I cant use most of the fancy desktop effects.
as I said, I would like help in fixing this issue with the graphical error I get when I activate the restricted ati driver

---

### Post by StuartN on 2009-09-09
It seems to me that you have a fully-functioning system, excluding a few pointless graphical effects that would not add to your system's functionality. If you really want to enable these then you could either a) buy a graphics card compatible with the latest fglrx driver, because yours appears to be incompatible, or b) install Ubuntu 8.10 and use the older fglrx driver that does support your current graphics card.

You will bang your head against a brick wall for a long time without any progress trying to force your existing card to be compatible. I have an unsupported card also and stayed with Ubuntu 8.10. When a release comes along with some significant enhancement then I might install it and use the open source drivers.

---

### Post by thebigschwag on 2009-09-09
WOOOOOT!!!
I got it to work, but now I got the FUGLY "unsuported hardware" watermark.
but atleast its working...
so nope StuartN I didnt bang my head, and I did make progress, I made my card work, got the watermark but thats ok for now unless someone knows how to remove it.
I banged my head more trying to install ubuntu 8.10 without any progress, LOL!

anywho...
if anyone would like the list, I post it...

01 - Applications -> Accsesories -> Terminal
02 - sudo apt-get install envyng-qt (not needed, but nice to chek the current ATI driver version and the new one, and to make shure it says a newer version after new driver is installed)
 03 - sudo aptitude install libc6
 04 - sudo apt-get update && sudo apt-get install xorg
 05 - sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot
 06 - sudo apt-get install xorg-driver-fglrx
 07 - sudo apt-get install ia32-libs
 08 - download the latest ATI driver at: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
09 - go to where you downloaded your ATI driver
10 - sudo sh ./ati-driver-installer-9-8-x86.x86_64.run --buildandinstallpkg Ubuntu/9.04
 11 - System -> Administration -> Hardware Drivers
 12 - Enable the restricted Ati driver
 13 - Reboot your computer
 14 - Enjoy

atleast it works, I dont know if I need ALL the first steps, but I iant trying my luck on retrying to install it AGAIN today, 3 times is enough for one day.
I see if I can get a new videocard at a later time.
I dont know if anyone know how to remove the unsuported hardware watermark, if anyone know please tell me

Thanks
-thebigschwag-

---

### Post by Helekryl on 2009-09-20
The official release note directly tells that even the most recent fglrx driver does not officially support 3870x2 (though producing some additional functionality). Probably they're not very enthusiastic about supporting the twin video adapters like this.

I also have Radeon 3870x2 and, after all possible driver upgrades and attempts to do smth, it is still recognized as a single 3870 chip and confirms the absence of full functionality in many other ways

The only good option is a possibility to remove the watermark through downloading the Intrepid release of xorg-driver-fglrx ([http://packages.ubuntu.com/intrepid/xorg-driver-fglrx](http://packages.ubuntu.com/intrepid/xorg-driver-fglrx)) and copying the "control" and "signature" from <unpacked folder>/data/etc/ati to /etc/ati over the existing ones.

---

### Post by thebigschwag on 2009-10-06
thanks for all the help...

seems the etc/ati is modification protected...
and I had little luck disabling that, after a few days...
no worries, in a few weeks or so a hardware shop where I buy my PC parts from will have the HIS version of the new ATI 5870.

---

