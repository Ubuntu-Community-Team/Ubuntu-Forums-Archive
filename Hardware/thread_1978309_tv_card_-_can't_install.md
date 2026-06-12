---
title: "tv card - can't install"
date: 2012-05-11
forum: Hardware
---

### Post by markobgd on 2012-05-11
Hello,

I have ubuntu 11.10 with 3.0.0-19-generic kernel

Recently i've got intex tv card saa7134 (04:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)) but i can't install it.

I searched google and found two solutions:

First, I have to load module "saa7134" with this options "card=? tuner=?" but I don't know what to enter or how to find out what to enter.
Some guy wrote "By trial and error i am able to find out that values like 37,55 are working fine for me." but that's just insane to go searching value by value...

Second solution is on this link [http://ubuntuforums.org/showthread.php?t=626780](http://ubuntuforums.org/showthread.php?t=626780) 
Author of that thread said that he recompiled kernel after changing "values of .vmux and .gpio values between comp2 and tv" in saa7134-cards.c , but i don't have saa7134-cards.c on my machine.

this is lsmod|grep saa

saa7134 181851 0 
rc_core 26963 9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_flyvide o,saa7134
videobuf_dma_sg 19354 1 saa7134
videobuf_core 26390 2 saa7134,videobuf_dma_sg
v4l2_common 16454 2 tuner,saa7134
videodev 93004 3 tuner,saa7134,v4l2_common
tveeprom 21249 1 saa7134



here is dmesg| grep saa


[ 16.662067] saa7130/34: v4l2 driver version 0.2.16 loaded
[ 16.662139] saa7134 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 16.662144] saa7130[0]: found at 0000:04:05.0, rev: 1, irq: 20, latency: 64, mmio: 0xfe8ffc00
[ 16.662149] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[ 16.662169] saa7130[0]: board init: gpio is c04000
[ 16.662170] saa7130[0]: there are different flyvideo cards with different tuners
[ 16.662171] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[ 16.662172] saa7130[0]: option to override the default value.
[ 16.696143] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:14.4/0000:04:05.0/rc/rc0/input5
[ 16.696182] rc0: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:14.4/0000:04:05.0/rc/rc0
[ 16.800261] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 17.292098] saa7130[0]: registered device video0 [v4l2]
[ 17.292114] saa7130[0]: registered device vbi0
[ 17.292133] saa7130[0]: registered device radio0


this is what i have done so far:
1) lspci -vnn
the result was:
04:05.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
Subsystem: Philips Semiconductors Behold TV 401 [1131:0000]
Flags: bus master, medium devsel, latency 64, IRQ 20
Memory at fe8ffc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: [40] Power Management version 1
Kernel driver in use: saa7134
Kernel modules: saa7134


2) i looked some list ov tv cards that i found on google and there stands:
67 -> Beholder BeholdTV 409 FM [0000:4091]
118 -> Beholder BeholdTV 401 [0000:4016]
119 -> Beholder BeholdTV 403 [0000:4036]
120 -> Beholder BeholdTV 403 FM [0000:4037]
121 -> Beholder BeholdTV 405 [0000:4050]
122 -> Beholder BeholdTV 405 FM [0000:4051]
123 -> Beholder BeholdTV 407 [0000:4070]
124 -> Beholder BeholdTV 407 FM [0000:4071]
125 -> Beholder BeholdTV 409 [0000:4090]
126 -> Beholder BeholdTV 505 FM [5ace:5050]
127 -> Beholder BeholdTV 507 FM / BeholdTV 509 FM [5ace:5070,5ace:5090]
128 -> Beholder BeholdTV Columbus TV/FM [0000:5201]
129 -> Beholder BeholdTV 607 FM [5ace:6070]
130 -> Beholder BeholdTV M6 [5ace:6190]
142 -> Beholder BeholdTV H6 [5ace:6290]
143 -> Beholder BeholdTV M63 [5ace:6191]
144 -> Beholder BeholdTV M6 Extra [5ace:6193]
159 -> Beholder BeholdTV 505 RDS [0000:505B]
160 -> Beholder BeholdTV 507 RDS [0000:5071]
161 -> Beholder BeholdTV 507 RDS [0000:507B]
162 -> Beholder BeholdTV 607 FM [5ace:6071]
163 -> Beholder BeholdTV 609 FM [5ace:6090]
164 -> Beholder BeholdTV 609 FM [5ace:6091]
165 -> Beholder BeholdTV 607 RDS [5ace:6072]
166 -> Beholder BeholdTV 607 RDS [5ace:6073]
167 -> Beholder BeholdTV 609 RDS [5ace:6092]
168 -> Beholder BeholdTV 609 RDS [5ace:6093]
171 -> Beholder BeholdTV X7 [5ace:7595]
176 -> Beholder BeholdTV 505 RDS [0000:5051]
178 -> Beholder BeholdTV H7 [5ace:7190]
179 -> Beholder BeholdTV A7 [5ace:7090]

so i assumed that my card number is 118

3) i run next commands:
rmmod saa7134_alsa; rmmod saa7134; modprobe saa7134 card=118

and started tvtime - on "television" input there was only one channel that i could watch...


4) then i run tvtime-scanner but no other channel was found


5) then i used this script to find my tuner number because i thought that it's maybe tuner problem

#/bin/sh
MAXTUNER=85
for i in $(seq 0 $MAXTUNER);
do
rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=118 tuner=$i
echo "Actual tuner is:" $i
sleep 1 # this is to make sure /dev/video is registered when tvtime starts
tvtime
done


but on every tuner number from 0 to 85 was the same - i could watch only one channel


6) then i entered 'options saa7134 card=118' into '/etc/modprobe.d/saa7134.conf'

7) restarted computer

it was the same as before - i could only watch one channel

this morning i started again tvtime, but now i even don't have that one channel...

does anyone have any idea what i should do?
tnx :-)

---

