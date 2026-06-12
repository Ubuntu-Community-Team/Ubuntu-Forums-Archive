---
title: "AGP aperture downsized to 4M in Edgy"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by Abraham Drinkin on 2007-04-05
Howdy everyone,
First time poster - long time reader.

I have a K8S-MX (SiS 760, I believe) motherboard by Asus and a Sapphire Ati X1600.  I cannot get fglrx to work at all, but that's not the current issue at hand.  

When I switch my AGP aperture size in my BIOS (currently only goes to 128MB -- I'm going to try flashing to a new BIOS soon), Ubuntu only reads it as 4M rather than 128M.

I've tried going from 128 to 64 to 32 in BIOS, but still the logs say 4M.

Any thoughts?  Let me know if you need any more information and I'll try to get it to you.

Thanks!

---

### Post by teaker1s on 2007-04-05
```
sudo dpkg-reconfigure xserver-xorg
```
for your memory size you need **1024 x mb = size**
example 1024 x 128 mb =131072

---

### Post by Abraham Drinkin on 2007-04-07
Thanks for the response, teaker1s.  I will try this wihen I get home tonight and report back.  I appreciate the help!

---

