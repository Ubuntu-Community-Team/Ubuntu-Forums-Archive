---
title: "TV-Card Terratec Cinergy HT PCI with Edgy"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by the_mechanical on 2007-01-15
Hi
I played around for some days with my new TV-Card Terratec Cinergy HT PCI.
Since it was not easy to use the informations i've found, i will post parts of my config-files for the card - maybe it helps someone ;) 

System: Ubuntu Edgy (6.10) with own Kernel, but 2.6.17-10(-386) should also work:

/etc/modules
```

saa7134 card=83 tuner=54
saa7134_alsa

```

/etc/modprobe.d/saa7134 (create it if it's not existing)
```

options saa7134 card=83 tuner=54 video_nr=1 vbi_nr=1 radio_nr=1 
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=2

```

I don't know (and i didn't try it) if i really need the entry in  /etc/modules, but it works and that's enough for me ;) 

If you use tvtime you have no sound:
Start tvtime, and run in a terminal:
```
arecord -D hw:2 -r 32000 -c 2 -f S16_LE | aplay -
```

Links:
[http://linuxtv.org/v4lwiki/index.php/Terratec_Cinergy_HT_PCI](http://linuxtv.org/v4lwiki/index.php/Terratec_Cinergy_HT_PCI)
[http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa](http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa)


If someone has expierience to get the LIRC-support of the USB remote controller (i don't know why but it was shipped with usb IR) - i would be glad

lsusb shows:
```
Bus 002 Device 004: ID 0419:0001 Samsung Info. Systems America, Inc. IrDA Remote Controller
```

---

### Post by jackcy on 2007-03-23
I have successfully installed the cinergy ht pci on a feisty box with the latest snapshop of v4l2 drivers.

[   14.305433] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.305505] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 21, latency: 64, mmio: 0xcddfd800
[   14.305511] saa7133[0]: subsystem: 153b:1175, board: Terratec Cinergy HT PCI [card=108,autodetected]
[   14.305518] saa7133[0]: board init: gpio is 0
[   14.449677] saa7133[0]: i2c eeprom 00: 3b 15 75 11 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.449686] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   14.449694] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 00 06 ff 00 94 02 51 96 2b
[   14.449702] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   14.449710] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 32 15 10 fd 79 44 9f c2 8f
[   14.449718] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.449726] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.449734] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.565500] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   14.887861] saa7133[0]: registered device video0 [v4l2]
[   14.887889] saa7133[0]: registered device vbi0
[   14.914017] saa7134 ALSA driver for DMA sound loaded
[   14.914047] saa7133[0]/alsa: saa7133[0] at 0xcddfd800 irq 21 registered as card -2
[   15.132632] DVB: registering new adapter (saa7133[0]).


Even the alsa module is loaded automatically on boot.

saa7134_dvb            18060  0
dvb_pll                14980  1 saa7134_dvb
video_buf_dvb           7684  1 saa7134_dvb
tda1004x               17028  2 saa7134_dvb
saa7134_alsa           15392  1
snd_pcm                79876  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
saa7134               127564  2 saa7134_dvb,saa7134_alsa
snd                    54020  17 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video_buf              26116  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
i2c_core               22784  9 i2c_ec,tda827x,saa7134_dvb,dvb_pll,tda1004x,tuner,saa7134,nvidia,ir_kbd_i2c
videodev               29312  1 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15236  2 saa7134,videodev


However, how hard I try, television is fine, but sound doesn't work at all. I am messing around with this for days, but sound is dead.

Calling mplayer with this command (also on various variations).

/usr/bin/mplayer -bpp 32 tv://  -tv driver=v4l2:norm=PAL:device=/dev/video0:input=0:quality=0:width=720:height=576:channel=E7:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:immediatemode=0 -nojoystick -nolirc -vf dsize=4/3 -vo xv 

All other hints using sox and arecord didn't work either.

Can anybody help, PLEASE

---

### Post by scognito on 2007-04-20
I cannot even get my new feisty (just installed) recognize the card.
It is the same, and this is the dmesg:
[   41.739784] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.740607] saa7133[0]: found at 0000:00:0d.0, rev: 209, irq: 19, latency: 32, mmio: 0xed800000
[   41.740615] saa7133[0]: subsystem: 153b:1175, board: Terratec Cinergy 250 PCI TV [card=83,insmod option]
[   41.740628] saa7133[0]: board init: gpio is 0
[   41.920232] saa7133[0]: i2c eeprom 00: 3b 15 75 11 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   41.920246] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   41.920255] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 00 06 ff 00 94 02 51 96 2b
[   41.920264] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   41.920273] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 32 15 10 fd 79 44 9f c2 8f
[   41.920281] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.920290] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.920299] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.172175] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   42.531022] saa7133[0]: registered device video1 [v4l2]
[   42.531068] saa7133[0]: registered device vbi1
[   42.531108] saa7133[0]: registered device radio1
[   42.558121] saa7134 ALSA driver for DMA sound loaded
[   42.558174] saa7133[0]/alsa: saa7133[0] at 0xed800000 irq 19 registered as card 2

It is recognized as 250 PCI tv, and the module i only have is saa7134, not saa7133.
I tried with and without the file in /etc/modules, and didn't worked.
Even passing the card argument=108 (as seen in the above post) the card is still recognized as 250.
2.6.20-15 generic, fresh feisty installation.
Thanks for help.

---

### Post by jackcy on 2007-04-22
the card is recognised as 250 because of the inmod option. The 108 doesn't work with original feisty modules - it did with herd 3 and herd 5, but obviously got lost in beta and the final release.
you could delete you /etc/modprobe.d/saa7134 file or - better modify it to card 108 instead of 83 after installing from linuxtv.

If I try to use the  Terratec Cinergy HT PCI with 7.04 the only message I get is: This card hasen't got a tuner.

So I installed the driver with:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd cd v4l-dvb
make
sudo make install

Here's my /etc/modprobe.d/saa7134

options saa7134 card=108 tuner=54 video_nr=1 vbi_nr=1 radio_nr=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=2

Then I get a video signal BUT still no sound using
/usr/bin/mplayer -bpp 32 tv://  -tv driver=v4l2:norm=PAL:device=/dev/video1:input=0:quality=0:width=720:height=576:channel=E7:adevice=/dev/dsp1:amode=1:audiorate=32000:forceaudio:immediatemode=0:volume=100 -nojoystick -nolirc -vf dsize=4/3 -vo xv

---

### Post by the_mechanical on 2007-05-01
Hello
I tried now the configuration in Feisty (fresh installation). All went good, i only hat to change some small things.
I didn't modify /etc/modules, but /etc/modprobe.d/saa7134 how described in my first post.
Looking which device is used from the TV-Card (look in the Hardware Information) in my case it was /dev/video1 (video0 is the webcam, in Edgy i had it the other way round). Also for the sound i had to change hw:2 to hw:1 (that was only trying until it worked :) )
That means for my case:
Channel list:
```
tvtime-scanner -d /dev/video1
```
Watching TV:
```
tvtime -d /dev/video1
```
And the sound:
```
arecord -D hw:1 -r 32000 -c 2 -f S16_LE | aplay -
```

That was it.
If you have problems with the sound then try to change hw:1 to an other number (i don't know how you can find out - so only try).

---

### Post by davil on 2007-05-14
I'm using the same card and it is basically working as described here (using the latest v4l-dvb drivers). However I don't know how to set this up in MythTV - when I do not start the "arecord" command, there is sound, but it's too fast (something like twice the speed and short breaks inbetween), causing "WriteAudio: buffer underrun" errors.

I also don't want the sound to play when I'm not in TV mode in MythTV. Do you know how I can make this work?

---

### Post by jackcy on 2007-05-17
Sorry, I don't know MythTV by detail, but I found this link in one of the wiki pages basing on gentoo

[http://gentoo-wiki.com/HOWTO_Use_MythTV](http://gentoo-wiki.com/HOWTO_Use_MythTV)

It could work with a combination of the commands v4lctl and mythtv - something like that:

v4lctl -c /dev/video0 volume mute off && mythtv && v4lctl -c /dev/video0 volume mute on

I use kdetv which does that automatically on start of the application.

---

### Post by davil on 2007-05-17
I think I'll wait a bit until the driver for this card has been improved, because I don't have that much time for playing around at the moment. But thanks for your help anyway!

---

### Post by scognito on 2007-05-17
> **jackcy said:**
> the card is recognised as 250 because of the inmod option. The 108 doesn't work with original feisty modules - it did with herd 3 and herd 5, but obviously got lost in beta and the final release.
you could delete you /etc/modprobe.d/saa7134 file or - better modify it to card 108 instead of 83 after installing from linuxtv.

If I try to use the  Terratec Cinergy HT PCI with 7.04 the only message I get is: This card hasen't got a tuner.

So I installed the driver with:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd cd v4l-dvb
make
sudo make install

Here's my /etc/modprobe.d/saa7134

options saa7134 card=108 tuner=54 video_nr=1 vbi_nr=1 radio_nr=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=2

Then I get a video signal BUT still no sound using
/usr/bin/mplayer -bpp 32 tv://  -tv driver=v4l2:norm=PAL:device=/dev/video1:input=0:quality=0:width=720:height=576:channel=E7:adevice=/dev/dsp1:amode=1:audiorate=32000:forceaudio:immediatemode=0:volume=100 -nojoystick -nolirc -vf dsize=4/3 -vo xv

TNX now the card get recognized :) :popcorn:

---

### Post by striscio on 2007-05-31
> **davil said:**
> I'm using the same card and it is basically working as described here (using the latest v4l-dvb drivers). However I don't know how to set this up in MythTV - when I do not start the "arecord" command, there is sound, but it's too fast (something like twice the speed and short breaks inbetween), causing "WriteAudio: buffer underrun" errors.

I also don't want the sound to play when I'm not in TV mode in MythTV. Do you know how I can make this work?

I have this card working using some info found on Mythtv web site:
[http://www.mythtv.org/docs/mythtv-HOWTO-22.html#Troubleshooting_Audio]("http://www.mythtv.org/docs/mythtv-HOWTO-22.html#Troubleshooting_Audio").
After that I had sound in Mythtv but too fast and with WriteAudio Errors. So I went to Setup -> Setup -> TV Settings -> Recording, choose "Software encoders (v4l based)" and set for every profile listed in there Audio quality to use 'Uncompressed' codec. That solved for me.
**Note:** do it for **every** profile or you will have right sound in LiveTv but not in recordings.

Anyone has got the remote working? I see on the modules:
```

lsmod | grep saa

```
```

ir_kbd_i2c
ir_common

```
does ir_* stand for infrared?
And how do I know if the remote is seen by my system?

---

