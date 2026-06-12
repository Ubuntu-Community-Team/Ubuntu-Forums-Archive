---
title: "UBUNTU 10.04 problem with MOUSEPAD stopped working"
date: 2011-01-18
forum: Hardware
---

### Post by unknown23 on 2011-01-18
i have a acer aspire 1350 laptop. i did a partial upgrade, and after i did this, the front panel of my pc is not working anymore, the led indicator ( battery state, wireless indicator ) is no longer working and my mouse pad is not working either, how do i fix this?

---

### Post by unknown23 on 2011-01-18
OK, i have been doing some research online, and this seems to be a common problem, i should be way more explicit about the nature of my problem.

So, i was using 10.04, really nice, no problems, then i did some updates, hings strated to go very wrong, i can no longer use the program mixxx, but that is a whole other story. the thing i am most concerned about is that i did a partial upgrade from 10.04 to 10.10, it has not been completed, so maybe this is a problem, i let the experts tell me , i did the process in the terminal where i could goto peripherals > touchpad etc; and marked the boxes to activate touchad, but it is not working still

i actually did all the things i could find online that i understand, i am not very clever with the system, i prefer it, but i need really simple and straight detailed instruction, i do not speak linux language and dont know a lot of what other people know who use linux

so, i just want to get my touchpad working, i am using my room mates usb wireless mouse right now, but i have to give that back then after i have a laptop that is not working the way i need, please help me!

---

### Post by unknown23 on 2011-01-18
i really do not understand what this is all about, please help

[https://wiki.ubuntu.com/DebuggingTouchpadDetection/evtest](https://wiki.ubuntu.com/DebuggingTouchpadDetection/evtest)

---

### Post by unknown23 on 2011-01-18
this seems like it could help

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

but i dont know what at all to do according to this

can someone just please help me fix this i am so tired of this i feel like to chuck my laptop out the window

---

### Post by unknown23 on 2011-01-18
this seems like it could help

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

but i dont know what at all to do according to this

can someone just please help me fix this i am so tired of this i feel like to chuck my laptop out the window

---

### Post by unknown23 on 2011-01-21
Thanks a lot everyone for all the wonderful help on this! What is the problem here, just because i use linux i am supposed to tolerate a complete malfunction of my computer afford myself hours of time learing how to fix this on my own with all the confusing information that is made available , this is really horrible that this can even happen, i have lost a lot of time with an important project because of this and that cost me money in the end ...thanx a lot linux!

---

### Post by pi/roman on 2011-01-21
It's true that this is a very common problem with touchpads that are not synaptic.  It almost seems as though these manufacturers are trying to make equipment that is incompatible with linux and they do not supply linux drivers for their hardware so it effectively has to be "hacked" in order to be usable.  Then as one device driver is fixed they come out with another hardware version that requires a different fix. If you say it worked on 10.04 then your best bet is to reinstall that.  You will have an option of running both operating systems side by side so if you do that then you will be able to transfer files and settings between them. Otherwise you can buy support through Canonical or get a non-free os.

---

### Post by unknown23 on 2011-01-21
it is just frustrating, i just wish i could find the help in order to fix this, i mean, it worked before, then i do updates and then it is dead, and also the front panel of my pc, has an indicator for battery, wireless, bluetooth etc; and it no longer is working either

i mean i went from 9.10 because it caused problems, was really happy with 10.04 and now why all of sudden do things change on the system ...i can no longer use some programs since i did some updates and was prompted to a partial upgrade and after i did that all hell broke loose, i am afraid to do a complete upgrade because i think 10.10 just has a lot of problems anyway.

i ca not afford to lose any data i in the middle of a huge project right now, that all these problems cause me delays which actually cost me money in the end .... i don't know, can't i just do a demsg output and someone who really knows what they are doing in linux can take a look at this output andtellme exactly what i have to do in order to have my system running like it was before, i was completely happy with the system, why did it go and change on me?

---

### Post by unknown23 on 2011-01-21
bump

shadowcast@shadowcast:~$ uname -r
2.6.32-28-generic
shadowcast@shadowcast:~$ lsmod|grep psmouse
psmouse                63245  0 
shadowcast@shadowcast:~$ dmesg|grep mouse
[    0.293342] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.368828] mice: PS/2 mouse device common for all mice
shadowcast@shadowcast:~$

---

### Post by unknown23 on 2011-01-21
~$ lsmod
Module                  Size  Used by
aes_i586                7268  837 
aes_generic            26863  1 aes_i586
via                    37920  2 
drm                   162409  3 via
dm_crypt               11331  0 
arc4                    1153  2 
binfmt_misc             6587  1 
snd_via82xx_modem       8486  0 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  2 snd_via82xx_modem,snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_mpu401_uart         5617  1 snd_via82xx
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
ar9170usb              51296  0 
i2c_viapro              5573  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 ar9170usb
ath                     7611  1 ar9170usb
psmouse                63245  0 
snd                    54180  16 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
via_ircc               21745  0 
led_class               2864  1 ar9170usb
serio_raw               3978  0 
cfg80211              126528  3 ar9170usb,mac80211,ath
joydev                  8740  0 
parport_pc             25962  1 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
snd_page_alloc          7076  3 snd_via82xx_modem,snd_via82xx,snd_pcm
irda                  186620  1 via_ircc
crc_ccitt               1339  1 irda
soundcore               6620  1 snd
shpchp                 28835  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvesafb                22297  1 
video                  17375  0 
via_rhine              19154  0 
usbhid                 36110  0 
ohci1394               26950  0 
hid                    67064  1 usbhid
via_agp                 5310  1 
floppy                 53016  0 
mii                     4381  1 via_rhine
output                  1871  1 video
ieee1394               81181  1 ohci1394
pata_via                7272  3 
agpgart                31724  2 drm,via_agp
shadowcast@shadowcast:~$

---

### Post by unknown23 on 2011-01-21
can someone tell me how to do this please

[http://andreascarpino.it/2010/04/xorg-1-8-synaptics-touchpad-configuration/](http://andreascarpino.it/2010/04/xorg-1-8-synaptics-touchpad-configuration/)

---

