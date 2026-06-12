---
title: "No sound at all......"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by reddeathdrinker on 2005-03-28
I've installed Warty on an old 400MHz Celeron laptop, and it's all gone fine, except for the sound.....It's an Advent 7340DVD model, with a Yamaha OPL3 soundcard. I've tried every trick I can think of to get sound working, 

On boot, I get an error message saying "Sound card not found, or busy", and if I try to load alsamixer, I get a "no device present" error message...... I've searched these (and other) forums without success. Any help gratefully appreciated!

```

alasdair@ubuntu:~ $ lsmod
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  4
ipv6                  230020  10
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
speedtch               14000  1
crc32                   4608  1 speedtch
uhci_hcd               29328  0
usbcore               104292  4 speedtch,uhci_hcd
analog                 10784  0
ns558                   5760  0
gameport                4736  2 analog,ns558
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
snd_opl3_lib            9728  0
snd_hwdep               9120  1 snd_opl3_lib
snd_cs4231_lib         24960  0
snd_mpu401_uart         7296  0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         11144  2 snd_cs4231_lib,snd_pcm
snd_timer              23172  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50660  10 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
apm                    19948  2
pppoatm                 6400  1
ppp_generic            27668  5 pppoatm
slhc                    7040  1 ppp_generic
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
ide_cd                 38276  0
evdev                   9088  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  670
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```

---

### Post by ubuntu-geek on 2005-03-28
You might have to rebuild the alsa-base to include your sound card. You can find your card and compile directions here. [http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

   Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386
  
  sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10
  
  cd /usr/src
  sudo wget [ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2")
  tar xvjf alsa-driver-1.0.8.tar.bz2
  cd alsa-driver-1.0.8
  sudo ./configure --with-cards=REPLACE WITH YOUR SOUND CARD --with-sequencer=yes
  sudo make
  sudo make install

---

### Post by reddeathdrinker on 2005-03-28
[QUOTE=ubuntu-geek]You might have to rebuild the alsa-base to include your sound card. You can find your card and compile directions here. [http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

   Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386
  
  sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10
  
  cd /usr/src
  sudo wget [ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2")
  tar xvjf alsa-driver-1.0.8.tar.bz2
  cd alsa-driver-1.0.8
  sudo ./configure --with-cards=REPLACE WITH YOUR SOUND CARD --with-sequencer=yes
  sudo make
  sudo make install[/QUOTE]
 Brilliant:)

Thanks for the help! I was beginning to look at messing around with the isapnp tools...

---

