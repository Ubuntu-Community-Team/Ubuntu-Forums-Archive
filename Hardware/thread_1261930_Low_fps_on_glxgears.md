---
title: "Low fps on glxgears"
date: 2009-09-09
forum: Hardware
---

### Post by rafa23189 on 2009-09-09
Hi:
I installed kubuntu on my new dell 1545, and I get 1000fps on glxgears more less.
The system is the following:
intel t4200
2gb ram ddr2 dual channel
intel gm45 chipset.
I updated xserver-xorg-video-intel
Whats wrong?
Here is my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Thanks
Rafa

---

### Post by Sam Lars on 2009-09-10
First of all, an Intel card is not going to give you the best performance.
Second of all, 1000 fps is really good (even if it isn't the best benchmark).

---

### Post by rafa23189 on 2009-09-11
On flightgear I get 10fps more less, which is almost the same I got with my old intel 945gcpe, the gm45 is suppossed to be much better. The desktop effects on kubuntu are also slow.
I heard somewhere that theres an issue with intel graphics on k/ubuntu 9.04. 
The solution suggested is to instal xf86-intel-video-2.7.99.1.tar.gz
Anyway when I run 'make' on the terminal I get an error thats something like 'none object specified or none makefile found'
What can I do?

---

### Post by Sam Lars on 2009-09-11
There are indeed confirmed issues with performance of Intel cards on 9.04
Where was this solution suggested?
In general, to install files like that, you should extract it either by right clicking on it and telling it to extract or with the command
```
tar xvfz filename.tar.gz
```
You should then go into the directory that is extracted and run
```
sudo make
```
and your other install commands there.

Also, I'm using version 2.8.1 on Karmic. You could at least test Karmic to see if the new version will make things better for you.

---

