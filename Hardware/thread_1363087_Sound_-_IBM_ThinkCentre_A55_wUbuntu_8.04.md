---
title: "Sound - IBM ThinkCentre A55 w/Ubuntu 8.04"
date: 2009-12-24
forum: Hardware
---

### Post by Alexander Barnes on 2009-12-24
Hi,
I've exhausted my abilities searching for answers on the net so I'm open to any ideas.  My IBM Thinkcentre A55 does not have sound.  I'm using Linux Mint Gloria, based on 8.04, kernel 2.6.28 (but I've tested Ubuntu 8.10 with the 2.6.31 kernel and still had the same problem).

Symptoms are:
1) I do have sound when I plug my portable laptop speakers into the sound jack
2) But there is no sound with just the normal speakers in the PC
3) there are some beeps from the BIOS (as I guess - start up/shutdown beeps and some odd key press events that beep)

More clues:
4) the latest Mandriva works, as did the Mandriva before it (seems to be ALSA) as far as I can tell (live CD)
5) Fedora doesn't (installed)
6) Ubuntu 8.10 doesn't (Live CD) (hoping the latest kernel would be a fix)

I've used this PC for several years and had sound previously - I believe I had Kubuntu 8.04 on it before, then Mandriva 2009.xx  The hardware gets good rating for Linux compatibility.  Not sure where to go next ... except, of course, to just turn to Mandriva (which seems like a fine distro on the whole.  I think I found the package manager a little awkward but that was about my only complaint - I use Ubuntu on my laptop and its absolutely a dream so I'd planned for Ubuntu on this desktop also, and basically I'm more familiar with Debian anyway).

I'm not really quite able to get all the ins and outs of drivers and so forth - I'm just a poor noob.  So, I would be appreciative of any tips.

Output from lshw that relates to my audio device:
>         *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

I sometimes think it's something really stupid so I've check for "mute" options and so on ... no luck there!  I'll still feel as though maybe somehow there's an On/Off button for sound!

Cheers.

---

### Post by Alexander Barnes on 2009-12-24
[SIZE="2"]Okay, found a clue in post #3 in this thread:
[http://ubuntuforums.org/showthread.php?t=1341288](http://ubuntuforums.org/showthread.php?t=1341288)

So, I fired up alsamixer and started turning things on - and found a muted or very low volume setting was the culprit.

Thank you Red Singularity you've saved my Ubuntu installation!  Thank you Ubuntu.  Everything's great now!  \\:D/[/SIZE]

---

