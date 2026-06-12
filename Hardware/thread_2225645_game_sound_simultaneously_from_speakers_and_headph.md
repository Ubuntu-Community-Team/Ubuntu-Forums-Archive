---
title: "game sound simultaneously from speakers and headphones"
date: 2014-05-22
forum: Hardware
---

### Post by dodik121 on 2014-05-22
hello please help  game sound simultaneously from speakers and headphones xubuntu 14.04 sorry for my english i dont speak english

 this procedure not working
[COLOR=#333333][FONT=ubuntu]added this line at the end of /etc/modprobe.d/alsa-base.conf:[/FONT][/COLOR]

[COLOR=#333333][FONT=ubuntu]options snd-hda-intel model=generic

motherboard:
[/FONT][/COLOR][COLOR=#333333][FONT=ubuntu]gigabyte GA-EP45-UD3L  audio : Realtek ALC888 codec.

[/FONT][/COLOR]neither option does not work:

 ALC88x/898/1150======================
  acer-aspire-4930g	Acer Aspire 4930G/5930G/6530G/6930G/7730G
  acer-aspire-8930g	Acer Aspire 8330G/6935G
  acer-aspire		Acer Aspire others
  inv-dmic		Inverted internal mic workaround
  no-primary-hp		VAIO Z/VGC-LN51JGB workaround (for fixed speaker DAC)


sudo leafpad /etc/modprobe.d/alsa-base.conf 


ALC882/883/885/888/889
======================
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  arima         Arima W820Di1
  targa         Targa T8, MSI-1049 T8
  asus-a7j      ASUS A7J
  asus-a7m      ASUS A7M
  macpro        MacPro support
  mb5           Macbook 5,1
  macmini3      Macmini 3,1
  mba21         Macbook Air 2,1
  mbp3          Macbook Pro rev3
  imac24        iMac 24'' with jack detection
  imac91        iMac 9,1
  w2jc          ASUS W2JC
  3stack-2ch-dig        3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig     6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire   Acer Aspire 9810
acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion        Medion Laptops
  targa-dig     Targa/MSI
  targa-2ch-dig Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e   Lenovo 101E
  lenovo-nb0763 Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66     Haier W66
  3stack-hp     HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell   Dell machines with 6stack (Inspiron 530)
  mitac         Mitac 8252D
  clevo-m540r   Clevo M540R (6ch + digital)
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
 3stack-6ch-intel Intel DG33* boards
  intel-alc889a Intel IbexPeak with ALC889A
  intel-x58     Intel DX58 with ALC889
  asus-p5q      ASUS P5Q-EM boards
  mb31          MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto          auto-config reading BIOS (default)

please help

---

