---
title: "ACER ASPIRE 5050/5051 ANWXMi"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by enoughsaid05 on 2007-12-14
I am using Acer Aspire 5050/5051 ANWXMi

Specifications:

[LIST=1]
[*]AMD Turion 64 Mobile Technology MK36 (2.0 GHz, 512 KB L2 cache)
[*]14.1" WXGA Acer CrystalBrite LCD
[*]ATI Radeon Xpress 1100
[*]80GB HDD
[*]DVD Super Multi double layer (supported DVD+R Double Layer/ DVD +/- RW)
[*]512mb ddr2
[*]802.11b/g wireless LAN
[/LIST]

I am intending to install Ubuntu 7.10 and have tried its live CD. Can anyone tell me which hardwares are working and which are not?

Things in particular that I would look out for:

1) Sound

Doesn't seems to work under LiveCD. Will it work when Ubuntu gets installed fully?

2) Wireless card

When I run Ubuntu 7.10 LiveCD, the wireless can detect only 56% of the signal strength of my router at home while the same wireless can detect 100% under windows. What can I do to increase the signal strength received by wireless card under this Linux OS?

3) Keyboard

Seems quite insensitive as compared to when using under windows. When I turned on the caps lock, the first letter appear block letter, then when I turn off the caps lock, the second letter remains block. Probably it is due to switching caps lock on and off too fast, but I do not seems to have the problem under windows.

Some of the things that I would like to look out for as well...

1) Will the 5-in-1 card reader work?
2) Bluetooth supported?


Any problems that I would expect when installing and using Ubuntu 7.1 on this laptop?

Advice please!!!!

[Preferably a most complete picture as possible]

---

### Post by willie_wang on 2007-12-14
i've got an acer aspire 5021WLMi, similar specs to you, but X700 grphx, 15.4 widescreen.

For the wireless to work properly on my machine i had to use the windows driver with ndiswrapper. wireless works like a charm now, even at long distances. the ubuntu bundled bcm43xx driver just didn't cut it.

Sounds works perfectly on my machine.

no card reader, but i haven't tried it at all yet.

my laptop doesn't come with bluetooth, so can't check that. But i know that if it doesn't work on your machine, then the latest acer_acpi (you can download a .deb installer from googlecode) will sort that out.

absolutely no problems with my keyboard, ever on ubuntu!

our hardware configs could be very different though. just so you know.

---

### Post by ugm6hr on 2007-12-14
I am assuming you are talking about the 5051 AWXMi, which I have.

I started with 7.04 (Feisty), but am now on 7.10 (Gutsy), which works almost flawlessly (32-bit / i386 version).  Some of the links refer to Feisty, but apply to Gutsy too.

These are useful:

Sound works fine with this 2 second fix (then change preferences to control PCM volume - will adjust headphone and speaker volume):
[http://ubuntuforums.org/showpost.php?p=2875211&postcount=14](http://ubuntuforums.org/showpost.php?p=2875211&postcount=14)

Card reader reads SD cards (but I can't get it to write), and doesn't (?yet) recognise MemorySticks:
[http://ubuntuforums.org/showthread.php?t=635148](http://ubuntuforums.org/showthread.php?t=635148)

After installing - do this 1 mintue fix to improve boot time (note it takes several minutes to load the first time before this fix):
[http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

For 3D Effects (Compiz), another minute: **SEE NOTE BELOW - THIS IS UNNECESSARY NOW**
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

For 3D Effects with latest ATI driver (fglrx) and AIGLX (not XGL):
Install Envy New: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Run Envy New, and allow it to automatically install ATI driver, and automatically update xorg.conf
Do not install XGL (uninstall xserver-xgl if installed)
Follow advice here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects) (edit xorg.conf and usr/bin/compiz)

Bluetooth:
I don't think mine came with an installed Bluetooth module - in any case, I haven't tried it (Windows or Linux).

Wifi:
Don't worry about the quoted "strength" - it is not an absolute measure of actual strength - it is merely a relative indicator.  I have had no problems with range in either Linux or Windows.

Keyboard:
I don't have that problem. Presumably you type much faster than me!

Mousepad - This stops accidental taps when typing:
[http://ubuntuforums.org/showpost.php?p=3136787&postcount=8](http://ubuntuforums.org/showpost.php?p=3136787&postcount=8)

Microphone:
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

Hope that lot helps you get everything working absolutely the way you want.  Don't be daunted by the number of forum links - apart from the sound and slow boot issue, the rest are very minor tweaks (and possibly unnecessary depending on your use).

---

