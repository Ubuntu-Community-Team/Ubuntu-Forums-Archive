---
title: "panasonic cf-y5 no sound out of speakers, snd-hda-intel"
date: 2009-10-18
forum: Hardware
---

### Post by discord on 2009-10-18
Hello, 

I have a panasonic cf-y5 with the ICH7 chipset.
I'm trying to figure out the model= option to get my audio to work from the speakers and mute when the headphone is plugged in. I have tried model=panasonic , which does not work. There are quite a lot of model options. Is there a way to test the model without having to reboot?


discord@crystal:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
discord@crystal:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


STAC9200
========
  ref		Reference board
  dell-d21	Dell (unknown)
  dell-d22	Dell (unknown)
  dell-d23	Dell (unknown)
  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
  dell-m22	Dell Latitude D620, Dell Latitude D820
  dell-m23	Dell XPS M1710, Dell Precision M90
  dell-m24	Dell Latitude 120L
  dell-m25	Dell Inspiron E1505n
  dell-m26	Dell Inspiron 1501
  dell-m27	Dell Inspiron E1705/9400
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)

STAC9205/9254
=============
  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)

STAC9220/9221
=============
  ref		Reference board
  3stack	D945 3stack
  5stack	D945 5stack + SPDIF
  intel-mac-v1	Intel Mac Type 1
  intel-mac-v2	Intel Mac Type 2
  intel-mac-v3	Intel Mac Type 3
  intel-mac-v4	Intel Mac Type 4
  intel-mac-v5	Intel Mac Type 5
  intel-mac-auto Intel Mac (detect type according to subsystem id)
  macmini	Intel Mac Mini (equivalent with type 3)
  macbook	Intel Mac Book (eq. type 5)
  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
  imac-intel	Intel iMac (eq. type 2)
  imac-intel-20	Intel iMac (newer version) (eq. type 3)
  ecs202	ECS/PC chips
  dell-d81	Dell (unknown)
  dell-d82	Dell (unknown)
  dell-m81	Dell (unknown)
  dell-m82	Dell XPS M1210
  auto		BIOS setup (default)

STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  auto		BIOS setup (default)

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  auto		BIOS setup (default)

STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  auto		BIOS setup (default)

STAC92HD83*
===========
  ref		Reference board
  mic-ref	Reference board with power managment for ports
  dell-s14	Dell laptop
  auto		BIOS setup (default)

---

