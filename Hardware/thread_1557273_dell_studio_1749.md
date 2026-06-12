---
title: "dell studio 1749"
date: 2010-08-20
forum: Hardware
---

### Post by oly on 2010-08-20
Below are my notes to make this laptop work i will add any new things i discover, thought i would post it for my future reference and others who may purchase this laptop, this is for a lucid but may work for future versions but hopefully will not be needed at all :)

I bought a dell studio 1749 from dell, i changed out the wireless card for an intel model as the default was broadcom, i am pleased to say this worked out of the box.

First of if you want to keep windows on for duel boot make sure you remove dell data safe backup when your finished with it as it breaks grub on each boot into windows and you will not be able to boot either operating system until you repair grub.

Generally everything works very well, there are a few teaks for better operation however, the first being 3d to get this to work well i had to use the driver from the propietary driver from the ati site.

First remove any fglrx drivers already installed and reboot.

sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

if your laptop boots into safe graphics mode this is great mean the old drivers are gone you can now install the driver from the ati site and reboot and you shoudl get a decent looking desktop back so try something with 3d if it still fails try installing.

sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core

by default the earphone jacks (yes there are two) do not work to fix this edit the file /etc/modprobe.d/alsa-base.conf and add the line below.

options snd-hda-intel model=dell-m6 

then reboot and the sockets will work.

One other tweak for some strange reason dell decided to make the laptop function key on by default so f5 (refresh) instead changes your brightness and f2 (rename) switches of your wireless, this can be changed in the bios and put back to the default behaviour.

Hope this is usefull for some one, will add anything else i figure out in the future.

---

### Post by NightFoxyarrith on 2010-09-03
Thanks, this is very helpfull.
I have a question, is installing the ati drivers found on their website better than installing the drivers in the proprietary driver manager in ubuntu? And will this solve the problems I'm having with games under wine because games that seem to work on every computer under wine crash if I enter a big area.

---

### Post by NightFoxyarrith on 2010-09-05
Installing the proprietary ati drivers from the ati site rather then using the ubuntu proprietary driver manager to install them actually solved the problems I was having with wine, thanks for your help man!

---

### Post by oly on 2010-09-12
yeah definitely helps i can also suggest if the games are a bit sluggish or the graphics are glitchy put the shader level in the game to it lowest setting can knock up textures and other settings but ati driver does not seem to like using shaders it certainly helps with starcraft 2 which runs quite nicely on wine on these laptops.

---

### Post by oly on 2010-09-22
Just thought I would add a note to say I tried the hdmi output on this laptop, and the tv came on instantly the only thing I had to do was to switch to hdmi audio in pusle audio to make the sound go through the hdmi port so that's another thing that worked out the box :-D

---

### Post by sailcappy on 2010-11-24
HDMI out is not working.  Is there a setting or should this just work?
 
Thanks!

---

### Post by oly on 2010-11-26
pretty sure it just worked did you try fn + f2, other than that make sure you have fglrx drivers installed and check catalyst control center to see if it detects a second screen.

---

### Post by NightFoxyarrith on 2011-05-01
I can't get suspend to work on natty, and I'm pretty sure it worked in maverick.

---

### Post by mpace965 on 2011-05-01
I can confirm it did work on Maverick. I'm having the same suspend problem. Hibernate does not seem to work either.

---

### Post by NightFoxyarrith on 2011-05-02
It doesn't seem to work on any distro, I tried openSUSE, arch, fedora, ...
The only distro that had suspend and hibernate set up correctly for this laptop was ubuntu, but not anymore...

---

### Post by dnns on 2011-06-04
Guys,

This might be of help:

I wanted to upgrade my Dell Studio 1749 to 11.04 via a fresh install.

But, I could not for the life of me figure out why the Natty 11.04 Live CD would not boot on my Dell Studio 1749.

32 bit, 64 bit, alternate CD, nothing worked. I eventually upgraded to 11.04 from within 10.10 (64 bit). The upgrade installation completed without errors, but tragedy struck again, after a reboot I could not boot the 2.8.38 kernel!

Long story short: THIS IS THE SOLUTION: 
The Dell Studio had the A05 BIOS installed. I upgraded to the A08 BIOS and now everything works!

---

### Post by mikhalek on 2011-10-13
Today I,ve made fresh install of 11.10 32bit on this laptop.
Everything works fine, but... 
1.installed latest AMD Catalyst driver from AMD website - working.
2.wireless BROADCOM did not work after install - found solution:

    -Download the 32 or 64-bit version:
    [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
    -Download patch for > 2.6.37 support:
    [http://www.mindwerks.net/wp-content/uploads/2011/03/broadcom-sta_4_kernel-2.6.38.patch](http://www.mindwerks.net/wp-content/uploads/2011/03/broadcom-sta_4_kernel-2.6.38.patch)
    -Extract the sources:
    cd ~/Downloads; mkdir -p wl; cd wl; tar xf ../hybrid- portsrc*-v5_100_82_38.tar.gz
    -Patch the sources, compile and install:
    patch -p1 < ../broadcom-sta_4_kernel-2.6.38.patch
    make; sudo make install; sudo depmod; sudo modprobe wl

Give Ubuntu a few seconds after loading the “wl” kernel module, then eventually the Network Manager will start looking for wireless networks.
3.(thank's to oly)by default the earphone jacks (there are two) do not work, to fix this edit the file /etc/modprobe.d/alsa-base.conf and add the line below:

options snd-hda-intel model=dell-m6

then reboot and the sockets will work.
4.installed SKYPE - but internal microphone is not working. I was trying to play with alsamixer, but with no results. Then found this in internet:
 Try adding the line in /etc/modprobe.d/alsa-base.conf :

options snd-hda-intel model=6stack-dell

After doing so and reboot - mic is working but earphone jacks not. As far as I understood, after editing /etc/modprobe.d/alsa-base.conf only the last added line is making effect on the system. Is there any solutuion on how to make them both - earphone jacks and microphone working? 
For SKYPE already installed pavucontrol and pulse audio control.
Any suggestions?

---

### Post by NightFoxyarrith on 2011-12-03
No idea, I'll try this myself. I'm having the same issue with the internal mic. I think the mic worked up to version 10.10, so since then everything went downhill. They did fix the suspend issues in 11.10 so it's not all bad.

---

### Post by NightFoxyarrith on 2012-01-22
I can't get the internal mic and headphone working at the same time. I just use a usb mic now. I've also tested the mic jack next to the headphone jack, and you can connect a mic to that and still get headphone sound.

---

### Post by NightFoxyarrith on 2012-05-20
Adding this line to /etc/modprobe.d/alsa-base.conf solves the headphones/microphone problem:

```
options snd-hda-intel model=dell-m6-dmic
```

---

### Post by ricklahaye on 2012-09-16
Thanks, this helped me alot.
¨options snd-hda-intel model=dell-m6¨

---

