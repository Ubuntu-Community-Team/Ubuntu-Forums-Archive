---
title: "ALSA questions??? need help badly"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by narmenia on 2005-09-25
[http://www.mepis.org/node/6890#comment-23759](http://www.mepis.org/node/6890#comment-23759)
> I found a solution for the sound issue!

The D915 chipset (with "HDA" audio) needs Alsa 1.0.9. I got finally it running successfully on the beta version of Kannotix 2005-4. Once installed, you must run:

alsaconf
then alsamixer
then check KDE control center in root make sure sound system is ok
Also check kmixer

Don't know when Alsa 1.0.9 is going to be generally available. All Debian distros seem to currently be running 1.0.8.

Cosmo

Detailed changelog between 1.0.8 and 1.0.9 releases
***************************************************
-----snip------
- Summary: Add Intel HDA driver
Added a new Intel High-Definition audio driver.
The driver consists of two separate modules: the generic support
module for HD codecs (snd-hda-codec), and the driver for Intel ICH6/7
chipset (snd-hda-intel). The snd-hda-intel was called formerly
snd-azx in the ALSA 1.0.8 rlease.
- Summary: Move azx driver to alsa-kernel tree
snd-azx driver is moved to alsa-kernel tree.
Now it's renamed to snd-hda-intel (to avoid the codename).
-------snip---------

Looks like you need at least alsa-1.0.9 to support sound on the chipset.

1st question: What is ALSA???
2nd question: What version of ALSA in Ubuntu 5.04???
3rd question: Is it possible to update ALSA??? If Yes... How???

Thanx...

btw im a linux n00b. so sorry...  ](*,)

---

### Post by adwait on 2005-09-25
1)ALSA stands for Advanced Linux Sound Architecture. It's one of the things that make the sound go in Linux.
2)Umm......Dunno, using 5.10 now
3)Running
```

sudo apt-get update
sudo apt-get upgrade

```
Should upgrade everything including ALSA.

---

