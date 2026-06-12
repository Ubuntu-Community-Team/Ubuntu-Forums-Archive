---
title: "sound and wireless problems"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by nareshmamidi on 2008-03-08
hi, mine is lenovo 3000 y410 laptop. actually when i start my ubuntu, it doesn't detect sound drivers and sometimes wireless. but if then i suspend it(i mean sleep mode) and return to normal mode, both will get detected..why so, can any1 help me?

---

### Post by jan quark on 2008-03-09
can you please post the result of these terminal commands:

```
iwconfig
```
```

cat /etc/network/interfaces
```

```
sudo lshw -C multimedia
```

---

### Post by nareshmamidi on 2008-03-09
thanq for replying...

for ***_"iwconfig"_***

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0D:54:9E:13:2D   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4397   Missed beacon:0

for   ***_"cat /etc/network/interfaces"_***

auto lo
iface lo inet loopback

and for *_** "sudo lshw -C multimedia"**_*

*-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Yellow Pasque on 2008-03-09
Maybe you want to add to your /etc/network/interfaces file something like this (the fragment below is set up for dynamic IP, static IP will be a bit different):
```
auto eth1
iface eth1 inet dhcp
```

For sound, you might want to try these scripts to update to the latest ALSA:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
Also, make sure your alsa-base file is configured correctly (try model=lenovo first):
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by superprash2003 on 2008-03-10
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

