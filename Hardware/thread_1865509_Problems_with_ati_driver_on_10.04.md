---
title: "Problems with ati driver on 10.04"
date: 2011-10-20
forum: Hardware
---

### Post by nowave7 on 2011-10-20
As of today my 10.04 installation of Ubuntu is not using fglrx ati driver, but uses vga16fb instead. Don't know what was the cause of this, but I've tried pretty much everything I could think of to restore it to previous state. I've tried reinstalling the ati driver, didn't help, I've tried ```
dpkg-reconfigure xserver-xorg
```, didn't help. I've also tried running System/Administration/Hardware Drivers, only to see that there were no hardware drivers available. ```
aticonfig --list-adapters
``` reports that there are no adapters present, even though lspci does not agree:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
```
Kernel version is:
```
2.6.32-34-generic-pae
``` on a 32bit Ubuntu 10.04.

This is what lsmod shows:
```
Module                  Size  Used by
binfmt_misc             6587  1 
pci_stub                1102  1 
vboxpci                14595  0 
vboxnetadp              6808  0 
vboxnetflt             16652  0 
vboxdrv               249958  3 vboxpci,vboxnetadp,vboxnetflt
vmnet                  40981  13 
vmblock                10766  1 
vsock                  37367  0 
vmci                   53002  1 vsock
vmmon                  63160  0 
xt_limit                1382  8 
xt_tcpudp               2011  16 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
radeon                699277  0 
ttm                    49943  1 radeon
drm_kms_helper         29329  1 radeon
drm                   164308  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
deflate                 1645  0 
zlib_deflate           19568  1 deflate
ctr                     3197  0 
twofish                 5419  0 
twofish_common         12799  1 twofish
camellia               18884  0 
serpent                17517  0 
blowfish                7306  0 
cast5                  15576  0 
des_generic            15983  0 
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
xcbc                    2255  0 
rmd160                  6272  0 
sha256_generic         11191  0 
sha1_generic            1751  0 
crypto_null             2262  0 
af_key                 24195  0 
iptable_nat             3543  0 
nf_nat                 15560  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10346  9 iptable_nat,nf_nat
nf_conntrack           60943  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          1549  0 
iptable_filter          1369  1 
snd_intel8x0           25652  2 
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14175  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
w83627ehf              17634  0 
hwmon_vid               2298  1 w83627ehf
snd_seq_oss            26722  0 
coretemp                4417  0 
snd_seq_midi            4557  0 
ppdev                   5259  0 
parport_pc             26250  1 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
psmouse                63677  0 
vga16fb                11385  1 
serio_raw               3978  0 
vgastate                8961  1 vga16fb
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24671  0 
agpgart                31788  3 ttm,drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67288  1 usbhid
r8169                  34396  0 
mii                     4381  1 r8169
```

I'm suspecting that the fact that I have two display controllers is the issue here, but don't know how to fix this. Any ideas?

---

### Post by nowave7 on 2011-10-20
My bad, these two adapters that are present, that is ok, because this card's got both DVI and D-SUB.

---

### Post by nowave7 on 2011-10-21
Also, the latest driver for x1300/1550 is no longer compatible with latest kernel. I don't actually want ati proprietary driver, open source one is good enough, but is not working either.

So, no ideas anyone?

---

