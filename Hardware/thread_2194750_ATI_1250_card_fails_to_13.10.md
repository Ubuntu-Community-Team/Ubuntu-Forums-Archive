---
title: "ATI 1250 card fails to 13.10"
date: 2013-12-20
forum: Hardware
---

### Post by xaviman on 2013-12-20
Hi all,


I had my notebook PackardBell DOT running 64-bit Athlon and ATI Radeon 1250 to 12.04 and install 13.10 version. When system start return a  graphics card faulty screenshoot and restart in command console.
Anyone know how I can fix the problem?


Thank you.

---

### Post by Bashing-om on 2013-12-20
xaviman; Hi !

Was a proprietary graphics driver in use in the 12.04 install ?
If so, try (re-)installing a graphics driver.
I understand that version 13.10 has great open source driver support.
[INDENT][INDENT]what I think
[/INDENT][/INDENT]

---

### Post by xaviman on 2013-12-21
Hi Bashing-om,

In version 12.04 I had problems and I had to install free drivers and make:


sudo apt-get remove - purge xorg-driver-fglrx fglrx *
sudo apt-get install - reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-updates
sudo dpkg-reconfigure xserver-xorg


But now this did not work :-(
What do I?

---

### Post by richardsdma on 2013-12-21
i have a ati x1270 on my laptop, the same family card as yours and it works fine in 13.10. 
there in no proprietary driver available for 12.04 nor 13.10, the last ubuntu with proprietary driver for this card was ubuntu 8.04, back in april 2008.
you dont have to do anything about the video driver, it comes toghether with kernel. 
the easiest way would be to reinstall the OS and dont mess around with xorg/xserver anymore.

---

### Post by coldraven on 2013-12-21
I had the same problem with the X1250 so I went back to 12.04. This card will is not suitable for 3D games but works OK in 2D.

---

### Post by xaviman on 2013-12-29
I next try:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-updates
sudo dpkg-reconfigure xserver-xorg

And don't work.
What can I do?

---

### Post by Mark Phelps on 2013-12-30
> What can I do? 

For a start, STOP reinstalling the fglrx drivers!  

The second apt-get command includes "fglrx-updates" at the end, and as richardsma stated, the last Ubuntu version to support that was 8.04.

The default open-source Radeon drivers should work OK for you.

---

