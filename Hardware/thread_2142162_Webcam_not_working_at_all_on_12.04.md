---
title: "Webcam not working at all on 12.04"
date: 2013-05-04
forum: Hardware
---

### Post by pdvrosado on 2013-05-04
My webcam was working just fine on 11.10, but since I've upgraded from 11.10 to 12.04 (which I wan to stay with), it's not working at all. On websites, it says It does not recognize the webcam or that i do not have one. On cheese, it crashes the app, and other webcam apps, only show one part of the recorded image of the camera

[https://www.dropbox.com/s/l3l27hp2zdlet5y/Webcam-1367514258.png](https://www.dropbox.com/s/l3l27hp2zdlet5y/Webcam-1367514258.png)

this is a photo taken with another app i do not remember the name, you can see 4 fingers, but the rest is all green. Same happens on cheese, but after that, cheese crashes. 


I asked on the debian community and ubuntu on google+, and they said me to rune the lsmod command on my ubuntu 11.10 in order to get the driver from 11.10 to use it on 12.04 after the upgrade, but I didn't get any response or any help at all from anyone or any forum. 

here is the output of the lsmod:

[COLOR=#555555][FONT=arial]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]rfcomm                 47946  8[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]bnep                   18436  2[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]parport_pc             36962  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]ppdev                  17113  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]lp                     17799  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]parport                46562  3 parport_pc,ppdev,lp[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]binfmt_misc            17540  1[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]pcmcia                 49378  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]joydev                 17693  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_hda_codec_idt      70553  1[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_hda_intel          33390  2[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_hwdep              13668  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_pcm                96755  2 snd_hda_intel,snd_hda_codec[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_seq_midi           13324  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_rawmidi            30547  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]gspca_vc032x           32863  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]gspca_main             28314  1 gspca_vc032x[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]videodev               93004  1 gspca_main[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]v4l2_compat_ioctl32    17083  1 videodev[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]btusb                  18600  2[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]arc4                   12529  2[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]psmouse                73882  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]bluetooth             166112  23 rfcomm,bnep,btusb[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]serio_raw              13166  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]nouveau               728662  3[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]sony_laptop            45393  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_timer              29991  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]tifm_7xx1              13089  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]iwl3945                83391  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]tifm_core              15654  1 tifm_7xx1[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]iwl_legacy             83487  1 iwl3945[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]mac80211              310872  2 iwl3945,iwl_legacy[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]yenta_socket           28084  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]pcmcia_rsrc            18430  1 yenta_socket[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]ttm                    76805  1 nouveau[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]drm_kms_helper         42558  1 nouveau[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]drm                   236330  5 nouveau,ttm,drm_kms_helper[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd                    68266  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]cfg80211              199587  3 iwl3945,iwl_legacy,mac80211[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]i2c_algo_bit           13423  1 nouveau[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]mxm_wmi                12979  1 nouveau[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]wmi                    19256  1 mxm_wmi[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]video                  19412  1 nouveau[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]soundcore              12680  1 snd[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]snd_page_alloc         18529  2 snd_hda_intel,snd_pcm[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]e100                   37213  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]firewire_ohci          40722  0[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]firewire_core          63626  1 firewire_ohci[/FONT][/COLOR]
[COLOR=#555555][FONT=arial]crc_itu_t              12707  1 firewire_core&#65279;
[/FONT][/COLOR]

my laptop model is a [COLOR=#555555][FONT=arial]sony vaio vgn-fe31m
[/FONT][/COLOR]
I also tried other commands to online, to isntall stuff like:

[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

but I don't know what I'm doing wrong, or why all linux versions prevent my webcam from working since, 2 years to now.

Plz help

---

