---
title: "how to use edimax ew7711uan dongle in Access Point (master) mode"
date: 2009-12-12
forum: Hardware
---

### Post by nesimi on 2009-12-12
Hi there,
Is there anybody who knows how to set a wireless dongle as access point on Ubuntu/Kubuntu 9.10? I use Edimax ew7711uan 150MBs usb wireless dongle. I have spent a lot of time to install the appropriate driver for the newest kernel. Now it works with rt2870sta in normal mode (client mode) on Kubuntu 9.10. I use this dongle on windows xp/7 as an access point.

Some outputs for the Edimax ew7711uan wireless adoptor:
Regards,

```
homeless@nesimi:~$ lsusb
Bus 001 Device 002: ID 7392:7711
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
homeless@nesimi:~$
```

```
homeless@nesimi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

homeless@nesimi:~$
```
```
homeless@nesimi:~$ lsmod
Module                  Size  Used by
ppdev                   6688  0
snd_via82xx_modem      11204  0
snd_via82xx            23576  3
gameport               11368  1 snd_via82xx
snd_ac97_codec        101216  2 snd_via82xx_modem,snd_via82xx
snd_pcm_oss            37920  0
ac97_bus                1532  1 snd_ac97_codec
snd_mixer_oss          16028  1 snd_pcm_oss
snd_mpu401_uart         6940  1 snd_via82xx
snd_pcm                75296  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
iptable_filter          3100  0
ip_tables              11692  1 iptable_filter
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               9586440  36
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  18 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0
snd_page_alloc          9156  3 snd_via82xx_modem,snd_via82xx,snd_pcm
soundcore               7264  1 snd
shpchp                 32272  0
k8temp                  4188  0
i2c_viapro              7312  0
serio_raw               5280  0
rt3070sta             515520  1
lp                      8964  0
parport                35340  2 ppdev,lp
floppy                 54916  0
skge                   39180  0
sata_via                9184  2
amd64_agp               9796  1
agpgart                34988  2 nvidia,amd64_agp
homeless@nesimi:~$
```

---

### Post by mgc8 on 2009-12-13
The rt*sta drivers will never work in AP mode, they lack the necessary code and firmware and the company behind them (RaLink) is uninterested in further development. You must use the free drivers from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) -- they have been under development for several years, at a very slow pace, and still not quite working. If you can help with testing and debugging I'm sure it's going to be appreciated.

---

### Post by nesimi on 2009-12-13
> **mgc8 said:**
> The rt*sta drivers will never work in AP mode, they lack the necessary code and firmware and the company behind them (RaLink) is uninterested in further development. You must use the free drivers from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) -- they have been under development for several years, at a very slow pace, and still not quite working. If you can help with testing and debugging I'm sure it's going to be appreciated.
 
Hmm, I understood. I will check the web-site. Hopefully, I will contribute to the group.
Regards,

---

### Post by nesimi on 2009-12-17
I have good news and bad news to you. I have successfully set up an AP with Edimax ew7711uan on Ubuntu 9.04.  However I couldn't do it on Ubuntu 9.10. It is very easy in 9.04. I have firstly updated the system and then "created" a wireless connection with an arbitrary name and password. Afterwards I have seen the connection from my laptops which work on Windows. Now laptops have a good quality internet connection.
Regards,

---

### Post by timmilicious on 2009-12-23
Hi Nesimi,

Please confirm what driver you used for the Edimax with Ubuntu 9.04. 

By the way, I don't have any interest in Linux per se; I just want an AP running on my netbook. The Soft AP software you mention that comes with the Edimax dongle works pretty well but it isn't configurable enough. I want to create a captive portal, so that anyone who connects can only go to one site.  Does anyone have experience with using Windows settings or with a program such as nat32 along with Soft AP to achieve that?

Thanks in advance.

---

