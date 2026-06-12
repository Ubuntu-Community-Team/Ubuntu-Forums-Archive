---
title: "Which Ubuntu version for N330 Ion machine?"
date: 2009-11-19
forum: Hardware
---

### Post by rossmoore on 2009-11-19
Hi,

I'd appreciate some advice on which version of Ubuntu Karmic to install on a new machine I'm building. The motherboard is going to be a Zotac IONITX N330 - so a dual Atom, with Nvidia 9400 GPU. I want the machine to be silent, small, HD capable (plugged into the TV via HDMI, and using the restricted drivers) and to be the house router / wireless provider, video and music player, occasional light web browser and file server which explains the choice I hope (I don't want advice on the hardware!).

What I would like help on is the choice of Ubuntu version. My default option is just the standard 32-bit i686 desktop version. Is there another version that is better optimized for the Atom (I see stuff in Moblin and the Ubuntu Netbook Remix that talks about "optimization" but I don't know how important / significant that stuff really is).

Does anyone have any practical experience of trying the two out on a similar platform?

---

### Post by snowpine on 2009-11-19
Hi Rossmore, the Atom 330 is a unique chip, in that you have your choice of 3 architectures: i386 (32 bit), amd64 (64 bit), or lpia (low power intel architecture). I am currently running Ubuntu 9.10 lpia on my Foxconn Atom 330 barebones (integrated Intel, not Ion). I'm also testing 32-bit Arch and 64-bit Fedora.

Honestly, performance is *very* close with all three architectures. I would be curious to see some detailed benchmarks, because the difference is not detectable to my naked eye. If you are most comfortable with the 32-bit desktop version, I'd say that is a fine choice.

---

### Post by rossmoore on 2009-11-19
Thanks, snowpine, that's very helpful info. I wondered what lpia stood for! Looks like I'll try out the 32-bit i386 since I don't need more than 3Gb of memory, and see how the chip copes with Gnome before I bother trying one of the lighter windowing environments.

---

### Post by snowpine on 2009-11-19
My integrated Intel chip does Gnome + compiz no problem. I'm sure it will be even better with the Ion. I thought about spending a couple extra $$ for the Ion, maybe next time... I hope you will post back and share your experiences!

---

### Post by movieman on 2009-11-19
I run 64-bit on my Atom 330, I don't see any reason to stick to 32-bit.

---

### Post by rossmoore on 2009-11-19
Even simpler. I'll stick with my tried and tested 32-bit Gnome environment then. Thanks snowpine, and I'll add back to this thread in a couple of weeks when I've had time to build the system.

I can't see that there are any benefits from moving to 64-bit, and I have seen the odd problem thrown up by Flash or restricted drivers in these forums in the past with 64-bit. Given that I reckon I won't be doing anything that'll use more than 1Gb of memory, is here any reason to bother with 64-bit?

---

### Post by movieman on 2009-11-20
> **rossmoore said:**
> Given that I reckon I won't be doing anything that'll use more than 1Gb of memory, is here any reason to bother with 64-bit?

Typically 5-20% better performance in CPU-intensive apps, and you'll be part of the future, not part of the past :). Actually, you might get more than that performance-wise if you're comparing against i386 rather than i686.

There are also potential security benefits: for example, I believe the NX bit isn't supported in standard 32-bit kernels?

---

### Post by MultiBox on 2009-11-20
I have 9.10 64 bit on my Asrock AS330ion BT HT. After installation only thing to install was the NVidia drivers

I also tested 9.04 64 bit that works as well however you have to upgrade the kernel to a later version for your wifi

---

### Post by rossmoore on 2009-12-14
I went with 32-bit Karmic in the end, with 190 nvidia drivers from the nvidia-team ppa (+its patched mplayer version for vdpau acceleration).

I'm fairly happy with the result - it plays HD videos no problem, allows me to surf well and to share the big hard drives attached to it over samba. With a fan controller (physical rheostat) the board is pretty much silent - quieter than the high-pitched whine of a TV or just about anything electrical.

My 2 gripes:
1. I can't have compositing and compiz enabled AND have tear-free video viewing. Not a deal-breaker, but an annoying and unnecessary bug that I spent a lot of time trying to get around.
2. I can't persuade the "802.11n" capable atheros 928x chipset to go into master mode and thus act as a router, sharing my PPPoE connection. Instead I have had to use my 802.11g standalone router. This is an unecessary extra bit of kit to go wrong and take up a power socket, and limits the range and power of the signal. Again, not a deal-breaker but also something I spent ages trying to fix before gving up.

---

### Post by rossmoore on 2009-12-20
Just in case anyone is still interested, I fixed the second of my two gripes:
[http://ubuntuforums.org/showthread.php?t=1269671](http://ubuntuforums.org/showthread.php?t=1269671)
Much happier with the result, and it now means the network is fast enough to stream video off the server hard drive over wireless to my laptop reliably.

---

