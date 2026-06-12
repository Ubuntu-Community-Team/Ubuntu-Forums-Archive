---
title: "dvb-t recording server"
date: 2010-04-11
forum: Hardware
---

### Post by desmane on 2010-04-11
Hi community, 

I have a problem with my MSI DIGIVOX DUAL TUNER (chip: af9015.fw see installation below). 
It always worked exceptionally good on a generic kernel, now it stops working on my Ubuntu 10.04 LTS server, during installation I get some errors (i dont have the full kernel source installed, should build against vanilla 2.6.34 and so on). If I'd use the generic kernel, I am running into trouble going headless on that machine :(
**The tuner should work with kaffeine as the tuner is successfully initialized**, but the app complaints that it cant open adapter0 (see output below). 

I am running a small file server at home, I would use the generic kernel but when I reboot I cant login over ssh without a monitor plugged in and I ran in some other problems as well.

Here is what I did so far: 

```
sudo apt-get install linux-source-2.6.32 linux-headers-server mercurial -y

wget http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw
sudo mv dvb-usb-af9015.fw /lib/firmware/dvb-usb-af9015.fw

#hg clone

hg clone http://linuxtv.org/hg/v4l-dvb
hg clone http://linuxtv.org/hg/~anttip/af9015

cd v4l-dvb
make
sudo make install

cd af9015
make
sudo make install
```



```
andi@kas:~$ dmesg | grep dvb
[    7.396715] dvb-usb: found a 'MSI DIGIVOX Duo' in warm state.
[    7.396857] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.581673] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.825444] dvb-usb: MSI DIGIVOX Duo successfully initialized and connected.
[    8.836545] usbcore: registered new interface driver dvb_usb_af9015
```

a```
ndi@kas:~$ kaffeine
kaffeine(2608) DvbLinuxDevice::identifyDevice: couldn't open "/dev/dvb/adapter1/frontend0"
kaffeine(2608) DvbLinuxDevice::identifyDevice: couldn't open "/dev/dvb/adapter0/frontend0" 
```

thanks for your help!!

(should I move the thread to server??)

---

### Post by old_codger on 2011-07-27
If anyone is using ubuntu 11.04 and has bought one of the later versions of this model which has the lsusb ID of 1d19:1101 , (i.e. not the af9105 chipset but the rtl 8232u), it CAN be made to work but you have to,

a) boot up with the previous kernel version of 2.6.38-8
b) follow the instructions, (unfortunately in german but easy enough to follow), at...

[http://forum.ubuntuusers.de/topic/msi-digi-vox-mini-ii-v-3-0/7/#post-2980757](http://forum.ubuntuusers.de/topic/msi-digi-vox-mini-ii-v-3-0/7/#post-2980757)

Basically it involves running the following commands...

[I]cd

sudo apt-get install mercurial linux-headers-$(uname -r) build-essential git-core

git clone git://linuxtv.org/mchehab/new_build.git

cd new_build/

wget [http://goo.gl/CnJJu](http://goo.gl/CnJJu) -O rtl2832u_v2.0.1-new_build-set.tar.gz

tar -xf rtl2832u_v2.0.1-new_build-set.tar.gz

./build-rtl2832u.sh

sudo make install[/I]

You then have to restart your machine and try running the...

*dmesg | grep -i dvb*

as given to confirm it's connected. I haven't managed to get the IR connector working yet but will come back if I do.

---

