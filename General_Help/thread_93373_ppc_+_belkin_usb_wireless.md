---
title: "ppc + belkin usb wireless"
date: 2005-11-21
forum: General Help
---

### Post by mizarc on 2005-11-21
ok i'm stressed.. i installed breezy on my iBook, and i have a belkin F5D7050 usb wireless g adapter.. i'm seeing tons of guides/howtos that show people having a painless experience installing ndiswrapper and the drivers off the cd.. 

so i have questions.. i've run linux on i386 before, but does ppc change things like device usage or anything? i can't get ndiswrapper to compile for the life of me.. i installed a bunch of stuff using synaptic/apt-get, noticed my install didn't include a lot of stuff i needed.. there has to be something i am missing..

also, i'm noticing a lot of these guides say ndiswrapper comes as binary.. at least, i'm assuming it does.. since there is only mention of compiling from the official install guide.. others include apt-get commands to install (binaries?)..

i didn't post this in the mac/apple/ppc sub-forum because i'm not sure if this is an architecture issue, or if this is a device/driver issue.. 

EDIT: the device uses the rt2500 off the cd.. so i ditched ndiswrapper because it wasn't working at all.. and i tried to use the howto/guide on the wiki for the rt2500 drivers: [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

everything compiled and installed, but my card isn't showing up or anything.. i also tried the rt2500usb drivers from ralink with a ndiswrapper binary i found.. no go..

can anyone help? 

EDIT EDIT: ok after searching around more, i read somewhere that ndiswrapper doesn't work for ppc, is this true? if so, can anyone point me in the direction of what devices have been tested? i think i'm pretty much stuck hunting down an airport card and stuck using 802.11b..

expect a post in the ppc forum about airport and experience with breezy :)

---

