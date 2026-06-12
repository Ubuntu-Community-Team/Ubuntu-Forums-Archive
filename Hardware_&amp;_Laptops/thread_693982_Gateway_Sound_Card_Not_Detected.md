---
title: "Gateway Sound Card Not Detected"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by garnetrook on 2008-02-11
So I have a Gateway E-100M with, I'm pretty sure, the Sigmatel STAC9200 sound card.  I know it works -- I've gotten it running with Pardus, Archlinux, and Fedora -- but I really want to run Linux Mint.

So far I've tried the fix from here:
[http://linuxmint.com/forum/viewtopic.php?f=42&t=6788&p=44870&hilit=gateway+sound#p44870](http://linuxmint.com/forum/viewtopic.php?f=42&t=6788&p=44870&hilit=gateway+sound#p44870)

Also, I added the line 

options snd-hda-intel probe_mask=1

to my /etc/modprobe.d/alsa-base file.

Right now I'm getting a problem where my sound card is no longer even detected =/  It doesn't appear under hardware configuration anywhere and "asoundconf list" produces no results.

Any ideas?

---

### Post by Yellow Pasque on 2008-02-11
Some things you could try:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Newer version of ALSA:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

OSS4:
(see link in sig)

---

