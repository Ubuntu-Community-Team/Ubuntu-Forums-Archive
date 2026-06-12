---
title: "Problems installing DVB-T express card"
date: 2011-02-26
forum: Hardware
---

### Post by nibor64 on 2011-02-26
Hi,

I owned a HP ExpressCard EC300 DVB-T TV Tuner YUAN Hight-Tech.

I've some troubles configuring and installing it on a ubuntu 10.10.
I can't found any channels with me-tv or kaffeine.

Could someone help me ?

---

### Post by nibor64 on 2011-02-26
anyone ?

---

### Post by nibor64 on 2011-02-27
?

---

### Post by realzippy on 2011-02-27
If you go on bumping a mod will jump in:Only 1 bump/day here...

You also should post the output from
```
lspci
```
(Only the line concerning your device) 
or maybe
```
sudo lshw
```




*I can't found any channels with me-tv or kaffeine.*

... means that you can scan for channels with your device,so device is recognised and working,but a scan finds nothing..?

---

### Post by locutus42 on 2011-06-18
just a shot in the dark but maybe updating the pci ids so capabilities might be recognized.

sudo update-pciids

if you want hot swapping working then run this:

sudo modprobe acpiphp

I hope this is helpful.

---

