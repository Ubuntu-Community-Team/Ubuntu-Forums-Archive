---
title: "Huagepauge PVR-150 remote setup"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Darkdelusions on 2007-06-20
I am currently on my last step of getting my myth box setup however I am running into an issue getting LIRC to see my remote. I  have 2 pvr-150's in my machine currently I downloaded the LIRC package and followed [this]("http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft") link. When I go and do  mode2 -d /dev/lirc0 or mode2 -d /dev/lirc1 I'm not seeing any remote output according to the walk threw i should see 

 code: 0x17a5
 code: 0x17a5
 code: 0x1fa5
 code: 0x1fa5

Anyone have any suggestions



Dmsg after the modprobe lirc_i2c

```
[ 1493.831292] lirc_dev: IR Remote Control driver registered, at major 61
[ 1493.832053] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel t                      ainted.
[ 1493.845975] bttv: driver version 0.9.16 loaded
[ 1493.845979] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 1493.903799] cx2388x v4l2 driver version 0.0.6 loaded
[ 1493.935567] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 1493.935606] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 1494.036953] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[ 1494.037245] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 2806.592278] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa                      0060/serio0).
[ 2806.592283] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2806.886995] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0                      060/serio0).
[ 2806.886999] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

---

