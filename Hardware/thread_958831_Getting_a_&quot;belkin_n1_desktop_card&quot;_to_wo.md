---
title: "Getting a &quot;belkin n1 desktop card&quot; to work with ubuntu."
date: 2008-10-25
forum: Hardware
---

### Post by fatherrabbi on 2008-10-25
I have been very interested in Linux distributions for a long time, and have tried a few on a virtual machine. I tried OpenSuSE, Ubuntu, Kubuntu, Fedora, and Knoppix,and I have to say that I am the most impressed with Ubuntu. I am very newbish with Ubuntu, however, and would like to dual boot my machine with Win XP and Ubuntu. I know how to do that, but I am unable to get my "belkin n1 desktop card" wifi reciever to work with Ubuntu. I know that I have to use NdisWrapper to use the driver, but I dont know how to install programs without using the Syntax installer, which only works online (to my knowledge). I also have NO idea how to use the terminal (but i have used it to install KDE on Ubuntu, but that takes no skill). I have both a .exe file driver for my network card, and a cd that came with it. Assuming that I've already installed Ubuntu, what do I have to do to install it?

PS- Please use simple lingo, lol, I'm a newb :confused:

---

### Post by pytheas22 on 2008-10-25
To figure out what exactly you need to do, please open a terminal (Applications>Accessories menu), run the following commands (one per line), and post the output here.  Make sure your wireless card is plugged in first:
```

lsusb
lspci -nn
lshw -C Network
uname -m
```

Since it doesn't sound like you have any Internet connection available, not even wired, you can copy and paste your command-line output into a text file (you can copy the terminal text by highlighting it, right-clicking and selecting 'copy'), then transfer it to a computer with Internet access via a USB drive or CD so that you can post it here.

---

