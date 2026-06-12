---
title: "via82xx sound loops :("
date: 2004-12-14
forum: Hardware &amp; Laptops
---

### Post by MaZiNgA on 2004-12-14
ho there ubuntuers!

Problem: every sound that is played on my system (gdm sound, wavs or whatever) loops the first 1 second of the sound file for almost 2 mins(!), rendering my audio inaudible :(

Motherboard: I think it's a VIA with 8233A Southbridge and apollo266A onboard sound card. (Yah I know crappy card)

Workarounds in vain: 
-added "options snd_via82xx dxs_support=2" at /etc/modutils/alsa --->nothing happened
-added "pci=noacpi" at menu.lst --->X won't boot!   8|
-modprobe via82cxxx_audio --->nothing happened :(

Anyone? Thanks in advance.

Module                  Size  Used by
nvidia               4821428  0 
ppp_deflate             6144  0 
zlib_deflate           20760  1 ppp_deflate
bsd_comp                5888  0 
ppp_async              10624  1 
ppp_generic            27668  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7040  1 ppp_generic
proc_intf               3968  0 
cpufreq_powersave       2048  0 
cpufreq_userspace       5336  0 
freq_table              4356  0 
button                  6936  0 
ac                      5132  0 
battery                 9740  0 
ipv6                  230020  10 
bt878                  11184  0 
snd_bt87x              13640  2 
tuner                  18448  0 
tda9887                12036  0 
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tda9887,bttv,i2c_algo_bit
videodev                9856  1 bttv
snd_via82xx            26660  3 
snd_ac97_codec         59268  1 snd_via82xx
snd_pcm_oss            48168  0 
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  3 snd_bt87x,snd_via82xx,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_bt87x,snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  14 snd_bt87x,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  5 bttv,snd
uhci_hcd               29328  0 
usbcore               104292  3 uhci_hcd
via_ircc               20368  0 
irda                  167360  1 via_ircc
crc_ccitt               2432  2 ppp_async,irda
8139cp                 19072  0 
8139too                23936  0 
mii                     4864  2 8139cp,8139too
crc32                   4608  2 8139cp,8139too
pciehp                 83948  0 
shpchp                 87276  0 
pci_hotplug            30640  2 pciehp,shpchp
via_agp                 8832  1 
agpgart                31784  1 via_agp
analog                 10784  0 
gameport                4736  2 snd_via82xx,analog
floppy                 54996  0 
pcspkr                  3816  0 
rtc                    12216  0 
nls_iso8859_1           4352  2 
nls_cp437               6016  2 
vfat                   13312  2 
fat                    41792  1 vfat
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
parport                37320  2 parport_pc,lp
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
evdev                   9088  0 
tsdev                   7168  0 
mousedev               10124  1 
psmouse                17800  0 
reiserfs              207600  1 
ide_generic             1664  0 
ide_disk               16768  6 
via82cxxx              13084  1 
ide_core              125272  4 ide_cd,ide_generic,ide_disk,via82cxxx
unix                   25904  728 
fan                     4236  0 
thermal                13200  0 
processor              17712  1 thermal
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb



0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:00:13.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:13.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)

---

### Post by MaZiNgA on 2004-12-16
All right I think I'm getting somewhere now. I loaded the knoppix cd and copied the lsmod output.

Module                  Size  Used by    Not tainted
reiserfs              169616   1 (autoclean)
nls_iso8859-7           3612   0 (autoclean)
autofs4                 8756   1 (autoclean)
af_packet              13544   0 (autoclean)
nls_iso8859-1           2844   1 (autoclean)
nls_cp437               4348   1 (autoclean)
agpgart                42660   0 (unused)
via82cxxx_audio        19448   1
ac97_codec             11916   0 [via82cxxx_audio]
uart401                 6052   0 [via82cxxx_audio]
sound                  55276   0 [via82cxxx_audio uart401]
8139too                13736   0
mii                     2240   0 [8139too]
crc32                   2816   0 [8139too]
tuner                   9440   1 (autoclean)
tda9887                 2876   1 (autoclean)
tvaudio                12444   0 (autoclean) (unused)
bttv                   96352   0 (unused)
i2c-algo-bit            6952   1 [bttv]
i2c-core               12228   0 [tuner tda9887 tvaudio bttv i2c-algo-bit]
soundcore               3428   4 [via82cxxx_audio sound bttv]
videodev                5600   2 [bttv]
serial                 52100   0 (autoclean)
pcmcia_core            39840   0
thermal                 6564   0 (unused)
processor               8976   0 [thermal]
fan                     1568   0 (unused)
button                  2508   0 (unused)
battery                 5888   0 (unused)
ac                      1824   0 (unused)
rtc                     7036   0 (autoclean)
cloop                   8740   2
ieee1394              183076   0
usb-storage            61696   0 (unused)
usb-uhci               21644   0 (unused)
usbcore                57600   1 [usb-storage usb-uhci]
ataraid                 6180   0
ide-cd                 28512   0
ide-scsi                8816   1

Seems like I have been using the wrong module all over!! I should be using via82cxxx_audio instead of snd_via82xx...
/me bangs head on wall.
So I added the new module but I can't remove the old one(it says it's in use). Does anyone know how I can configure the modules to start?? Is there an app for that?

I hope that this thread also helps someone with the same problem

---

### Post by MaZiNgA on 2004-12-16
Still no sound after almost one month after installing ubuntu.Please if anyone in these forums has these drivers please help me. I've googled the whole planet and found no answer.

Ubuntu is so perfect but sound screws it up...

---

### Post by MaZiNgA on 2004-12-21
RESOLVED!!!! After two months I got my sound working!! Hooray!
The fix was really stupid: I just disabled my acpi through BIOS!! Hope this helps!

PS: Mods plz add resolved to title!

---

