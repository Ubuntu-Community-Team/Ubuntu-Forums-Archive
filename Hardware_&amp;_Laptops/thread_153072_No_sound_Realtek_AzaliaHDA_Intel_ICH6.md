---
title: "No sound: Realtek Azalia/HDA Intel ICH6"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by saurabhnanda on 2006-03-31
I've bought a new Acer 4061NWLCi laptop. Almost everything worked out of the box except the sound and the battery status.

I tried to get the sound working by following the intructions given at [HDAIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29) but I ran into troubles.

1. I downloaded the alsa-source-1.0.9b-4 package and looked around for the "azx" driver but it wasn't there.
2. I downloaded the alsa source of the ALSA website -- version 1.0.10 -- no "azx" driver there too.
3. I downloaded version 1.0.11rc4 as well -- again no luck. 

**Where/how can I get the driver for my sound card?**

**Ubuntu version:** Ubuntu 5.10 Breezy Badger
**Kernel Version:** 2.6.12-10-386
**lspci output:** 0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

A CD along with my laptop has windows drivers for the sound card and a setup.ini file on it says:
AppName=Realtek Azalia Audio Driver
ProductGUID=f132af7f-7bca-4ede-8a7c-958108fe7dbc
CompanyName=Realtek Semiconductor Corp.

Apart from that -- can anyone tell me which sound card do I really have? An Intel card or a Realtek card?

TIA
Nandz.

---

### Post by saurabhnanda on 2006-04-01
Finally! **Sound works!** Here is what I did:

1. Compiled & installed the 2.6.16.1 kernel (source downloaded off [http://kernel.org](http://kernel.org))
2. Created the initrd image for my custom kernel
3. Download and compiled alsa-1.0.11rc4 driver. Steps for compilation
# tar -jxf alsa-driver-1.0.11rc4.tar.bz2
# cd alsa-driver-1.0.11rc4
# ./configure --with-cards=hda-intel
# make
# make install
4. Loaded the brand new kernel module
# modrpobe snd-hda-intel

Gnome popped up a window telling me about a new sound device. Fixed the volume settings and the next minute I was listening to music on XMMS [:)]

---

