---
title: "Right speaker volume so low I can't hear it (not a balance issue)"
date: 2010-11-05
forum: Hardware
---

### Post by beccatoria on 2010-11-05
Hey all, 

I recently put 10.10 on my new Toshiba Satellite L650-12Q laptop and had the common problem about the headphones not being picked up and sound only coming from the speakers.  I fixed that by installing the alsa linux drivers as suggested here - 

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

That fixed that issue fine - the headphones are now working in stereo, perfectly, as are the external speakers I have that connect via the headphone jack.  

The problem is that the actual laptop speakers aren't working right.  The left speaker works fine and plays the left-stereo track, but the right speaker's volume is so low I can't hear it at all unless I crank every volume option up to absolute maximum and then I can *just about* hear a tiny amount of noise.  

I'm really not sure what the issue is - I've checked to make sure the balance is okay and it is, and it works when I pan between left and right speakers (at least in my headphones it does, on the laptop speakers, obviously when I pan too far right, I can't hear anything at all!)  

I've also installed Gnome Alsa Mixer and there doesn't seem to be an issue with anything there having been muted.  One weird thing I will note is that when I got to program preferences I see that under slider style, it has "single slider with pan" selected.  When I try to select "double slider with lock" instead, it initially lets me choose it but when I close the preferences box, nothing changes and when I go back to the preferences box, it's...miraculously back on the single slider option again.  I don't know if that's at all relevant but given the issue may be to do with the volume of a single speaker, I thought it was worth noting.  

I've seen various suggestions to try editing the alsa-base.conf file and I've tried all the commonly suggested models for a Toshiba, but none of them seem to make a difference, so I took out the extra line most of the fixes suggest and returned the file to its original state.  

Using the lspci code, the relevant audio information seems to be:  

> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

And when I enter:

> cat /proc/asound/card0/codec#* | grep Codec

I get:  

> Codec: Conexant CX20585
Codec: Intel IbexPeak HDMI

I'm pretty much a linux newb, though very happy to learn anything new.  If there's any other information I can provide to assist, please let me know.  

The issue isn't a critical one as I have external speakers I can use, but it is a bit annoying, plus I'm curious as to what could be causing this.  

With many thanks for all assistance, 
becca.

---

