---
title: "Motherboard compatability"
date: 2015-11-18
forum: Hardware
---

### Post by Liamdale on 2015-11-18
Want to build a new linux computer:  heard that some motherboards could incompatable with linux.

looking at the 
MSI H97 PC MATE H97 S1150 ATX Mainboard

does anyone know of any issues related to this board.

Is there a site where motherboards are listed in the linux world?

---

### Post by pqwoerituytrueiwoq on 2015-11-18
the only thing you need to check are the audio and lan chipsets on the board (find the chipset and google "[chipset] ubuntu" *no news is good news*)

the only thing on that board worth checking is the onboard lan RTL8111G and audio ALC887 chipsets
i would be cautious with that lan chipset, i would not count on it working perfectly and if it does you may have to reinstall the driver after every kernel update

this board has a intel lan (so you dont even have to bother looking it up)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157511](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157511) (about the same price as that msi board)
audio chipset is ALC892
if you have a issue with the audio it seems to be a easy fix
[http://askubuntu.com/questions/456425/alc892-low-sound-issue-fixed-with-changing-alsa-config-why-does-it-work]("http://askubuntu.com/questions/456425/alc892-low-sound-issue-fixed-with-changing-alsa-config-why-does-it-work")

if you are going to be using hdmi for audio and not using onboard graphics the video card has a audio chipset on it so you don't need to worry about the motherboards audio chipset
if you don't like a motherboards lan chipset you can get a pci/pcie lan card (i found out my onboard Killer E2200 lan does not have WOL support on linux, got a new intel lan card off ebay)

---

### Post by Liamdale on 2015-11-20
Thanks[COLOR=#000000]  pqwoerituytrueiwoq;

Will seriously consider the ASRock H97 motherboard.
> 
the only thing on that board worth checking is the onboard lan RTL8111G and audio ALC887 chipsets
i would be cautious with that lan chipset, i would not count on it  working perfectly and if it does you may have to reinstall the driver  after every kernel update


More research on Lan and audio, to better understand the implications.

It's been 10 years since my last computer purchase and I have alot of catching up to do

again thanks[/COLOR][B][COLOR=#000000]




[/COLOR][/B]

---

### Post by Liamdale on 2015-11-21
[B][U]For general information:

[/U][/B]Found a site which may be of interest for a person who may want to build (or have built) a new computer.[B][U]

[http://www.linux-drivers.org/index.html](http://www.linux-drivers.org/index.html)
[/U][/B]
Don't know if this site is well maintained but it is a start to try and avoid hardware imcompatability

---

