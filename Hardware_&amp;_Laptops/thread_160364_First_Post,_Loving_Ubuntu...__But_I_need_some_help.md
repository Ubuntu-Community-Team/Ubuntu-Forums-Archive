---
title: "First Post, Loving Ubuntu...  But I need some help!"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by n00buntu NJ on 2006-04-14
**My introduction (Skip it if you don't want to get too bored to help me)**

Hello all, I'm a total noob at all thing Linux but have taken the dive big time and I love it.  The community is excellent, the How-To's put every other tech project I've ever done to shame.  I work for a global tech company and I'm seriously in awe of my experience with Ubuntu and these forums.  (Kudos to everyone who get's themselves involved...)

On to my scenario:  Like a bunch of other people I've been sucked in by the fancy Compiz desktop stuff.  Last week I installed Ubuntu and got the whole thing up and running on my system, including the Compiz - :o   AMAZING STUFF!  Then I tried to go on to phase two of my project which was getting the Hauppauge PVR150 installed and setup with MythTV, since this box resides in the living room on the 32" LCD HDTV.  (I'd like to put my dinky little Tivo to the grave.)  I was following a great how to but got so far in that I didn't know which way was up and which way was down, somehow screwed up my xorg.conf file so many times (but learned how to work from the old school command line interface in the process and recover my gui)  that I finally decided to wipe the system and start over.

[B]My System (So you know what I'm working with)
[/B]
It's my low-end training wheels for linux:
AMD Sempron 2200 
512MB DDR SDRAM
PNY Verto GeForce 6200 AGP 8X 128MB 
  (Just for playing back video full screen - no games)
Hauppauge PVR150 PCI 
40GB HD 
  (Soon to be 250GB)

[B]
Where I'm Stuck:[/B]

I've been following [THESE]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") instructions which I previously finished but wasn't quite fully functional.  Now, on my second time through, starting with a fresh install of Ubuntu Breezy I've figured out a few things I did wrong the first time and now have part of my problem figured out.  

At the last step of installing the ivtv drivers, where you modprobe ivtv and output the dmesg mine shows the following:


[4296813.804000] ivtv:  ==================== START INIT IVTV =================== =
[4296813.804000] ivtv:  version 0.4.4 (tagged release) loading
[4296813.804000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4296813.805000] ivtv:  In case of problems please include the debug info betwee n
[4296813.805000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4296813.805000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4296813.812000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4296813.812000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> I RQ 17
[4296813.812000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4296813.867000] tveeprom: ivtv version
[4296813.867000] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 93452 36
**[4296813.867000] tveeprom: tuner = <unknown> (idx = 112, type = 4)**
[4296813.867000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4296813.867000] tveeprom: audio processor = CX25843 (type = 25)
[4296813.867000] tveeprom: decoder processor = CX25843 (type = 1e)
[4296813.867000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4296813.897000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4296813.897000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4296814.165000] cx25840 0-0044: ivtv driver
[4296814.165000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4296816.783000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4296816.840000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4296816.869000] wm8775 0-001b: ivtv driver
[4296816.869000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4296816.876000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4296817.640000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4296817.850000] ivtv0: Encoder revision: 0x02050032
[4296817.852000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4296817.854000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4296817.856000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4296817.859000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4296817.859000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[4296818.059000] ivtv0: Initialized WinTV PVR 150, card #0
[4296818.059000] ivtv:  ====================  END INIT IVTV  =================== =


So that's where I'm stuck.  Please help!

---

### Post by jisgod on 2006-04-19
I think that you have a new version of the Hauppauge (did I spell it correct??) card and the ivtv drivers do not recognize the tuner. I had the same error thrown at me. Here is how I got around it...

Edit the /etc/modprobe.d file so that it looks like this

alias char-major-81-0 ivtv
[B]options ivtv tuner=57
[/B]

If 57 does not work for you, you could try other tuners.. There was some link mapping the tuners with these numbers. You can probably google that up. 

-J


[QUOTE=n00buntu NJ]**My introduction (Skip it if you don't want to get too bored to help me)**

Hello all, I'm a total noob at all thing Linux but have taken the dive big time and I love it.  The community is excellent, the How-To's put every other tech project I've ever done to shame.  I work for a global tech company and I'm seriously in awe of my experience with Ubuntu and these forums.  (Kudos to everyone who get's themselves involved...)

On to my scenario:  Like a bunch of other people I've been sucked in by the fancy Compiz desktop stuff.  Last week I installed Ubuntu and got the whole thing up and running on my system, including the Compiz - :o   AMAZING STUFF!  Then I tried to go on to phase two of my project which was getting the Hauppauge PVR150 installed and setup with MythTV, since this box resides in the living room on the 32" LCD HDTV.  (I'd like to put my dinky little Tivo to the grave.)  I was following a great how to but got so far in that I didn't know which way was up and which way was down, somehow screwed up my xorg.conf file so many times (but learned how to work from the old school command line interface in the process and recover my gui)  that I finally decided to wipe the system and start over.

[B]My System (So you know what I'm working with)
[/B]
It's my low-end training wheels for linux:
AMD Sempron 2200 
512MB DDR SDRAM
PNY Verto GeForce 6200 AGP 8X 128MB 
  (Just for playing back video full screen - no games)
Hauppauge PVR150 PCI 
40GB HD 
  (Soon to be 250GB)

[B]
Where I'm Stuck:[/B]

I've been following [THESE]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") instructions which I previously finished but wasn't quite fully functional.  Now, on my second time through, starting with a fresh install of Ubuntu Breezy I've figured out a few things I did wrong the first time and now have part of my problem figured out.  

At the last step of installing the ivtv drivers, where you modprobe ivtv and output the dmesg mine shows the following:


[4296813.804000] ivtv:  ==================== START INIT IVTV =================== =
[4296813.804000] ivtv:  version 0.4.4 (tagged release) loading
[4296813.804000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4296813.805000] ivtv:  In case of problems please include the debug info betwee n
[4296813.805000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4296813.805000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4296813.812000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4296813.812000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> I RQ 17
[4296813.812000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4296813.867000] tveeprom: ivtv version
[4296813.867000] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 93452 36
**[4296813.867000] tveeprom: tuner = <unknown> (idx = 112, type = 4)**
[4296813.867000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4296813.867000] tveeprom: audio processor = CX25843 (type = 25)
[4296813.867000] tveeprom: decoder processor = CX25843 (type = 1e)
[4296813.867000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4296813.897000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4296813.897000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4296814.165000] cx25840 0-0044: ivtv driver
[4296814.165000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4296816.783000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4296816.840000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4296816.869000] wm8775 0-001b: ivtv driver
[4296816.869000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4296816.876000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4296817.640000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4296817.850000] ivtv0: Encoder revision: 0x02050032
[4296817.852000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4296817.854000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4296817.856000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4296817.859000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4296817.859000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[4296818.059000] ivtv0: Initialized WinTV PVR 150, card #0
[4296818.059000] ivtv:  ====================  END INIT IVTV  =================== =


So that's where I'm stuck.  Please help![/QUOTE]

---

### Post by jisgod on 2006-04-19
I should have said /etc/modprobe.d/aliases

-J

---

