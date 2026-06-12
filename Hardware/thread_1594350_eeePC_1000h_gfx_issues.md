---
title: "eeePC 1000h gfx issues"
date: 2010-10-12
forum: Hardware
---

### Post by kingmanowar on 2010-10-12
Hello,

I did a clean install the maverick RC om my eee 1000h a few days ago. Things went well except a very annoying issue with graphics.
As a quick test I ran glxgears to make sure everything was ok. However I had very bad performance compared to lucid lynx. It was really jerky with very small values. Compiz was disabled and metacity composite too.
I tried now to install the final version but things have not improved and glxgears is still very jerky with very small fps:

Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
217 frames in 5.0 seconds = 43.335 FPS
160 frames in 5.0 seconds = 31.913 FPS
151 frames in 5.0 seconds = 30.122 FPS
150 frames in 5.0 seconds = 29.907 FPS
155 frames in 5.0 seconds = 30.911 FPS

The funny thing is if I move the mouse while running glxgears, everything improves a lot. glxgears is getting really smooth and I have much higher values:

Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
283 frames in 5.0 seconds = 56.517 FPS
298 frames in 5.0 seconds = 59.411 FPS
296 frames in 5.0 seconds = 59.195 FPS
298 frames in 5.0 seconds = 59.396 FPS
298 frames in 5.0 seconds = 59.425 FPS
297 frames in 5.0 seconds = 59.391 FPS

I'm getting basically synchronised with the refresh rate of the monitor.

Any idea ? I bet I am not the only one trying to run Maverick on a eee 1000h.

I tried to enable X-Updates ppa. But it does not change anything.

I noticed those messages when I run dmesg:

[    1.820768] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 202
[    1.820775] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    1.820783] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 a2 28 00 00  ........"d...(..
[    1.820789] <3>12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
[    1.820794] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
[    1.820800] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    1.820805] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X& 
[    1.820811] <3>5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00  ]#..............
[    1.820816] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe  ................
[    1.820821] <3>00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8  ................
[    1.820826] 
[    1.922640] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 202
[    1.922647] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    1.922655] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 a2 28 00 00  ........"d...(..
[    1.922661] <3>12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
[    1.922666] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
[    1.922672] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    1.922677] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X& 
[    1.922683] <3>5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00  ]#..............
[    1.922688] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe  ................
[    1.922693] <3>00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8  ................
[    1.922697] 
[    2.024074] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 202
[    2.024080] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    2.024086] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 a2 28 00 00  ........"d...(..
[    2.024091] <3>12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
[    2.024097] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
[    2.024102] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    2.024107] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X& 
[    2.024113] <3>5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00  ]#..............
[    2.024118] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe  ................
[    2.024123] <3>00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8  ................
[    2.024127] 
[    2.125466] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 202
[    2.125472] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[    2.125478] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 a2 28 00 00  ........"d...(..
[    2.125484] <3>12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
[    2.125489] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
[    2.125494] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    2.125500] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X& 
[    2.125505] <3>5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00  ]#..............
[    2.125511] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe  ................
[    2.125516] <3>00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 c8  ................
[    2.125520] 
[    2.125527] i915 0000:00:02.0: LVDS-1: EDID block 0 invalid.

I am not too sure what it means and it could explain my issues.

Thanks for any help

Eric

---

