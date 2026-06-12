---
title: "usb 3.0 pciE card"
date: 2011-11-11
forum: Hardware
---

### Post by spezticle on 2011-11-11
when i installed ubuntu 11.04 x64, the pcie card worked oob
upon installing i386 now it doesn't work.

any insight as to why or how to fix?
thanks,

---

### Post by northd_tech on 2011-11-11
Could you copy/paste the results of the following terminal commands here:

```
lsusb
lsmod
```

Also, if you still have the LiveCD/DVD for the x64 11.04 version, it could be very helpful to post the results of those same commands from the x64 'work OOB' version (to hopefully highlight the missing 32-bit i386 module(s) ).

---

### Post by spezticle on 2011-11-12
alright, here's my i386 output:
lsusb:
```


Bus 006 Device 002: ID 1058:0740 Western Digital Technologies, Inc. 
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 003: ID 0d62:001c Darfon Electronics Corp. Benq X120 Internet Keyboard Pro
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and lsmod:
```


Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
xt_multiport           12533  1 
binfmt_misc            13213  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  451013  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40971  1 i915
drm                   184164  3 i915,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
ipt_REJECT             12512  1 
ipt_LOG                12784  5 
xt_limit               12541  7 
xt_tcpudp              12531  15 
ipt_addrtype           12535  4 
usbhid                 41704  0 
dcdbas                 14054  0 
xt_state               12514  7 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hid                    77084  1 usbhid
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
psmouse                73312  0 
ses                    17137  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
snd_timer              28659  2 snd_pcm,snd_seq
nf_conntrack_ipv4      19024  9 nf_nat
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
enclosure              14656  1 ses
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
iptable_filter         12706  1 
i2c_algo_bit           13184  1 i915
ip_tables              18125  1 iptable_filter
x_tables               21907  11 xt_multiport,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
e100                   40108  0 
xhci_hcd               68062  0 

```

i will post again with the output from x64. must reboot.

> **northd_tech said:**
> Could you copy/paste the results of the following terminal commands here:

```
lsusb
lsmod
```

Also, if you still have the LiveCD/DVD for the x64 11.04 version, it could be very helpful to post the results of those same commands from the x64 'work OOB' version (to hopefully highlight the missing 32-bit i386 module(s) ).

---

### Post by spezticle on 2011-11-12
okay, this is strange. it's working now.

all throughout today, every time I plugged my external HDD into the usb 3.0 card, it wouldn't detect. I unplugged it and put it away.

I read your reply, plug in the HDD, do the lsusb and lsmod, you seen the results before this message.

Well, the hdd is sitting a few inches from my keyboard. Right before I click 'restart' so i can boot to an x64 cd, i hear the hdd spin up. I do lsusb and lsmod again and these are my results:

lsusb:
```


Bus 006 Device 002: ID 1058:0740 Western Digital Technologies, Inc. 
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 003: ID 0d62:001c Darfon Electronics Corp. Benq X120 Internet Keyboard Pro
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod:
```


Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
xt_multiport           12533  1 
binfmt_misc            13213  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  451013  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40971  1 i915
drm                   184164  3 i915,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
ipt_REJECT             12512  1 
ipt_LOG                12784  5 
xt_limit               12541  7 
xt_tcpudp              12531  15 
ipt_addrtype           12535  4 
usbhid                 41704  0 
dcdbas                 14054  0 
xt_state               12514  7 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hid                    77084  1 usbhid
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
psmouse                73312  0 
ses                    17137  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
snd_timer              28659  2 snd_pcm,snd_seq
nf_conntrack_ipv4      19024  9 nf_nat
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
enclosure              14656  1 ses
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
iptable_filter         12706  1 
i2c_algo_bit           13184  1 i915
ip_tables              18125  1 iptable_filter
x_tables               21907  11 xt_multiport,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
e100                   40108  0 
xhci_hcd               68062  0 

```

now lsusb shows my hdd, first entry.
interesting indeed.
damn computer likes to mess with me, i swear.

Edit:
wait, this is kind of strange. it seems as though it is working before as well and I just didn't notice it. I wonder if the USB 3.0 cable I have is faulty. it's a 3meter usb3.0 cable that I bought off of amazon.com for the hdd.

---

### Post by northd_tech on 2011-11-12
Well, my first impression (based upon my old USB 2.0 experiences) is that 3 meters is WAAAY too long for high speed communications- I'm still not sure HOW they get those **claimed** transfer rates on a USB port.

I'd try it with a different **USB 3.0-rated** cable in the [COLOR=Blue]**0.5-1m**[/COLOR] length range.  Perhaps you can test the external HDD out at a computer store with one of their USB 3.0 cables if you ask nicely.

It is curious, because your device showed up both times to **lsusb** as:
>  [COLOR=Red]**Bus 006 Device 002**[/COLOR]: ID 1058:0740 Western Digital Technologies, Inc. 
Also, lsmod shows a "usb_storage" module both times.  You can make that USB part easier to read with this command:

```
lsmod | grep usb
```Also, it might be worth taking a look at what this command tells us:

```
sudo modinfo usb_storage
```It could be that your device is connected and talking, but the USB 3.0 bus is 'timing out' before that Western Digital device ID# 1058:0740 WAAAY out there on [COLOR=Red]**Bus #006 Device #002**[/COLOR] is taking too long to respond, so this guy is giving up waiting for a resonse:

> [COLOR=Red]**Bus 006**[/COLOR] Device 001: ID 1d6b:0003 Linux Foundation **3.0 root hub**
Edit:  What are the chances that you have an 'iffy' USB port- have you tried connecting it do different USB ports and get the exact same results (except of course your Bus & Device numbers might/will change)?

---

