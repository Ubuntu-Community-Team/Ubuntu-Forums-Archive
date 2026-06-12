---
title: "Moschip Semiconductor - mcs7780 not working"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by CyberCod on 2007-09-01
I've got a usb-irda dongle recognized as:
```

ID 9710:7780 MosChip Semiconductor 

```


It is using the driver mcs7780, which is loaded properly.
```

 lsmod | grep mcs7780
mcs7780                13060  0 
irda                  201532  1 mcs7780
crc_ccitt               3072  2 mcs7780,irda
usbcore               135048  6 mcs7780,at76_usb,xpad,usbhid,uhci_hcd

```

unfortunately, it doesn't seem to associate itself in /dev.  

When its freshly plugged in, dmesg gives
```

<6>usb 1-2.4.4: new full speed USB device using uhci_hcd and address 11
[ 7642.901853] usb 1-2.4.4: configuration #1 chosen from 1 choice

```


I found a similar bug report at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/125882]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/125882")

And someone stated there that the driver would be implemented in Gutsy.  My question is whether this driver will be fully implemented, or will it be used in its current broken state.  Also, is there any way to add proper functionality for this device without doing a distro upgrade?

---

### Post by CyberCod on 2007-09-02
I have found that when the dongle is plugged in, that iwconfig shows irda0 as a detected interface...

```

irda0     no wireless extensions.

```

the question is whether there is a place under /dev that this is tied to, and what it is called.

are there any log files that might help me find out?

---

### Post by CyberCod on 2007-09-02
Another update, I managed to use **irdadump** to capture some signals from the dongle while doing a sync operation on my Treo 300.

I piped this into a text file...

```


02:09:35.350653 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:35.439525 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:35.439577 xid:rsp a68bd733 > ae142630 S=6 s=4 desk-machine hint=0400 [ Computer ] (28) 
02:09:35.517531 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:35.609488 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:35.659476 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=36 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:35.659559 ua:rsp ca=36 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:36.222399 rr:cmd < ca=36 pf=1 nr=0 (2) 
02:09:36.222471 rr:rsp > ca=36 pf=1 nr=0 (2) 
02:09:36.228355 i:cmd  < ca=36 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:36.228424 i:rsp  > ca=36 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:36.239359 i:cmd  < ca=36 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:36.239404 i:rsp  > ca=36 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:36.247350 disc:cmd < ca=0x36 pf=1 (2) 
02:09:36.247373 ua:rsp ca=36 pf=1 a68bd733 > ae142630 (10) 
02:09:38.437961 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:38.519955 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:38.609919 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:38.699895 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:38.789905 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:38.789972 xid:rsp a68bd733 > ae142630 S=6 s=4 desk-machine hint=0400 [ Computer ] (28) 
02:09:38.867874 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:39.018841 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:39.068845 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=3c 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:39.068952 ua:rsp ca=3c pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:39.632729 rr:cmd < ca=3c pf=1 nr=0 (2) 
02:09:39.632791 rr:rsp > ca=3c pf=1 nr=0 (2) 
02:09:39.639696 i:cmd  < ca=3c pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:39.639754 i:rsp  > ca=3c pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:39.649696 i:cmd  < ca=3c pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:39.649730 i:rsp  > ca=3c pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:39.657727 disc:cmd < ca=0x3c pf=1 (2) 
02:09:39.657785 ua:rsp ca=3c pf=1 a68bd733 > ae142630 (10) 
02:09:41.708335 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:41.708402 xid:rsp a68bd733 > ae142630 S=6 s=0 desk-machine hint=0400 [ Computer ] (28) 
02:09:41.787299 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:41.869290 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:41.959274 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:42.049252 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:42.139257 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:42.239244 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:42.288200 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=10 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:42.288290 ua:rsp ca=10 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:42.853110 rr:cmd < ca=10 pf=1 nr=0 (2) 
02:09:42.853173 rr:rsp > ca=10 pf=1 nr=0 (2) 
02:09:42.860079 i:cmd  < ca=10 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:42.860140 i:rsp  > ca=10 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:42.871077 i:cmd  < ca=10 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:42.871112 i:rsp  > ca=10 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:42.879087 disc:cmd < ca=0x10 pf=1 (2) 
02:09:42.879134 ua:rsp ca=10 pf=1 a68bd733 > ae142630 (10) 
02:09:44.927703 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:45.008742 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:45.098683 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:45.188661 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:45.278646 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:45.368673 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:45.368730 xid:rsp a68bd733 > ae142630 S=6 s=5 desk-machine hint=0400 [ Computer ] (28) 
02:09:45.456624 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:45.505595 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=a0 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:45.505692 ua:rsp ca=a0 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:46.072549 rr:cmd < ca=a0 pf=1 nr=0 (2) 
02:09:46.072612 rr:rsp > ca=a0 pf=1 nr=0 (2) 
02:09:46.079502 i:cmd  < ca=a0 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:46.079636 i:rsp  > ca=a0 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:46.090519 i:cmd  < ca=a0 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:46.090649 i:rsp  > ca=a0 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:46.098530 disc:cmd < ca=0xa0 pf=1 (2) 
02:09:46.098653 ua:rsp ca=a0 pf=1 a68bd733 > ae142630 (10) 
02:09:48.147094 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:48.147160 xid:rsp a68bd733 > ae142630 S=6 s=0 desk-machine hint=0400 [ Computer ] (28) 
02:09:48.226090 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:48.309075 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:48.399049 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:48.489013 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:48.578998 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:48.678037 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:48.727996 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=2a 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:48.728112 ua:rsp ca=2a pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:49.291860 rr:cmd < ca=2a pf=1 nr=0 (2) 
02:09:49.291914 rr:rsp > ca=2a pf=1 nr=0 (2) 
02:09:49.298840 i:cmd  < ca=2a pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:49.298901 i:rsp  > ca=2a pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:49.309851 i:cmd  < ca=2a pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:49.309905 i:rsp  > ca=2a pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:49.317836 disc:cmd < ca=0x2a pf=1 (2) 
02:09:49.317861 ua:rsp ca=2a pf=1 a68bd733 > ae142630 (10) 
02:09:51.367465 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:51.448464 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:51.538441 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:51.538497 xid:rsp a68bd733 > ae142630 S=6 s=2 desk-machine hint=0400 [ Computer ] (28) 
02:09:51.616427 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:51.698416 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:51.788399 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:51.888384 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:51.937368 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=34 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:51.937471 ua:rsp ca=34 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:52.501270 rr:cmd < ca=34 pf=1 nr=0 (2) 
02:09:52.501345 rr:rsp > ca=34 pf=1 nr=0 (2) 
02:09:52.507240 i:cmd  < ca=34 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:52.507321 i:rsp  > ca=34 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:52.518264 i:cmd  < ca=34 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:52.518359 i:rsp  > ca=34 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:52.526253 disc:cmd < ca=0x34 pf=1 (2) 
02:09:52.526315 ua:rsp ca=34 pf=1 a68bd733 > ae142630 (10) 
02:09:54.576851 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:54.576907 xid:rsp a68bd733 > ae142630 S=6 s=0 desk-machine hint=0400 [ Computer ] (28) 
02:09:54.655870 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:54.737828 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:54.827808 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:54.917777 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:55.007755 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:55.107772 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:55.157751 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=9e 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:55.157864 ua:rsp ca=9e pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:55.721631 rr:cmd < ca=9e pf=1 nr=0 (2) 
02:09:55.721695 rr:rsp > ca=9e pf=1 nr=0 (2) 
02:09:55.728626 i:cmd  < ca=9e pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:55.728715 i:rsp  > ca=9e pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:55.739644 i:cmd  < ca=9e pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:55.739730 i:rsp  > ca=9e pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:55.747613 disc:cmd < ca=0x9e pf=1 (2) 
02:09:55.747656 ua:rsp ca=9e pf=1 a68bd733 > ae142630 (10) 
02:09:57.796241 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:09:57.878208 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:09:57.968197 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:09:58.058170 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:09:58.148177 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:09:58.238166 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:09:58.238237 xid:rsp a68bd733 > ae142630 S=6 s=5 desk-machine hint=0400 [ Computer ] (28) 
02:09:58.325131 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:09:58.375105 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=86 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:09:58.375196 ua:rsp ca=86 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:09:58.940024 rr:cmd < ca=86 pf=1 nr=0 (2) 
02:09:58.940089 rr:rsp > ca=86 pf=1 nr=0 (2) 
02:09:58.945986 i:cmd  < ca=86 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:09:58.946046 i:rsp  > ca=86 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:09:58.956983 i:cmd  < ca=86 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:09:58.957017 i:rsp  > ca=86 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:09:58.964980 disc:cmd < ca=0x86 pf=1 (2) 
02:09:58.965009 ua:rsp ca=86 pf=1 a68bd733 > ae142630 (10) 
02:10:01.016621 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:10:01.097618 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:10:01.187594 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:10:01.277583 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:10:01.277650 xid:rsp a68bd733 > ae142630 S=6 s=3 desk-machine hint=0400 [ Computer ] (28) 
02:10:01.355548 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:10:01.437538 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:10:01.537521 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:10:01.586492 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=2c 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:10:01.586584 ua:rsp ca=2c pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:10:02.151396 rr:cmd < ca=2c pf=1 nr=0 (2) 
02:10:02.151455 rr:rsp > ca=2c pf=1 nr=0 (2) 
02:10:02.158369 i:cmd  < ca=2c pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:10:02.158427 i:rsp  > ca=2c pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:10:02.169367 i:cmd  < ca=2c pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:10:02.169401 i:rsp  > ca=2c pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:10:02.177364 disc:cmd < ca=0x2c pf=1 (2) 
02:10:02.177386 ua:rsp ca=2c pf=1 a68bd733 > ae142630 (10) 
02:10:04.305985 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:10:04.386945 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:10:04.476947 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:10:04.566917 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:10:04.566964 xid:rsp a68bd733 > ae142630 S=6 s=3 desk-machine hint=0400 [ Computer ] (28) 
02:10:04.644906 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:10:04.726922 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:10:04.826890 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:10:04.875846 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=26 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:10:04.875921 ua:rsp ca=26 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:10:05.439777 rr:cmd < ca=26 pf=1 nr=0 (2) 
02:10:05.439840 rr:rsp > ca=26 pf=1 nr=0 (2) 
02:10:05.445736 i:cmd  < ca=26 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:10:05.445793 i:rsp  > ca=26 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:10:05.456734 i:cmd  < ca=26 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:10:05.456768 i:rsp  > ca=26 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:10:05.464730 disc:cmd < ca=0x26 pf=1 (2) 
02:10:05.464752 ua:rsp ca=26 pf=1 a68bd733 > ae142630 (10) 
02:10:07.515371 xid:cmd ffffffff < ae142630 S=6 s=0 (14) 
02:10:07.597335 xid:cmd ffffffff < ae142630 S=6 s=1 (14) 
02:10:07.687325 xid:cmd ffffffff < ae142630 S=6 s=2 (14) 
02:10:07.777327 xid:cmd ffffffff < ae142630 S=6 s=3 (14) 
02:10:07.777390 xid:rsp a68bd733 > ae142630 S=6 s=3 desk-machine hint=0400 [ Computer ] (28) 
02:10:07.855292 xid:cmd ffffffff < ae142630 S=6 s=4 (14) 
02:10:07.997273 xid:cmd ffffffff < ae142630 S=6 s=5 (14) 
02:10:08.096247 xid:cmd ffffffff < ae142630 S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23) 
02:10:08.146236 snrm:cmd ca=fe pf=1 a68bd733 < ae142630 new-ca=c6 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=5 Min Turn Time=1000us Link Disc=40s (32) 
02:10:08.146324 ua:rsp ca=c6 pf=1 a68bd733 > ae142630 
	LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=1000us Link Disc=12s (31) 
02:10:08.201224 rr:cmd < ca=c6 pf=1 nr=0 (2) 
02:10:08.201276 rr:rsp > ca=c6 pf=1 nr=0 (2) 
02:10:08.208207 i:cmd  < ca=c6 pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6) 
02:10:08.208264 i:rsp  > ca=c6 pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6) 
02:10:08.218206 i:cmd  < ca=c6 pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37) 
02:10:08.218241 i:rsp  > ca=c6 pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11) 
02:10:08.226211 disc:cmd < ca=0xc6 pf=1 (2) 
02:10:08.226254 ua:rsp ca=c6 pf=1 a68bd733 > ae142630 (10) 

195 packets received by filter


```


Now I just gotta figure out what all that means! :lolflag:

So, in essence, the dongle is working, its sending and receiving... so that is something.

I just gotta figure out what to put as the location for the device under the Palm Pilot sync app.

---

### Post by CyberCod on 2007-09-02
A little more info I squeezed out of it.

```

#> cat /proc/net/irda/irlap
irlap0 state: LAP_NDM
  device name: irda0, hardware name: usb#8
  caddr: 0xce, saddr: 0xa68bd733, daddr: 0xa26f303f
  win size: 1, win: 1, line capacity: 4800, bytes left: 4800
  tx queue len: 0 win queue len: 0 rbusy: FALSE mbusy: FALSE
  retrans: 0 vs: 2 vr: 2 va: 0
  qos   bps     maxtt   dsize   winsize addbofs mintt   ldisc   comp
  tx    9600    0       64      1       12      0       0
  rx    9600    0       64      1       12      0       0

```

---

### Post by CyberCod on 2007-09-02
I'm starting to feel like the Ubuntu gurus may just be getting a little overwhelmed by the popularity of Ubuntu.  Perhaps the forums need to be split up a little further.

Instead of just "Hardware & Laptops" it should be

Hardware/Video
Hardware/Sound
Hardware/Input
Hardware/Network

and etcetera...

May make things a little more manageable.  I dunno.

Seems like it only takes 5 minutes for a post in here to get buried 3 pages deep.


Just the price of popularity I guess.... Would M$ suck so much if they weren't so popular?

---

