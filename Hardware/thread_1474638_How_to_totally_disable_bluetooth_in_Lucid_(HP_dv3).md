---
title: "How to totally disable bluetooth in Lucid? (HP dv3)"
date: 2010-05-06
forum: Hardware
---

### Post by inverseroom on 2010-05-06
I'm running Lucid on an HP dv3 notebook.  It's great!  Much snappier than Karmic, everything feels sorted.  But my battery life is awful all of a sudden.  What's the current best way to prevent the bluetooth radio from turning on at boot?  I can't seem to find any reference to bluetooth in the BIOS of this machine.

Also, I installed powertop and it told me to run "hciconfig hci0 down ; rmmod hci_usb."  But when I sudo the second command I get an error: "Module hci_usb does not exist in /proc/modules".

Thanks!

---

### Post by inverseroom on 2010-05-06
FWIW, here's the actual contents of /proc/modules:

> michael_mic 1732 8 - Live 0xf80d6000
arc4 1153 4 - Live 0xf80b4000
binfmt_misc 6587 1 - Live 0xf8094000
ppdev 5259 0 - Live 0xf867d000
rfcomm 33421 4 - Live 0xf8667000
sco 7885 2 - Live 0xf864e000
bridge 45582 0 - Live 0xf8633000
stp 1655 1 bridge, Live 0xf8618000
bnep 9436 2 - Live 0xf860b000
l2cap 30624 16 rfcomm,bnep, Live 0xf85f5000
snd_hda_codec_atihdmi 2367 1 - Live 0xf85c3000
fbcon 35102 71 - Live 0xf85d5000
tileblit 2031 1 fbcon, Live 0xf8596000
font 7557 1 fbcon, Live 0xf857b000
bitblit 4707 1 fbcon, Live 0xf8128000
softcursor 1189 1 bitblit, Live 0xf810d000
vga16fb 11385 0 - Live 0xf80fb000
vgastate 8961 1 vga16fb, Live 0xf80bf000
snd_hda_codec_idt 51914 1 - Live 0xf803d000
snd_hda_intel 21877 2 - Live 0xf90b3000
snd_hda_codec 74201 3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel, Live 0xf8f84000
snd_hwdep 5412 1 snd_hda_codec, Live 0xf8d5c000
snd_pcm_oss 35308 0 - Live 0xf8d51000
snd_mixer_oss 13746 1 snd_pcm_oss, Live 0xf8cee000
snd_pcm 70662 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xf8cca000
snd_seq_dummy 1338 0 - Live 0xf8ca9000
snd_seq_oss 26726 0 - Live 0xf8a0a000
snd_seq_midi 4557 0 - Live 0xf89e0000
snd_rawmidi 19056 1 snd_seq_midi, Live 0xf89b4000
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi, Live 0xf811e000
lib80211_crypt_tkip 7596 0 - Live 0xf8111000
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf879b000
radeon 674135 2 - Live 0xf86c5000
snd_timer 19098 2 snd_pcm,snd_seq, Live 0xf814a000
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf80a1000
ttm 49943 1 radeon, Live 0xf8154000
drm_kms_helper 29297 1 radeon, Live 0xf80e0000
uvcvideo 56990 0 - Live 0xf85c5000
drm 162471 4 radeon,ttm,drm_kms_helper, Live 0xf8a6e000
snd 54148 16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8a1d000
btusb 10925 0 - Live 0xf85a2000
videodev 34361 1 uvcvideo, Live 0xf8169000
v4l1_compat 13251 2 uvcvideo,videodev, Live 0xf813b000
bluetooth 49892 7 rfcomm,sco,bnep,l2cap,btusb, Live 0xf8587000
agpgart 31724 2 ttm,drm, Live 0xf812e000
i2c_algo_bit 5028 1 radeon, Live 0xf8103000
i2c_piix4 8335 0 - Live 0xf80eb000
soundcore 6620 1 snd, Live 0xf80dc000
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm, Live 0xf809a000
psmouse 63245 0 - Live 0xf8077000
serio_raw 3978 0 - Live 0xf804d000
wl 1959598 0 - Live 0xf87bf000 (P)
lib80211 5046 2 lib80211_crypt_tkip,wl, Live 0xf85ab000
shpchp 28820 0 - Live 0xf8598000
joydev 8708 0 - Live 0xf8582000
lirc_ene0100 6536 0 - Live 0xf8174000
video 17375 0 - Live 0xf8162000
output 1871 1 video, Live 0xf8151000
hp_accel 11144 0 - Live 0xf8145000
lis3lv02d 6007 1 hp_accel, Live 0xf8137000
input_polldev 2482 1 lis3lv02d, Live 0xf812b000
led_class 2864 1 hp_accel, Live 0xf8121000
lirc_dev 8884 1 lirc_ene0100, Live 0xf8114000
lp 7028 0 - Live 0xf8106000
parport 32635 2 ppdev,lp, Live 0xf80f1000
usb_storage 39425 0 - Live 0xf80c4000
pata_atiixp 3148 0 - Live 0xf809e000
r8169 33884 0 - Live 0xf8089000
mii 4381 1 r8169, Live 0xf8073000
ahci 32008 2 - Live 0xf8069000

---

### Post by IcarusR on 2010-05-06
To disable bluetooth you need to stop the module/service starting up. This can be done using 'Boot-up manager' which shold be in the repos.

> Boot-Up Manager is a graphical tool to allow easy configuration
of init services in user and system runlevels, as far as changing
Start/Stop services priority.

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

As for your powertop question I have no idea.

---

### Post by inverseroom on 2010-05-07
> **IcarusR said:**
> To disable bluetooth you need to stop the module/service starting up. This can be done using 'Boot-up manager' which shold be in the repos.



[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

As for your powertop question I have no idea.

Excellent, I'll try it--thank you!

---

