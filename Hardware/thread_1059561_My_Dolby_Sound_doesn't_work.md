---
title: "My Dolby Sound doesn't work"
date: 2009-02-03
forum: Hardware
---

### Post by CoraCoronel on 2009-02-03
Hi
This is my first Lap and SO Ubuntu. I'm running Intrepid in a Toshiba A 205 SP 5820. All works fine, except the volumne of sound, is so low!!
So I hope someone help me please.
Thanks

---

### Post by Paconator on 2009-04-06
> **CoraCoronel said:**
> Hi
This is my first Lap and SO Ubuntu. I'm running Intrepid in a Toshiba A 205 SP 5820. All works fine, except the volumne of sound, is so low!!
So I hope someone help me please.
Thanks

I Have the exact same problem and i think that you can fix it by upgrading the driver, I'll let you know when i fix it. 

Or it someone told us how to fix it it would be great, 'cause i am an absolute beginner with this kind of things.

---

### Post by Paconator on 2009-04-06
You can try to turn the volume up introducing in a terminal the command: "alsamixer"  (the quote is mine), the problem to some people was that the front option volumen was too low.

If that doesn't worked, I  managed to turn the volumen up a bit, it's not as loud as it is on windows but at least it is luoder then before:

	
SOLUTION
After searching and searching for information I met with this "guide" who have kept up my system 100% functional (well, I mean to make the headphones work properly:

"... The problem: The default configuration of ALSA is not always suitable for all laptops, and some, like me, has some small problems that are not difficult to solve. Some of the" symptoms "are that by plugging headphones the sound still coming out of the speakers, to raise the maximum volume of laptop is heard as a hum or static and the volume controls do not respond very well.

My machine: The solution worked well written that I leave my laptop is a VAIO VGN-NR310 working with Ubuntu 8.04 (Hardy Heron) and sound card with Intel chip.

The solution: The first thing to do is find out what type of card we are using, and so we must go to Terminal and type: aplay-l

We will return something like this:

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]

Subdispositivos: 1 / 1

Subdispositivo # 0: subdevice # 0

What interests us is the part that says ALC262. With this
data must edit a file. In the terminal

sudo gedit / etc / modprobe.d / alsa-base

This file included at the end of it:

options snd-hda-intel model = XXXX

where XXXX is the first word that appears below
the list for your card and will best suit the brand of your computer:

Example: In my case, I find ALC262, and I have a sony, add the following line:
options snd-hda-intel model = sony-assamd save changes and exit. Reboot and test if there is sound and if everything works correctly. While the test to verify that this high volume of sound, otherwise it will not naturally sonido.Si the above option does not work try another option on the list.

It is all, I hope that someone will prove, and if so
I ask them to add a comment as the model and features of their machines in order to know what works.

ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

ALC260
hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
will Will laptops (PBV7900)
replacer Replacer 672V
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

ALC262
fujitsu Fujitsu Laptop
hp-bpc HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000 HP BPC D7000
benq Benq ED8
benq-t31 Benq T31
hippo Hippo (ATI) with jack detection, Sony UX-90s
hippo_1 Hippo (Benq) with jack detection
sony-assamd Sony ASSAMD
basic fixed pin assignment w/o SPDIF
auto auto-config reading BIOS (default)

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)

ALC662
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
auto auto-config reading BIOS (default)

ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

CMI9880
minimal 3-jack in back
min_fp 3-jack in back, 2-jack in front
full 6-jack in back, 2-jack in front
full_dig 6-jack in back, 2-jack in front, SPDIF I/O
allout 5-jack in back, 2-jack in front, SPDIF out
auto auto-config reading BIOS (default)

AD1882
3stack 3-stack mode (default)
6stack 6-stack mode

AD1884
N/A

AD1981
basic 3-jack (default)
hp HP nx6320
thinkpad Lenovo Thinkpad T60/X60/Z60
toshiba Toshiba U205

AD1983
N/A

AD1984
basic default configuration
thinkpad Lenovo Thinkpad T61/X61

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet
PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant
5045
laptop Laptop config
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

Conexant 5047
laptop Basic Laptop config
laptop-hp Laptop config for some HP models (subdevice 30A5)
laptop-eapd Laptop config with EAPD support
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

STAC9200
ref Reference board
dell-d21 Dell (unknown)
dell-d22 Dell (unknown)
dell-d23 Dell (unknown)
dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
dell-m22 Dell Latitude D620, Dell Latitude D820
dell-m23 Dell XPS M1710, Dell Precision M90
dell-m24 Dell Latitude 120L
dell-m25 Dell Inspiron E1505n
dell-m26 Dell Inspiron 1501
dell-m27 Dell Inspiron E1705/9400

STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

STAC9220/9221
ref Reference board
3stack D945 3stack
5stack D945 5stack + SPDIF
intel-mac-v1 Intel Mac Type 1
intel-mac-v2 Intel Mac Type 2
intel-mac-v3 Intel Mac Type 3
intel-mac-v4 Intel Mac Type 4
intel-mac-v5 Intel Mac Type 5
macmini Intel Mac Mini (equivalent with type 3)
macbook Intel Mac Book (eq. type 5)
macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel Intel iMac (eq. type 2)
imac-intel-20 Intel iMac (newer version) (eq. type 3)
dell-d81 Dell (unknown)
dell-d82 Dell (unknown)
dell-m81 Dell (unknown)
dell-m82 Dell XPS M1210

STAC9202/9250/9251
ref Reference board, base config
m2-2 Some Gateway MX series laptops
m6 Some Gateway NX series laptops
pa6 Gateway NX860 series

STAC9227/9228/9229/927x
ref Reference board
3stack D965 3stack
5stack D965 5stack + SPDIF
dell-3stack Dell Dimension E520

STAC9872
vaio Setup for VAIO FE550G/SZ110
vaio-ar Setup for VAIO AR 

I got this info on: [http://www.ubuntu-es.org/index.php?q=node/103227](http://www.ubuntu-es.org/index.php?q=node/103227) and i made the translation, i really hope this help you.

Note: The "aplay-l" command didn't worked for me so i use the "ALC268" to do my process.

---

### Post by Favux on 2009-04-06
Hi Paconator,

I think it's suppose to be aplay space dash little-L.  Like:
```
aplay -l
```
Give it a try.

---

### Post by Paconator on 2009-04-06
It works perfectly when i use "aplay -l"
Thanks

---

