---
title: "many segfault error"
date: 2008-08-20
forum: General Help
---

### Post by allorder on 2008-08-20
Hi everyone, since I logged in ubuntu I got segfault today :confused:, please help

Aug 20 00:39:41 ubuntu kernel: [ 2424.459986] apt-check[1310]: segfault at 987694a0 eip b7cbe7e6 esp bf98a2a0 error 4
Aug 20 01:00:33 ubuntu kernel: [ 3675.843720] deb_checkmd5sum[31841]: segfault at bffe7d54 eip 0804b1f0 esp bffa7d30 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.412075] deb_checkmd5sum[819]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.413711] deb_checkmd5sum[818]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.415594] deb_checkmd5sum[823]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.417181] deb_checkmd5sum[822]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.419003] deb_checkmd5sum[827]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.420628] deb_checkmd5sum[826]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.423302] deb_checkmd5sum[831]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.424940] deb_checkmd5sum[830]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:34 ubuntu kernel: [ 3677.426713] deb_checkmd5sum[835]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:00:56 ubuntu kernel: [ 3699.409414] printk: 16 messages suppressed.
Aug 20 01:00:56 ubuntu kernel: [ 3699.409420] deb_checkmd5sum[20229]: segfault at bffe7ad8 eip 0804b575 esp bffa7ab0 error 4
Aug 20 01:01:00 ubuntu kernel: [ 3703.346801] deb_checkmd5sum[23796]: segfault at bffe7d54 eip 0804b1f0 esp bffa7d30 error 4
Aug 20 01:01:07 ubuntu kernel: [ 3709.726321] deb_checkmd5sum[29437]: segfault at b7ffb69c eip b7fad35b esp bffa7a88 error 4
Aug 20 01:01:21 ubuntu kernel: [ 3723.835030] deb_checkmd5sum[11758]: segfault at b7ffb69c eip b7fad35b esp bffa7968 error 4
Aug 20 01:01:21 ubuntu kernel: [ 3723.835984] deb_checkmd5sum[11756]: segfault at b7ffb69c eip b7fad35b esp bffa7a88 error 4
Aug 20 01:01:23 ubuntu kernel: [ 3726.390359] sed[13638]: segfault at b7f7d440 eip b7e53bc0 esp bfd02560 error 4
Aug 20 01:04:46 ubuntu kernel: [ 3929.380385] deb_checkmd5sum[26028]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:04:46 ubuntu kernel: [ 3929.382612] deb_checkmd5sum[26027]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:04:46 ubuntu kernel: [ 3929.384394] deb_checkmd5sum[26032]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:04:46 ubuntu kernel: [ 3929.385921] deb_checkmd5sum[26031]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 01:04:46 ubuntu kernel: [ 3929.386244] deb_checkmd5sum[26025]: segfault at ff0a0000 eip ff0a0000 esp ff0a0000 error 4
Aug 20 07:25:08 ubuntu kernel: [26746.589980] sierpinski3d[24508]: segfault at 001c021c eip b7840487 esp bf808fec error 4
Aug 20 08:17:17 ubuntu kernel: [29874.477571] jigglypuff[1081]: segfault at 08002810 eip 0804bc4d esp bfc02d60 error 4
Aug 20 08:43:55 ubuntu kernel: [31472.666966] hyperspace[5081] general protection eip:b73d5988 esp:bff45640 error:0
Aug 20 08:54:13 ubuntu kernel: [32090.356586] metaballs[6542]: segfault at 0005a654 eip b7bd74b1 esp bf8ef490 error 4

Aug 20 10:29:30 ubuntu kernel: [37805.730335] synaptic[19873]: segfault at 00000000 eip b7f9a69e esp bf8d4d68 error 4
Aug 20 10:34:46 ubuntu kernel: [38122.131835] apt-check[20490]: segfault at 712579f0 eip b7bf17e6 esp bfab0da0 error 4
Aug 20 10:36:39 ubuntu kernel: [38235.105111] lsb_release[20569]: segfault at 00007f70 eip b7de7f79 esp bfc544cc error 6
Aug 20 10:54:48 ubuntu kernel: [39323.970645] synaptic[20577]: segfault at 00000001 eip b7982f99 esp bf9eae30 error 4
Aug 20 11:03:33 ubuntu kernel: [39848.567309] rhythmbox[19502]: segfault at 00c848a8 eip b746511e esp bf9cd500 error 4
Aug 20 11:19:10 ubuntu kernel: [40785.156562] rhythmbox[21616]: segfault at efe2287c eip b71e7508 esp b2f07e20 error 5
Aug 20 11:31:57 ubuntu kernel: [41552.285944] compiz.real[6166]: segfault at 0000f6a2 eip 08055a6d esp bfe539b0 error 4

Aug 20 14:50:05 ubuntu kernel: [53438.471182] x-session-manag[22878]: segfault at 00000000 eip b7ff069e esp bfbbae8c error 4
Aug 20 14:55:08 ubuntu kernel: [53740.872122] rolauncher[24249]: segfault at 0001495c eip b70c2e1c esp bf909e70 error 4
Aug 20 14:57:36 ubuntu kernel: [53889.073938] python[23382]: segfault at 00000000 eip b7efeb90 esp bfb9ba1c error 6
Aug 20 14:59:14 ubuntu kernel: [53986.977430] rhythmbox[24899]: segfault at 00000010 eip b295b0ec esp af5d82a0 error 4

---

### Post by amo-ej1 on 2008-08-20
It might not be a bad idea to have memcheck run a diagnosis on the state of your memory ...

---

### Post by allorder on 2008-08-20
> **amo-ej1 said:**
> It might not be a bad idea to have memcheck run a diagnosis on the state of your memory ...

thanks a lot, fixed now :)

---

