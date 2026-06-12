---
title: "AverTV DVB-T usb2.0"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by hotcha3 on 2006-05-10
Hi, i have bought this dvb receiver a week ago and i still haven't found how to make the system recognize it. I've tried to download dvb-usb drivers from linuxtv.org but i get problems compiling (im a real newbie). Could someone please help me and please tell me what can i do to make it work? 
Im on a Dapper beta, thanks in advance.

---

### Post by minio on 2006-06-02
Well, this question is 3 weeks old but maybe it could help someone (it would help me). This was tested on Ubuntu 6.06 (final release).
First download firmware from [here]("http://www.linuxtv.org/downloads/firmware/dvb-usb-avertv-a800-02.fw").
Copy it to /lib/firmware/number_of_your_kernel/
```
sudo cp dvb-usb-avertv-a800-02.fw /lib/firmware/number_of_your_kernel/
```
Plug the device in USB port (if it's plugged then unplug it first ;) )
Blue light on device should light up.

Hardware is working but we need to see some pictures
Install dvb-utils
```
sudo apt-get install dvb-utils
```
make channels.conf
Adopt this line for your place
```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Oxford > channels.conf
```

install mplayer (xine would be better for this but it dont work for me in dapper)
```
sudo apt-get install mplayer
```
copy channels.conf to mplayer config directory
```
cp channels.conf ~/.mplayer/
```
and watch :)
```
mplayer dvb://name_of_your_station
```

---

### Post by KosmoZ on 2008-04-27
Thanks man! Just need to figure out what name_of_your_station is now..

---

