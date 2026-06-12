---
title: "Mini-ITX MythBuntu/XBMC HTPC project - Hardware check (Using J&amp;W Mini-ITX 780G Board)"
date: 2009-05-09
forum: Hardware
---

### Post by X00M on 2009-05-09
Ok, I have decided on the hardware for my purchase:

J&W MINIX 780G-SP128MB Mini-ITX

Silverstone BLue-ray slim combo BD player and dvd-writer, based on UJ-120

AMD ATHLON X2 Dual Core 5050e

4GB 800MHz Corsair value SO-DIMM kit

500GB W.D green power or an OCZ 30GB SSD drive.

Now I am venturing into new territory here so bare with me, last time I used linux was a very long time ago, back when red hat 7 was the big daddy. For the first time I want to dump windows for a system/htpc that will be used for entertainment purposes.

To tell you honestly all these detailed instructions/switches/ versions  Jaunty/hardy etc. and driver issues make me want to vomit! 

For a quick test I am about to:

1. Download latest stable Mythbuntu ISO
2. Boot off the cd and install MythUbuntu
3. Install drivers (Do I find Linux drivers from motherboard manufacturers website or is there some Linux driver cave I don't know about?)
4.Install the front end/back-end XBMC package for linux.


Also ATI 780G IGP chipset, I've read people are having trouble with it? In general everyone seems to be suggesting nvidia cards. Now I don't need 5.1 sound over HDMI, I simply want the optical out/coax on my mobbo to output DTV/Dolby bitstream to the receiver.    
     
Ideally I want XBMC to go full screen and auto start up as soon as the OS is loaded. So I get seamless media player like feel, not a linux pc box. MythTV I may use at a later date when I install a TV tuner, but none the less I want XBMC as the primary GUI for my HTPC. 

Also which remote control/receiver combos are best to use with ubuntu and are supported ? Imon, Logitech MCE keyboard etc. Where can I check what is supported and what is not?


Thanks for all your advice..

---

### Post by lefox on 2009-06-13
Be wary with the ATI IGP and ubuntu/xbmc.
I'm no expert but I have been struggling to try to get a configuration based on the mb MA78GM-US2H (same Radeon HD3200 as your mobo), and couldn't get the ubuntu release of XBMC or Moovida working either with the ATI catalyst driver (XBMC starts but I quickly got CPU issues) or the open source driver (XBMC does not even starts, black screen... but I believe that it is normal as the open source does not support acc 3D which is necessary for XBMC).

As I said, I might not have found yet the magic formula and if you do, I'm interested! ;)

Else if you want out-of-the-box HTPC on ubuntu, be careful with this HW.

---

