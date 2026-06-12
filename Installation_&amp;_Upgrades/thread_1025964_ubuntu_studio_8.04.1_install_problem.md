---
title: "ubuntu studio 8.04.1 install problem"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by dcanno on 2008-12-30
Hi all!

this is my first day with Ubuntu and the first post on the forum really. 

I am trying to install Ubuntu Studio, with no success so far. 

First I tried with version 8.10, but the installation process was stopping at the point of formatting partitions and nothing was really happening. I tried with 8.04.1 and it looked like the installation was successful. The problem is I can work with the command line only. I checked an installation online tutorial and one of the points there is setting the resolution for the video card. I realized that in my case it was no screen like this. 

I have had Fedora 9 and Windows XP working on computer .
My PC is 3 years old:
MOTHERBOARD: DFI S939 nForce4 SLI PCIe ATX
PROCESSOR: Athlon 64 X2 4200+ S939 512KB
HDD: 4 x 250 GB Maxtor DiamondMax Plus10 SATA2 7200rpm 16MB Cache
RAM: 	2 of Patriot Extreme Performance 1GB PC3200 DDR 400 (Single-Stick) Low Latency
	2Gb Patriot PC3200 Low Latency Dual Channel kit
SOUND: Soundblaster Audigy SE
VIDEO: 256MB Leadtek PX 6800GT TDH PCI-E


I am a bit confused about what to do next to make it running?

Thank you for help in advance.

Dariusz

---

### Post by namdung on 2008-12-30
I reckon Ubuntu 8.04.1 is installed in ur PC. Are u sure that u've not installed the Server Version which doesn't have a GUI?

Just to be sure, type in terminal
```
sudo apt-get install ubuntu-desktop
```

To start GUI
```
sudo startx
```

If the above doesn't work, post the output of 
```
cat /etc/X11/xorg.conf
```

Ur video card driver might need to be installed.

---

### Post by danielpalos on 2008-12-30
I recommend formatting the hard drive. A low level format will help detect and "swap out" bad sectors from your hard drive.

Be sure to back up your data before you format the hard drive if you want to save your data.

---

### Post by dcanno on 2008-12-30
> **namdung said:**
> I reckon Ubuntu 8.04.1 is installed in ur PC. Are u sure that u've not installed the Server Version which doesn't have a GUI?

Just to be sure, type in terminal
```
sudo apt-get install ubuntu-desktop
```

To start GUI
```
sudo startx
```

If the above doesn't work, post the output of 
```
cat /etc/X11/xorg.conf
```

Ur video card driver might need to be installed.
hi

thank you both for the advice.
namdung - 
the version I installed is here: [http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/)    - 64-bit PC (AMD64) alternate install DVD

Following your advice I typed all the commands in terminal:

sudo apt-get install ubuntu-desktop - E: Couldn`t find package ubuntu-desktop

sudo startx - command not found

cat /etc/X11/xorg.conf - not such file or directory

---

