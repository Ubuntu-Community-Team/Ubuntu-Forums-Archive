---
title: "Headphones do not mute speakers-FIX"
date: 2009-02-20
forum: Hardware
---

### Post by kitts on 2009-02-20
This is a solution for the benefit of all. 
Those of using 8.10 Ubuntu intrepid (in my case) might have noticed that the ALSA drivers play the sound ..but it is not upto the mark.
It may not be able to 

1) play sound from all the speakers if it is a 4.1 or 5.1 supported  speakers. and or 
2) Insertion of headphones into the jack does not automatically mute your speakers. The speakers and headphones continue to play simultaneously.

The following is the fix.

1) first find out your soundcard MODEL by checking it in the terminal
  type  > "sudo cat /proc/asound/card0/codec#* | grep Codec"
you'll get the manufacturers name followed by some number like for example
> "Codec: Realtek ALC888"  Note down the ALCxxx number.

2) check the ALCxxx number against the following list.

```
Model name Description
---------- -----------
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
will Will laptops (PB V7900)
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
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant 5045
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
```

Under your corresponding ALCxxxor other number you'll find "xxx-dig".
This is your MODEL number.

THen Run ```
"sudo gedit /etc/modprobe.d/alsa-base
```" and add the following line to the script:
```
options snd-had-intel model=MODEL
```

where MODEL is the one you discovered above. Save it and reboot.
ON reboot open the volume control and click preferences and select all boxes you find there. This will give additional options on the playback panel. Adjust them and you'll find that all speakers are working and the headphones are able to cutoff sound from speakers when inserted in jack.

---

### Post by EliteBlack on 2009-02-20
As you will probably notice im new to unbuntu but i have the same problem and i have the ALC262 and following your instructions i see nothing that has "xxx-dig" in the listing here

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

---

### Post by kitts on 2009-02-28
Any suggestions for the above problem. How do i know my exact MODEL number?

---

### Post by a person on 2009-03-26
I did:

```

aperson@blue:~$ sudo cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

```

I have no idea where this xxx-dig number is.

Anyone?

---

### Post by pabloferz on 2009-05-11
Hi

For everyone asking what is the 'MODEL number' you should use. You have to use the first number in the line that fits to your computer model.

For example, I have an Acer Aspire 5530, and I'm using the Realtek ALC888 codec. So the line for me was the one in bold and the 'MODEL number' the one underlined (acer).

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
**_acer_ Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)**
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

If I've had a Lenovo NB0763, I should have used 'lenovo-nb0763'

Hope it'll be useful.

---

### Post by nmfralich on 2009-11-12
If I may bring this thread up to date.  I now have Karmic installed but still have trouble with my sound settings.  Firstly, I've tried this patch before with little success.  However, I believe the fix here has a typo.  I believe it should read

options snd-hda-intell model=MODEL

my second concern is that I have a lenovo y510 and see nowhere a reference to a lenovo 500 series...can anybody shed some light on these two issues?

---

### Post by prince2689 on 2009-12-27
thanks buddy......................:):):P:P:):)

---

### Post by Marvin666 on 2009-12-27
Running jaunty xubuntu on an msi. Tried it, but it didn't work. For some reason on my machine, that file was empty before I edited it.

---

### Post by googeek on 2010-02-28
If the file shows up blank for you, try base.conf

mine showed up blank without the conf as well.

Still can't get it to work but I think it's because my model isn't listed, just been taking shots in the dark...

---

