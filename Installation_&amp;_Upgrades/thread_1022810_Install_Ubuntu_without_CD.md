---
title: "Install Ubuntu without CD?"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by Maqz447 on 2008-12-27
Hi folks. I'm trying to install 8.10 server edition on an oldish IBM NetVista. This is turning out to be easier said than done though, as it seems impossible to get the machine to boot from the CD drive. It seemingly just ignores the bios boot order settings and merrily boots me into Windows even if I disable booting from the hard drive entirely.

So I was wondering, is there any way to install Ububntu without using the CD? My guess is "no", but I'm asking anyway.

---

### Post by damis648 on 2008-12-27
That is quite odd... have you tried updating the BIOS? You could also try [this]("https://help.ubuntu.com/community/Installation/Netboot") guide, as long as the machine can do a network boot.

---

### Post by Maqz447 on 2008-12-27
Thanks! That's exactly what I was looking for. I'll try it later when I have the time.

---

### Post by Hydrid on 2008-12-27
Another tip is to open the case and see if the jumper at the cd rom is set correctly to cable select or master.

---

### Post by Biznarie on 2008-12-27
A lot of those IBM's have problems booting off the CD drive but usually I can get it to work just by retrying, if thats not working you might want to try booting off a USB thumb drive.

---

