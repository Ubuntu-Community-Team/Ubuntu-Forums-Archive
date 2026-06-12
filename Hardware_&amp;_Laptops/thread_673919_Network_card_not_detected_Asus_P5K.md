---
title: "Network card not detected Asus P5K"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by InfoTech on 2008-01-21
I just installed Ubuntu 7.10 server on Asus MB P5K. The MB comes with integrated gigabit Attansic NIC.

sudo lshw -C network provided:
*-network DISABLED
description: Ethernet interface
product: L1 Gigabit Ethernet Adapter
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: b0
..... etc.

as advised on [http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html) , I downloaded the driver l1-linux-v1.2.40.2.tar.gz

BUT

when I try to do, as advised in readme

MAKE INSTALL

i get error message

The program 'make' is currently not installed. You can install it by typing:
sudo apt-get install make

after I done that, make install generate message
make: *** No rule to make target 'install'. Stop.

Any idea? Any help? Please? Thank you!

---

### Post by InfoTech on 2008-01-22
I found the solution. Thanks anyway :)

---

### Post by Sef on 2008-01-22
Could you post your solution, so that others may benefit.  Thank you.

---

### Post by InfoTech on 2008-01-30
Sure thing. Since i am very new to Linux stuff, I am not quite sure how to put all of this, but here it comes:

I downloaded the driver for the NIC, from the [http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)

There where several problems:
1. README suggested that I should type "sudo make install" from the directory the driver was extracted to, but actually I had to go to "src" directory under that one.
2. On some forums I read that I need to download kernel source, in order to compile the driver, but it didnt helped. In the end, after downloading kernel headers everything compiled properly and the NIC started working.
3. Of course, it was problem to download and install all the stuff from the Internet, since the NIC was not working on the computer. So, I downloaded manually to a XP laptop, burned them on a CD, mounted CD into Ubuntu 7.10 server and installed the stuff.

Please note that I did so many different things that I am not 100% sure which combination actually made things work, but, my best guess is this.

---

### Post by SpaceBas on 2008-02-02
For the life of me I cannot get this NIC working with 7.04 server or 7.10 Server (64bit)

I've tried the drivers from sourceforge and tried the ones on the CD from Aesus, neither will compile cleanly. 

I have the kernel headers installed, but that doesnt seem to help.

Has anyone managed to get this working with the server edition of Ubuntu?

---

