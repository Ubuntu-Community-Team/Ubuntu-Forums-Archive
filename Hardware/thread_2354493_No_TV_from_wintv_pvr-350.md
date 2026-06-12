---
title: "No TV from wintv pvr-350"
date: 2017-03-03
forum: Hardware
---

### Post by bookie2 on 2017-03-03
Hi guys! 
Have recently reinstalled my media center with Xubuntu 16.04...
I have the above card installed but can't seem to set it up for TV analog Sweden...
I have a splitter on my aerial from my tv to my media center and the tv has no problems with my channels so the cable is ok..:D

i have the results of dmesg | grep ivtv

```

martyn@Media-Center:~$ dmesg | grep ivtv
[    4.365103] ivtv: Start initialization, version 1.4.3
[    4.365167] ivtv0: Initializing card 0
[    4.365169] ivtv0: Autodetected Hauppauge card (cx23415 based)
[    4.418656] ivtv0: Autodetected Hauppauge WinTV PVR-350
[    4.593880] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[    5.097420] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[    5.176007] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
[    5.218152] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[    5.218288] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[    5.218421] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[    5.218549] ivtv0: Registered device video24 for encoder PCM (320 kB)
[    5.218680] ivtv0: Registered device radio0 for encoder radio
[    5.218809] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[    5.218939] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[    5.219070] ivtv0: Registered device vbi16 for decoder VOUT
[    5.219200] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[    5.219201] ivtv0: Initialized card: Hauppauge WinTV PVR-350
[    5.219260] ivtv: End initialization
[    5.223715] ivtv-alsa: module loading...
[    5.223926] ivtv0-alsa: snd_ivtv_init: Instance 0 registered as ALSA card 2
[    6.200132] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[    6.210569] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[    6.409251] ivtv0: Encoder revision: 0x02060039
[    6.409573] ivtv0: Decoder revision: 0x02020023
[    6.506422] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[ 1043.834270] ivtv0: All encoder YUV stream buffers are full. Dropping data.
[ 1043.834275] ivtv0: Cause: the application is not reading fast enough.
martyn@Media-Center:~$ 


```

So my card is getting detected ok...

I have tried to use vlc to add my tv channels but not getting any where...

Has anyone the next steps I need to do to try and get this working...

I don't mind a bit of leg work...:D

Please just tell me what you need....:D

bookie

---

### Post by leunam12 on 2017-03-03
Install ivtv-utils.

To list inputs:
```
v4l2-ctl -d /dev/video0 --list-inputs
```
My inputs are:

0 = Tuner 1
1 = S-Video 1
2 = Composite 1
3 = S-Video 2
4 = Composite 2
5 = Composite 3

if I want to set the tuner as input the command is: ```
v4l2-ctl -d /dev/video0 -i 0
```
To set the channel:
```
ivtv-tune -c 3
``` sets to channel 3.

To watch from VLC```
vlc 'v4l2c://'
```

---

### Post by bookie2 on 2017-03-04
Hi leunam12

I have used your info and done as follows:

```

martyn@Media-Center:~$ v4l2-ctl -d /dev/video0 --list-inputs
ioctl: VIDIOC_ENUMINPUT
    Input       : 0
    Name        : Tuner 1
    Type        : 0x00000001
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x000000000000000F (PAL-B/B1/G/H)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 1
    Name        : S-Video 1
    Type        : 0x00000002
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 2
    Name        : Composite 1
    Type        : 0x00000002
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 3
    Name        : S-Video 2
    Type        : 0x00000002
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 4
    Name        : Composite 2
    Type        : 0x00000002
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 5
    Name        : Composite 3
    Type        : 0x00000002
    Audioset    : 0x00000007
    Tuner       : 0x00000000
    Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)
martyn@Media-Center:~$ v4l2-ctl -d /dev/video0 -i 0
Video input set to 0 (Tuner 1: ok)



```

I don't know what channels I have...?

I have tried to use VLC to scan for them but not sure how to set it up...

Can I search for channels?

If so how do I search for Swedish ones...?

Thanks!

bookie

---

### Post by bookie2 on 2017-03-04
I tried running your code:

```

martyn@Media-Center:~$ ivtv-tune -c 3
/dev/video0: 61.250 MHz


```

But I don't know how to use that information because after running that is ran:

```

vlc 'v4l2c://'
VLC media player 3.0.0-git Vetinari (revision 3.0.0~~git20160813+r65787+62~ubuntu16.04.1)
[00000000010c51a8] core libvlc: Kör vlc med standardgränssnittet. Använd "cvlc" för att använda vlc utan gränssn

```


Sorry about the Swedish....

This opened VLC and it kept searching and searching and searching....not getting anywhere...?

---

### Post by leunam12 on 2017-03-04
Well, I don't know anything about Swedish TV, but here in the USA if I want to watch TV using my card I need a converter because the TV signal is digital and the PVR-350 can only capture analog signal; so, a digital-to-analog converter is required. The converter does all the scanning and channel changing, I only set the card to channel 3.

---

### Post by leunam12 on 2017-03-04
It is probably the same in Sweden, you will need a set-top box to converter the signal from digital to analog.

---

### Post by slickymaster on 2017-03-04
*Thread moved to **Hardware**.*

---

### Post by bookie2 on 2017-03-04
Hi again!
We can have digital if we want but we get a good selection of channels analog , so we haven't bothered with the box or extra expense if that makes sense...

bookie

---

### Post by leunam12 on 2017-03-04
well... what analog channels do you have? if you have, let's say channel 47, do```
v4l2-ctl -d /dev/video0 -i 0
```to set the input to tuner. Then...
```
ivtv-tune -c 47
```to set the input to channel 47 (use your own channel number that you know it exists and it's broadcasting and you can get a signal from your house), I don't know how to scan for channels, you may need another program.

---

### Post by bookie2 on 2017-03-05
Hi leunam12!
I do thank you for your help...I have a lot to do at the moment but will get to this as soon as I have a mo...
You have given me a lot to get going...:)

bookie

---

