---
title: "Instaling ASrock drivers in Xp then dualbooting Ubuntu"
date: 2011-11-14
forum: Hardware
---

### Post by mace200200 on 2011-11-14
So I'd like to build a computer running ubuntu and using the ASRock A55 PRO3 motherboard (it's a fm1 socket amd apu board link on bottom). The only problem is that I looked at their website and it appears that none of the drivers have linux support. What i was thinking I could do was install Windows XP 32bit from a disc i already have and haven't even opened yet and install all the drivers for the motherboard, and then I could install ubuntu 64bit side by side with that xp installation. 

Now i have two questions:
1. Will this work, after i install the drivers for the motherboard in XP when i boot into ubuntu will the motherboard sound and video drivers be there and will they all work right?

-and
2. Since all i have is a windows xp 32 bit disc will i be able to install ubuntu 64bit along side it becuase i would like to run more than 4 gigs of RAM. 

Oh yeah and I've never done a dual boot before but from what I've read on the site is that you can make them share disc space which is what I'm thinking I would want and need to do to make the drivers work for both operating systems.

Motherboard Link:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157278](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157278)



Thx for taking the time to read my long questions and for any help you can give me :D

---

### Post by BillyBoa on 2011-11-14
Let's see now.

1. Using win xp 32b you will not use all of the 4G of RAM for the windows part.

2. The motherboard drivers are already included on the Linux kernel so don't worry about them.

3. The 2 new computers will have -Windows and Linux- they don't have any connection between them. Only from Ubuntu you will have access to your files in Windows side. Nothing more.

4. The drivers in each side should installed separately. In win part you have to download them from your brand site and install them manually. From Ubuntu apart from some video card and wireless drivers, everything is included to the kernel so you have nothing to add. When you first boot to Ubuntu, an application is going to ask you to download and install if any driver is missing.

---

### Post by mace200200 on 2011-11-14
[QUOTE=BillyBoa;11456968]Let's see now.

2. The motherboard drivers are already included on the Linux kernel so don't worry about them.


So I don't need to install anything for the motherboard at all and it'll just work right out of the box? Because I probably won't set up a dual boot if i don't have to I just want the motherboard drivers to all work out. Plus after i posted this I decided to find my old 32 bit disc but it turns out it was actually 2003 microsoft office for 32 bit lol.

---

### Post by BillyBoa on 2011-11-14
Yes the Linux OSs include on their kernel most of the drivers needed for an installation. In any case you can just have a try. Just download the Ubuntu 11.10 64b desktop, burn a CD and boot it. Then you have the option to install it or better for you try it. So you choose -try and you can check if Ubuntu recognizes your computer's drivers. Then if you are satisfied you can click on the icon install and start the installation.

If you don't have a Win CD just try to install only Ubuntu. BUT it will be needed a special procedure to install Windows afterwords. Not very difficult but is better if you can avoid it.
 
In any case you should be asking for a 64b Windows version to exploit the 4G of RAM.

---

### Post by mace200200 on 2011-11-14
> **BillyBoa said:**
> Yes the Linux OSs include on their kernel most of the drivers needed for an installation. In any case you can just have a try. Just download the Ubuntu 11.10 64b desktop, burn a CD and boot it. Then you have the option to install it or better for you try it. So you choose -try and you can check if Ubuntu recognizes your computer's drivers. Then if you are satisfied you can click on the icon install and start the installation.

If you don't have a Win CD just try to install only Ubuntu. BUT it will be needed a special procedure to install Windows afterwords. Not very difficult but is better if you can avoid it.
 
In any case you should be asking for a 64b Windows version to exploit the 4G of RAM.

Awsome that's good to know because i don't have $100 to spend on windows!

---

