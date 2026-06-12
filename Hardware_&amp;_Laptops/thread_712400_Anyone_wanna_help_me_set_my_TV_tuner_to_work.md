---
title: "Anyone wanna help me set my TV tuner to work ?"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by b0rka7a on 2008-03-01
Hi guys :)
My tv tuner is PixelView PlayTV Pro with stereo and tvtime cant scan for channels. Any ides ?
Thanks :)

**Edit: **I used xawtv to scan for my tv tuner and here's the output:
```
boris@ubuntu:~$ xawtv -hwscan
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UNKNOWN/GENERIC
    flags:  capture  

boris@ubuntu:~$
```

**Edit 2: **Here's what dmesg says:
```
..............
[   32.902103] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   32.902105] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   32.902106] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   32.902108] cx88[0]: the TV card.  Best regards,
[   32.902109] cx88[0]:         -- tux
[   32.969787] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   32.983390] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   32.996722] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   33.009852] cx88[0]:    card=2 -> GDI Black Gold
[   33.022840] cx88[0]:    card=3 -> PixelView
[   33.035696] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   33.048420] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   33.061110] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   33.073631] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   33.086093] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   33.098701] cx88[0]:    card=9 -> Leadtek PVR 2000
[   33.111189] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   33.123651] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   33.136054] cx88[0]:    card=12 -> ASUS PVR-416
[   33.148407] cx88[0]:    card=13 -> MSI TV-@nywhere
[   33.160721] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   33.173081] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   33.185430] cx88[0]:    card=16 -> KWorld LTV883RF
[   33.197736] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   33.210059] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   33.222314] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   33.234600] cx88[0]:    card=20 -> Provideo PV259
[   33.246765] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   33.258896] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   33.270879] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   33.282838] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   33.294712] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   33.306706] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   33.318609] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   33.330577] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   33.342377] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   33.354021] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   33.365523] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   33.376934] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   33.388415] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   33.399778] cx88[0]:    card=34 -> ATI HDTV Wonder
[   33.410875] cx88[0]:    card=35 -> WinFast DTV1000-T
[   33.421650] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   33.432111] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   33.442481] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   33.452495] cx88[0]:    card=39 -> KWorld DVB-S 100
[   33.462173] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   33.471835] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   33.481294] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   33.490627] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   33.499966] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   33.509245] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   33.518560] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   33.527761] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   33.536743] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   33.545695] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   33.554623] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   33.563629] cx88[0]:    card=51 -> WinFast DTV2000 H
[   33.572626] cx88[0]:    card=52 -> Geniatech DVB-S
[   33.581523] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   33.590711] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   33.599884] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   33.609331] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   33.618964] CORE cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   33.628949] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   33.760906] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   33.771311] cx88[0]/0: found at 0000:02:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xeb000000
[   33.848788] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   33.895818] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   33.921547] cx88[0]/0: registered device video0 [v4l2]
[   33.932431] cx88[0]/0: registered device vbi0
[   33.943160] tuner 0-0061: tuner type not set
..............
```

---

### Post by super breadfish on 2008-03-01
Looks like Ubuntu can't identify your TV card, so you'll need to manually give it a card and tuner number. From your dmesg output I'd say start with cards 59 or 27.
If I remember correctly you need to put them in /etc/modprobe.d/options

There are also a couple of scripts to find the right settings automatically, though they don't seem to work for a lot of people.

---

### Post by b0rka7a on 2008-03-02
Thank you for the reply. I didn't know what exactly to add in /etc/modprobe.d/options, but I found this on the net for Debian 4.0:
> Type as root:
```
rmmod bttv
rmmod cx8800
rmmod cx88xx
```

Next type:
```
modprobe cx88xx card=27 tuner=38 i2c_scan=1
modprobe cx8800
```

You don't need bttv, because it's incompatible with this card.
For check - dmesg

Here's the output of dmesg now:
```
.......
[41144.115009] CORE cx88[0]: subsystem: 0000:0000, board: PixelView PlayTV Ultra Pro (Stereo) [card=27,insmod option]
[41144.115014] TV tuner 38 at 0x1fe, Radio tuner -1 at 0x1fe
[41144.239225] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[41144.239361] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[41144.239365] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[41144.240981] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[41144.327617] cx88[0]: i2c scan: found device @ 0xc2  [tuner (analog/dvb)]
[41144.328864] cx88[0]: i2c scan: found device @ 0xc6  [???]
[41144.353495] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[41144.353730] input: cx88 IR (PixelView PlayTV Ultra as /class/input/input7
[41144.353875] cx88[0]/0: found at 0000:02:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xeb000000
[41144.361069] cx88[0]/0: registered device video0 [v4l2]
[41144.361201] cx88[0]/0: registered device vbi0
[41144.361294] cx88[0]/0: registered device radio0
boris@ubuntu:~$
```
And the output of `xawtv -hwscan`:
```
boris@ubuntu:~$ xawtv -hwscan
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : PixelView PlayTV Ultra Pro (Ste
    flags:  capture tuner 

boris@ubuntu:~$
```
tvtime found some channels, but the picture is Bad. Look at the screenshot ...
[ATTACH]61358[/ATTACH]
What's up with that ?

---

### Post by b0rka7a on 2008-03-02
Come on people !! Help me fix it !!

---

### Post by super breadfish on 2008-03-06
Probably the wrong tuner/card. I did some reading and some are using tuner 5, and cards 3 and 11. Substitute those into the commands you've been using. There seem be several variations of this card so it might take a bit of experimenting. You could also try looking on the TV card. Tuner information is often printed on it.

Sorry about the modprobe.d thing, I probably didn't explain myself very well.  If you want to do it this way, edit the file:

```
gksudo gedit /etc/modprobe.d/options
```

and add something like this to the bottom:

```
options cx8800 video_nr=0 radio_nr=0
options cx88xx card=3 tuner=5
```

cx88xx is the chipset of your TV card, card=3 is the card number, and tune=5 is the tuner number. You then need to reload the module:

```
modprobe -r cx8800
modprobe -r tuner
modprobe cx880
```

I also recommend checking your TV aerial, you never know. If you are using one of those little indoor aerials they often bundle with TV cards it might not be up to the job.

---

### Post by b0rka7a on 2008-03-07
thanks, i'll try this :)

---

### Post by b0rka7a on 2008-03-07
No, it's not working.... I only see the same bad picture ;( Why everything must be SO hard ?!?!?!

---

### Post by oldsoundguy on 2008-03-07
You have several Pixel views from which to choose for your setup according to the list you posted.  Try them all .. one at a time.

Sort of like trying different printer drivers to get the one that works for you.

---

### Post by b0rka7a on 2008-03-07
I know, I tried everything - card=27, 11, 3, 49... not working.

---

