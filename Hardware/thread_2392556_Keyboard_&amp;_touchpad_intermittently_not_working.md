---
title: "Keyboard &amp; touchpad intermittently not working after unlocking screen"
date: 2018-05-22
forum: Hardware
---

### Post by kazakore on 2018-05-22
I've had this problem with my touchpad in the past (since 16.04 at least), which I think I've finally solved yesterday by adding a line to my kernel parameters in Grub but since installing 18.04 I am also getting it with the keyboard. Luckily it comes back usually when performing certain functions with the mouse (clicking of the workspace selector in the Panel to change workspace fixes it, I haven't found any other action that works regularly. Changing tty also works but it doesn't work back in xwindows when I go back to tty7 but at least it gives me the chance to force a reboot.) Now I've fixed the touchpad issue hopefully I wont get both locked at the same time again but it would be good to track down the cause of it. Not had any joy generally searching for solutions, maybe I'm using the wrong terms....

Here is the dmesg output from when it failed just now.

```
[24260.274257] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
[24260.274259] atkbd serio0: Use 'setkeycodes e005 <keycode>' to make it known.
[32320.777064] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
[32320.777067] atkbd serio0: Use 'setkeycodes e005 <keycode>' to make it known.
[33896.609884] wlo1: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-22)
[33911.792702] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[33968.914623] wlo1: authenticate with 00:50:7f:73:d3:00
[33968.920686] wlo1: send auth to 00:50:7f:73:d3:00 (try 1/3)
[33968.923634] wlo1: authenticated
[33968.924397] wlo1: associate with 00:50:7f:73:d3:00 (try 1/3)
[33968.928239] wlo1: RX AssocResp from 00:50:7f:73:d3:00 (capab=0x411 status=0 aid=2)
[33968.932188] wlo1: associated
[33969.211517] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[34196.870396] wlo1: AP 00:50:7f:73:d3:00 changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[34341.248202] perf: interrupt took too long (5022 > 5005), lowering kernel.perf_event_max_sample_rate to 39000

```

The atkdb lines always appear when I close and open the lid, whether the keyboard then freezes or not. Almost everything else is wifi related. I've checked the perf interrupt thing the other day and as far as I could tell it is not related at all.


Xorg.0.log output over the same timeframe. Not sure what to look for here but I believe it handles most keyboard events....
```
[ 18057.908] (II) event15 - HP WMI hotkeys: device is a switch device
[ 24627.110] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 24627.953] (II) event2  - Power Button: device removed
[ 24627.966] (II) event4  - Video Bus: device removed
[ 24627.982] (II) event0  - Sleep Button: device removed
[ 24627.998] (II) event3  - AT Translated Set 2 keyboard: device removed
[ 24628.006] (II) event5  - PS/2 Generic Mouse: device removed
[ 24628.059] (II) event7  - HP Wireless hotkeys: device removed
[ 24628.086] (II) event15 - HP WMI hotkeys: device removed
[ 24628.102] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 24633.444] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 24633.444] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 24633.512] (II) event2  - Power Button: is tagged by udev as: Keyboard
[ 24633.512] (II) event2  - Power Button: device is a keyboard
[ 24633.514] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[ 24633.514] (II) event4  - Video Bus: device is a keyboard
[ 24633.515] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[ 24633.515] (II) event0  - Sleep Button: device is a keyboard
[ 24633.516] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[ 24633.516] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[ 24633.516] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 24633.516] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 24633.516] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 24633.517] (II) event7  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[ 24633.517] (II) event7  - HP Wireless hotkeys: device is a keyboard
[ 24633.517] (II) event15 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[ 24633.517] (II) event15 - HP WMI hotkeys: device is a keyboard
[ 24633.517] (II) event15 - HP WMI hotkeys: device is a switch device
[ 36102.605] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 36103.951] (II) event2  - Power Button: device removed
[ 36103.957] (II) event4  - Video Bus: device removed
[ 36103.974] (II) event0  - Sleep Button: device removed
[ 36103.991] (II) event3  - AT Translated Set 2 keyboard: device removed
[ 36104.007] (II) event5  - PS/2 Generic Mouse: device removed
[ 36104.065] (II) event7  - HP Wireless hotkeys: device removed
[ 36104.100] (II) event15 - HP WMI hotkeys: device removed
[ 36104.116] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 36183.394] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 36183.394] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 36183.479] (II) event2  - Power Button: is tagged by udev as: Keyboard
[ 36183.479] (II) event2  - Power Button: device is a keyboard
[ 36183.480] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[ 36183.480] (II) event4  - Video Bus: device is a keyboard
[ 36183.481] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[ 36183.481] (II) event0  - Sleep Button: device is a keyboard
[ 36183.482] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[ 36183.482] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[ 36183.483] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 36183.483] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 36183.483] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 36183.484] (II) event7  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[ 36183.484] (II) event7  - HP Wireless hotkeys: device is a keyboard
[ 36183.485] (II) event15 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[ 36183.485] (II) event15 - HP WMI hotkeys: device is a keyboard
[ 36183.485] (II) event15 - HP WMI hotkeys: device is a switch device

```

Thanks.

---

### Post by kazakore on 2018-05-23
> **kazakore said:**
>  Now I've fixed the touchpad issue.....


I was wrong, touchpad still stops working on occasion too! :(

dmesg for lid closed over night
```
[ 4503.295588] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
[ 4503.295591] atkbd serio0: Use 'setkeycodes e005 <keycode>' to make it known.
[ 4512.734488] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[ 4512.756342] wlo1: authenticate with f4:6b:ef:0e:8f:43
[ 4512.762622] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[ 4512.765185] wlo1: authenticated
[ 4512.765754] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[ 4512.766716] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[ 4512.768507] wlo1: associated
[ 4512.806933] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[ 5786.910175] perf: interrupt took too long (4167 > 4096), lowering kernel.perf_event_max_sample_rate to 48000
[ 7616.873759] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[ 7616.883273] wlo1: authenticate with f4:6b:ef:0e:8f:42
[ 7616.887453] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[ 7616.890558] wlo1: authenticated
[ 7616.892157] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[ 7616.895609] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[ 7616.896544] wlo1: associated
[11493.981090] perf: interrupt took too long (5218 > 5208), lowering kernel.perf_event_max_sample_rate to 38000
[31612.432732] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[31612.449005] wlo1: authenticate with f4:6b:ef:0e:8f:43
[31612.455316] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[31612.458358] wlo1: authenticated
[31612.459396] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[31612.460340] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[31612.462022] wlo1: associated
[31612.480525] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[33039.084462] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[33039.094000] wlo1: authenticate with f4:6b:ef:0e:8f:42
[33039.098810] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[33039.102330] wlo1: authenticated
[33039.103434] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[33039.106915] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[33039.108606] wlo1: associated
[33071.263233] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[33071.275673] wlo1: authenticate with f4:6b:ef:0e:8f:43
[33071.282114] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[33071.283610] wlo1: authenticated
[33071.284126] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[33071.285124] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[33071.287395] wlo1: associated
[33071.311029] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[34306.370979] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[34306.382758] wlo1: authenticate with f4:6b:ef:0e:8f:42
[34306.387497] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[34306.391617] wlo1: authenticated
[34306.392460] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[34306.401062] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[34306.403260] wlo1: associated
[34337.577956] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[34337.589993] wlo1: authenticate with f4:6b:ef:0e:8f:43
[34337.596951] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[34337.599171] wlo1: authenticated
[34337.600228] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[34337.601207] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[34337.603969] wlo1: associated
[34337.624081] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[36396.616377] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[36396.625747] wlo1: authenticate with f4:6b:ef:0e:8f:42
[36396.630010] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[36396.634969] wlo1: authenticated
[36396.635707] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[36396.639224] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[36396.640824] wlo1: associated
[36406.649473] wlo1: deauthenticated from f4:6b:ef:0e:8f:42 (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[36406.722682] wlo1: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-22)
[36406.824726] wlo1: authenticate with f4:6b:ef:0e:8f:43
[36406.832445] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[36406.834018] wlo1: authenticated
[36406.834666] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[36406.835639] wlo1: RX AssocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[36406.837906] wlo1: associated
[36406.877621] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[37135.760300] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[37135.770347] wlo1: authenticate with f4:6b:ef:0e:8f:42
[37135.774799] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[37135.777381] wlo1: authenticated
[37135.778559] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[37135.782055] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[37135.783674] wlo1: associated
[37166.970614] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[37166.979063] wlo1: authenticate with f4:6b:ef:0e:8f:43
[37166.985664] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[37166.987334] wlo1: authenticated
[37166.988344] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[37166.989308] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[37166.991363] wlo1: associated
[37167.013327] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
[39224.319509] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[39224.331042] wlo1: authenticate with f4:6b:ef:0e:8f:42
[39224.335791] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[39224.338915] wlo1: authenticated
[39224.339546] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[39224.342976] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[39224.344582] wlo1: associated
[39653.669422] wlo1: disconnect from AP f4:6b:ef:0e:8f:42 for new auth to f4:6b:ef:0e:8f:43
[39653.683047] wlo1: authenticate with f4:6b:ef:0e:8f:43
[39653.688068] wlo1: send auth to f4:6b:ef:0e:8f:43 (try 1/3)
[39653.692530] wlo1: authenticated
[39653.692745] wlo1: associate with f4:6b:ef:0e:8f:43 (try 1/3)
[39653.693691] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:43 (capab=0x11 status=0 aid=1)
[39653.695482] wlo1: associated
[39653.762981] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by f4:6b:ef:0e:8f:43
```

Then I closed and opened again as it occasionally seems to work before running removing and restarting psmouse with modprobe, which fixed it but only on second attempt.
```
[39678.922997] atkbd serio0: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
[39678.923000] atkbd serio0: Use 'setkeycodes e005 <keycode>' to make it known.
[39719.382886] wlo1: disconnect from AP f4:6b:ef:0e:8f:43 for new auth to f4:6b:ef:0e:8f:42
[39719.396629] wlo1: authenticate with f4:6b:ef:0e:8f:42
[39719.401719] wlo1: send auth to f4:6b:ef:0e:8f:42 (try 1/3)
[39719.405922] wlo1: authenticated
[39719.407028] wlo1: associate with f4:6b:ef:0e:8f:42 (try 1/3)
[39719.410464] wlo1: RX ReassocResp from f4:6b:ef:0e:8f:42 (capab=0x411 status=0 aid=2)
[39719.412107] wlo1: associated
[39777.387664] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input26
[39778.172111] psmouse serio3: synaptics: queried max coordinates: x [..5668], y [..4762]
[39778.205718] psmouse serio3: synaptics: queried min coordinates: x [1360..], y [1160..]
[39778.205721] psmouse serio3: synaptics: Trying to set up SMBus access
[39778.208415] psmouse serio3: synaptics: SMbus companion is not ready yet
[39778.267063] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26800/0x0, board id: 2768, fw id: 1658220
[39778.304538] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input27
[39779.132324] psmouse serio3: synaptics: queried max coordinates: x [..5668], y [..4762]
[39779.165918] psmouse serio3: synaptics: queried min coordinates: x [1360..], y [1160..]
[39779.165920] psmouse serio3: synaptics: Trying to set up SMBus access
[39779.168617] psmouse serio3: synaptics: SMbus companion is not ready yet
[39779.229757] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26800/0x0, board id: 2768, fw id: 1658220
[39779.266926] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input30
[39790.391924] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input242
[39791.173168] psmouse serio3: synaptics: queried max coordinates: x [..5668], y [..4762]
[39791.207733] psmouse serio3: synaptics: queried min coordinates: x [1360..], y [1160..]
[39791.207735] psmouse serio3: synaptics: Trying to set up SMBus access
[39791.210485] psmouse serio3: synaptics: SMbus companion is not ready yet
[39791.268289] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26800/0x0, board id: 2768, fw id: 1658220
[39791.304624] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input243
[39792.146736] psmouse serio3: synaptics: queried max coordinates: x [..5668], y [..4762]
[39792.182307] psmouse serio3: synaptics: queried min coordinates: x [1360..], y [1160..]
[39792.182309] psmouse serio3: synaptics: Trying to set up SMBus access
[39792.185633] psmouse serio3: synaptics: SMbus companion is not ready yet
[39792.242366] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26800/0x0, board id: 2768, fw id: 1658220
[39792.278065] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input246
```

Seems to me the only bits related to the touchpad are from me getting it working again, nothing related to the failure.


And Xorg.0.log:
```

[    11.364] (II) intel(0): Modeline "1920x1080"x0.0  141.00  1920 1936 1952 2104  1080 1083 1097 1116 -hsync -vsync (67.0 kHz eP)
[ 39652.124] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 39652.950] (II) event2  - Power Button: device removed
[ 39652.954] (II) event4  - Video Bus: device removed
[ 39652.960] (II) event0  - Sleep Button: device removed
[ 39652.971] (II) event3  - AT Translated Set 2 keyboard: device removed
[ 39652.983] (II) event5  - PS/2 Generic Mouse: device removed
[ 39653.043] (II) event7  - HP Wireless hotkeys: device removed
[ 39653.075] (II) event15 - HP WMI hotkeys: device removed
[ 39653.091] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 39668.808] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 39668.808] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 39668.892] (II) event2  - Power Button: is tagged by udev as: Keyboard
[ 39668.892] (II) event2  - Power Button: device is a keyboard
[ 39668.893] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[ 39668.893] (II) event4  - Video Bus: device is a keyboard
[ 39668.893] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[ 39668.893] (II) event0  - Sleep Button: device is a keyboard
[ 39668.894] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[ 39668.894] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[ 39668.894] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39668.894] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39668.894] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39668.895] (II) event7  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[ 39668.895] (II) event7  - HP Wireless hotkeys: device is a keyboard
[ 39668.895] (II) event15 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[ 39668.895] (II) event15 - HP WMI hotkeys: device is a keyboard
[ 39668.895] (II) event15 - HP WMI hotkeys: device is a switch device
```
```

[ 39685.608] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 39686.950] (II) event2  - Power Button: device removed
[ 39686.956] (II) event4  - Video Bus: device removed
[ 39686.971] (II) event0  - Sleep Button: device removed
[ 39686.984] (II) event3  - AT Translated Set 2 keyboard: device removed
[ 39687.001] (II) event5  - PS/2 Generic Mouse: device removed
[ 39687.051] (II) event7  - HP Wireless hotkeys: device removed
[ 39687.081] (II) event15 - HP WMI hotkeys: device removed
[ 39687.094] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 39706.661] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 39706.661] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 39706.746] (II) event2  - Power Button: is tagged by udev as: Keyboard
[ 39706.746] (II) event2  - Power Button: device is a keyboard
[ 39706.746] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[ 39706.746] (II) event4  - Video Bus: device is a keyboard
[ 39706.747] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[ 39706.747] (II) event0  - Sleep Button: device is a keyboard
[ 39706.747] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[ 39706.747] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[ 39706.748] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39706.748] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39706.748] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39706.748] (II) event7  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[ 39706.748] (II) event7  - HP Wireless hotkeys: device is a keyboard
[ 39706.749] (II) event15 - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[ 39706.749] (II) event15 - HP WMI hotkeys: device is a keyboard
[ 39706.749] (II) event15 - HP WMI hotkeys: device is a switch device
[ 39741.196] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39766.798] (II) config/udev: removing device PS/2 Generic Mouse
[ 39766.798] (II) event5  - PS/2 Generic Mouse: device removed
[ 39766.808] (II) UnloadModule: "libinput"
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.858] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39766.859] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[ 39766.876] (II) UnloadModule: "synaptics"
[ 39776.861] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[ 39776.861] (II) No input driver specified, ignoring this device.
[ 39776.861] (II) This device may have been added with another device file.
[ 39776.876] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event5)
[ 39776.876] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[ 39776.876] (**) PS/2 Generic Mouse: Applying InputClass "libinput pointer catchall"
[ 39776.876] (II) Using input driver 'libinput' for 'PS/2 Generic Mouse'
[ 39776.876] (**) PS/2 Generic Mouse: always reports core events
[ 39776.876] (**) Option "Device" "/dev/input/event5"
[ 39776.876] (**) Option "_source" "server/udev"
[ 39776.876] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39776.876] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39776.876] (II) event5  - PS/2 Generic Mouse: device removed
[ 39776.886] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input26/event5"
[ 39776.886] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 10)
[ 39776.886] (**) Option "AccelerationScheme" "none"
[ 39776.886] (**) PS/2 Generic Mouse: (accel) selected scheme none/0
[ 39776.886] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[ 39776.886] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[ 39776.887] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39776.887] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39777.778] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 39777.778] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 39777.805] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[ 39777.805] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 39777.805] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[ 39777.805] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 39777.805] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 39777.805] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 39777.805] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39777.805] (**) Option "Device" "/dev/input/event6"
[ 39777.817] (EE) xf86OpenSerial: Cannot open device /dev/input/event6
        No such device.
[ 39777.817] (EE) synaptics: SynPS/2 Synaptics TouchPad: Synaptics driver unable to open device
[ 39777.817] (EE) PreInit returned 11 for "SynPS/2 Synaptics TouchPad"
[ 39777.817] (II) UnloadModule: "synaptics"
[ 39778.741] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 39778.741] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 39778.760] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[ 39778.760] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 39778.760] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[ 39778.760] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 39778.760] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 39778.760] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 39778.760] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39778.760] (**) Option "Device" "/dev/input/event6"
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1360 - 5668 (res 43)
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1160 - 4762 (res 70)
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[ 39778.782] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39778.782] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39778.807] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio3/input/input30/event6"
[ 39778.807] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[ 39778.807] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 39778.807] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[ 39778.807] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[ 39778.807] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 39778.807] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 39778.807] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 39778.807] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 39778.807] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39781.537] (II) config/udev: removing device PS/2 Generic Mouse
[ 39781.537] (II) event5  - PS/2 Generic Mouse: device removed
[ 39781.543] (II) UnloadModule: "libinput"
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.583] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (EE) SynPS/2 Synaptics TouchPad: Read error 19
[ 39781.584] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[ 39781.605] (II) UnloadModule: "synaptics"
[ 39789.865] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[ 39789.865] (II) No input driver specified, ignoring this device.
[ 39789.865] (II) This device may have been added with another device file.
[ 39789.878] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event5)
[ 39789.878] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[ 39789.878] (**) PS/2 Generic Mouse: Applying InputClass "libinput pointer catchall"
[ 39789.878] (II) Using input driver 'libinput' for 'PS/2 Generic Mouse'
[ 39789.878] (**) PS/2 Generic Mouse: always reports core events
[ 39789.878] (**) Option "Device" "/dev/input/event5"
[ 39789.878] (**) Option "_source" "server/udev"
[ 39789.879] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39789.879] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39789.879] (II) event5  - PS/2 Generic Mouse: device removed
[ 39789.898] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input242/event5"
[ 39789.898] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 10)
[ 39789.898] (**) Option "AccelerationScheme" "none"
[ 39789.898] (**) PS/2 Generic Mouse: (accel) selected scheme none/0
[ 39789.898] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[ 39789.898] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[ 39789.899] (II) event5  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[ 39789.899] (II) event5  - PS/2 Generic Mouse: device is a pointer
[ 39790.778] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 39790.778] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 39790.797] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[ 39790.797] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 39790.797] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[ 39790.797] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 39790.797] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 39790.797] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 39790.797] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39790.797] (**) Option "Device" "/dev/input/event6"
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1360 - 5668 (res 43)
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1160 - 4762 (res 70)
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[ 39790.805] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39790.805] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39790.811] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio3/input/input243/event6"
[ 39790.811] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[ 39790.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 39790.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[ 39790.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[ 39790.811] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 39790.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 39790.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 39790.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 39790.817] (EE) xf86OpenSerial: Cannot open device /dev/input/event6
        No such device.
[ 39790.817] (WW) synaptics: SynPS/2 Synaptics TouchPad: cannot open input device
[ 39790.817] [dix] couldn't enable device 11
[ 39790.817] (EE) Couldn't init device "SynPS/2 Synaptics TouchPad"
[ 39790.819] (II) UnloadModule: "synaptics"
[ 39791.752] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 39791.752] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 39791.768] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[ 39791.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 39791.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[ 39791.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 39791.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 39791.769] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 39791.769] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39791.769] (**) Option "Device" "/dev/input/event6"
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1360 - 5668 (res 43)
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1160 - 4762 (res 70)
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[ 39791.780] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 39791.780] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 39791.800] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio3/input/input246/event6"
[ 39791.800] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[ 39791.800] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 39791.800] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[ 39791.800] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[ 39791.800] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 39791.800] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 39791.800] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 39791.800] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 39791.800] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

```


Nothing in the top section, which is from  before I perform steps to correct it, look like an error to me.......

---

### Post by kazakore on 2018-05-23
Realised I've forgotten to give any system details to go with the logs. Also realised I am fairly sure it is related to xflock4 of XFCE so probably not hardware related so maybe should have been posted in the DE section....

Computer is a HP 840 G2.
Now running Ubuntu Studio 18.04
The touchpad is using Synaptic as this was a fix done by Xubuntu to get al functionality back but I had to manually change it on Studio.

What I thought had fixed the touchpad issue but hasn't is adding this to the /etc/defaults/grub and rebuilding grub: psmouse.synaptics_intertouch=1 as I got an error message than pointed to this as a solution from searching the web.

I've had the touchpad issue across three or four different laptops running Studio since 14.04 and have never solved it, rather in the end I have given up having my laptop ever lock itself which is an obvious security issue! I've thought I've fixed it a few times but as it's intermittent I've always been mistaken thus far....

The keyboard issue is new to 18.04.

---

