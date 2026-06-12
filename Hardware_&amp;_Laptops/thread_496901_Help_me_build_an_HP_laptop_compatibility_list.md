---
title: "Help me build an HP laptop compatibility list"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by arashiko28 on 2007-07-09
I need to make a cotization for a HP Pavilion laptop, the model I have is ze2000 but they're out of order. Now I ask your help so that any Linux user with an HP laptop could tell me the model (if its recent, better) and how do you think is the grade of compatibility. Ex; HP Pavilion ze2000 98% compatibility, (not compatible, wifi card, bcm4306 and mute volume led). Or something like that. Please help, I really, really need this.

---

### Post by louiech21 on 2007-07-18
I also have an HP Pavilion ze2000 laptop, the only things that I am having problems with are my PCMCIA slots, I can't use my verizon wireless broadband card, as a matter of fact it only gets power from that slot and that's about it.  My wireless took some effort but I have it working.  I used this link to get my on board wireless working.  I haven't had any other issues yet but I would also love to see a compatibility list for this laptop since I do own one and almost no one else that I know does.  I purchased mine from the "PX" when I was in Iraq near Baghdad.

[http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310]("http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310")

Other than that I am actually very pleased with Ubuntu on my laptop.  Everything else is working great.

My only issues are:
1.  Wireless wasn't working but it does now.  The light even works too.  Ubuntu will not auto-detect this particular wireless card but I think certain Dell users have the same issue.

2.  PCMCIA does not auto-detect either.  (I was at least trying to see if I could get the the card working.)

3.  Mute button light doesn't work, but it shows up on the screen no problem so it's no big deal.

If there's anything I can do to help with this list please let me know or e-mail me on this forum.

---

### Post by BoardDWorld on 2007-07-18
I own a DV9224TX and it's highly compatible except for one issue when searching which I'm about to open a thread on. WiFi worked out of the box just booting from the CD, all media slots were recognized and even my multimedia remote & sensor touch pad works well in all media applications thus far. The only thing I needed a driver for was the webcam and that can be found as a .deb package [HERE]("http://www.arakhne.org/spip.php?article51")

---

### Post by arashiko28 on 2007-07-20
> **louiech21 said:**
> I also have an HP Pavilion ze2000 laptop, the only things that I am having problems with are my PCMCIA slots, I can't use my verizon wireless broadband card, as a matter of fact it only gets power from that slot and that's about it.  My wireless took some effort but I have it working.  I used this link to get my on board wireless working.  I haven't had any other issues yet but I would also love to see a compatibility list for this laptop since I do own one and almost no one else that I know does.  I purchased mine from the "PX" when I was in Iraq near Baghdad.

[http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310]("http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310")

Other than that I am actually very pleased with Ubuntu on my laptop.  Everything else is working great.

My only issues are:
1.  Wireless wasn't working but it does now.  The light even works too.  Ubuntu will not auto-detect this particular wireless card but I think certain Dell users have the same issue.

2.  PCMCIA does not auto-detect either.  (I was at least trying to see if I could get the the card working.)

3.  Mute button light doesn't work, but it shows up on the screen no problem so it's no big deal.

If there's anything I can do to help with this list please let me know or e-mail me on this forum.

Thanks, i quite don't understand the PCMCIA part, since my LAN card is PCMCIA, the one embedden on the motherboard fried out when a lightning hited my fence (3 years ago and it was the only thing damaged on the laptop). How ever, does not work if I put it in after turned on, or when it wakes up from hibernate mode, but never did on windows, so, no complains for that. Don't pull it out for restart or put it before turn it on, it should recognize it and when you log in, should be connected.:)

---

### Post by hessiess on 2007-07-20
dv2000.
wireless card works
had a major grub problem when i furst installed ubuntu
sound is buggy, dusent work on most apps
shortcut keys work perfectily

---

### Post by Atomic Dog on 2007-07-20
The problem with HP laptop models (dv2000, dv6000 and dv9000 series) is that every model number can have an array or different components.  If it is a centrino laptop then it should be very ubuntu/linux compatible (due to the intel c2d processor, intel wireless and intel graphics).  If it is an AMD based laptop or non-centrino it can be a crap chute as to whether it will work out of the box with ubuntu or not.

I see very few posts for help with centrino based HP laptops, I see many posts for help with the AMD flavors.  Just my observations.

---

### Post by hessiess on 2007-07-21
its a 1.66 ghz centrino, althow it runs at 1.7 most of the time! gforce go 7200, hda intell sound, 2 gig ram, sound dident work atall for ages, still cannot record. 

when i furst installed ubuntu as a dual boot grub would work perfectly untill windows was booted, then it went into a reboot loop when restarted. i dont know what was coasing it becose i diddent fix it lol:)

---

### Post by louiech21 on 2007-07-22
> **arashiko28 said:**
> Thanks, i quite don't understand the PCMCIA part, since my LAN card is PCMCIA, the one embedden on the motherboard fried out when a lightning hited my fence (3 years ago and it was the only thing damaged on the laptop). How ever, does not work if I put it in after turned on, or when it wakes up from hibernate mode, but never did on windows, so, no complains for that. Don't pull it out for restart or put it before turn it on, it should recognize it and when you log in, should be connected.:)

I do have my on-board wire card working and I use it in Ubuntu do you think that may be a conflict?  For some reason Ubuntu doesn't know what my Verizon wireless broadband PCMCIA is.

---

### Post by louiech21 on 2007-07-22
> **Atomic Dog said:**
> The problem with HP laptop models (dv2000, dv6000 and dv9000 series) is that every model number can have an array or different components.  If it is a centrino laptop then it should be very ubuntu/linux compatible (due to the intel c2d processor, intel wireless and intel graphics).  If it is an AMD based laptop or non-centrino it can be a crap chute as to whether it will work out of the box with ubuntu or not.

I see very few posts for help with centrino based HP laptops, I see many posts for help with the AMD flavors.  Just my observations.

My HP is also an AMD, nothing worked out of the box so it was very painful at first using Ubuntu, but I am actually very satisfied with it because I was able to find the commands necessary to manually configure my on board wireless card, my video card, beryl etc.  Many things were not working such as the desktop effects.  I wasn't able to enable them.  Now I have everything working due to the help of this Ubuntu community forum.

---

### Post by louiech21 on 2007-07-22
> **Atomic Dog said:**
> The problem with HP laptop models (dv2000, dv6000 and dv9000 series) is that every model number can have an array or different components.  If it is a centrino laptop then it should be very ubuntu/linux compatible (due to the intel c2d processor, intel wireless and intel graphics).  If it is an AMD based laptop or non-centrino it can be a crap chute as to whether it will work out of the box with ubuntu or not.

I see very few posts for help with centrino based HP laptops, I see many posts for help with the AMD flavors.  Just my observations.

My AMD was a pain but now everything works except my PCMCIA, The AMD Sempron will give you many problems with desktop effects, wireless and PCMCIA support.  Now that I know that Centrino based laptops are more compatible, I will keep that in mind when I select my next laptop.  Thanks for the heads up.

---

### Post by louiech21 on 2007-07-22
> **arashiko28 said:**
> Thanks, i quite don't understand the PCMCIA part, since my LAN card is PCMCIA, the one embedden on the motherboard fried out when a lightning hited my fence (3 years ago and it was the only thing damaged on the laptop). How ever, does not work if I put it in after turned on, or when it wakes up from hibernate mode, but never did on windows, so, no complains for that. Don't pull it out for restart or put it before turn it on, it should recognize it and when you log in, should be connected.:)

I have an AMD Mobile Sempron processor, that is probably why I run into a compatibility issue.
Is your laptop AMD based as well?  It seems that most people I talk to do not have any issues and everything
works seemless.  I suppose it could be the processor itself.  Most people do run Intel or Pentium in their laptops.

---

### Post by arashiko28 on 2007-09-03
> **louiech21 said:**
> I do have my on-board wire card working and I use it in Ubuntu do you think that may be a conflict?  For some reason Ubuntu doesn't know what my Verizon wireless broadband PCMCIA is.

Have you tried to change the IP's of each card? and second, haven't you found any driver for that card on linux? there should be.

---

### Post by arashiko28 on 2007-09-05
> **louiech21 said:**
> I have an AMD Mobile Sempron processor, that is probably why I run into a compatibility issue.
Is your laptop AMD based as well?  It seems that most people I talk to do not have any issues and everything
works seemless.  I suppose it could be the processor itself.  Most people do run Intel or Pentium in their laptops.

Nope, mine is Intel celeron M

---

### Post by BoojiBoy on 2007-09-06
I have a HP DV6426US and I would say it's 99% compatible. It has an Intel Core Duo processor, 945 video chipset and Intel wireless. I have some issues with the Synaptic-touchpad when switching users. It just doesn't work for about 3 minutes. Other than that, it's been a pretty painless install.

---

