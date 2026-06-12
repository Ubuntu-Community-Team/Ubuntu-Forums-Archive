---
title: "Ubuntu 14.04 Bluetooth A2DP"
date: 2014-07-29
forum: Hardware
---

### Post by fatalkill3r on 2014-07-29
Hi,

I am using Ubuntu 14.04. When I try to connect my cell phone to my desktop using bluetooth I am able to connect but I cannot get any audio from cell phone. On searching forums I found that we need to write "Enable=Source" in /etc/bluetooth/audio.conf. On writing above setting in audio.conf file, my bluetooth connection doesnt work at all. My cell phone instantly gets disconnected from my PC. 

I am using following commands to setup bluetooth

sudo hciconfig hci0 piscan
sudo hciconfig hci0 sspmode 0
sudo bluetooth-agent 123456

Please Help! Thank you

---

### Post by fatalkill3r on 2014-07-30
Anyone ? Please Help

---

