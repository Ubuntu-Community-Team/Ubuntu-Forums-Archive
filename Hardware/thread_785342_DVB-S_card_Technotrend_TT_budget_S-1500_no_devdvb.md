---
title: "DVB-S card Technotrend TT budget S-1500: no /dev/dvb"
date: 2008-05-07
forum: Hardware
---

### Post by pavel__ on 2008-05-07
hi

i try to configure the new dvb-s card, but /dev/dvb* is not created. here are some outputs:

```
# ls /dev/dv*
ls: /dev/dv*: No such file or directory 
```
```
# uname -a
Linux eisen 2.6.25.1 #11 Tue May 6 18:48:58 CEST 2008 i686 GNU/Linux 
```
```
# lspci
0000:00:0c.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01) 
```
```
# lspci -v
...
0000:00:0c.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: Technotrend Systemtechnik GmbH: Unknown device 1017
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at fde00000 (32-bit, non-prefetchable) [size=512]
...
```
```
# lsmod
Module                  Size  Used by
cx24110                 8080  0
mxb                    17040  0
hexium_orion            8724  0
hexium_gemini           9492  0
saa7134_empress         9876  0
dpc7146                 7764  0
saa7134               144708  1 saa7134_empress
cpia                   46232  0
msp3400                33524  0
vivi                   17068  0
cafe_ccic              26824  0
saa5249                13028  0
tuner                  29968  0
saa7146_vv             48984  4 mxb,hexium_orion,hexium_gemini,dpc7146
saa5246a               10784  0
tda7432                 8312  0
wm8739                  5184  0
dib3000mc              12888  0
saa7115                17428  0
tuner_simple           15552  0
dib7000m               15888  0
wm8775                  6608  0
upd64031a               4672  0
tvaudio                25184  0
videobuf_dma_sg        14224  3 saa7134_empress,saa7134,saa7146_vv
videodev               33828  11 saa7134_empress,saa7134,cpia,msp3400,vivi,cafe_ccic,saa5249,tuner,saa7146_vv,saa5246a,tda7432
dib7000p               17368  0
tcm825x                 7432  0
ir_kbd_i2c             10080  1 saa7134
saa717x                16704  0
ov7670                  9288  0
cs53l32a                6996  0
tvp5150                21352  0
saa7127                10180  0
upd64083                4544  0
videobuf_vmalloc        7632  1 vivi
ves1x93                 6864  0
adv7175                 5584  0
ves1820                 6352  0
vpx3220                 8080  0
v4l2_common            10952  14 saa7134,msp3400,tuner,wm8739,saa7115,wm8775,upd64031a,tvaudio,saa717x,ov7670,cs53l32a,tvp5150,saa7127,upd64083
dvb_pll                 8948  0
au8522                  7504  0
stv0297                 8072  0
compat_ioctl32          1224  2 saa7134,vivi
bt856                   5264  0
dib3000mb              12040  0
adv7170                 5712  0
v4l2_int_device         3016  1 tcm825x
tda8083                 6352  0
saa7185                 4944  0
s5h1409                 9744  0
tda8290                17040  0
mt2266                  5584  0
lnbp21                  2120  0
tda9840                 7208  0
ks0127                  9252  0
dibx000_common          4176  3 dib3000mc,dib7000m,dib7000p
bt819                   6928  0
mt2131                  6032  0
saa7110                 8080  0
videobuf_core          18704  6 saa7134_empress,saa7134,vivi,saa7146_vv,videobuf_dma_sg,videobuf_vmalloc
tea6415c                6120  0
tuner_types            14280  1 tuner_simple
tda10023                6476  0
tua6100                 3080  0
l64781                  7312  0
tveeprom               12432  1 saa7134
saa7114                 9360  0
mt20xx                 13920  0
tda9887                11808  0
isl6421                 2184  0
tuner_3036              4564  0
mt2060                  5264  0
zl10353                 8024  0
tda18271               36640  0
tda10021                6672  0
tda827x                10576  0
cx22702                 6160  0
cx22700                 6096  0
saa7111                 5648  0
s5h1420                12240  0
tda10086                9808  0
mt352                   6672  0
saa7191                 6280  0
tea5767                 7440  0
bt866                   4232  0
mt312                   8400  0
saa6752hs               9888  0
lgdt330x                8784  0
v4l1_compat            14992  2 saa7146_vv,videodev
tea6420                 6120  0
stv0299                10648  0
cx24123                14680  0
tda826x                 3664  0
dib0070                 7952  0
isl6405                 2184  0
qt1010                  6416  0
nxt6000                 7632  0
tda1004x               15760  0
s5h1411                10000  0
itd1000                 6544  0
tda9875                 8040  0
i2c_viapro              9060  0
ide_pci_generic         4368  0 [permanent]
saa7146                19736  5 mxb,hexium_orion,hexium_gemini,dpc7146,saa7146_vv
ttpci_eeprom            2504  0
ir_common              39896  2 saa7134,ir_kbd_i2c
skge                   40604  0
sk98lin               153372  0
```

but

```
# dmesg | grep dvb
dvb_core: module is already loaded
budget_core: disagrees about version of symbol dvb_dmxdev_init
budget_core: Unknown symbol dvb_dmxdev_init
budget_core: disagrees about version of symbol dvb_register_adapter
budget_core: Unknown symbol dvb_register_adapter
budget_core: disagrees about version of symbol dvb_net_init
budget_core: Unknown symbol dvb_net_init
budget_core: disagrees about version of symbol dvb_dmxdev_release
budget_core: Unknown symbol dvb_dmxdev_release
budget_core: disagrees about version of symbol dvb_net_release
budget_core: Unknown symbol dvb_net_release
dvb_core: module is already loaded
budget_core: disagrees about version of symbol dvb_dmxdev_init
budget_core: Unknown symbol dvb_dmxdev_init
budget_core: disagrees about version of symbol dvb_register_adapter
budget_core: Unknown symbol dvb_register_adapter
budget_core: disagrees about version of symbol dvb_net_init
budget_core: Unknown symbol dvb_net_init
budget_core: disagrees about version of symbol dvb_dmxdev_release
budget_core: Unknown symbol dvb_dmxdev_release
budget_core: disagrees about version of symbol dvb_net_release
budget_core: Unknown symbol dvb_net_release

```

the kernel ist self-compiled. what do i have to do next, in order to find out, why /dev/dvb* is missing?

hope for help

---

