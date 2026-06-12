---
title: "VoIP and other Problems"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by neo.patrix on 2007-10-06
Now this a long story nearly one full working day wasted without success....

I have SigmaTel STAC9200 sound card. Is having this kind of card a sin,
just like my ATI X1300 graphics card  (i had real pain installing Feisty and Berly, 
i know having ATI card is a sin :twisted: )

Now, i am trying to use Gtalk, i know there is gaim , don't jump to solution. I use it,
i like it. But i want to TALK, not just CHAT.

SO i was trying to setup VoIP, now default software for purpose EGIKA sucks, no stinks!
Obviously my next choice was Jabbin, it work just like Gaim, when i try to make call ,
it acts wierd., useless. It simply has no idea which sound player to use most probably.

I have tried "aoss jabbin", i gives segmentation fault. I have already posted this on Jabbin
forum. (So frankly tell me having SigmaTel is a sin.) Because i do not see support for
SigmaTel on ALSA webpage. (Yes, I am using HDA Intel Alsa, because of all that OSS trouble).

Finally, I gave in on jabbin , decided to try Tapioca, wow! A long list of installations, probably 
everything took more than 100 MB space, god knows i he can understand Frameworks.
But luckly entire frame installed with a small niche, WHERE IS MY VOIP CLIENT?

Oh yes, obviously it has no client , it is a framework, it supplies tools to "develop clients".
Naturally I have to install it separately, because Tapioca webpage does not specify any client.
Therefore I had to download this client development tools like tapioca-glib, tapioca-python.
I managed to install it succesfully (atleast seemingly). I also installed this flimsy Ereseva

I is simply beautiful, it does not understand god damn Tapioca , output after installing all that

```

Traceback (most recent call last):
  File "/usr/local/bin/ereseva", line 25, in <module>
    from ereseva import ereseva
  File "/usr/local/lib/python2.5/site-packages/ereseva/ereseva.py", line 28, in <module>
    import tapioca
  File "/usr/local/lib/python2.5/site-packages/tapioca-0.14/tapioca/__init__.py", line 2, in <module>
    from _client import *
ImportError: /usr/local/lib/python2.5/site-packages/tapioca-0.14/tapioca/_client.so: undefined symbol: tpa_channel_has_joined

```

[COLOR="Red"]I did restart X, no entire notebook for dbus, before starting erevesa[/COLOR]

Well i thought maybe, I am a sinner, because I have ATI card & SigmaTel card, so I should 
try harder. Hence i decided to try another client "pytapioca". I got package [COLOR="Blue"][here]("http://linux.softpedia.com/get/Communications/Telephony/Tapioca-VoIP-10805.shtml")[/COLOR]

I tried to compile the code,

```

./autogen.sh

```

Poor chap is looking for CLIENT....

```

checking for TAPIOCA_CLIENT... no
configure: error: you need tapioca-client development packages installed !
  configure failed

```

Well, hmmm.....let's get back to Jabbin, maybe....:-k

But then i had this spark of enlightenment, let me first check sound recorder, how bloody
stupid of me, how can i assume that since i had no problems with sound (it worked out of box
, i have not made much changes). But this is not windows, that working sound implies working
capture also. Well you know the answer, It did not work. ](*,)

I followed [COLOR="Blue"][this]("http://ubuntuforums.org/showthread.php?t=206145")[/COLOR] thread as much as I could , by the way i had sleepless night.

Henceforth, lspci, I have no clue if my Soundcard should be here or not

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [ATI Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

By the way if anyone could tell me how to fix "Ricoh Co Ltd. Unknown Devices", but that is off
topic.

The main topic , IS HAVING SigmaTel Card a SIN? If yes, I also have ATI card, Intel PRO/WIreless, should i throw my laptop?.....oh no no, i will use Windows, how foolish
my Intel/PRO driver gives a beautiful blue-screen whenever i try online streaming.....

Oh yeah Thanx for bearing with me till here. :)

---

