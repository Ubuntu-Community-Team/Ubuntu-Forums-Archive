---
title: "general question: new laptop samsung x11 - should i return it or keep fighting?"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by annda on 2007-01-16
i just bought a new laptop, a samsung x11. it's great (except for that ugly silver plastic), and i read that all components are somehow working under linux. i wanted to replace a highly-compatible but a bit worn-out acer extensa 2900 and got this:

Centrino Core Duo T7200 (2 GHz)
2 GB RAM
nVidia 7400 Go
Intel sound and wireless
160 GB SATA HDD

the problem is, i can't seem to get WLAN to work and sound ALWAYS comes out of the speakers, even if the headphones are plugged in (lots of people with intel hda driver seem to get this, as well as some iBook users) - very inconvenient for a laptop user.

i'm not posting specific requests for help yet since i haven't gone through all the howtos and suggestions (btw it seems to work best with gentoo, but that is way beyond my abilities), so i would like to ask you if it reasonable at all to stick to the computer and try to get it to work the way it's supposed to, or whether a fairly ignorant person should rather give up and get the money back?

i am pretty comfortable with the command line, can mostly find out what is not working, but i have never compiled the kernel (just 3-4 little thingies). i want to learn but do not want to be a stubborn fool and loose quite a lot of money on hardware that i'm not satisfied with.

it's been a bit of a rant and honestly i'm probably waiting for you to convince me that intel is good and nothing is impossible.

please tell me if you have experience with unresolvable problems with intel chipsets.

---

### Post by discord on 2007-01-16
You should do a google search for the centrino chipset you use in your laptop. Also try ubuntu 6.10 and search for info for your sound chipset .

---

### Post by annda on 2007-01-17
a short update: 

wireless is of course working (in case somebody is searching the forums considering buying that model and gets scared by me previous post) - i was just too excited (read: not thinking clearly) to realize that if the chipset was properly detected and the drivers loaded, then the problem must lie somewhere else, not in incompatibility.

the Intel 3945ABG is supported out of the box on edgy. it's just not willing to work with 64-bit WEP encryption. as soon as i do more test, i'll post the results to the [list of supported laptops]("https://wiki.ubuntu.com/LaptopTestingTeam/SamsungX11").

as to headphones/speakers problem: i have the right driver for my chipset, but ALSA obviously needs some configuration/tweaking here - the problem persists with feisty, which uses newer ALSA. that's something for the weekend.

anyway, discord, thanks for telling me to keep on searching. i needed your "quit whining, do something" attitude :cool:

EDIT: it seems that the headphone problem cannot be fixed with available ALSA drivers. everything else works fine.

---

