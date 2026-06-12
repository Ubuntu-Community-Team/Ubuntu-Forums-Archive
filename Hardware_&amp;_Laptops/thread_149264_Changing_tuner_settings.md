---
title: "Changing tuner settings"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by mycroft on 2006-03-23
Hi!
I'm trying to make my tuner card work properly. The colours are a bit weird, the sound has got some static noise at times, and I'm unable to scan for any channels. From what I've read this suggests that incorrect tuner settings are to blame, so I have to adjust the tuner settings - presumably in some module...

This is the output of lspci -v

```
0000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3401
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

0000:00:0a.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3401
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2
```

...and this is the output of lsmod
```
Module                  Size  Used by
nvidia               3711364  22
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
analog                 10528  0
snd_mpu401              6344  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  2 analog,snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  2 snd_mpu401,snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  14 snd_mpu401,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_viapro              7696  0
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
tda9887                13208  0
cx8800                 28812  0
cx88xx                 50976  1 cx8800
ir_common               7428  1 cx88xx
v4l1_compat            12420  1 cx8800
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  2 nvidia,via_agp
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
bttv                  141456  0
video_buf              19844  3 cx8800,cx88xx,bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  2 cx88xx,bttv
v4l2_common             5888  2 cx8800,bttv
btcx_risc               4872  3 cx8800,cx88xx,bttv
tveeprom               12568  2 cx88xx,bttv
i2c_core               19728  7 i2c_acpi_ec,i2c_viapro,tda9887,cx88xx,bttv,i2c_algo_bit,tveeprom
videodev                9344  3 cx8800,cx88xx,bttv
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  379
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

Any ideas on how to proceed from here?

---

### Post by mikedtemple on 2006-03-23
Are you using ivtv?  If so do a dmesg | grep ivtv and post, we'll have a better idea then.

Also, what modprobe aliases are you using?  Depending on your version of ivtv you may or may not need different ones.

However, it looks like from lsmod you might be using bttv, and that I have no experience with.  Let me know.

If you are using bttv, check the [http://www.ivtvdriver.org](http://www.ivtvdriver.org) website and see if your tv card is supported.  Ivtv is pretty darn stable for me.

EDIT- I briefly checked out your card- looks like you need to add the cx8800 and tda9887 drivers.  Try to:

modprobe cx8800
modprobe tda9887

then check your dmesg, and google around for tuner settings, sorry I can't help you more.


From Linuxquestions.org
tv tuner card with remote control.
works good, video & audio quality both good.
use driver modules tda9887 and cx8800
sound lead from card plugs in to your sound card aux input, don't forget to turn up your line input volume control with aumix or alsa mixer. Using kmix was not sufficient.

---

### Post by mycroft on 2006-03-23
[QUOTE=mikedtemple]Are you using ivtv?  If so do a dmesg | grep ivtv and post, we'll have a better idea then.

Also, what modprobe aliases are you using?  Depending on your version of ivtv you may or may not need different ones.

However, it looks like from lsmod you might be using bttv, and that I have no experience with.  Let me know.

If you are using bttv, check the [http://www.ivtvdriver.org](http://www.ivtvdriver.org) website and see if your tv card is supported.  Ivtv is pretty darn stable for me.[/QUOTE]

Ivtv? Bttv? I must admit I don't really know what they are - and I don't know about modprobe aliases either :(

Anyway, dmesg | grep ivtv returned nothing, and I checked out ivtvdriver.org, but was unable to find my card listed anywhere.
My card is a Hauppauge WinTV-Radio card - I found this additional info on it using hdinfo.exe from Hauppauge in Windows:

```
Model 34519 Rev. J189
Serial #8201332
Tuner Model: TCL MFPE05_2
Tuner Formats: (B/G/I/D/K/L/L')
Tuner Audio: Stereo (CX881)
Video Formats: NTSC ( M 443 ) PAL ( B G H I D K M N NCOMBO ) SECAM ( L L' )
Audio Outputs: External
External Inputs: 2
S-Video Inputs: 1
Teletext: Yes (Software)
Radio: FM
Decoder: CX881
IR: Yes
```

Don't know if it helps though.


-- EDIT--

Tried doing the modprobe commands, but dmesg simply returned a lot of text along the lines of
```
[4300539.122000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300539.220000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
```

Doesn't appear to be related to the tuner card issues, however.

---

### Post by mikedtemple on 2006-03-24
Sorry, should have been more specific.  Bttv is the linux TV Card Driver for Non-MPEG-2 TV Cards which ust the Bt878 chipset. IVTV is for Many MPEG-2 Cards.  Unfourtunately, I've only worked with IVTV becuase I have Happague Win-TV PVR-350 in my system.  

According to Linuxquestions.org, you have a card that needs the bttv driver.

From my understanding, setting up the bttv drivers is not easy- 

I found this on another site (videoHelp.com)

> his section applies to linux:

After much suffering, I got it to "work" with
modprobe cx8800 card=5 tuner=44
however as of 12/8/2004 it still doesnt have any sound, despite the card having an audio out which I ran directly into speaker. Video is okay. 

Perhaps you should try those modprobe settings.  Google around for settings, looks like some people have had this card working in linux.

Sorry I can't help you more...

[QUOTE=mycroft]Ivtv? Bttv? I must admit I don't really know what they are - and I don't know about modprobe aliases either :(

Anyway, dmesg | grep ivtv returned nothing, and I checked out ivtvdriver.org, but was unable to find my card listed anywhere.
My card is a Hauppauge WinTV-Radio card - I found this additional info on it using hdinfo.exe from Hauppauge in Windows:

```
Model 34519 Rev. J189
Serial #8201332
Tuner Model: TCL MFPE05_2
Tuner Formats: (B/G/I/D/K/L/L')
Tuner Audio: Stereo (CX881)
Video Formats: NTSC ( M 443 ) PAL ( B G H I D K M N NCOMBO ) SECAM ( L L' )
Audio Outputs: External
External Inputs: 2
S-Video Inputs: 1
Teletext: Yes (Software)
Radio: FM
Decoder: CX881
IR: Yes
```

Don't know if it helps though.


-- EDIT--

Tried doing the modprobe commands, but dmesg simply returned a lot of text along the lines of
```
[4300539.122000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300539.220000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
```

Doesn't appear to be related to the tuner card issues, however.[/QUOTE]

---

### Post by mycroft on 2006-03-26
Ok, now I've sorted out the keycode issue, which completely filled the kernel log, rendering dmesg useless.

With the identification of the card as belonging to Hauppauge's WinTV 34xxx series, followed by a bit of googling, it seemed that the cx88 chipset was also a possibility - and sure enough:
*dmesg | grep cx* returned:
```
[4294700.889000] cx2388x v4l2 driver version 0.0.4 loaded
[4294700.891000] cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected]
[4294701.003000] i2c-algo-bit.o: cx88[0] passed test.
[4294701.116000] cx88[0]: registered IR remote control
[4294701.116000] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 5, latency: 32, mmio: 0xe6000000
[4294701.205000] cx88[0]/0: registered device video0 [v4l2]
[4294701.206000] cx88[0]/0: registered device vbi0
[4294701.207000] cx88[0]/0: registered device radio0
```

Judging from the second line of the output, and according to [http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)#Supported_cards]("http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)#Supported_cards") this suggests that the card is indeed equipped with a cx88 chip. 

Now I should be well on my way using the instructions for the WinTV PVR on the site listed above, but mysteriously, *modprobe cx88xx tuner=56 && modprobe cx8800*  refuses to return anything at all, even with the -v parameter!?

---

### Post by mikedtemple on 2006-03-27
Hmmm- nothing shows up in dmesg when you do the modprobe, or just nothing on the screen???

whenever I do a modprobe, I just get a new prompt, I have to check dmesg or /var/log/syslog to acutally see if stuff worked, that is, if I don't get an error message.

Seems to me as if your device registered itself.  Hook up a source (cable tv??) and try doing a 

```
cat /dev/video0 > test.mpg
```

and then a 

```
mplayer -vo xv test.mpg
```

to see if you have a picture.


[QUOTE=mycroft]Ok, now I've sorted out the keycode issue, which completely filled the kernel log, rendering dmesg useless.

With the identification of the card as belonging to Hauppauge's WinTV 34xxx series, followed by a bit of googling, it seemed that the cx88 chipset was also a possibility - and sure enough:
*dmesg | grep cx* returned:
```
[4294700.889000] cx2388x v4l2 driver version 0.0.4 loaded
[4294700.891000] cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected]
[4294701.003000] i2c-algo-bit.o: cx88[0] passed test.
[4294701.116000] cx88[0]: registered IR remote control
[4294701.116000] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 5, latency: 32, mmio: 0xe6000000
[4294701.205000] cx88[0]/0: registered device video0 [v4l2]
[4294701.206000] cx88[0]/0: registered device vbi0
[4294701.207000] cx88[0]/0: registered device radio0
```

Judging from the second line of the output, and according to [http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)#Supported_cards]("http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)#Supported_cards") this suggests that the card is indeed equipped with a cx88 chip. 

Now I should be well on my way using the instructions for the WinTV PVR on the site listed above, but mysteriously, *modprobe cx88xx tuner=56 && modprobe cx8800*  refuses to return anything at all, even with the -v parameter!?[/QUOTE]

---

### Post by mycroft on 2006-03-28
Mplayer won't play it straight away - I cannot rule out I need some codecs installed however. (haven't got time to test it right away)

But the modprobe issue was a bit stupid - it turned out I should unload the modules first (rmmod), and then modprobe would work perfectly fine.

Now my gripes are with tvtime. As I have cable-tv I use the tvtime-scanner app, which seemingly scans and detect a signal all right - but nothing is written to stationlist.xml in spite of proper file permissions.

It would seem that my tuner settings are possibly not correct yet...

---

### Post by mikedtemple on 2006-03-28
I never used tvtime before- did you run it as a user or root?  Try changing the permissions on the video device itself too.  It might be failing to write to the stationlist becuase of another error.


[QUOTE=mycroft]Mplayer won't play it straight away - I cannot rule out I need some codecs installed however. (haven't got time to test it right away)

But the modprobe issue was a bit stupid - it turned out I should unload the modules first (rmmod), and then modprobe would work perfectly fine.

Now my gripes are with tvtime. As I have cable-tv I use the tvtime-scanner app, which seemingly scans and detect a signal all right - but nothing is written to stationlist.xml in spite of proper file permissions.

It would seem that my tuner settings are possibly not correct yet...[/QUOTE]

---

### Post by mycroft on 2006-03-29
No, I don't think it's a device permissions issue - root and the 'video' user group (of which I'm a member) both have read/write permissions.

-- EDIT --
Running tvtime as root doesn't appear to change anything either. But I just noticed something which may be important. I can only get a signal if I boot into Windows and start my tv app. before booting into Linux and tvtime.

---

