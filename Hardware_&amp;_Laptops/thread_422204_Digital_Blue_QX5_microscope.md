---
title: "Digital Blue QX5 microscope"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-04-24
Since linux is for geeks, has anyone installed a digital blue qx5 microscope?

I've read the Qx3 (when intel produced them) worked under linux, but nothing from QX5.

I've read I need xawtv, but I cant' seem to install it.

lsusb
> Bus 002 Device 003: ID 0553:0151 STMicroelectronics Imaging Division (VLSI Vision) Digital Blue QX5 Microscope


any ideas?

---

### Post by ahriman06 on 2007-10-19
I did it but there is something not working : light !
Here is what i did :
- get qx5view (search in google, a site has it but this site is down... but you can click the "cache" site in google, the website still works and you can get the file...)

- Do as follows :

sudo apt-get install mercurial

sudo apt-get install build-essential linux-headers-`uname -r`

hg clone [http://mcentral.de/hg/~mrec/v4l-dvb](http://mcentral.de/hg/~mrec/v4l-dvb)

cd v4l-dvb/v4l
make
sudo make install

sudo apt-get install gtk

sudo apt-get install libjpeg_dev

sudo apt-get install libgtk-dev


THEN EXTRACT THE QX5VIEW TAR GZ AND DO THIS :

./configure
make

sudo mknod /dev/video0 c 81 0
sudo mknod /dev/video1 c 81 1
sudo mknod /dev/radio0 c 81 64
sudo mknod /dev/radio1 c 81 65
sudo mknod /dev/vtx0 c 81 192
sudo mknod /dev/vtx1 c 81 193
sudo mknod /dev/vbi0 c 81 224
sudo mknod /dev/vbi1 c 81 225 
sudo ln -s video0 bttv
sudo ln -s video0 video
sudo mknod /dev/video c 81 0



sudo ./qx5view


IF IT DOESN T WORK TRY THIS AT THE END :
sudo rm /dev/video
sudo mknod /dev/video c 81 0
sudo ./qx5view

---

### Post by jazzcat on 2007-12-24
Hello,

I note that 7.10 inclues the cpia2 driver.  In fact, when I plug in the qx5, the driver installs itself.  However, running qx5view just hangs, and trying to use vlc to view the video stream doesn't do anything.  Does the cpia2 driver included in 7.10 not work with the qx5?  If so, how do I disable the built-in driver to compile the one included on the website?

Cheers,
-J

---

