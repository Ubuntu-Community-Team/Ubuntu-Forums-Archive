---
title: "TV card not loading after resume"
date: 2014-05-01
forum: Hardware
---

### Post by mariogdlt on 2014-05-01
Hi,

Since last Ubuntu versions, when I resume after suspending PC, TV card (a PCI "cx88" card) does not load. I need to reboot to have it working, but IR works (I use lirc)
I have tried something but no luck.

TV card, if I remember, is Hauppauge WinTV-HVR-4400-
```
lspci
``` shows:
```
04:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)04:02.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
04:02.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
```

I tried to include in */etc/pm/config.d/unload_modules* the following:
```
SUSPEND_MODULES="$SUSPEND_MODULES cx88_dvb cx8802 cx8800 cx88xx"
```
and also tried with
```
SUSPEND_MODULES="$SUSPEND_MODULES cx88_dvb cx8802 cx8800 cx88xx  cx22702 cx24116 cx88_alsa"
```
but it didn't work

My modules (using *lsmod*) are:
```
Module                  Size  Used bypci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13213  3 
cfg80211              409394  0 
rfcomm                 53664  4 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
dm_crypt               22622  0 
snd_hda_codec_hdmi     45303  4 
ip6t_REJECT            12809  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      14318  8 
nf_defrag_ipv6         26163  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17445  20 
gpio_ich               13229  0 
xt_limit               12541  3 
xt_tcpudp              12756  20 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  8 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  16 
snd_emu10k1_synth      13007  0 
cx22702                13257  1 
snd_emux_synth         33455  1 snd_emu10k1_synth
isl6421                12638  1 
snd_seq_midi_emul      13432  1 snd_emux_synth
snd_seq_virmidi        13220  1 snd_emux_synth
cx24116                18497  1 
cx88_dvb               33353  0 
cx88_vp3054_i2c        12799  1 cx88_dvb
videobuf_dvb           13820  1 cx88_dvb
dvb_core              101206  2 cx88_dvb,videobuf_dvb
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
wm8775                 12906  1 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
ir_lirc_codec          12869  0 
lirc_dev               19324  1 ir_lirc_codec
nf_nat_ftp             12645  0 
ir_mce_kbd_decoder     13030  0 
ir_sanyo_decoder       12727  0 
ir_sony_decoder        12625  0 
nf_nat                 20826  1 nf_nat_ftp
ir_jvc_decoder         12655  0 
gspca_pac207           13129  0 
nf_conntrack_ftp       14056  1 nf_nat_ftp
ir_rc6_decoder         12754  0 
ir_rc5_decoder         12622  0 
gspca_main             27814  1 gspca_pac207
nf_conntrack           83685  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
ir_nec_decoder         12787  0 
joydev                 17101  0 
r8712u                158706  0 
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
rc_hauppauge           12484  0 
tuner_simple           22016  2 
tuner_types            19268  1 tuner_simple
tda9887                17666  1 
tda8290                22060  0 
tuner                  26740  2 
snd_hda_codec_realtek    51029  1 
snd_emu10k1           141250  3 snd_emu10k1_synth
snd_hda_intel          42730  6 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  3 snd_hda_codec,snd_emux_synth,snd_emu10k1
cx88_alsa              17946  1 
coretemp               13195  0 
snd_ac97_codec        105709  1 snd_emu10k1
kvm_intel             132549  0 
ac97_bus               12642  1 snd_ac97_codec
kvm                   388083  1 kvm_intel
snd_pcm                85501  7 snd_ac97_codec,cx88_alsa,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_emu10k1
snd_page_alloc         14230  3 snd_pcm,snd_hda_intel,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25135  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
cx8802                 18516  1 cx88_dvb
cx8800                 32767  0 
psmouse                91033  0 
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
cx88xx                 82439  4 cx88_dvb,cx88_alsa,cx8800,cx8802
serio_raw              13230  0 
btcx_risc              13400  4 cx88_alsa,cx8800,cx8802,cx88xx
tveeprom               16984  1 cx88xx
videobuf_dma_sg        18710  5 cx88_dvb,cx88_alsa,cx8800,cx8802,cx88xx
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
rc_core                26724  12 lirc_dev,ir_lirc_codec,rc_hauppauge,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,cx88xx,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder
lpc_ich                16864  0 
v4l2_common            15132  4 tuner,cx8800,cx88xx,wm8775
videobuf_core          25098  5 videobuf_dma_sg,videobuf_dvb,cx8800,cx8802,cx88xx
snd_timer              28584  3 snd_pcm,snd_seq,snd_emu10k1
videodev              108503  8 tuner,cx88_alsa,gspca_pac207,cx8800,cx88xx,gspca_main,v4l2_common,wm8775
snd                    60871  35 snd_hda_codec_realtek,snd_ac97_codec,cx88_alsa,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_hda_codec,snd_hda_intel,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
i2c_algo_bit           13197  2 cx88_vp3054_i2c,cx88xx
emu10k1_gp             12541  0 
gameport               15189  2 emu10k1_gp
nvidia              10304642  50 
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
hid_logitech           22181  0 
ff_memless             13325  1 hid_logitech
usbhid                 47035  0 
hid                    87604  3 hid_generic,hid_logitech,usbhid
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
r8169                  61562  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 r8169
floppy                 55378  0 
```

I also tried to remove modules before suspending but modprobe gives me FATAL errors. For this, I tried some of this info: [http://ubuntuforums.org/archive/index.php/t-1523921.html](http://ubuntuforums.org/archive/index.php/t-1523921.html)

Could anyone help me?

Thanks in advance!

---

### Post by mariogdlt on 2014-05-01
Anyone could help me?

---

