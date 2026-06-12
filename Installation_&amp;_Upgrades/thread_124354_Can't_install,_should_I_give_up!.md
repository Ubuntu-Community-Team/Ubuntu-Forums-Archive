---
title: "Can't install, should I give up?!"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by helgman on 2006-02-01
I've been working on this all day (almost 8 hours) with no success, maybe it's time to quit?

All I want to do is install ubuntu on my Acer Travelmate 4151. At first I wanted to have a dual-boot but now I'd be happy with just ubuntu.

Problem 1:

When ever I try to start the installation it work great up till the "how do you whish to install"-screen (the first screen!). I can always get past that one but then the how thing stops (no Ctrl+Alt+Del, no nothing) after the "Uncompressing Linux ... Ok, booting the kernel." Only thing after that is the fan buzzing.

Played around some and found out that I could get past that stepp by saying "linux noapic" at "boot:" instead of just hammering "Enter". Nice.

Problem 2:

When I get to the detection hardware part it can't find my CD-ROM (DVD r/w). I posted about this in the forum but with no luck [(here is the post)]("http://ubuntuforums.org/showthread.php?t=121920"). I played around with that a good part of this morning but without any luck.

Problem 3:

As a final desperat solution I went for a network installation [(used this fine guide)]("https://wiki.ubuntu.com/Installation/LocalNet"). After some fiddeling with my (ubunut)server I managed to get things going. All the way up to the partition, cause now it can't find the disk. Now I don't know what to do. (I used the noapic parameter here too.) I tells me to manualy make the partition but there is nothing to do the partion on ...

I managed to install Mandriva on it just before I tried the networkthing, but I never managed to boot it (the installation went fine but then it stoped when it was trying to load the kernel).

Should I give up and stick to good ol' Windows or is there anyone out there who can give me a hand?

Helgman

---

### Post by az on 2006-02-01
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelmate4150?highlight=%28laptop%29%7C%28testing%29](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelmate4150?highlight=%28laptop%29%7C%28testing%29)

Seems to be known....
It says you can install Warty....  I wonder if you can install Warty, then dist-upgrade to breezy?

---

### Post by helgman on 2006-02-01
Thanks for the reply and the link. (Managed to google right past all these postes it seems, didn't know the problem was so specific.)

If that is the problem ... I might try and do the whole warty thing (I think I have an old CD laying around here somewhere), just to see if the upgrade workes. Will post my findings ...

---

### Post by Lord Illidan on 2006-02-01
If Ubuntu is not working, have a shot at Open Suse. According to their HCL [http://en.opensuse.org/HCL/Laptops/Acer]("http://en.opensuse.org/HCL/Laptops/Acer"), it works.

---

### Post by BenWilson on 2006-02-01
This is the dual-boot I use for Gentoo (just starting to move toward Ubuntu. It spares the MBR so Window's does not complain. My first time dual booting I had a problem that forced me to recover windows, but because I'd replaced the MBR with grub Windows carped. I had to do a complete system restore. This was a couple of years ago, but I assume it still holds.

[http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)

---

### Post by helgman on 2006-02-04
I'm sad to say, Ubuntu didn't work out for me.

I installed Warty but didn't get the GUI up and running ... upgrade to Hoary (no problem) and upgrade to Breezy (no problem) ... still no GUI. Having spent over 14 hours on trying to get things to work that day I gave up. (Tried the 20060201 version of Drapper but no luck there either.)

SuSE workes (and after some bad advice I've got the wireless up and running too). But I'm sad say SuSE is NOT Unbuntu. Still have my Ubuntu-server but it's not the same thing. Then again, everything takes some time getting use too.

Since I'm still lost concerning most part of Linux (still learning after about a year) I wonder what it is that make SuSE run so smooth on my machine. At installation I went for default (there was a no apic option but I didn't use it) and everything but the wireless was up and running at first boot.

Why couldn't this be done with Ubuntu?

---

