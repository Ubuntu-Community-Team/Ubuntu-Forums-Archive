---
title: "Palm m125 irda sync"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Grue on 2005-12-01
I just got me an old Palm M125 and want to use it with my Laptop and other devices. I got HotSync working over USB and the Dongle with Kpilot without a hitch, but I really want to just use my IrDA port in my laptop.

The port seems to be working without problems. I get this when I do an "irdadump /dev/ttyS1" while pressing 'HotSync' on the Palm:

```

01:12:31.729611 xid:cmd ffffffff < a11ac65e S=6 s=0 (14)
01:12:31.814456 xid:cmd ffffffff < a11ac65e S=6 s=1 (14)
01:12:31.904440 xid:cmd ffffffff < a11ac65e S=6 s=2 (14)
01:12:31.994446 xid:cmd ffffffff < a11ac65e S=6 s=3 (14)
01:12:32.084452 xid:cmd ffffffff < a11ac65e S=6 s=4 (14)
01:12:32.085467 xid:rsp 7c422f39 > a11ac65e S=6 s=4 stormbox hint=0400 [ Computer ] (24)
01:12:32.234427 xid:cmd ffffffff < a11ac65e S=6 s=5 (14)
01:12:32.334415 xid:cmd ffffffff < a11ac65e S=6 s=* IrCOMM hint=8204 [ PDA/Palmtop IrCOMM ] (23)
01:12:32.383398 snrm:cmd ca=fe pf=1 7c422f39 < a11ac65e new-ca=ec
        LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=512B Window Size=1 Add BOFS=0 Min Turn Time=5000us Link Disc=40s (32)
01:12:32.384513 ua:rsp ca=ec pf=1 7c422f39 > a11ac65e
        LAP QoS: Baud Rate=115200bps Max Turn Time=500ms Data Size=2048B Window Size=7 Add BOFS=0 Min Turn Time=5000us Link Disc=12s (31)
01:12:32.443366 rr:cmd < ca=ec pf=1 nr=0 (2)
01:12:32.444396 rr:rsp > ca=ec pf=1 nr=0 (2)
01:12:32.458782 i:cmd  < ca=ec pf=1 nr=0 ns=0 LM slsap=01 dlsap=00 CONN_CMD (6)
01:12:32.459471 i:rsp  > ca=ec pf=1 nr=1 ns=0 LM slsap=00 dlsap=01 CONN_RSP (6)
01:12:32.477355 i:cmd  < ca=ec pf=1 nr=1 ns=1 LM slsap=01 dlsap=00 GET_VALUE_BY_CLASS: "IrDA:IrCOMM" "IrDA:TinyTP:LsapSel" (37)
01:12:32.478453 i:rsp  > ca=ec pf=1 nr=2 ns=1 LM slsap=00 dlsap=01 GET_VALUE_BY_CLASS: No such class (11)
01:12:32.493387 disc:cmd < ca=0xec pf=1 (2)
01:12:32.494414 ua:rsp ca=ec pf=1 7c422f39 > a11ac65e (10)

```

That looks like it should so I detach and start Kpilot. Sadly it gives me this output while I try to HotSync:

```

02:04:34 Starting the KPilot daemon ...
02:04:35 Daemon status is `not running'
02:04:38 Trying to open device /dev/ttyS1...
02:04:38 Device link ready.
02:04:46 Cannot accept Pilot (Bad address)

```

I tried googling the error but there didn't seem to be much info on the stuff.

I hope someone has a solution as the dongle is a bit too large and unhandy to be useful in anything but a desktop system.

[Edit]

Oh I forgot. I made sure the Palm and kpilot connects at the same speed (115200).

---

