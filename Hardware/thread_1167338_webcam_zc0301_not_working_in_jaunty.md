---
title: "webcam zc0301 not working in jaunty"
date: 2009-05-22
forum: Hardware
---

### Post by Salute on 2009-05-22
Z-Star Microelectronics Corp. ZC0301 WebCam << my webcam

I've been looking at these pages and have followed the instructions, but have had no luck yet, so I'm here asking :"how do I use my webcam?"

[http://ubuntuforums.org/showthread.php?t=1002421&highlight=zc0301](http://ubuntuforums.org/showthread.php?t=1002421&highlight=zc0301)
[http://ubuntuforums.org/showpost.php?p=4582711&postcount=22](http://ubuntuforums.org/showpost.php?p=4582711&postcount=22)

:: my lsmod

Module                  Size  Used by
xt_limit               10116  8 
xt_tcpudp              11008  66 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13220  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
ath5k                 107008  0 
mac80211              217208  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_nat            13700  0 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat
nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
iptable_mangle         10880  0 
pcmcia                 44748  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
iptable_filter         10752  1 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
ppdev                  15620  0 
psmouse                61972  0 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
**gspca_zc3xx            55552  0 **
**gspca_main             29952  1 gspca_zc3xx**
pcspkr                 10496  0 
irda                  197180  0 
serio_raw              13316  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
i2c_sis96x             12420  0 
**videodev               41600  1 gspca_main**
**v4l1_compat            21764  1 videodev**
shpchp                 40212  0 
crc_ccitt              10112  1 irda
sis_agp                15360  1 
agpgart                42696  1 sis_agp
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

so I've
#modprobe -r gspca_main  (a bit different from the gutsy way, but hmm)
#modprobe -r gspca_zc03xx
#modprobe -r videodev
#modprobe gspca_main
...but no luck
...what's the difference here? what should I do differently?

---

### Post by Salute on 2009-05-25
being so close to having a working webcam, I decided to use a process of elimination and hope for the best, first I did #locate zc3xx ,and found all the drivers ( /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko ) ,then ,after a few different combos ,I got it

#modprobe -r gspca_zc3xx
#modprobe -r gspca_main
#modprobe -r v4l1-compat
#modprobe -r videodev  (as you can see, I went abit crazy with this (as I wasn't sure about it)
#modprobe gspca_zc3xx
#cheese
and rebooted (without the blacklist thing)
...great drivers, I'm thankful and happy

---

