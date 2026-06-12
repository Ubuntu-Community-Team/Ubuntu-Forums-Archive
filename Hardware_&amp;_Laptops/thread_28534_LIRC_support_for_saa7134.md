---
title: "LIRC support for saa7134?"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-04-20
Hi

I have a TV-card, a Terratec Cinergy 400 (stereo, no fm tuner) which
came with a remote control. I've downloaded both the latest version
and the cvs version of lirc and I can't find anything saa7134 related in the
device setup in ./configure . Is this "remote control" supported?

root@fackamato:/usr/src/linux-source-2.6.10 # lsmod | grep saa
saa7134               103240  0
video_buf              21956  1 saa7134
v4l2_common             5888  1 saa7134
v4l1_compat            14468  1 saa7134
ir_common               5028  1 saa7134
videodev               10080  1 saa7134
soundcore              10400  2 saa7134,snd
i2c_core               22720  7
saa7134,tuner,w83781d,eeprom,i2c_sensor,i2c_isa,i2c_i801

root@fackamato:/proc/bus/input # cat devices
I: Bus=0001 Vendor=153b Product=1142 Version=0001
N: Name="saa7134 IR (Terratec Cinergy 40"
P: Phys=pci-0000:03:03.0/ir0
H: Handlers=kbd
B: EV=100003
B: KEY=c0104 100000 0 0 30000 0 8000 1a8 80500001 9e1680 7bba0 0 0

---

