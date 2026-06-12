---
title: "Trying to get Accer laptop setup for wireless"
date: 2011-09-29
forum: Hardware
---

### Post by waterleat on 2011-09-29
I am trying to get my laptop working so that I can use its wireless connection. 
It is an ACER Travelmate 292LCi. maybe not the best laptop!

Here are some outputs that will give you a starting point to find out what is going on

d@d-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux d-laptop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux


d@d-laptop:~$ lspci -nnk | grep -iA2 net
01:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
01:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200


d@d-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:eek:ff/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


d@d-laptop:~$ rfkill list all                                    [COLOR=Blue]Note here that no output is shown even though the command was entered[/COLOR]


d@d-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
pcmcia                 30784  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
joydev                  8740  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
yenta_socket           20408  1 
ipw2200               135216  0 
rsrc_nonstatic         10015  1 yenta_socket
snd                    54244  14  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_   oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti  mer,snd_seq_device
libipw                 39896  1 ipw2200
i915                  288611  3 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                5046  2 ipw2200,libipw
drm_kms_helper         29329  1 i915
ppdev                   5259  0 
soundcore               6620  1 snd
intel_agp              24375  2 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
led_class               2864  0 
psmouse                63677  0 
serio_raw               3978  0 
parport_pc             25962  1 
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ieee1394               81181  1 ohci1394
d@d-laptop:~$ 

d@d-laptop:~$ dmesg | grep ipw2200
[   17.450213] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.450216] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.917806] ipw2200 0000:01:02.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   17.925065] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.925139] ipw2200 0000:01:02.0: firmware: requesting ipw2200-bss.fw
[   18.165219] ipw2200: Radio Frequency Kill Switch is On:
[   18.197849] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 4493.012243] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[ 4493.012283] ipw2200 0000:01:02.0: PCI INT A disabled
[ 4493.028242] PM: suspend of drv:ipw2200 dev:0000:01:02.0 complete after 1021.875 msecs
[ 4493.105231] ipw2200 0000:01:02.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[ 4493.105231] ipw2200 0000:01:02.0: restoring config space at offset 0x4 (was 0x0, writing 0xe0000000)
[ 4493.105231] ipw2200 0000:01:02.0: restoring config space at offset 0x3 (was 0x0, writing 0x8000)
[ 4493.105231] ipw2200 0000:01:02.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[ 4494.705339] ipw2200 0000:01:02.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[ 4494.822615] ipw2200: Radio Frequency Kill Switch is On:
d@d-laptop:~$ 

I hope that you can point me in right direction

---

