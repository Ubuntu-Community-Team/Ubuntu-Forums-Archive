---
title: "Ubuntu detecting incorrect driver"
date: 2010-04-08
forum: Hardware
---

### Post by Macus on 2010-04-08
Hi

I posted this in the mythbunu section, and it hasn't gotten any replys. also its more a hardware issue than mythtv

Basically its a TV tuner that was working fine before
then after I upgraded to 9.10 its now getting detect as:

"Philips Semiconductors SAA7130 Video
Kernel driver in use: saa7134"
when (according to [http://www.mythtv.org/wiki/Leadtek_DTV-1000T](http://www.mythtv.org/wiki/Leadtek_DTV-1000T))
its meant to be "Conexant 2388x" using "cx88-dvb".

It is mounted to /dev/video0 (but doesn't work), it needs to be in /dev/dvb/adapter1

my other card 
("multimedia controller: Conexant Systems" using "Kernel driver in use: cx88-mpeg driver manager")
which is is working fine (mounted at /dev/dvb/adapter0), iv added everything I could think of to /etc/modules

So to me it looks like it just needs to be told what driver to use.

any help is appreciated, my ubuntu box is almost perfect and I cant think of any other way to fix this other than reinstall (which id rather not do)

Thanks.

---

### Post by Macus on 2010-04-10
Bump

I really need help with this :confused:

---

### Post by iponeverything on 2010-04-10
did you have working myth before? I am kind of curious about why you upgraded. I don't mess with our myth box unless there is a problem, my wife gets a little cranky if she misses American Idol.

What I would do is to first manually remove the incorrect module and manually insert the correct one, then check messages to if it picked it up correctly. Or you could blacklist the incorrect module and reboot the box..

---

### Post by Macus on 2010-04-10
Well I upgraded because I wanted to use a non pxe front end on my eeepc (as the pxe requires a wired lan) so I could watch tv on it anywhere in the house on the wifi

but when I installed it, it informed me that the schema was incompatible and I should update it 

I Googled it for a while and they said to open mythtv-setup and it should ask to update, which it did not

so I poked around the update manager thing and it was like do you want to upgrade to 9.10 

Seemed like an alright idea so I did. it worked when I opened mythtv-setup it asked to update the schema, also I do like the new themes

when and fixed up other issues like update the pxe server to 9.10, fixed LIRC 

so now everything is working great except the 2nd tuner

---

### Post by Macus on 2010-04-10
Blacklisting hasn't helped
it just removed the line that says 
"Kernel driver in use: saa7134"

01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f3001000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel modules: saa7134

---

### Post by IcarusR on 2010-04-10
If ubuntu is detecting the card as....

> 01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

Then...

> Kernel driver in use: saa7134 

is correct.

If you read on 
[http://linuxtv.org/wiki/index.php/Main_Page]("http://linuxtv.org/wiki/index.php/Main_Page")
you will find links to instructions howto get this card working with saa7134 module.

Suggest use of Google !!

---

### Post by Macus on 2010-04-10
Explain this then

[http://www.mythtv.org/wiki/Leadtek_DTV-1000T](http://www.mythtv.org/wiki/Leadtek_DTV-1000T)
"Leadtek DTV-1000T
   * Chipset: Conexant 2388x
   * Kernel module: cx88-dvb (Card type autodetected)
"

To my logic the card is using the wrong module and is not being auto detected as a digital tuner

and on the right of the page you gave me we can clearly see that saa7134 is an analogue tuner, which the DTV-1000T is not

Suggest reading the post

---

### Post by IcarusR on 2010-04-10
Post output of the following terminal command 
```
lspci
```

lspci will tell us what chipset your card is.

Sometimes manufacturers change the chipsets in their products. 

Where did this come from

> "Philips Semiconductors SAA7130 Video Kernel driver in use: saa7134"

If it came from log files it should be reporting the chipset of your card.
In which case it will need to use saa7134 module & not cx88-dvb.

Before you upgraded to 9.10 what was this card identified as ?? & which module did it use ??


> Chipset: Conexant 2388x 
Is also listed on that page as analogue tuner.

So are both tuner cards the same ??

Have you tried setting up with saa7134 as per this page ?...

[http://linuxtv.org/wiki/index.php/Saa713x_devices:_Generic_SAA7134_Card_Installation]("http://linuxtv.org/wiki/index.php/Saa713x_devices:_Generic_SAA7134_Card_Installation")

---

### Post by Macus on 2010-04-10
No, one is a terratec cinergy 1400 dvb-t which is working fine
the other Leadtek winfast DTV-1000T

they are both digital receivers and isn't the saa7134 an analogue driver?
if I open mythtv-setup it sees both of them under "analogue V4L" (they have analogue composite) however the leaktek card is identified as UNKNOWN/GENERIC
but for "DVB DTV capture card" (as thats how it was setup before) only the terratec shows up.
they should both be in /dev/dvb/

lspci -v

01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f3001000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

01:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: TERRATEC Electronic GmbH Device 1166
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

01:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: TERRATEC Electronic GmbH Device 1166
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802


Im not sure what it was before the upgrade
However I do remember using this [http://kernellabs.com/hg/~mkrufky/dtv1000s/archive/tip.tar.gz](http://kernellabs.com/hg/~mkrufky/dtv1000s/archive/tip.tar.gz)

il move it to another box see what it says

---

### Post by Macus on 2010-04-11
The Test box (mythbuntu 9.10) shows the same thing

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/763854.html:](http://forums.whirlpool.net.au/forum-replies-archive.cfm/763854.html:)
> 02:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
Subsystem: LeadTek Research Inc. WinFast DTV1000-T
Flags: bus master, medium devsel, latency 32, IRQ 12
Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
Capabilities: [44] Vital Product Data
Capabilities: [4c] Power Management version 2

02:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
Subsystem: LeadTek Research Inc.: Unknown device 665f
Flags: bus master, medium devsel, latency 32, IRQ 12
Memory at e3000000 (32-bit, non-prefetchable) [size=16M]
Capabilities: [4c] Power Management version 2

thats what it meant to show up as

---

### Post by Macus on 2010-04-27
So No one knowns any way to force a device to use a specific driver?

---

### Post by songoku10 on 2010-04-28
I'm looking for the same thing... if you are able to force a device to use an specific module please post...

---

### Post by Macus on 2010-05-23
Im finding it somewhat concerning that no one is able to post up how to do basic driver manipulation

I also find it worrying how theres no information on how to force drivers to devices, something which is child's play under windows

there must be ways to do it
if anyone has any info please post

---

### Post by dino99 on 2010-05-23
> **Macus said:**
> Im finding it somewhat concerning that no one is able to post up how to do basic driver manipulation

I also find it worrying how theres no information on how to force drivers to devices, something which is child's play under windows

there must be ways to do it
if anyone has any info please post

better to ask your request on launchpad, devs knows what you want

---

### Post by IcarusR on 2010-05-23
You could try modprobing the correct module with the card number as an option. ie..

```
modprobe cx88-dvb card=X
```

Where X is the card number.

I did see a list of cards & number on the net somewhere but can not find it now.

---

### Post by Wes Baker on 2010-10-09
Macus, did you ever fix your problem?  Im have similar issues with a Kworld DVBt-100 since my upgrade to lucid

---

### Post by Wes Baker on 2010-10-09
Also, This might help for anyone looking for the list of available card types:

[   37.811276] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   37.811282] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   37.811285] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   37.811289] cx88[0]:    card=2 -> GDI Black Gold
[   37.811292] cx88[0]:    card=3 -> PixelView
[   37.811295] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   37.811299] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   37.811303] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   37.811307] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   37.811310] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   37.811314] cx88[0]:    card=9 -> Leadtek PVR 2000
[   37.811317] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   37.811321] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   37.811324] cx88[0]:    card=12 -> ASUS PVR-416
[   37.811328] cx88[0]:    card=13 -> MSI TV-@nywhere
[   37.811332] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   37.811336] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   37.811340] cx88[0]:    card=16 -> KWorld LTV883RF
[   37.811343] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   37.811347] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   37.811351] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   37.811354] cx88[0]:    card=20 -> Provideo PV259
[   37.811358] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   37.811362] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   37.811366] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   37.811370] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   37.811374] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   37.811379] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   37.811382] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   37.811387] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   37.811391] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   37.811396] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   37.811400] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   37.811404] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   37.811409] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   37.811413] cx88[0]:    card=34 -> ATI HDTV Wonder
[   37.811416] cx88[0]:    card=35 -> WinFast DTV1000-T
[   37.811419] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   37.811423] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   37.811426] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   37.811430] cx88[0]:    card=39 -> KWorld DVB-S 100
[   37.811434] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   37.811438] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   37.811443] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   37.811447] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   37.811451] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   37.811455] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   37.811447] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   37.811451] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   37.811455] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   37.811459] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   37.811463] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   37.811467] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   37.811470] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   37.811474] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   37.811478] cx88[0]:    card=51 -> WinFast DTV2000 H
[   37.811481] cx88[0]:    card=52 -> Geniatech DVB-S
[   37.811485] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   37.811490] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   37.811494] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   37.811498] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder

---

