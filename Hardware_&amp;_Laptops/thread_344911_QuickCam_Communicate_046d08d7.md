---
title: "QuickCam Communicate 046d:08d7"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by Terry of Astoria on 2007-01-23
I have a Logitech QuickCam Communicate 046d:08d7 and I've been able to get it working in amsn. I'll try to give the basics of how I did it. 
First, though, check to see that you have the same camera by typing
```
lsusb
```
You should see devices listed. Mine looks like this. 
```
me@bluebird:~$ lsusb
Bus 001 Device 007: ID 046d:08d7 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```
You can see it's the same camera since the 046d:08d7 is listed as a device.
OK here we go.
I first installed camorama and an old webcam was detected, but the QuickCam wasn't. I then downloaded and installed the driver located at 
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html). There are two choices there. I have the kernel 2.6.11 or higher so I took the one at [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz)
  So you could do 
```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz
tar -zxvf gspcav1-20070110.tar.gz
cd gspcav1-20070110/
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe gspca

```
After that my camera worked. I think I got all that right. I am retracing my steps rather than noting them as I go. 
Anyway, now for amsn. I had to get the source and compile it. 
The web site is [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)
You can try this:

```
mkdir amsninst
cd amsninst
wget http://prdownloads.sourceforge.net/amsn/amsn-0.96.tar.bz2
tar -xvjf amsn-0.96.tar.bz2

```
I had missing deps errors upon running the configure script until I did
```
sudo apt-get build-dep amsn
```
OK now
```
./configure
```
then
```
make
```
then
```
su -c 'make install'
```
That last command might be better issued as "sudo -c 'make install'"
I don't know, but I'll tell you you'll have to create a password for your root account before it'll work the way I have it written. You'll have to look in the wiki for how to do that.

---

### Post by duojet on 2007-03-01
thank you! I've been going through howtos and docs for at least four hours now, and this made it work the first time!

---

### Post by Alajjana on 2008-05-11
Thank you!!

---

### Post by DannyB2 on 2008-06-30
That worked for me on 8.04.  Thank you so much.  (Note that the filename had changed to 20071224, but otherwise your instructions were perfect.)

I did not install amsn.  Instead I tried Kopete for instant messaging.  I did not even bother to create an IM account in Kopete.  I just went right to the Configure, clicked devices, and could instantly see that my webcam was working.

---

