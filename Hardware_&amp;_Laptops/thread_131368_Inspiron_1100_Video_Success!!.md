---
title: "Inspiron 1100 Video Success!!"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by racsw on 2006-02-16
Hi Guys,
  I'm new to Umbutu, having put up and run Suse and Mandrake for years, but I decided to install this on the wifes Dell Inspiron 1100, which sounded great until I ended up with nothing more than a miniature 7" x 6", 640x480 res screen.
After some help from various folks, and another forum from Suse 9.0, I finally got the dang thing to work, and it looks good.
So I thought I'd pass this along.
Here we go...

Download this file:
[www.chzsoft.com.ar/845patch.tar.gz](www.chzsoft.com.ar/845patch.tar.gz)

Do this:
sudo su
tar zxvf 845patch.tar.gz
cd 845patch
make
cp 845patch /sbin

Create this file:
/etc/init.d/patch845

Put in these two lines:
#!/bin/sh
/sbin/845patch 16384

Next:
cd /etc/init.d
chmod +x patch845
cd /etc/rc5.d
ln -s ../init.d/patch845 S14patch845

Now run this:
dpkg-reconfigure -p high xserver-xorg
make sure 1024x768 is selected.  This is the intended resolution for this computer.

We're almost done...

Now get into the terminal.
sudo su
gedit /etc/X11/xorg.conf

Modify these lines:

under Section "Device"
add this line below "BusID "PCI:0:2:0"
VideoRam  16384
 
under Section "Monitor"
add these two lines below Option "DPMS"
HorizSync 31.5-80
VertRefresh 36.5-75

reboot, and Umbutu should come up full screen for login.
Hope it works for you too :D 

Robert

---

### Post by computerdave on 2006-02-21
THANK YOU, THANK YOU, THANK YOU!!!  I worked through these directions and it worked like a charm.  I had just recently installed a fresh copy of kubuntu 5.10 and I was so upset because with Knoppix it worked fine, full-screen.  I ran into some problems with make not being installed and then gcc wasn't working right.  But I prevailed and now I'm happily using my 1024x768 screen res.

---

### Post by test on 2006-05-28
[http://www.ubuntuforums.org/showthread.php?t=183285]("http://www.ubuntuforums.org/showthread.php?t=183285")

---

