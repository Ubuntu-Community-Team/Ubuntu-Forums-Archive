---
title: "Dell Vostro 3550 Fingerprint Reader"
date: 2013-09-19
forum: Hardware
---

### Post by demisgc on 2013-09-19
Did anyone get this feature working on Vostro? 

Bus 002 Device 003: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader

I would like to unlock the screen using the fingerprint and not typing the password.

Thanks in advance!

---

### Post by audiobat on 2013-11-13
*bump - I'd like to know this also.  Is there any Ubunut equivalent for the fingerprint/identity software and/or is there another way to use the swiper?

---

### Post by locutus42 on 2013-12-12
Got it reading and verifying on a Thinkpad Edge e531( running Kubuntu 13.10 ) which has the vfs5011 finger print device like yours.
I had to download the driver from git(see the git trouble report below and look to the for the zip file and then for trouble shooting compiling).
In a nutshell, I got the fingerprint-gui software but it would not recognize the device. Downloading the latest libfprint source and building it does the trick. BUT, once the driver was compiled and I compiled and ran the example verify-live, you have to install the new driver(sudo make install) and then unlink the old driver and link in the new one.
The new driver is in /usr/local/lib while the old one is in /usr/lib. What I did was renamed /usr/lib/libfprint.so.0.0 to libfprint.so.0.0.ORIGINAL and then linked the new one with:
sudo ln -s /usr/local/lib/libfprint.so.0.0 /usr/lib/


[https://github.com/ars3niy/fprint_vfs5011/issues/4](https://github.com/ars3niy/fprint_vfs5011/issues/4)


I then had to setup a udev rule so that permissions worked for the usb device the fingerprint sensor is on. 
So I created /etc/udev/rules.d/fprint.rules with this:

# Validity VFS5011
SUBSYSTEM=="usb", ATTRS{idVendor}=="138a", ATTRS{idProduct}=="0011", RUN+="/bin/chmod 666 /dev/bus/usb/001/004"

but you have to change the bus device to match your system. Mine was on usb 001/004 and it looks like yours is 002/003.

At this point fingerprint.gui works when run as a standard user. I don't have login working yet.

---

