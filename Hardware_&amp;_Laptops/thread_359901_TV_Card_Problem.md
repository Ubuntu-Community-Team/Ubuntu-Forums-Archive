---
title: "TV Card Problem"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by LilMissPhoenix on 2007-02-12
Hi All

Been having some problems trying to get my TV card to work properly.  The card I have is an AverTV card.  According to the device manager in Ubuntu, this uses the Bt878 chipset, and it has recognized 2 video4linux devices.

The program I'm using to watch TV is TVTime, which seems to detect the card ok, but when I do a channel scan it does not detect any TV channels :(

I've tried setting the Television standard to various things, however I'm pretty sure it should just use PAL, which is what the UK uses I think??

Any ideas on how to get it working would be great! :D

---

### Post by DrNick on 2007-02-16
Hmm not sure, there are several different versions of PAL though.

Do you even get a distorted picture?

Anyone else any ideas???

---

### Post by zacbarton on 2007-02-16
I have a AVerMedia AVerTV DVB-T Volar USB2.0 and got it working with the help of this page [http://dramor.net/blog/archives/76](http://dramor.net/blog/archives/76) ( translated [http://translate.google.com/translate?hl=en&sl=es&u=http://dramor.net/blog/archives/76&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://dramor.net/blog/archives/76%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DCbO](http://translate.google.com/translate?hl=en&sl=es&u=http://dramor.net/blog/archives/76&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://dramor.net/blog/archives/76%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DCbO)  ) and firmware from  [http://www.omskakas.se/wp-content/uploads/2007/01/linuxtv-firmwaretar.bz2](http://www.omskakas.se/wp-content/uploads/2007/01/linuxtv-firmwaretar.bz2) [dvb-usb-dib0700-01.fw]

Heres what I did
sudo apt-get install mercurial
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

sudo cp dvb-usb-dib0700-01.fw /lib/firmware/dvb-usb-dib0700-01.fw
sudo modprobe cx88_dvb

dmesg now shows
7200967.880000] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in cold state, will try to load a firmware
[17200967.912000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[17200968.088000] dib0700: firmware started successfully.
[17200968.592000] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in warm state.
[17200968.592000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17200968.592000] DVB: registering new adapter (AVerMedia AVerTV DVB-T Volar).
[17200968.824000] DVB: registering frontend 0 (DiBcom 7000MA/MB/PA/PB/MC)...
[17200968.848000] MT2060: successfully identified (IF1 = 1220)
[17200969.308000] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully initialized and connected.

I used the scan tool to get my channels.conf and mythtv, I didnt get it working in tvtime. Im using digital TV signal.

Good luck

---

