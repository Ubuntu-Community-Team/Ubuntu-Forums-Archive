---
title: "HowTo: watch TV with AVerMedia A309"
date: 2009-02-28
forum: Hardware
---

### Post by K. Hendrik on 2009-02-28
Hi,
after a few month of trying to get my TV Tuner to work I finnaly made it and though there was no guide for ubuntu i wrote this.
(I hope my english is good enough)

**UPDATE:**
This HowTo was originally written for ubuntu 8.10 if you are using ubuntu 9.04 jump directly to Step 4 "install w_scan" because ubuntu 9.04 already ships the needed drivers.

[SIZE="4"]install v4l-dvb[/SIZE]
First you need to install v4l-dvb using the following commands:
```

sudo apt-get install mercurial
hg clone http://linuxtv.org/hg/v4l-dvb
cd ./v4l-dvb/
make
sudo make install
sudo reboot

```
After rebooting check if the hardware is recognized.
```

dmesg | grep dvb

[   14.847900] dvb-usb: found a 'AVerMedia A309' in cold state, will try to load a firmware
[   14.847919] firmware: requesting dvb-usb-af9015.fw
[   17.827545] dvb-usb: did not find the firmware file. (dvb-usb-af9015.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   17.827591] dvb_usb_af9015: probe of 2-1:1.0 failed with error -2
[   17.827635] usbcore: registered new interface driver dvb_usb_af9015

```
You should now see that the hardware is recognized but that the firmware is missing.



[SIZE="4"]install firmware[/SIZE]
With google i found the requestet dvb-usb-af9015.fw file at  [[COLOR="Blue"]http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files[/COLOR]]("http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files")
You can install it by executing:
```

cd /lib/firmware/
sudo wget http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw
sudo reboot

```
After rebooting check again.
```

dmesg | grep dvb

[    8.890750] dvb-usb: found a 'AVerMedia A309' in cold state, will try to load a firmware
[    8.890768] firmware: requesting dvb-usb-af9015.fw
[   11.499561] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   12.364604] dvb-usb: found a 'AVerMedia A309' in warm state.
[   12.377766] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.502408] dvb-usb: AVerMedia A309 successfully initialized and connected.
[   14.662594] usbcore: registered new interface driver dvb_usb_af9015

```
You should now see that the firmware was found. Now you can use the Hardware to watch TV, first you need to scan for channels with scan or w_scan, i personally prefer w_scan.



[SIZE="4"]install w_scan[/SIZE]
You can find w_scan on the [[COLOR="Blue"]Projectpage(german)[/COLOR]]("http://wirbel.htpc-forum.de/w_scan/index2.html").
This will install w_scan on your system:
```

cd ~
wget http://wirbel.htpc-forum.de/w_scan/w_scan-20081106.tar.bz2
tar xfj w_scan-20081106.tar.bz2
cd ./w_scan-20081106
sudo cp w_scan /usr/local/bin/

```



[SIZE="4"]scan channels with w_scan[/SIZE]
To scan for channels just execute the following command:
```

cd ~
w_scan -X > channels.conf

```



[SIZE="4"]watch TV with vlc[/SIZE]
I like to watch TV with vlc but you could use other programms too like me-tv. You can watch TV with vlc by executing:
```

cd ~
vlc ./channels.conf

```
The playlist will list all found channels.




So that's it I hope it's usefull.

---

### Post by SickBastard on 2009-04-18
Incredibly helpful! Your instructions worked perfectly for my TerraTec Cinergy T USB XE on Intrepid 8.10. 

:D

---

### Post by K. Hendrik on 2009-04-21
nice to know it helped someone.:D

---

### Post by piranha1 on 2009-05-12
on ya for posting some helpful info for getting this working hendrick unfortunately didnt work for me however could be because I am using a e506 & 9.04 ubuntu. I originally went straight to the wscan and when when I use it it just says no usable dvb found when I use this command
dmesg | grep dvb  
nothing happens it just goes onto the next line,, any idea if the e506 should work just as the 309 does, it is a pcmcia card I need to get it going as its intended for a media centre pc.

---

